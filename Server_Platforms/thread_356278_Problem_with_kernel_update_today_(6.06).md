---
title: "Problem with kernel update today (6.06)"
date: 2007-02-08
forum: Server Platforms
---

### Post by prodsacnetworking on 2007-02-08
Hi,

today I made my routine updates check ups on my servers...

when I run: 

apt-get install linux-image-server
or for x64
apt-get install linux-image-amd64-server

I get: 
The following packages have unmet dependencies:
  linux-image-amd64-server: Depends: linux-image-2.6.15-28-amd64-server but it is not installable
E: Broken packages

I tried installing with the -f option. Same thing...

any ideas?
Thanks a lot

---

### Post by esaym on 2007-02-09
This might be of some information [http://ubuntuforums.org/showthread.php?p=2129087](http://ubuntuforums.org/showthread.php?p=2129087)

---

