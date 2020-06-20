# Курсовой проект по предмету "Инфраструктура больших данных"

Репозиторий содержит код проекта "Анализ влияния развития уровня инфраструктуры на стоимость квартир в Санкт-Петербурге". Проект реализован в рамках курса "Инфраструктура больших данных" университета ИТМО, весенний семестр 2020 года.

## Авторы проекта:
* Анастасия Филатова, C41323
* Анастасия Белых, C41323
* Александра Чаликова, C41323
* Марк Мережников, C41324

## Краткое описание проекта
Проект состоит из трех основных частей:
* Сбор данных
* Организация хранения и работы с данными
* Анализ данных

Ниже приводится более подробное описание каждой из частей и структуры файлов с кодом для этой части.

Каждый файл оформлен для удобства чтения и понимания основной функциональности. Для получения подробной информации по любой части проекта можно прочитать содержимое соответствующих файлов.

## Часть 1. Сбор данных

Мы работали с данными о новостройках Санкт-Петербурга. Для этого мы собирали актуальную на март 2020 года (и обновляли в конце мая 2020 года) информацию о предложениях о покупке квартир в новых жилых комплексах Санкт-Петербурга, а также информацию об объектах инфраструктуры.

Для сбора данных мы использовали два источника
* Раздел "Новостройки" сайта `Cian.ru` - для сбора предложений
* `Yandex.Maps`, используя API Поиска по организациям - для сбора информации об объектах инфраструктуры

Все файлы с кодом сбора данных находятся в папке `data_gathering`.

### Структура папки `data_gathering`.
Файлы перечислены в логическом порядке, для корректной работы порядок запуска кода в них необходимо сохранить.
* `new_complexes_information_grabber.ipynb` - ноутбук с кодом функций извлечения информации о новостройках (название, id жк и id застройщика) с сайта Циан
* `infrastructure_information_extraction.ipynb` - ноутбук с кодом функций извлечения информации о координатах жк и полным кодом извлечения данных об инфраструктуре с использованием API Поиска по организациям
* `links_generator.ipynb` - ноутбук с кодом функции, генерирующей ссылки на предложения о продаже квартир в новых жк
* `offers_grabber.ipynb` - ноутбук с кодом функций извлечения данных о предложениях о продаже квартир с сайта Циан
* `extracted_info_processing.ipynb` - ноутбук с кодом функций обработки полученных данных о предложениях 

## Часть 2. Организация распределенного хранения и обработки данных

Для организации распределенного хранилища мы использовали два сервера Amazon, которые мы объединили в кластер и на которые установили СУБД ClickHouse.

Ноутбук `clickhouse_database_creation.ipynb` содержит код запросов на создание базы данных, создание таблиц и заполнение их данными, полученными в процессе сбора данных, описанном в части 1.

## Часть 3. Анализ данных

Анализ данных состоит из двух частей:
* предварительный анализ данных, чтобы разобраться в структуре перед основным анализом, он реализован в ноутбуке `exploratory_data_analysis.ipynb`
* основной анализ данных, в котором решаются ключевые задачи - он реализован в ноутбуке `main_data_analysis.ipynb`

## Данные парсинга

Если вы хотите воспользоваться результатами анализа, но часть извлечения данных вам не интересна - вы можете использовать наши подготовленные файлы с данными - они находятся в папке `final_data`. 
