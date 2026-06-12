---
title: "Ubuntu Server 8.04 Mysql and My-*.cnf"
date: 2009-02-25
forum: Server Platforms
---

### Post by xofs on 2009-02-25
Good afternoon,

I'm setting up a LAMP on Server 8.04(yes, required) using the standard installer. The database (mysql) will be getting a work-out and in the past I just copied and edited the my-large.cnf to provide more RAM for key buffers and etc. So. . .

I can not find the my-medium, my-large, etc. config files this time--even after goobling my head off :)

ALSO, I noticed that 8.04 is using something called apparmor (yes, I'm trying to read up) and the my.cnf warns not to muck about and get apparmor crossed.

FINALLY, the questions:

-- Will editing *memory* settings in /etc/mysql/my.cnf create problems with apparmor?

-- Are the my-medium,my-large, etc. base files available 8.04 and, if not, does anyone know where I could get them for the 5.x that comes with 8.04?

-- Should I even worry with fiddling the mysql memory settings?
(In the past we've seen improvement from bumping up some of the variables and that was on machines with 1Gb physical--the new machines have twice that and I want mysql to take advantage of it)

I realize some of this is a bit vague without hard info (queries/per, tables, sizes), etc. but I'm basically looking to tweak without breaking and in the past the my-*.cnf files were great for that.

Thanks in advance.

---

