---
title: "Installing apache/php does not work"
date: 2009-01-21
forum: Server Platforms
---

### Post by Snowball on 2009-01-21
I would like to perform a pretty common task which is installing php5 and apache so I can check my php-creations locally.

The Ubuntu-Forums have a very clear item on this. It says that I only have to type

'sudo tasksel install lamp-server'

However, I get the following output:

tasksel: aptitude failed (100)

If I try to start apache2 by typing the command in a terminal I get:

apache2: bad user name ${APACHE_RUN_USER}

What happened? Why can't I just install it?
Does anybody have an idea?
Maybe it is caused by me first trying to install it via Synaptic?
I am stuck...

---

### Post by Coreigh on 2009-01-21
Here is some more detailed help;
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by drubin on 2009-01-21
> **Snowball said:**
> 
'sudo tasksel install lamp-server'

However, I get the following output:

tasksel: aptitude failed (100)

If I try to start apache2 by typing the command in a terminal I get:

apache2: bad user name ${APACHE_RUN_USER}


I would go with the previous posted link instead of tasksel lamp-server. this way it allows you to chose your modules you would like to install.

Never seen that error but it leeds me to belive it wasn't installed 100% so re-install using the link provided (if the packages are already it stalled successfully it should do much)

as for that bad user name. What command did you use to start your apache server?

---

### Post by Snowball on 2009-01-23
Thanks.

I just opened a terminal and typed 'apache2'.

I will try the 'old way' of installing. It is indicated on that web page for Dapper Drake, but apparently you and Coreigh recommend it also for Hardy Heron (that is my version).

---

### Post by Snowball on 2009-01-23
Thanks, but I already found that page. That's where I got the Tasksel thing from. But apparently, I should use the 'older' method that is described for Dapper Drake

---

### Post by Snowball on 2009-01-25
OK. I finally managed to get php working locally.

Step 1:
I installed all the packages that are described on the page 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Not via the 'Tasksel' method but using Synaptic Package manager for the following packages:

apache2 php5-mysql libapache2-mod-php5 mysql-server

Step 2:
I moved my website to my home-directory, sub-folder 'public_html'. Then, I exactly followed the steps on the previously mentioned website under the header 'Virtual Hosts'. For some reason, the apache server wants to 'know' what sites it must 'serve'.

Step 3:
Make sure that the rights of all files are set appropriately. i.e. they have to be readable for everbybody. You can set this right by the command 'chmod a+r filename' or for all files: 'chmod a+r *'

Step 4:
I started the apache server. Not by simply typing 'apache2' but by the command 'sudo /etc/init.d/apache2 start' which is described in the previously mentioned website.

---

