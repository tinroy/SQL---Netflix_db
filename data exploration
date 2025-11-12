-- exploration queries
-- Count how many titles are in the database.
select count(*)
from titles;

-- How many Movies vs TV Shows are there?
select type, count(*) as titles_count
from titles
group by type;

-- List the top 10 most recent releases.
select title,release_year
from titles
order by release_year desc
limit 10;

-- Find the average IMDb score by type (Movie vs TV Show)
select type, round(avg(imdb_score),1) as Avg_IMDB_score
from titles
group by type;

-- Which age certification has the highest average IMDb score?
select rating, max(Avg_IMDB_score)
from
(select rating, round(avg(imdb_score),1) as Avg_IMDB_score
from titles
group by rating) avg_table;

-- Find the top 10 longest movies.
select title, runtime
from titles
where type='Movie'
order by runtime desc
limit 10;

-- Which actors have appeared in the most titles?
select name,count(cr.id) as appearances
from credits cr
join titles ti
on cr.id = ti.id
group by name
order by appearances desc;

select name, count(id) as appearances
from credits
group by name
order by appearances desc;

-- List actors who worked in high-rated titles (IMDb > 8)
select name, title, imdb_score
from credits cr
join titles ti
on cr.id = ti.id
where imdb_score>8
order by imdb_score desc;

-- Find average IMDb score by rating
select rating,round(avg(imdb_score),1) average_imdb_score
from titles
group by rating
order by average_imdb_score desc;

-- Who are the top actors by number of high-rated titles (IMDb ≥ 8)?
select cr.name, count(score.id) as cnt
from credits cr
join
(select id
from titles
where imdb_score>=8) score
on cr.id=score.id
group by cr.name
order by cnt desc;

select cr.name, count(ti.id) as cnt
from credits cr
join titles ti
on cr.id = ti.id
where ti.imdb_score>=8
group by cr.name
order by cnt desc;

-- For each release year, what’s the average IMDb rating of all titles?
select release_year, round(avg(imdb_score),1) avg_score
from titles
group by release_year
order by avg_score desc;

