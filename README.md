**Movie Ticket Booking System – MySQL Database Documentation**
1. System Overview
The Movie Ticket Booking System is a simplified MySQL-based backend project designed to manage
essential movie booking operations.
It allows storing and retrieving information about movies, users, shows, seats, and bookings.
This documentation provides a concise but industry-style technical specification suitable for academic
or small-scale professional use.

2. System Scope
The system covers:-
User information storage- Movie information management- Show scheduling for movies- Seat management- Ticket booking records
The purpose is to demonstrate a clean relational database design with minimal required tables and
optimized SQL operations.

3. Functional Requirements
FR1: The system shall store user account details (name, email, password).
FR2: The system shall store movie metadata (title, genre, duration).
FR3: The system shall maintain show schedules for each movie.
FR4: The system shall allow assigning seats to bookings.
FR5: The system shall retrieve available seats for any show.
FR6: The system shall store booking information linked to users and shows.

4. Non-Functional Requirements
NFR1: Database must ensure data consistency using primary and foreign keys.
NFR2: Queries must execute within acceptable performance limits for small datasets.
NFR3: System should follow standard normalization practices (up to 3NF).
NFR4: MySQL must be used as the database engine.

5. ER Diagram (Textual Representation)
Entities:-
USERS(user_id, name, email, password)- MOVIES(movie_id, title, genre, duration)- SHOWS(show_id, movie_id, show_date, show_time, price)- SEATS(seat_id, seat_number)- BOOKINGS(booking_id, user_id, show_id, seat_id, booking_time)
Relationships:-
A USER may have multiple BOOKINGS.- A MOVIE may have multiple SHOWS.- A SHOW may have multiple BOOKINGS.- A SEAT can be booked many times, but only once per show.- BOOKINGS link USERS → SHOWS → SEATS.

6. Database Schema (MySQL) users:
CREATE TABLE users (
user_id INT PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(100),
email VARCHAR(100) UNIQUE,
password VARCHAR(100)
);

movies:
CREATE TABLE movies (
movie_id INT PRIMARY KEY AUTO_INCREMENT,
title VARCHAR(150),
genre VARCHAR(50),
duration INT
);

shows:
CREATE TABLE shows (
show_id INT PRIMARY KEY AUTO_INCREMENT,
movie_id INT,
show_date DATE,
show_time TIME,
price DECIMAL(6,2),
FOREIGN KEY (movie_id) REFERENCES movies(movie_id)
);

seats:
CREATE TABLE seats (
seat_id INT PRIMARY KEY AUTO_INCREMENT,
seat_number VARCHAR(10)
);

bookings:
CREATE TABLE bookings (
booking_id INT PRIMARY KEY AUTO_INCREMENT,
user_id INT,
show_id INT,
seat_id INT,
booking_time DATETIME,
FOREIGN KEY (user_id) REFERENCES users(user_id),
FOREIGN KEY (show_id) REFERENCES shows(show_id),
FOREIGN KEY (seat_id) REFERENCES seats(seat_id)
);


**Summary**
This document provides a compact industrial-style technical specification for a MySQL-based Movie
Ticket Booking System.
It includes requirements, schema design, relationships, and essential SQL queries, suitable for
academic submission or small-scale professional demonstration.











