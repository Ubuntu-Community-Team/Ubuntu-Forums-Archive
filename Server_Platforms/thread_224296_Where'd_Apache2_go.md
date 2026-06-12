---
title: "Where'd Apache2 go?"
date: 2006-07-27
forum: Server Platforms
---

### Post by superpwnage on 2006-07-27
I cant find apache2 in the repositories anymore. When I do a-
```
sudo aptitude install apache2
```
I get "package could not be found",

What am I doing wrong?

---

### Post by harisund on 2006-07-27
Hmmm.. are you trying this out after a fresh install? Have you modified your sources.list file? 

Do one thing ... either post your sources.list file here, or do a "sudo aptitude update; sudo aptitude install apache2" and paste the output.

---

### Post by az on 2006-07-27
Make sure that you not only have the dapper repositories enabled, but the dapper-security and the dapper-updates ones as well.

You likely edited your sources.list and now have no Dapper main enabled, but instead have Dapper-security main instead (a common mistake) not realising that was not the same thing.

---

### Post by superpwnage on 2006-07-29
Hey guys, sorry for the delayed reply,

After waiting a few days now, I am getting something different when I try and install apache2 (without changing *anything*). Here is what I get from the terminal after a sudo aptitude install apache2 - 

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  apache2-common apache2-mpm-worker apache2-utils
The following NEW packages will be automatically installed:
  libapr0
The following NEW packages will be installed:
  apache2 libapr0
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 1247kB of archives. After unpacking 4276kB will be used.
The following packages have unmet dependencies:
  apache2-utils: Depends: libpcre3 (>= 4.5) which is a virtual package.
  apache2-common: Depends: ssl-cert (>= 1.0-7) which is a virtual package.
  apache2-mpm-worker: Depends: libpcre3 (>= 4.5) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
apache2 [Not Installed]
apache2-common [Not Installed]
apache2-mpm-worker [Not Installed]
apache2-utils [Not Installed]

Score is 26

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.


```

I now see it in the SPM which I didnt before, but I get a similar message when trying to install it from there aswell.

---

### Post by drivel on 2006-07-29
modify your /etc/apt/sources.list
and sudo apt-get update.
then you can install apache2

---

### Post by superpwnage on 2006-07-29
Thanks for all your help, works great now.

---

