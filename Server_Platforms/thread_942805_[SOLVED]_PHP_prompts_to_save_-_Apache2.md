---
title: "[SOLVED] PHP prompts to save - Apache2"
date: 2008-10-09
forum: Server Platforms
---

### Post by myth01 on 2008-10-09
A few things:
1. This is my first attempt at running a webserver
2. I've googled this problem for nearly 3 hours (today, and many more yesterday), and found lots on the subject, but nothing that helped.

I've managed to install apache2, php5 and mysql on ubuntu.  Normal html pages are served properly, but php pages prompt to save rather than run.  

I've followed the instructions from here:

[https://help.ubuntu.com/community/ApacheMySQLPHP#Using%20Apache]("https://help.ubuntu.com/community/ApacheMySQLPHP#Using%20Apache")

including the "if php doesnt work" bit but the situation doesn't change.

I'm guessing its a config problem somewhere but have no idea where to start.

---

### Post by cariboo on 2008-10-09
Usually when you have a problem like that it is an ownership or permissions issue. Any file located in /var/www should only be owned by root or www-data and have permissions of 755.

Jim

---

### Post by jamesrfla on 2008-10-09
This is how I got my server to work. [http://ubuntuforums.org/showthread.php?t=844409](http://ubuntuforums.org/showthread.php?t=844409)

---

### Post by cdenley on 2008-10-09
So you did all this?
```

sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

What do the logs show after a request for a php script?
```

tail /var/log/apache2/error.log
tail /var/log/apache2/access.log

```

---

### Post by myth01 on 2008-10-09
cheers guys for your replies.

in /var/www i did this:

```
sudo chown root:root test.php
```

and cleared my browser cache, tried test.php (the phpinfo test page) again and it is still prompting to save.

aah!

---

### Post by myth01 on 2008-10-09
cdenley:

at the terminal i did:

sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server

ill check the logs now....

---

### Post by cdenley on 2008-10-09
> **myth01 said:**
> cdenley:

at the terminal i did:

sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server

ill check the logs now....

In addition to the other commands I posted, correct?

---

### Post by myth01 on 2008-10-09
oops, sorry, yep, a2enmod php5 returned 'This module is already enabled' and I restarted apache.

the last entry in errors.log was nearly 2 hours ago, and access.log shows:

127.0.0.1 - - [09/Oct/2008:22:20:49 +0100] "POST /submit.php HTTP/1.1" 200 931 "http://localhost/form.html" "Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3"
127.0.0.1 - - [09/Oct/2008:22:26:47 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [09/Oct/2008:22:26:47 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [09/Oct/2008:22:26:47 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [09/Oct/2008:22:26:47 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [09/Oct/2008:22:26:47 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [09/Oct/2008:22:26:47 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"

---

### Post by myth01 on 2008-10-10
...bump...

please help!  I do not have much hair left to pull out....

---

### Post by kaivalagi on 2008-10-10
> **myth01 said:**
> ...bump...

please help!  I do not have much hair left to pull out....

If you've done all the necessary already posted it should work, can you try the following, on the off chance it will sort things out:

```
sudo /etc/init.d/apache2 force-reload
```

Hope that helps

---

### Post by kaivalagi on 2008-10-10
> **myth01 said:**
> cheers guys for your replies.

in /var/www i did this:

```
sudo chown root:root test.php
```

and cleared my browser cache, tried test.php (the phpinfo test page) again and it is still prompting to save.

aah!

Should this be more like:

```
sudo chown www-data:www-data test.php
```

---

### Post by myth01 on 2008-10-11
Thank you kaivalgi, I'll give those a try now.  Out of curiosity, should the user www-data be listed in the Users and Groups window under System -> Adminisatration?  Because it isn't, but it does appear in apache2.conf as the user and group to run as (off the top of my head) but then in webmin, it has user and group 'apache' to run as....

---

### Post by ivikas on 2008-10-11
Hello myth01,

            I has been facing this problem for a long time and was in despair like you.All you have to do is read this documentation REAL Carefully and follow the instruction especially relating to **php5 troubleshooting**.Most problems are not solved simply because we do not have patience to read the manuals or documentations.Here is the link

[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP#Troubleshooting%20PHP%205)

                           I have almost same problem like you so as suggested by this guide i done this a2enmod php5 and after this i restarted apache and it was working.As evident from the above post,you have done this too and not working.

                    well,i have a suggestion,i even do not know whether this will help you,so do as a final resort.Instaed of using apt-get remove (package name) do  apt-get  purge (package name)see apt-get manual(open terminal and type man apt-get and read manual)Purge will remove the package completely and then do a fresh install.For me this guide(above link) has helped me and hope may it also help you.

 

with regards,
vikas

---

### Post by myth01 on 2008-10-11
Thank you guys, kaivalagi, the chown www-data seems to have worked.  I'm quite new to ubuntu (former windows user :( ) so I'm still trying to get my head round the concept of users and programs running as different users etc that linux uses (any tips on a good in depth guide related to this and any other linux concepts would be appreciated - I prefer to fully understand how my machine works, not just be glad when it does and annoyed when it doesn't)

ivikas, I got php working just before your post but thank you still, for good luck I followed your steps and it still works and is hopefully a cleaner setup.

Now the next drama, I cant access the mysql database from an html form, but I guess that'll be a new thread in a few hours once I've brought Google to it's knees trying to find out (a rather stubborn male-ego side of me refuses to ask for help on here until just before the point the pc will take flying lessons)... until the next time...

---

### Post by kaivalagi on 2008-10-11
> **myth01 said:**
> Thank you guys, kaivalagi, the chown www-data seems to have worked.  I'm quite new to ubuntu (former windows user :( ) so I'm still trying to get my head round the concept of users and programs running as different users etc that linux uses (any tips on a good in depth guide related to this and any other linux concepts would be appreciated - I prefer to fully understand how my machine works, not just be glad when it does and annoyed when it doesn't)

ivikas, I got php working just before your post but thank you still, for good luck I followed your steps and it still works and is hopefully a cleaner setup.

Now the next drama, I cant access the mysql database from an html form, but I guess that'll be a new thread in a few hours once I've brought Google to it's knees trying to find out (a rather stubborn male-ego side of me refuses to ask for help on here until just before the point the pc will take flying lessons)... until the next time...

Glad I could help

Good luck with it all :)

---

