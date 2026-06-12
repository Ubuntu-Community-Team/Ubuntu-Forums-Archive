---
title: "wireless madwifi install problems"
date: 2007-08-10
forum: Slackware and derivatives
---

### Post by eier on 2007-08-10
hi.

I'm trying to install madwifi 0.9.3.1 on my slackware 12
First i cd the madwifi directory,then i do a "make",then i do a "make install"
but when i do "modprobe ath_pci" it gives me "ath_pci mod not found"or something similar. I tried several time's but it give's me the same.

can you help me?

---

### Post by johnny4north on 2007-08-10
i believe that you need to use "sudo" in the "make install" and "sbin/modprobe ath-pci".  this is for a Atheros wireless card{are you sure its an atheros card}  found this here - 
 [http://xlayn.blogspot.com/2007/07/slackware-12-review.html](http://xlayn.blogspot.com/2007/07/slackware-12-review.html)

 1. extract the driver
      $tar -jxf madwifi-0.9.3.1.tar.bz2
   2. enter the directory of the driver
      $cd madwifi-0.9.3.1
   3. make the kernel modules
      $make
   4. install the kernel modules
      $sudo make install
   5. insert the kernel module
      $sudo /sbin/modprobe ath-pci
   6. configure your wireless with kwifimanager :D

here is another great how-to [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

---

### Post by eier on 2007-08-11
Thanks for your help.it's working now

---

### Post by angryfirelord on 2007-08-16
You can compile it or save yourself some time by using the slackware package.
[http://www.slackware.com/~alien/slackbuilds/madwifi/pkg/]("http://www.slackware.com/~alien/slackbuilds/madwifi/pkg/")

---

