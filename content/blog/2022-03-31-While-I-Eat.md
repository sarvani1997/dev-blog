+++
title = "While I Eat - A Web App for All Streaming Services"
[taxonomies]
tags = [ "react", "beginner" ]
+++

While I Eat is a web application to plan what movies/TV shows to watch in a week/month. This web App allows you to browse movies/TV shows and add it to your watchlist or calendar.
You can share the details of the show with your friends/family to watch them together.

## Tech Stack

### Frontend

1. Build Tool: Vite
2. Javascript Library: React
3. Styling: Bootstrap, Reach UI
4. API: The Movie DB
5. HTTP Request: Axois

### Backend

1. Database: SQlite
2. Framework: Express
3. ORM: Sequelize
4. Query prettifier: sql-log-prettifier

## Plan

1. Shortlist the required APIs to fetch all movies/TV shows.
2. Render the data and add css.

## 1. Shortlist the required APIs to fetch all movies/TV shows

Initially, registration for an API key is required. Once an API key is issued, it is used as a query parameter for making API requests.

Here, in this application, I want to fetch all movies according to their popularity.

```
https://api.themoviedb.org/3/discover/movie?api_key=<<api_key>>&sort_by=popularity.desc
```

Now, to filter the data a few parameters like `language`, `genre` and `watch providers` are added as query parameters to the above API.

```
https://api.themoviedb.org/3/discover/movie?api_key=<<api_key>>&sort_by=popularity.desc&with_genres=<<genre>>&with_original_language=<<lang>>&watch_region=IN&with_watch_providers=<<providers>>
```

Some elements of the API require some knowledge of configuration data. Here are the URLs

#### Languages

```
https://api.themoviedb.org/3/configuration/languages?api_key=<<api_key>>
```

#### Watch Providers

These watch providers Id's should be combined with watch regions to filter results by a specific watch provider in a specific region.

##### Regions

```
https://api.themoviedb.org/3/watch/providers/regions?api_key=<<api_key>>
```

here, I choose watch region as `IN` (India)

##### Movie providers

```
https://api.themoviedb.org/3/watch/providers/movie?api_key=<<api_key>>&watch_region=IN
```

#### Pagination

For, pagination add `page` as a query parameter.

```
https://api.themoviedb.org/3/discover/movie?api_key=<<api_key>>&page=1
```

For TV shows data replace `movie` with `tv`
