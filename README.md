# Data Modeling with PostGres
![Cover](image.jpg)

### Introduction

A music streaming startup, **Sparkify**, wants to ***analyze song and user data*** they've collected from their app. In particular, the company wants to see ***which songs are being listened to***, but the data they have is not in a usable format for queries.

**Problem**: The data Sparkify does have is held in a serises o fJSON logs and JSON metadata, and the company needs to be able to access the data more readily.


**Solution**: Using the JSON files, python scripts and PostGres, I built a star schema for song play analysis queries.

### Star Schema Tables

#### Fact Table
**songplays**: records in log data associated with song play
 - songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
 
#### Dimension Tables
**users**: users in the app
 - user_id, first_name, last_name, gender, level

**songs**: songs in the database
 - song_id, title, artist_id, year, duration
 
**artists**: artists in the database
 - artist_id, name, location, latitude, longitude
 
**time**: timestamps of songplay records in specific time units
 - start_time, hour, day, week, month, year, weekday
 
 
 ### ETL Process
 
 Using etl.py, **extract, transform, & load processes** populate the songs & artists tables with data from JSON song files, and the time & users tables with data from JSON log files. I use a SELECT query to pull song and artist data from the corresponding tables and combines this with the JSON metadata to create the songplays fact table.