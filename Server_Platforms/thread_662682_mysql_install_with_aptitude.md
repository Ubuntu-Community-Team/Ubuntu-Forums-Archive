---
title: "mysql install with aptitude"
date: 2008-01-09
forum: Server Platforms
---

### Post by vanderkerkoff on 2008-01-09
I've just installed gutsy gibbon and chose no options at all.

I've then ran sudo aptitiude install mysql-server, it installs fine, and then near the end of the script it does this.

Setting up mysql-server-5.0 (5.0.45-1ubuntu3) ...
 * Stopping MySQL database server mysqld
   ...done.
 * Starting MySQL database server mysqld
   ...done.
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

So it looks like mysqld is already installed, as it stops it successfully, and then when it restarts is gives me this error.

* Checking for corrupt, not cleanly closed and upgrade needing tables.

Can anyone tell me what's going on and if that message is in fact an error or is it Ok to ignore it?

thanks

---

### Post by adityakavoor on 2008-01-09
the best way to install LAMP on ubuntu

```
sudo tasksel
```

select LAMP say OK

---

### Post by vanderkerkoff on 2008-01-09
thanks adityakavoor

I dont need lamp mate, I"m installing a django system and I only want to compile mysql.

Mysql is working, and I'm continuing with the install.  I was only wondering if anyone had seen that message before and if they knew if it was a problem or not.

Thanks again.

---

### Post by Caligatio on 2008-01-09
I did some quick Googling, check out the following SQL commands:

CHECK <TABLE_NAME>
REPAIR <TABLE_NAME>

---

### Post by vanderkerkoff on 2008-01-09
Hi Caligatio

so it's an data integrity check on start up you'd say?

nothing to worry about?

please say yes

---

### Post by Caligatio on 2008-01-09
Well, it is a data integrity check.. but I can't say that it isn't anything to worry about.

Run those commands on your tables(s) or you can try:

mysqlcheck --repair --all-databases

It only works for some engines though.

EDIT: Does it do this all the time or just this one time?  As long as it starts normally without an issue (sudo /etc/init.d/mysql restart) you are OK.

---

### Post by vanderkerkoff on 2008-01-10
I've run that command, and the repair and check tables and it's still doing it.

I'm not sure what you mean by start normally without issuing that command.

That's how I start and stop the daemon.

Do you mean kill the process, and try starting it using the safe_mysqld command?

---

