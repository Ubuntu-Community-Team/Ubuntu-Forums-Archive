---
title: "Apache 2.2.2 + PHP 5.1.4"
date: 2006-05-30
forum: Server Platforms
---

### Post by odyn_owl on 2006-05-30
I compiled Apache from sources, after that I'm trying compiled php. 
but libphp5.so there isn't after **make**, and **make install** crush with error "apxs:Error: Command failed with rc=65536"](*,) 

Any help appreciated.Thanks.

---

### Post by chlag on 2006-05-30
It's better to install apache2 and php5, by doing this:
```
sudo apt-get update
```
```
sudo apt-get install apache2 php5
```

ok!

---

### Post by ady on 2006-05-30
try apache deb package &  php 5.0.x  source package

---

### Post by xpmaniac4ever on 2006-06-04
```
sudo apt-get install apache2
``` installs Apache 2.0.55, but how can we install Apache 2.2.2 ?

---

### Post by xpmaniac4ever on 2006-06-04
?

---

### Post by odyn_owl on 2006-06-05
from sources

---

### Post by jms1989 on 2006-08-07
How can I just obtain 'libphp5.so'?

---

### Post by lamego on 2006-08-07
Why do you need Apache 2.2.2 + PHP 5.1.4 instead of the versions available on the repositories ?

---

### Post by printmkr on 2006-08-08
Can't speak for anyone else but I want Apache 2.2 for use with Ruby on Rails using Mongrel with mod_proxy_balancer, which is only in 2.2. (see "Time For A Grown-Up Server: Rails, Mongrel, Apache, Capistrano and You" at [http://blog.codahale.com/tags/mod_proxy_balancer/]("http://blog.codahale.com/tags/mod_proxy_balancer/") )

I have 2.2 installed in Windows and OS X (thanks DarwinPorts!), but I am a total n00b with Linux and Ubuntu, and in a different post, was told installing Apache 2.2 in Ubuntu for a n00b was, well, problematic. So I am thinking of putting my Ubuntu server migration on hold until Ubuntu offers an "apt-get" for 2.2. I was hoping to host on Ubuntu and develop on the Mac (TextMate rocks!) and take Windows out of the equation.

---

### Post by shodson on 2006-08-19
I would like Apache 2.2 support as well, for similar Ruby on Rails reasons, in addition to knowing that I have a superior, more scalable version of Apache on here.  I've had some negative experiences with compiling source on linux so that's usually the last thing I want to have to do and I'd love to just depend on apt-get for my installs.

I'm pretty new to Linux administration myself, and I've used Fedora but just played around with it, not really attempted to do any serious web hosting with it.  I'm a little leary, in general, about Ubuntu as a best-of-breed server platform.  I know they get a lot of accolades for their advancements on the desktop and ease of installation, but I really want a solid, easy to use, best of breed web/application linux distro.  I was a little worried to find out that Ubuntu doesn't even ship with a LAMP stack!  That was a sign of lack of emphasis for servers.  Should I stick with the Red Hat/Fedora line, or is Ubuntu going to serve me well as a server platform as well?

On a side note, who decides when a module like Apache get updated to 2.2 in the apt-get system?  What does it take for a program to get upgraded as an Ubuntu module?

---

### Post by chrisfay on 2006-08-20
>  I was a little worried to find out that Ubuntu doesn't even ship with a LAMP stack!

It does....

[http://www.ubuntu.com/server](http://www.ubuntu.com/server)

---

### Post by shodson on 2006-08-20
Ubuntu server ships with LAMP, but no window manager.  Sorry, maybe I'm a wimp for wanting a graphical user interface out of the box, and I'm sure there's a way to install GNOME after install, just didn't want to fuss with it.

---

### Post by mbeach on 2006-08-25
> **lamego said:**
> Why do you need Apache 2.2.2 + PHP 5.1.4 instead of the versions available on the repositories ?

a very good reason to want PHP 5.1x is for those wanting to finally take advantage of a pg_prepare function (if anyone other than me is really starting to like postgresql).

[http://www.php.net/manual/en/function.pg-prepare.php](http://www.php.net/manual/en/function.pg-prepare.php)

---

### Post by Saeven on 2006-09-27
> I compiled Apache from sources, after that I'm trying compiled php.
but libphp5.so there isn't after make, and make install crush with error "apxs:Error: Command failed with rc=65536"Have you ever found a solution to this?  I'm running into the same problem..

---

### Post by shodson on 2006-09-27
No, I gave up on the effort.  I'm just waiting for it to be available via apt

---

