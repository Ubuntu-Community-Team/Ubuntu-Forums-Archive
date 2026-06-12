---
title: "How to Remove linux-image-2.6.15-26-server"
date: 2007-01-09
forum: Server Platforms
---

### Post by esaym on 2007-01-09
I could not boot with the default kernel so I installed the i386 one and everything is fine.  I did apt-get remove linux-server but now when I run apt-get upgrade it trys to update the linux-image-2.6.15-26-server kernel.  Therefor it must not have been uninstalled.  I tried apt-get remove linux-image-2.6.15-26-server and it tried to remove linux-image-2.6.15-26-server but install linux-image-2.6.15-27-server.  Since I can't ever boot with that kernel I would like to just get it off of my server.  I certainly don't want to spend time downloading updates for a kernel I don't need....:-k

Thanks!

---

### Post by esaym on 2007-01-09
Ok I figured it out

> 
aptitude remove linux-image-server


then

```
aptitude remove linux-image-2.6.15-26-server
```

---

### Post by esaym on 2007-02-11
Ok looks like I have another problem.  The latest kernel update won't install:

```
root@lindsay:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

root@lindsay:~# uname -a
Linux lindsay 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i586 GNU/Linux
```

Yes I did run apt-get update before hand.

I'm guessing this is because of the way I removed the old kernel...

I looked into this problem for about an hour today but I ran out of time.  I'm sure it's a dependency issue and I am going to have to end up reading the whole aptitude manual.  Not sure when I will fine time for that :p

But if anyone knows a quick fix or has any tips let me know :biggrin:

---

### Post by esaym on 2007-02-11
Ok just an update.  I ran aptitude dist-upgrade and it spit this out:

```
Building tag database... Done
The following NEW packages will be automatically installed:
  linux-image-2.6.15-28-386 linux-restricted-modules-2.6.15-28-386
The following NEW packages will be installed:
  linux-image-2.6.15-28-386 linux-restricted-modules-2.6.15-28-386
The following packages will be upgraded:
  linux-image-386 linux-restricted-modules-386
2 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.9MB of archives. After unpacking 84.4MB will be used.
Do you want to continue? [Y/n/?]
```

Looks safe but I am scared.  Can anyone with more knowledge than me look this over before I commit it :-k

---

### Post by esaym on 2007-02-11
Ok looks like you have to use "dist-upgrade" to get a new kernel.  Hmm I guess I learned something today.


edit:
I used "dist-upgrade" and it worked fine.  All is well :D

---

