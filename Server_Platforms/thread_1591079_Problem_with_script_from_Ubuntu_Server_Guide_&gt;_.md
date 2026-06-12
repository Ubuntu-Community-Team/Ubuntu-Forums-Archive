---
title: "Problem with script from Ubuntu Server Guide &gt; Backups &gt; Archive Rotation"
date: 2010-10-08
forum: Server Platforms
---

### Post by buntolith on 2010-10-08
I'm setting up some scripts for automatic backup of photos on my ssh/nfs server at home and I'm modifying the script in the official ubuntu 10.04 server guide on Ubuntu Documentation > Ubuntu 10.04 > Ubuntu Server Guide > Backups > Archive Rotation, but there must be something wrong with this script. I don't know what it is?

When I isolate the functions and only run 

```
# Find which week of the month 1-4 it is.
day_num=$(date +%d)
if (( $day_num <= 7 )); then
        week_file="$hostname-week1.tgz"
elif (( $day_num > 7 && $day_num <= 14 )); then
        week_file="$hostname-week2.tgz"
elif (( $day_num > 14 && $day_num <= 21 )); then
        week_file="$hostname-week3.tgz"
elif (( $day_num > 21 && $day_num < 32 )); then
        week_file="$hostname-week4.tgz"
fi

echo $week_file
```

the output is 

```
johan@kevinisha:~/.bashscripts$ /home/johan/.bashscripts/weekly_bu_familjealbum
/home/johan/.bashscripts/weekly_bu_familjealbum: line 28: ((: 09: value too great for base (error token is "09")
/home/johan/.bashscripts/weekly_bu_familjealbum: line 30: ((: 09: value too great for base (error token is "09")
/home/johan/.bashscripts/weekly_bu_familjealbum: line 32: ((: 09: value too great for base (error token is "09")
/home/johan/.bashscripts/weekly_bu_familjealbum: line 34: ((: 09: value too great for base (error token is "09")

```

When I try this it is the 9th of the month so the printed message should be kevinisha-week2.tgz. I don't know if this is the problem but the output from "date +%d" is 09 and not 9.

Does anybody have any suggestions on how to correct the script?

---

### Post by psusi on 2010-10-08
Yes, the problem is the 0 prefix indicates the number is octal.  Change date argument +%d to +%-d to get rid of the zero padding.

---

### Post by buntolith on 2010-10-09
That was a simple fix (: Thanks a lot for your help!

Is there anyone that can update the server guide so others don't bump into the same problem I did?

---

### Post by buntolith on 2010-10-09
That was a simple fix (: Thanks a lot for your help!

Is there anyone that can update the server guide so others don't bump into the same problem I did?

---

