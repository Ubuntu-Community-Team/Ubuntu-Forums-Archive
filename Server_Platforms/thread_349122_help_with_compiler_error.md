---
title: "help with compiler error"
date: 2007-01-29
forum: Server Platforms
---

### Post by bigredcherokee on 2007-01-29
root@NSLLCSRVR:/usr/src/proftpd/proftpd-1.3.0a# ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

How do I fix this error?

---

### Post by p!=f on 2007-01-29
What's in config.log?
Do you have build-essential package installed?

---

### Post by bigredcherokee on 2007-01-29
all i install to get the compiler running is gcc. what do I use when using apt-get? to down load the dev tools?
any specific package?

I'm new so please go easy.



Thanks.

---

### Post by p!=f on 2007-01-29
> **bigredcherokee said:**
> all i install to get the compiler running is gcc. what do I use when using apt-get? to down load the dev tools?
any specific package?

I'm new so please go easy.



Thanks.
Type
```

sudo apt-get install build-essential

```
(or use synaptic in GNOME or adept in KDE)
to get basic tools for working with sources. 

Btw, ProFTPD 1.3.0 is in Edgy or in Dapper's backports. 
Running ./configure without any parameter may do the job but you probably won't get  functionality expected. If you're new to Linux I would suggest not to compile software from sources.
Use binaries (packages) instead, trust the package maintainer :). Once you get more familiar with the environment, compile or even better make your own .deb packages.

---

### Post by bigredcherokee on 2007-01-30
ProFTPD 1.3.0 is in Edgy or in Dapper's backports?

well I have been searching the web for the correct syntax but haven't found it yet. 

I would like to use the package manager. I have tried sudo apt-get install proftpd  and it dosn't locate them I did apt-get update to see if I could get udated list but that didn't work.

Thanks for your help I got the dev tools install correctly now.

---

### Post by p!=f on 2007-01-30
> **bigredcherokee said:**
> ProFTPD 1.3.0 is in Edgy or in Dapper's backports?

[http://packages.ubuntu.com/proftpd](http://packages.ubuntu.com/proftpd)

> **bigredcherokee said:**
> 
I would like to use the package manager. I have tried sudo apt-get install proftpd  and it dosn't locate them I did apt-get update to see if I could get udated list but that didn't work.

Sounds like you don't have universe sources enabled.

How to add them in Gnome/KDE take a look at K/Ubuntu Desktop Guide - Extra Repositories at:
(Ubuntu)
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html)
(Kubuntu)
[https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/extra-repositories.html)

---

### Post by bigredcherokee on 2007-01-30
p!=f I'm runing 6.06 server all I got is a bash prompt. I bet there is a config file I can edit to enable universal source.

---

### Post by az on 2007-01-30
> **bigredcherokee said:**
> p!=f I'm rinng server all I got is a bash prompt. I bet there is a config file I can edit to enable universial source.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by bigredcherokee on 2007-01-30
Thanks That I believe will fixer up.:D

---

