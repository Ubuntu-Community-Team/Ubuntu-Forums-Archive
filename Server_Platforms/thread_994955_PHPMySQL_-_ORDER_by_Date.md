---
title: "PHP/MySQL - ORDER by Date?"
date: 2008-11-27
forum: Server Platforms
---

### Post by Johnsie on 2008-11-27
Hi, Im trying to pull some data out of a table in order of date


My query is a follows:
> $tquery = "SELECT TransDate,RefNo,TransPointsAmount from $tableName WHERE Member='$thisMemberID'ORDER BY TransDate ASC";


The format of the data in the TransDate field is dd/mm/yy (UK style). When I perform my query the results are not in order. Is there any way I can get this to work by changing the query rather than changing the format of every record. 


Ps. I use phpmyadmin.  Will changing the field description  for TransDate help?

Thanks to anyone who can help

---

### Post by Philio on 2008-11-27
Server platforms is an interesting choice of forum for this post :)

You should consider using unix timestamps for storing dates!

I'm not surprised it's not working as MySQL uses the YYYY-MM-DD format even in date fields, if you have it in DD/MM/YY format it will probably sort it numerically.

What data type are you using to store this?

---

### Post by Johnsie on 2008-11-27
Yeah, I would normally use the Unix formatting but unfortunately most of my clients don't and I don't want to perform too many conversions on their data. The more you convert data the higher the chance of damaging it.  The answer to my problem was:

> 
$tquery = "SELECT TransDate,RefNo,TransPointsAmount FROM $tableName
    WHERE Member='$thisMemberID' ORDER BY STR_TO_DATE(TransDate, '%d/%m/%y') ASC"; 

I posted it on servers because this is where most of the php/mysql people hang out ;-)

---

### Post by Philio on 2008-11-27
Well don't encourage them :)

Offer to fix it up for them, it'll improve their application's performance in the long run!

---

