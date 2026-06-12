---
title: "Mysql database is empty, yet app keeps running"
date: 2007-12-04
forum: Server Platforms
---

### Post by tommyvon on 2007-12-04
Hi, im running 6.06 and running a web backend app called "joomla".   It requires MYSQL to be running.  I've always done mysql backups.. however now  I've noticed in my backups of mysql, that they were empty.  I logged in both via command line and phpmyadmin and confirmed.. all my joomla tables are empty.  

However, the site (and the backend) is running fine.   I noticed from a backup a month ago that the database is fully populated.   How is it that joomla (and my site) continue to work without mysql??   the Mysql daemon is running (and taking up a good chunk of CPU).  I'm only seeing one instance however.. how could this be??

The only changes i've made is i've been running all the ubuntu updates.

---

### Post by tommyvon on 2007-12-05
anyone??

---

### Post by crouton on 2007-12-05
Are you sure that Joomla is using the tables in that particular database?  They might be in a different database.

---

