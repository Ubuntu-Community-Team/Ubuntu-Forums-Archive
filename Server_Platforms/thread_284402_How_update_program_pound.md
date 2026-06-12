---
title: "How update program pound"
date: 2006-10-25
forum: Server Platforms
---

### Post by dirkdekker on 2006-10-25
Hi , recently I installed pound (proxyserver)version 1.9.4 on a simple Ubuntu server dapper version 6.0.6.
The installation was done as repository. The latest version of pound is 2.1.5 .The Download (wget) and make file are allready in the directory : Pound-2.1.5 .Then 
$ Sudo apt-get remove pound 
cd ../Pound-2.1.5
$ sudo apt-get build-dep pound
$ sudo pound -v -f /usr/local/etc/pund.cfg
with 
$ ps aux ww I don't see process pound... and With 
$ apt-cache policy pound 
   I still see version table : 1.9.4
What do I wrong to start the new version of pound??

---

### Post by Jussi Kukkonen on 2006-10-25
You didn't compile or install the app (not in the pasted part at least...). 
Not sure if that was just a copy-paste error, but you also used "Sudo" with a capital S while removing pound.

Read the INSTALL and README files in the Pound-2.1.5 directory to find out how to compile and install. Alternatively, use packages.ubuntu.com to find the edgy package (version 2.0) and try to install that.

---

### Post by dirkdekker on 2006-10-25
Hi,Jussi, thanks for fast reaction!! 
The text was not copy-paste; I have no idea to to that. So there will be an error. Alternatively, use packages.ubuntu.com 
I followed this instruction: [http://blog.tupleshop.com/2006/7/8/deploying-rails-with-pound-in-front-of-mongrel-lighttpd-and-apache](http://blog.tupleshop.com/2006/7/8/deploying-rails-with-pound-in-front-of-mongrel-lighttpd-and-apache)

A rather clear instruction. 
compiling is $ ./configure is-not-it?

You say:Alternatively, use packages.ubuntu.com ?? How ?
wget [http://packages.ubuntu.com](http://packages.ubuntu.com) ??

Dirk

---

### Post by Jussi Kukkonen on 2006-10-26
From your instructions:
> $ ./configure
$ make 
$ sudo make install
*configure* configures (duh!) the Makefile for your system and settings. You may need to set some options... *make* compiles the program, and *make install* installs it. 

There are two problems with this approach on Ubuntu: First you might have to give configure some parameters, like the install path... Second, the installed software won't be added into the package manager, so removing it or upgrading the OS becomes more difficult. That's why I suggested trying the edgy package although that's not without possible problems either:
> You say:Alternatively, use packages.ubuntu.com ?? How ?
wget [http://packages.ubuntu.com](http://packages.ubuntu.com) ??
Like I said, this is not guaranteed to work. There may be dependencies you can't fix. I'd say it's worth a try.

Go to the address with your web browser, search for pound (for Edgy), find the download link to the .deb-file and download it. Try to install it with 
```
sudo dpkg -i <name-of-package.deb>
```

---

### Post by dirkdekker on 2006-10-26
Hi,Jussi, thanks! I'm gratefull for your patients with me ;)
I was succesfull ( this morning 01:00) to reinstall the pound version 2.1.5. ( I hope)
The results of the $sudo make install action was wrong. It say's >make clock skew detected
Time stamp 2006-18-23 09:24:32 is: 277930051. This looks like an absolute time structure and made the dissision to delete the Pound-2.1.5 map totaly. 

Then  I had removed pound it with :
$ pound stop
$ apt-get remove pound. 
Started with wget to get the latest version from [www.apsis.ch](www.apsis.ch)
Did the tar , unpacking and start over again.
With $sudo sysv-rc-conf I was able to make a cross somewhere in the table ( 2,3,4,5) that I had seen before yesterday, to make the pound program start at reboot. 

So far so good. Only maybe I did something stupid because apt-get upgrade has downloaded a very old version 1.8.2 :
$apt-cache policy pound ->
Pound: 
       installed: 1.8.2-1Sarge1
       candidate: 1.8.2-1Sarge1
       Version table:
     *** 1.8.2-1Sarge1 0

500 [http://http.us.debian.org](http://http.us.debian.org) stable/main Packages
100  /var/lib/dpkg/status

I think I have do do the job over again.
Anyway, something is working and first I will test Pound somehow.
Do you work with pound as proxyserver?

Dirk

---

### Post by Jussi Kukkonen on 2006-10-26
No, I use privoxy for my personal use. 

By the way, are you sure you need the newest version of Pound? As you've seen, installing software that's not in the repositories might take a lot more work and experience than a simple *aptitude install xyz*...

---

### Post by dirkdekker on 2006-10-26
Hi, Jussi, yes I want one of the latest because the developer Rober Segall is repairing bugs and makes new features. 
Do you know a better way to deinstall a programm?
And do you understand the problem with the Time stamp 2006-18-23 09:24:32 is: 277930051.

Dirk

---

