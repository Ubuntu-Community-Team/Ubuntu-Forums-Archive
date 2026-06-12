---
title: "rootkit warning"
date: 2005-11-15
forum: Server Platforms
---

### Post by ntlnsideidiotoutside on 2005-11-15
Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
 /dev/.static
/dev/.udevdb
/dev/.initramfs-tools /etc/.pwd.lock
---------------
Please inspect:  /dev/.static (directory)  /dev/.udevdb (directory)

Is this ok,plz help
thank you

---

### Post by LordHunter317 on 2005-11-15
Both are fine.  All of those are false-positives, in fact.

---

### Post by HJThis on 2005-11-16
Hey,To all

Yes as said by LordHunter317 it's cool i also get this same thing

but may i add make sure to do this here

sudo 

rkhunter --update
 
there are some new updates for rk

BOL ;)

---

