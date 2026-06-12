---
title: "Wired connection seems to be dropped while updating"
date: 2012-06-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-06-11
I need to reboot (or possibly just restart X) to look into this further but I seem to be stuck:

[ATTACH]219520[/ATTACH]

Anything "local" works but I can't connect, no browser, etc. So I had to use a flash drive to transfer this info to a working machine.

No huge surprise this early in a dev cycle, just wanted to give a "heads-up", or should that be heads-down :lolflag:

---

### Post by kansasnoob on 2012-06-11
Possibly useful info:

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.6-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.6-3_i386.deb)
  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups-filters/libcupsfilters1_1.0.18-2build1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups-filters/libcupsfilters1_1.0.18-2build1_i386.deb)
  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu48_4.8.1.1-8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu48_4.8.1.1-8_i386.deb)
  Hash Sum mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/opencc/libopencc1_0.3.0-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/opencc/libopencc1_0.3.0-3_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libr/librest/librest-0.7-0_0.7.12-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libr/librest/librest-0.7-0_0.7.12-2_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtheora/libtheora0_1.1.1+dfsg.1-3.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtheora/libtheora0_1.1.1+dfsg.1-3.1_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libshout/libshout3_2.2.2-8_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libshout/libshout3_2.2.2-8_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.26-12_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.26-12_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util2_0.9.4.0+git201206081144.2efeac8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util2_0.9.4.0+git201206081144.2efeac8-0ubuntu1_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib4_0.9.4.0+git201206081144.2efeac8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib4_0.9.4.0+git201206081144.2efeac8-0ubuntu1_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.4.0+git201206081144.2efeac8-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.9.4.0+git201206081144.2efeac8-0ubuntu1_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/x-kit/python-xkit_0.5.0_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/x-kit/python-xkit_0.5.0_all.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-drivers-common/ubuntu-drivers-common_0.2.54_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-drivers-common/ubuntu-drivers-common_0.2.54_i386.deb)
  




Once again I had to use a flash drive to copy that info to a machine with working inter-webs :D

I'll see what happens after a reboot, cleanup, and some CLI magic ;)

---

### Post by dino99 on 2012-06-11
here on i386, network service start but i get the same issue: no network, so after each boot i need to:

gksu gedit /etc/resolv.conf

to add : nameserver 8.8.8.8

save that change, then:

 sudo service network-manager restart

that's usually is enough, but sometimes the previous nameserver entry is wiped, so i need to re-do again.

---

### Post by kansasnoob on 2012-06-11
This was too easy :)

I just rebooted, opened synaptic, reloaded the software info, and finished updating ............... now all is well :)

Such boring breakage :lolflag:

---

### Post by kansasnoob on 2012-06-11
> **dino99 said:**
> here on i386, network service start but i get the same issue: no network, so after each boot i need to:

gksu gedit /etc/resolv.conf

to add : nameserver 8.8.8.8

save that change, then:

 sudo service network-manager restart

that's usually is enough, but sometimes the previous nameserver entry is wiped, so i need to re-do again.

As indicated in my last post mine was very temporary.

---

