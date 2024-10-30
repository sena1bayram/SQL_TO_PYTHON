**SQL'den Python'a Dönüşüm Projesi**

***Proje Amacı***: Bu proje, SQL sorgularını Python koduna dönüştürmeyi ve Pandas kütüphanesi kullanarak veri analizi yapmayı göstermektedir. Temel amaç, SQL sorgularının Python'da nasıl yazılacağını ve veritabanı işlemlerinin Pandas DataFrame'leri ile nasıl gerçekleştirileceğini örneklemektir.

***Temel Dönüşüm Örnekleri***

***1. Basit Sorgu Dönüşümü***

SQL:
SELECT * FROM rental;

Python:
import pandas as pd
import sqlite3

conn = sqlite3.connect('sqlite-sakila.db')
rental_df = pd.read_sql_query("SELECT * from rental", conn)

***2. Birleştirme (JOIN) İşlemleri***

SQL:
SELECT film.title, actor.first_name, actor.last_name

FROM film

JOIN film_actor ON film.film_id = film_actor.film_id

JOIN actor ON film_actor.actor_id = actor.actor_id;


Python:
film_actor_info = df['film'].merge(df['film_actor'], on='film_id') \
                           .merge(df['actor'], on='actor_id')
result = film_actor_info[['title', 'first_name', 'last_name']]

***3. Gruplama ve Toplama İşlemleri***

SQL:
SELECT category.name, COUNT(*) as film_count

FROM category

JOIN film_category ON category.category_id = film_category.category_id

GROUP BY category.name;

Python:
category_counts = df['category'].merge(df['film_category'], on='category_id') \
                               .groupby('name').size() \
                               .reset_index(name='film_count')


***Önemli Noktalar***

***Veritabanı Bağlantısı:***

* SQLite veritabanına bağlantı kurma
* Pandas ile SQL sorgularını çalıştırma
* Veri Manipülasyonu:
* DataFrame'ler arası birleştirme işlemleri
* Gruplama ve toplama fonksiyonları
* Veri filtreleme ve seçme işlemleri
  
***Pandas Avantajları:***

* Daha okunabilir kod
* Veri manipülasyonu için zengin fonksiyonlar
* Verimli veri işleme kapasitesi
  
***Gereksinimler***

* Python 3.x
* Pandas
* SQLite3
* Jupyter Notebook
  
***Kullanım***

* Veritabanı bağlantısını oluştur
* SQL sorgularını Python/Pandas koduna çevir
* DataFrame'ler üzerinde gerekli manipülasyonları gerçekleştir
* Sonuçları analiz et ve görselleştir
  
Bu proje, SQL bilgisi olan geliştiricilerin Python'da veri analizi yapabilmeleri için bir köprü görevi görmektedir. SQL sorgularını Python'da nasıl yazacaklarını öğrenerek, Pandas'ın güçlü veri analizi özelliklerinden faydalanabilirler.






















                               
