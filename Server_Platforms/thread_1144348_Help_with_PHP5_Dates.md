---
title: "Help with PHP5 Dates"
date: 2009-04-30
forum: Server Platforms
---

### Post by lonewolf72 on 2009-04-30
Ok so I move our webserver from Debian 4 to Ubuntu 8.04 and everything went smooth... except now all our posts show up as being posted in December 31, 1969.

echo $row['releaseDate'];
returns the following:

Debian = Dec 22 2008 04:12PM
Ubuntu = Dec 22 2008 04:12:48:357PM


If you try to format the date output (one example date("M. j, Y g:i a", strtotime($row['startTime'])); ) returns...  December 31, 1969 instead of December 22, 2008.  Looking at the data in the database, the data is correct.  It is something with the way Ubuntu is returning the date that is throwing it off.  Debian was running php 5.2.0.something, Ubuntu is running php 5.2.4.something

This problem only occurs when I try to format the output from the database ($row['startTime']).

We are running Ubuntu 8.04.2 with PHP5 and connecting to a MS SQL Database (version 2000).  I don't know the code real well as I inherited this whole mess.

I don't even know what to search google on...  Any help would be gratefully accepted...

---

### Post by edpatterson on 2009-04-30
What is the 'date' datatype in the database? You say it is right, but do not give an exmaple.

---

