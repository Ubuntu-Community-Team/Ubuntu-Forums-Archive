---
title: "Apache and php"
date: 2008-08-24
forum: Server Platforms
---

### Post by ingeva on 2008-08-24
I've finally made Apache work with several virtual hosts, except for one thing:

Apache doesn't find php.

It complains that the file it finds is a "PHTML" file and asks what program should be used to execute it. I've tried to find the location of php without success.

I've done the installation according to instructions I have found various places, but some are just way too complicated and some seem to be outdated.

Here are my installation instructions:

```
#php5 and apache2
apt-get install php5 php-pear libapache2-mod-php5 php5-common
apt-get install apache2 apache2.2-common apache2-mpm-prefork apache2-utils apache2-doc

```Is the sequence out of order?
Something missing (I've included everything that was reported as missing)?
Is some more configuration necessary in Apache's configuration files?

(the script containing the above is run using "sudo").

---

### Post by brujoand on 2008-08-24
> **ingeva said:**
> I've finally made Apache work with several virtual hosts, except for one thing:

Apache doesn't find php.


Where do you get this output, and what are your doing at the time? 
Did your server manage to serve php pages before you started editing the httpd.conf file, if so, you could post it here.

Anders

---

### Post by ingeva on 2008-08-24
> **GrimmVarg said:**
> Where do you get this output, and what are your doing at the time? 
Did your server manage to serve php pages before you started editing the httpd.conf file, if so, you could post it here.

Anders

I get the output from FireFox, but it's evidently caused by Apache not identifying the index file as php. Snapshot enclosed.

I just managed to have Apache find the correct virtual hosts,
and the next step is to make it work with php.

My httpd.conf file is empty now. All I've done is to add the virtualhosts files.

I can see that the correct php file is found because if I chose "save" I can identify and read the file. It's renamed to something else though, and has lost the original "index.php" name.

---

### Post by wirepuller134 on 2008-08-24
I have never had that problem, but have had different issues with php while moving to php5.  Not sure if you are just loading a bland php page or a full script, if it's a full script is it compatible with php5?

---

### Post by ingeva on 2008-08-24
> **wirepuller134 said:**
> I have never had that problem, but have had different issues with php while moving to php5.  Not sure if you are just loading a bland php page or a full script, if it's a full script is it compatible with php5?

They are all fully working php5 scripts. They are in daily use on the web (php 5.2.6), but I haven't been able to make apache work with php since I installed it about a month ago.
I'm getting frustrated because I'm unable to update my websites except by doing it "in place", and I don't want to do that. Too easy to introduce errors.

When I used Windows I used another httpd package. Very much easier to work with, but the company behind it has folded and there was never any linux version. I tried to install Apache on Windows too but couldn't make it work.

Even if apache is an extremely clumsy program package (and the documentation is just beyond .... :) ) I want to stay with it because it's something of a standard in the web world.

---

### Post by wirepuller134 on 2008-08-24
Ok you got my curiosity up, we don't use Ubuntu on our production servers.  But!! since we have been upgrading our server room, we have I think 10 IBM xseries 235's sitting (yes they are antique...but still function).  Gonna load Ubuntu server on one of them this afternoon and see if i can duplicate the issue.  Will post back after it works or blows itself up.

---

### Post by ingeva on 2008-08-24
> **wirepuller134 said:**
> Ok you got my curiosity up, we don't use Ubuntu on our production servers.  But!! since we have been upgrading our server room, we have I think 10 IBM xseries 235's sitting (yes they are antique...but still function).  Gonna load Ubuntu server on one of them this afternoon and see if i can duplicate the issue.  Will post back after it works or blows itself up.

I don't know much about IBM computers but if you have 256MB of RAM you should be able to get the server version going.
I tried on my Dell laptop with 128M and the installation froze, but that may also have been caused by incompatible hardware.

Wish you luck!
Next step for me is to use an older computer as the web and file server, and possibly for backup.

---

### Post by wirepuller134 on 2008-08-24
Correction...xseries 342.....these are u3 servers...boat anchors....its loading as we speak.  But gotta eat lunch or the wife kills me.

---

### Post by wirepuller134 on 2008-08-24
It hiccuped!! Don't think the install likes the scsi cd drive, so put an ide drive in, so still working on the install.

---

