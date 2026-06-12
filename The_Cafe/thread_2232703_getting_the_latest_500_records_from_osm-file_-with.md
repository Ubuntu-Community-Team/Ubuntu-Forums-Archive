---
title: "getting the latest 500 records from osm-file -with timestamp"
date: 2014-07-03
forum: The Cafe
---

### Post by dilbert_one on 2014-07-03
i want to gather the latest 100 records that have the amenity=school - school from

a. south-america -(yes - the whole continent) 
b. Africa 
c. the planet - (guess that my notebook do not will do this job - the file is toooo big.

So as a first step i am willing to start with South-America.

According the manual here [http://m.m.i24.cc/osmconvert.c](http://m.m.i24.cc/osmconvert.c) I THINK THAT i can use some of the following terms to get the right data out of the bunch of data.

"--timestamp=<date_time>   add a timestamp to the data\n"
"--timestamp=NOW-<seconds> add a timestamp in seconds before now\n"
"--out-timestamp           **output the file\'s timestamp, nothing else\n"**

and if i want to gather all the results that contain a webseite then

a.  i reduce the new entries and records to a minimum - 
note we have approx 1000 new records..
b.  the question is : how to name this condition - " have a website" ?

i want to do this with osmconvert.... any and all help will be greatly appreciated. Question: i wonder where i can use the drop-statement. If it will be used very early then i can limit the amount of data that has to be parsed. What do you think !? Does this make sense..!?

See below - my first trials which are very very general... and not very sophisticatde --- lo-level-processing;-)


i am pretty new to Geographic-information Systems so do not bear with me if i ask newby questions: i am interested in gatherin information on schools Some days before i have heard that it is interesting to have a closer look at the taginfo-site (see below): i have question: what does this mean [https://taginfo.openstreetmap.org/tags/amenity=school](https://taginfo.openstreetmap.org/tags/amenity=school)

here we have two requests on the above site:

see the details:

```

593&#8201;454 - at 30 th of june 
593&#8201;319
593&#8201;194
592 853
592&#8201;443 - at 24 th of june


```

1000 records

you see: the results differs: approx 1000 x (entries, records or some what)

questions:

a. is it true that we can see the diff - that means how the entries of schools grow? b. is there a total growth of records (!!!) of schools or does the this mean - some records have been changed!? c. can i grab the neewst ones -- that are the newest entires with osmonvert?

look forward to hear from you

btw i have this code up and running...

```

 wget http://download.geofabrik.de/south-america/colombia-latest.osm.pbf
./osmconvert colombia-latest.osm.pbf -o=columbia.o5m
./osmfilter columbia.o5m --keep="amenity=school" -o=columbia-schools.o5m
./osmconvert columbia-schools.o5m --all-to-nodes -o=columbia-schools_nodes.o5m
./osmfilter columbia-schools_nodes.o5m --keep="amenity=school" -o=columbia-schools-results.o5m
./osmconvert columbia-schools-results.o5m --csv="@id @lon @lat name addr:street addr:housenumber addr:city website email" --csv-headline -o=columbia-schools-results.csv

```

any and all help will be greatly appreciated

---

