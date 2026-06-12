---
title: "Apache Document root ?"
date: 2005-10-17
forum: Server Platforms
---

### Post by dbee on 2005-10-17
What's the easiest way to find out which document root apache is using ?
I have a couple of httpd.conf's on my system and it's hard to tell which one it's working from.

Is there any other way ?

My apache server seems to be offering my .php files for download only. I'm tweaking the httpd.conf file, but I need to know whether I'm tweaking the correct one.

---

### Post by bluck on 2005-10-17
[QUOTE=dbee]What's the easiest way to find out which document root apache is using ?
I have a couple of httpd.conf's on my system and it's hard to tell which one it's working from.

Is there any other way ?

My apache server seems to be offering my .php files for download only. I'm tweaking the httpd.conf file, but I need to know whether I'm tweaking the correct one.[/QUOTE]

take a look at /var/log/apache2/access.log

---

### Post by bluck on 2005-10-17
[QUOTE=dbee]
My apache server seems to be offering my .php files for download only. I'm tweaking the httpd.conf file, but I need to know whether I'm tweaking the correct one.[/QUOTE]

you need to add:  

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

to your httpd.conf if you want php files to be parsed as such.

---

### Post by dbee on 2005-10-17
Hi bluck,

thanks for the speedy reply, 

I added the first one to the httpd.conf that I thought it was working from ...

I was a little unsure of the second one though ... is it really required for the php engine to parse the .php pages ?

It kinds looks like something that might spit out source code ?

---

### Post by bluck on 2005-10-17
[QUOTE=dbee]Hi bluck,

thanks for the speedy reply, 

I added the first one to the httpd.conf that I thought it was working from ...

I was a little unsure of the second one though ... is it really required for the php engine to parse the .php pages ?

It kinds looks like something that might spit out source code ?[/QUOTE]

nope, not 100% necessary, you're assumption is correct.

couple stupid q's:

is php actually installed?
did you restart apache after the edit?

sorry, gotta cover all the bases, you know ;)

---

### Post by dbee on 2005-10-17
Hi again,

I've tried to track down access_log but apparently it's no longer on my system, it only finds the one from my manual /usr/local/apache2 install 

root@ubuntu:/ # slocate access_log
/usr/local/apache2/logs/access_log
root@ubuntu:/ # cat /usr/local/apache2/logs/access_log
127.0.0.1 - - [17/Oct/2005:14:59:28 +0900] "GET / HTTP/1.1" 404 268
127.0.0.1 - - [17/Oct/2005:14:59:29 +0900] "GET /favicon.ico HTTP/1.1" 404 279
127.0.0.1 - - [17/Oct/2005:21:29:21 +0900] "GET / HTTP/1.1" 404 268
127.0.0.1 - - [17/Oct/2005:21:29:21 +0900] "GET /favicon.ico HTTP/1.1" 404 279
127.0.0.1 - - [17/Oct/2005:22:00:52 +0900] "GET / HTTP/1.1" 404 268
127.0.0.1 - - [17/Oct/2005:22:00:52 +0900] "GET /favicon.ico HTTP/1.1" 404 279
127.0.0.1 - - [17/Oct/2005:22:01:54 +0900] "GET / HTTP/1.1" 200 75
127.0.0.1 - - [17/Oct/2005:22:01:55 +0900] "GET /favicon.ico HTTP/1.1" 404 279
127.0.0.1 - - [17/Oct/2005:22:08:47 +0900] "GET / HTTP/1.1" 304 -
127.0.0.1 - - [17/Oct/2005:22:08:48 +0900] "GET /favicon.ico HTTP/1.1" 404 279
127.0.0.1 - - [17/Oct/2005:22:09:15 +0900] "GET / HTTP/1.1" 304 -
127.0.0.1 - - [17/Oct/2005:22:09:16 +0900] "GET /favicon.ico HTTP/1.1" 404 279

which gives me only logs from yesterday when I was running the manual install system. It also makes no mention of the document root ...

Is it just me or is the synaptic install incredibly annoying. It seems to install files all over the place and I can never seem to track down even the most basic ones. I think that apache should be put in 

/usr/local/apache2

---

### Post by dbee on 2005-10-17
Hi bluck,

In response to the earlier question ... I'm just trying to track down the local modules  now, and see if maybe it's compiled in. 

This may take a few minutes ....

---

### Post by bluck on 2005-10-17
[QUOTE=dbee]Hi bluck,

In response to the earlier question ... I'm just trying to track down the local modules  now, and see if maybe it's compiled in. 

This may take a few minutes ....[/QUOTE]

ok, 

im just trying to dig around and see where everything is myself, i'm used to running FreeBSD as my server :)


when i installed apache2, the .conf files where under /etc/apache2/
there was also a sites-available and sites-enabled 

./sites-available/default stores the info about the default site
./sites-enabled/000-default was a link to the ./sites-available/default

seems the default site's document root is /var/www/ 
you could edit your index.php there to echo the current dir..



something like: echo exec('pwd');

---

### Post by dbee on 2005-10-17
The exec(`pwd`) thing is a non-starter, but thanks for the attempt anyway bluck 

I'm following various paths trying to locate my installed and compiled mods and I'm getting absolutely nowhere. My httpd.conf file points to an include file for it's mods, but the include file doesn't exist

There's another httpd.conf file in /etc/apache2 that looks like this 

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

I can't seem to track down any of the binaries, apart from the one in /usr/sbin/apache2 ????

I think maybe that it's missing the LoadModule because it's pointing to a nonexistant file.

---

### Post by bluck on 2005-10-17
its sounding like you havent php installed.

try `sudo apt-get install libapache2-mod-php*#*`

where *#* is either 4 or 5, whichever php version you're after.

---

### Post by dbee on 2005-10-17
I had that done already, but it still didn't see the php4

I'm trying to get my hands on the php5 mod at the moment ...

where are the mod_php source files ??

I can't find them anywhere ... including apache.org

---

### Post by dbee on 2005-10-18
ok, I got them

[www.modules.apache.org](www.modules.apache.org)

cool

---

### Post by matw on 2005-10-18
dbee,

I too had troulble figuring out what symaptic put where until I found the "installed Files" tab. Select the package you're interested in and then press the Properties toolbar button (or right click and select Properties). The Installed Files listing looks pretty complete.

---

### Post by dbee on 2005-10-19
Thanks matw

---

