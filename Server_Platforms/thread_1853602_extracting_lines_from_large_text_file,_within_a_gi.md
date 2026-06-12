---
title: "extracting lines from large text file, within a given range"
date: 2011-10-02
forum: Server Platforms
---

### Post by boondocks on 2011-10-02
I have been looking around online at various text manipulation tutorials but could not find something that solves this problem.
[LIST]
[*]There are some very large data files.
[*]Each line has multiple fields.
[*]Each field has double quotes around it.
[*]There is a comma between 2 consecutive fields.
[/LIST]

> "2011 09 16 13 50 18","stat","data1  ","data2 ","data3   "
"2011 09 16 15 54 48","flex","data1  ","data2 ","data3   "
"2011 09 16 18 52 45","stat","data1  ","data2 ","data3   "
"2011 09 16 23 01 18","flex","data1  ","data2 ","data3   "
"2011 09 17 13 53 06","stat","data1  ","data2 ","data3   "
"2011 09 17 15 57 36","flex","data1  ","data2 ","data3   "
"2011 09 17 18 53 54","stat","data1  ","data2 ","data3   "
"2011 09 17 23 02 28","flex","data1  ","data2 ","data3   "
"2011 09 18 16 04 01","stat","data1  ","data2 ","data3   "
"2011 09 18 20 01 07","flex","data1  ","data2 ","data3   "
"2011 09 20 12 04 08","stat","data1  ","data2 ","data3   "
"2011 09 20 16 01 35","flex","data1  ","data2 ","data3   "
"2011 09 20 18 00 36","stat","data1  ","data2 ","data3   "
"2011 09 20 21 57 42","flex","data1  ","data2 ","data3   "
"2011 09 21 11 53 27","stat","data1  ","data2 ","data3   "
"2011 09 21 15 54 59","flex","data1  ","data2 ","data3   "
"2011 09 21 17 56 22","stat","data1  ","data2 ","data3   "
"2011 09 21 21 53 39","flex","data1  ","data2 ","data3   "
"2011 09 22 11 56 38","stat","data1  ","data2 ","data3   "

The first field in double quotes represents the date and time.
> "yyyy mm dd hh mm ss"


I need to extract each line from this file that is:
Equal to or greater than a TOP value.
Equal to or less than a BOTTOM value.

If TOP is "2011 09 16 23 00" and the
BOTTOM "2011 09 18 20 00" then the extracted lines would be:

> "2011 09 16 23 01 18","flex","data1  ","data2 ","data3   "
"2011 09 17 13 53 06","stat","data1  ","data2 ","data3   "
"2011 09 17 15 57 36","flex","data1  ","data2 ","data3   "
"2011 09 17 18 53 54","stat","data1  ","data2 ","data3   "
"2011 09 17 23 02 28","flex","data1  ","data2 ","data3   "
"2011 09 18 16 04 01","stat","data1  ","data2 ","data3   "


How would do this with a bash shell script?

---

### Post by Jonathan L on 2011-10-02
> **boondocks said:**
> I have been looking around online at various text manipulation tutorials but could not find something that solves this problem.
[LIST]
[*]There are some very large data files.
[*]Each line has multiple fields.
[*]Each field has double quotes around it.
[*]There is a comma between 2 consecutive fields.
[/LIST]



The first field in double quotes represents the date and time.



I need to extract each line from this file that is:
Equal to or greater than a TOP value.
Equal to or less than a BOTTOM value.

If TOP is "2011 09 16 23 00" and the
BOTTOM "2011 09 18 20 00" then the extracted lines would be:




How would do this with a bash shell script?

Hi Boondocks

The classical way is with awk, pretty much always installed

```
awk -F, '(($1>="\"2011 09 16 23 00\"")&&($1<="\"2011 09 18 16 20 00\"")) {print;}' datafile
```Does exactly what you want with your example data.  It is checking the first comma-separated value for being within the bounds (compared as strings) on every line, and printing those which are within bounds.

Hope that helps

Kind regards
Jonathan.

---

### Post by boondocks on 2011-10-03
> **Jonathan L said:**
> Hi Boondocks

The classical way is with awk, pretty much always installed

```
awk -F, '(($1>="\"2011 09 16 23 00\"")&&($1<="\"2011 09 18 16 20 00\"")) {print;}' datafile
```Does exactly what you want with your example data.  It is checking the first comma-separated value for being within the bounds (compared as strings) on every line, and printing those which are within bounds.

Hope that helps

Kind regards
Jonathan.

Hi Jonathan,

That works.  It helped.

There was a slight typo in the BOTTOM range, it should be:
```
awk   -F,   '(($1>="\"2011 09 16 23 00\"")&&($1<="\"2011 09 18 20 00\"")) {print;}'  datafile
```
Where "2011 09 18 20 00\" has no 16.

Thanks.

---

### Post by i.r.id10t on 2011-10-03
Basically you have a csv file.  I'd dump it all into a SQL database and just use SQL to extract the info you are after....

---

