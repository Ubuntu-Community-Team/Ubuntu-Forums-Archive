---
title: "apache no listening sockets available"
date: 2008-11-16
forum: Server Platforms
---

### Post by bluethundr on 2008-11-16
Hi guys, 

I'm running apache 2.2.9. I am using the old O'Reilly book to learn apache. I de-installed the apache that came with my distro by issuing an apt-get remove  so that I could follow the instructions in the book and start from scratch.

So I downloaded the latest (at the time) tarball and did a manual build of the app. O'Reilly has a script designed to run apache that I copied to my path. Here's the script, it's called simply 'go':

---------------------------------------------
test -d logs || mkdir logs
httpd -f `pwd`/conf/httpd$1.conf -d `pwd`
---------------------------------------------

Everything seemed to be going swimmingly as I ran my little toy example websites from the book. But then something, I don't know what happened and apache no longer launches. 

Now, when I run 'go' I get the following message. 

-----------------------------------------------
(13)Permission denied: make_sock: could not bind to address [::]:80
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
-------------------------------------------------

I tried issuing an lsof -i tcp:80 to try to track down the problem, and this is the output I get:

-------------------------------------------
COMMAND    PID       USER   FD   TYPE DEVICE SIZE NODE NAME
firefox-b 9955 confucious   35u  IPv4  19180       TCP 192.168.0.196:2321->an-in-f18.google.com:www (ESTABLISHED)
---------------------------------------------

(confucious is, of course, my username)

I have a _stunningly_ simple config file. Here it is:

-----------------------------------------------------
User webuser
Group webgroup

ServerName cassowary

DocumentRoot /usr/www/APACHE3/site.simple/htdocs

TransferLog logs/access_log

Listen 80

# these directives should not be necessary but the defaults when building
# apache with  ./configure --with-layout=GNU in v1.3.14 didn't work
# they should be unnecessary if you used the .../src/Configuration method
ErrorLog logs/error_log
PIDFile logs/httpd.pid
TypesConfig conf/mime.types
-----------------------------------------------------

Running 'ps awlx | grep httpd' yields nothing at all. 

I also tried listening on port 81, to no avail. HELP!!!!

---

### Post by spiderbatdad on 2008-11-16
run your "go" program as root...with sudo. Or make go owned by root. Obviously a permissions problem, so start there.

---

### Post by Iowan on 2008-11-16
I saw a similar error message in another thread - apparently a bug (and workaround) exists.  I'll see if I can find a link.

---

### Post by cariboo on 2008-11-16
Another problem you may run into, is if you don't shut down apache before you remove it, even using the purge option, apache will continue running. I found this out from personal experience, installing and trying to start apache will give you the above error. Make sure apache is not running, in a terminal type:

```
ps ax | grep apache
```

if it is already running the output should be something like this:

```
~$ ps ax | grep apache
 5411 ?        Ss     0:03 /usr/sbin/apache2 -k start
12542 ?        S      0:00 /usr/sbin/apache2 -k start
12543 ?        S      0:00 /usr/sbin/apache2 -k start
12544 ?        S      0:00 /usr/sbin/apache2 -k start
12545 ?        S      0:00 /usr/sbin/apache2 -k start
12546 ?        S      0:00 /usr/sbin/apache2 -k start
27065 pts/0    R+     0:00 grep apache
```

Jim

---

### Post by spiderbatdad on 2008-11-16
> **Iowan said:**
> I saw a similar error message in another thread - apparently a bug (and workaround) exists.  I'll see if I can find a link.

Wrong.

---

### Post by bluethundr on 2008-11-24
Thanks guys for the input. Ultimately, my machine was running so slowly with a literally YEARS old Ubuntu install (I think I installed Ubuntu on that machine back in '05 or at the very latest '06) that I decided a new beginning was in order. 

So I downloaded Intrepid Ibex 8.10 and installed that from scratch. After lurking on IRC and asking the same question, I invariably got the response "Why do you INSIST on doing things the hard way? USE APT!!!"

So ultimately I I relented and installed Apache using aptitude. Apache is happy now! Wish I could say the same for exim! ;) 

That's another question for another post, however.

Thanks again!
-t

---

