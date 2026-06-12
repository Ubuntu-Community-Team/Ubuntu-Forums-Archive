---
title: "Hosting Multiple Sites on Apache"
date: 2005-10-30
forum: Server Platforms
---

### Post by Rollo Tamasi on 2005-10-30
Hi Guys,

How do you setup Ubuntu/Apache so that you can host multiple websites on your box. I have a 60Gig Harddrive, and i would like to setup my box so that i can host 10 sites with 6Gig partitions each. I would like to have SQL running on each of those partitions as well, i'm guessing i would have to congfigure sql as well to work on each partition?

(I have a static IP, btw)

---

### Post by JLTB on 2005-10-30
Hey Rollo,

The easiest way to do this (and the most widely accepted) is to use virtual hosts in apache.  Basically apache will start up a seperate sub-instance of itself for each of your virtual hosts so they are essentially completely seperated from eachother.

I would suggest installing webmin or some other GUI tool to configure it up.  You can also do some searching on "apache virtual hosts" to find more info on the matter.

For your database I would set up 1 database server with 6 databases inside with 6 users who have permissions on only their own database.  This should be enough to get 6 sites going; however, if you want more of an ISP approach whereby each site can have multiple DB's etc... You'll need to get into "chrooting" and other more compliated stuff.

That should be enough to get you started.  For a basic setup, webmin and phpmyadmin should be enough to get it all config'ed up.

Cheers!

---

### Post by Rollo Tamasi on 2005-11-03
Thanks for your response, is this the best approach to take as recommended by JLTB?

When you say you would setup a database server, do you mean a dedicated box which just hosts db's connected to my LAN?
[QUOTE=JLTB]Hey Rollo,
For your database I would set up 1 database server with 6 databases inside with 6 users who have permissions on only their own database.  This should be enough to get 6 sites going; however, if you want more of an ISP approach whereby each site can have multiple DB's etc... You'll need to get into "chrooting" and other more compliated stuff.
[/QUOTE]

---

### Post by JTorres176 on 2005-11-04
running six different sql servers on one machine could cause some serious performance and memory (or lack of memory actually) problems.  if you're using PostgreSQL, install it once, then go through the commands for adding users and databases

sudo su - pgsql
createuser dbuser1
createdb -O dbuser1 db1
createuser dbuser2
createdb -O dbuser2 db2
(and so on)

You can run multiple databases in one installation, which will run completely different databases determined by user and database names...  access them by running
psql -U dbuser1  <-- accesses db1
psql -U dbuser2  <-- accesses db2
(and so on)

I'm sure MySQL has a similar process, but I'm unfamiliar with it.  :)

---

### Post by pmt on 2005-11-05
Put a textfile into the directory /etc/apache2/conf.d/
Name it virtual_host (for example)

Write the following configuration directives in this file

# Virtual host configuration
NameVirtualHost *

<VirtualHost *>
    DocumentRoot /var/www/domain1
    ServerName domain1
    <Directory /var/www/domain1>
       Options Indexes FollowSymLinks
    </Directory>
</VirtualHost>

<VirtualHost *>
    DocumentRoot /var/www/domain2
    ServerName domain2
    <Directory /var/www/domain2>
       Options Indexes FollowSymLinks
    </Directory>
</VirtualHost>

# and so on ...

restart apache2
> sudo /etc/init.d/apache2 restart

thats all.

---

### Post by LordHunter317 on 2005-11-06
No!

First off, 'NameVirtualHost' is already in sites-available/000-default, and should **not** be repeated anywhere else.

Second, you don't put virtual host definitions there.  That directory is reserved for configuration files installed by packages.

You place virtual host directives in one file per site, in sites-available.  You then symlink them to sites-enabled, perhaps changing the name so they're in the proper loading order.

---

### Post by obscenic on 2005-11-07
Why do you symlink the files, rather than just creating them in sites-enabled?

---

### Post by LordHunter317 on 2005-11-08
Mainly so you can enable/disable them as needed.

---

### Post by obscenic on 2005-11-08
Ah, case in point!  Thanks for all the tips. (working on similar problems)
Would I be hijacking if I asked what a proper setup for an individual virtual host file should be? 

[edit] Nevermind! Got it solved! Now to tackle the downloading phtml instead of processing as php issue... grr[/edit]
Also solved!

---

