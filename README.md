# PatikaSQL--Ödev12

--1. Film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film olduğunu gösterir.

SELECT COUNT(*) FROM film WHERE length > (SELECT AVG(length) FROM film);

--2. Film tablosunda en yüksek rental_rate değerine sahip kaç tane film olduğunu gösterir.

SELECT COUNT(*) FROM film WHERE rental_rate = (SELECT MAX(rental_rate) FROM film);

--3. Film tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralar.

SELECT title, rental_rate, replacement_cost FROM film WHERE rental_rate = (SELECT MIN(rental_rate) FROM film) AND replacement_cost = (SELECT MIN(replacement_cost) FROM film);

--4. Payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralar.

SELECT customer.first_name, customer.last_name, COUNT(*) as total_payments FROM payment JOIN customer ON payment.customer_id = customer.customer_id GROUP BY payment.customer_id ORDER BY total_payments DESC LIMIT 10;
