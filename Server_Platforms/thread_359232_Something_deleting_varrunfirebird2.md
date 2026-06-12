---
title: "Something deleting /var/run/firebird2"
date: 2007-02-11
forum: Server Platforms
---

### Post by bumpkin on 2007-02-11
The packages for Firebird2 do not properly configure the software. One thing that doesn't occur is the dir "/var/run/firebird2" is not created. With out this directory, invoking fbguard returns the error message. 

Could not open /usr/lib/firebird2/run/isc_guard1.quirky for write   

where

 /usr/lib/firebird2/run --> /var/run/firebird2

When I create this directory (sudo mkdir /var/run/firebird2) I am able to invoke fbguard and get the sever running. However, the next time I boot I find the directory has been deleted. 

What could be deleting this directory?

---

### Post by gpremuda on 2007-04-02
See [http://www.ubuntuforums.org/showthread.php?t=200837&highlight=%2Fvar%2Frun%2Ffirebird2](http://www.ubuntuforums.org/showthread.php?t=200837&highlight=%2Fvar%2Frun%2Ffirebird2)

---

