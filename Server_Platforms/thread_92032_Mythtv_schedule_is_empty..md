---
title: "Mythtv schedule is empty."
date: 2005-11-18
forum: Server Platforms
---

### Post by fragmental on 2005-11-18
My Mythtv schedule is empty.  I have the zap2it server thing setup.  It grabs the list of available stations but the schedule in the frontend says that the program information is unavailable.

If I run "/etc/cron.daily/mythtv-backend", I get a lot of db errors.

The errors look like they are either ```
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'repeat,stereo,subtitled,hdtv,closecaptioned,tvrating,partnumber,
``` or ```
Table 'mythconverg.dd_v_program' doesn't exist
```

I don't know a lot about mysql, I'm just trying to get mythtv to work.

I also can't get the sound to work. I have one of those capture cards where the sound outputs to the linein or mic on the sound card.  Hopefully, i'll be able to get that one figured out myself.

---

### Post by chipmonk010 on 2005-11-19
few questions:
did your run $mythfilldatabase 
after u setup zap2it?
what are the exact errors you are getting when you start the backend?

try uninstalling mythtv and mysql then do this:
#apt-get install mysql-server
#mysqladmin -u root password (any password here)
#apt-get install mythtv
(dpkg will ask you for the root password for mysql, tell it the same one u just entered)
your config files should be intact but check your zap2it config then run:
$mythfilldatabase

let me know were this get you

---

### Post by fragmental on 2005-11-19
I ran mythfilldatabase before, I'm fairly certain.  Running it again gives the same errors.

the full errors look like this:
```
DB Error (Inserting into programgenres table):
Query was:
INSERT IGNORE INTO programgenres (chanid, starttime, relevance, genre) SELECT chanid, starttime, relevance, class FROM dd_v_program, dd_genre WHERE (dd_v_program.programid = dd_genre.programid);
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.dd_v_program' doesn't exist

```

but the Database error can also be the other once I mentioned and the queries are different.  It seems to be errors trying to insert into or populate "dd_schedule" or some table or something.  There are a lot of errors, some of them look like they might be the same but some of them have similar but different errors as I mentioned.

It downloads the data from zap2it, spits out the errors, downloads more data, spits out the errors.  it does know the channels though.

---

### Post by tflanders on 2006-07-15
Downgrade to Mysql 4.0 or 4.1

---

### Post by kfb on 2006-08-22
I'm trying to downgrade, but neither apt nor synaptic are letting me use 4.1 instead of 5.0.  It insists on uninstalling mythtv when I remove 5.0.  Is there any way around this?

---

### Post by atomic0x on 2006-08-27
Using synaptic I was able to do this.  I selected mysql-server-4.1 package for installation and it did not want to remove mythtv.  If you select the mysql-client package it will try to remove myth.
[edit]
My mistake, as soon as I tried using the mysql 4.1 server I realized it was using the 5.0 client still.  When this is removed the mythtv packages need to be removed.

---

### Post by kfb on 2006-09-24
So, this looks to me like a serious problem.  MythTV 0.18 can't use mysql5, but requires it in order to install.  How do I get around this?  I can't manage to downgrade to 4.1 and keep mythtv installed.

---

