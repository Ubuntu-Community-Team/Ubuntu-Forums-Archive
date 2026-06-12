---
title: "Delete files - time estimate - Jaunty Ubuntu 9"
date: 2009-05-04
forum: Server Platforms
---

### Post by yasheshb on 2009-05-04
Hello:

  I've installed jaunty 9 AMD 64 server edition and copied my data from the older server
to the new one. (The size of data backup was approx 270gb). 

  unfortunately the copy was not clean and i decided to delete the backup and restart. the delete
is taking a long time approx 1Gb per 5 mins. 

  Is this the right speed of deletes ?

  here's my processor/mb/memory/hdd details

```
cpu - AMD Phenom(tm) 9650 Quad-Core Processor
motherboard  - ASUS  M2N68-AM SE2
memory - 4gb ddr2 ram
hdd - Seagate - ST3500418AS (7200rpm).
```
does the above delete speed look reasonable ?

thx.

yashesh

---

### Post by akoskm on 2009-05-04
> **yasheshb said:**
> Hello:

  I've installed jaunty 9 AMD 64 server edition and copied my data from the older server
to the new one. (The size of data backup was approx 270gb). 

  unfortunately the copy was not clean and i decided to delete the backup and restart. the delete
is taking a long time approx 1Gb per 5 mins. 

  Is this the right speed of deletes ?

  here's my processor/mb/memory/hdd details

```
cpu - AMD Phenom(tm) 9650 Quad-Core Processor
motherboard  - ASUS  M2N68-AM SE2
memory - 4gb ddr2 ram
hdd - Seagate - ST3500418AS (7200rpm).
```
does the above delete speed look reasonable ?

thx.

yashesh

No, of course not! :D That's totally lazy.
Are you deleted it - droped to the trash)? Because that process isn't equal with the command
```

rm

```
which is significantly faster.

---

### Post by yasheshb on 2009-05-04
nopes.. not a gui delete.. using 

rm -rf /bkp/oldmachine

looks like the hdd is slow. or maybe not configured correctly. or the cpu is not performing optimally. scary to reinstall :).

thx.

yashesh

---

### Post by wouterke on 2009-05-04
What kind of files are they (sizewise) ? 

i've seen this issue sometimes when trying to delete folders with a lot  of small files 
4-5 Gig in 10-100 kb files, single folder look about half an hour to delete. 

greetz

Wouter

---

### Post by yasheshb on 2009-05-04
> **wouterke said:**
> What kind of files are they (sizewise) ? 

i've seen this issue sometimes when trying to delete folders with a lot  of small files 
4-5 Gig in 10-100 kb files, single folder look about half an hour to delete. 

greetz

Wouter

most of the folders are devel environment which is under svn. the files are drupal codebase with contributed modules code. so yeah it's pretty much thousands of files 10-50k in size (all php code).

thx for the info.. i'll stop clicking ctrl-c every 20 mins now :). also is this something normal .. i.e does this happen on other distros ? 

my 2 year old server - FC6 was pretty fast.. i don't recall going thru such a slow copy/delete but i do remember transferring 5gb directories in under 10 mins in fc6. (single cpu, 2gb ram)

thx.

yashesh

---

