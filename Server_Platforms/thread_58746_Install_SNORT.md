---
title: "Install SNORT"
date: 2005-08-21
forum: Server Platforms
---

### Post by darkspider on 2005-08-21
For successfully install Snort manually (compile), I was asked to install so many files
and each of them also has its own dependency as well

1. pcre
2. libpcap
3. flex
4. strlcpy
5. ioccom.h 
6. sockio.h
7 .....

and many more.... is there any other way to install Snort easier and get the (most) up-to-date version ...something like a complete RPM / package or something.....
Please advise

Thnxz

---

### Post by jasmuz on 2005-08-21
open a terminal, type sudo gedit /etc/apt/sources.list add these two repositories:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

Save and close, now on the terminal type sudo apt-get update 
Afterwards just do a search for snort, like this sudo apt-cache search snort (it must be listed)

Then just sudo apt-get install snort

That's it!

---

### Post by Aussiein on 2005-08-21
Hi All,

Even when you do changes in repositories, you are going to get the older snort (2.2.x). In fact the best way will be to do installation from source only. I am also facing the simialr issue with Ubuntu.

Such issues were not there with Fedora. I am also in fix.

Best regards

Naveen

---

### Post by gruepig on 2005-08-22
Backports, or some other third-party .deb repository, sounds like the best solution if you can find a current snort package.

You might be able to get an RPM and use alien to install it.  ('apt-get install alien', then run 'alien -i snortpackage.rpm'.)

Installing from source may not be so bad. For dependencies, most likely you can use apt-get to install the -dev packages for each (e.g., libpcre3-dev, libpcap-dev, etc.), so you'll only need to compile snort yourself, as opposed to snort plus each of its dependencies.

---

### Post by Ainvar on 2005-09-27
I am trying to install the latest snort but with lack of decent documentation it is pretty difficult.

---

