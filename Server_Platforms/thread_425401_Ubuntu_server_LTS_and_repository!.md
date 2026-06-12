---
title: "Ubuntu server LTS and repository!"
date: 2007-04-27
forum: Server Platforms
---

### Post by petterah on 2007-04-27
Hello all, this may seem like a stupid question, but since I've been using debian for a long time, I don't seem to get the LTS server vs. desktop support options? They mention support for 3 years on the desktop, and 5 years for the server edition. I know there are server CD and desktop CD, but, i also know all these packages come from the same repository...

So, how do they do it? Are there some key added to the packages to tag them server or desktop? If I install the server edition, which i guess is the same as an alternate ISO with "installing command line" option, how do I know I got the long term support of 5 years, if I add a package not included in the standard installation? Hope this doesn't sound weird, I'm not good at explaining...

Summing up:

1. How do i see if a package is supported for 3 or 5 years
2. Does "command line system" from the alternate iso count as an ubuntu-server install, like from the original ubuntu-server iso?
 
Thanks, Petter :)

---

### Post by az on 2007-04-27
> **petterah said:**
> 

1. How do i see if a package is supported for 3 or 5 years
2. Does "command line system" from the alternate iso count as an ubuntu-server install, like from the original ubuntu-server iso?
 

Good question.

1.  AFAIK, there is not a formal word on this.  I think it is assumed that the desktop packages will just stop getting support, but the server packages in main will continue to get security updates and bug fixes.  I don't know if each package will get "tagged" per se.

2.  They are exactly the same packages.  But the alternate command-line-only install will not install the LAMP stack by default.  You can easily install the LAMP stack.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The alternate cd also installs the desktop kernel and not the server kernel.  You would have to install the linux-server package by hand.  The server kernel will give you better performance on higher-end server hardware, but for most home computers, the desktop (386) kernel works just fine.  The server kernel will not boot on some desktop hardware (like a pentium one or a VIA C3 processor).

---

### Post by petterah on 2007-04-27
Ok, thank you for your answer :)

---

### Post by imagine on 2007-04-27
Maybe the section of a package can be used, but I don't know of anything official either.
```
apt-cache show <package> | grep Section:
```

[http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/)

---

