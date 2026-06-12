---
title: "error when installing driver for network interface"
date: 2009-05-17
forum: Server Platforms
---

### Post by gobbledigook on 2009-05-17
Hey!

thought i had this on sorted here: [http://ubuntuforums.org/showthread.php?t=1161465](http://ubuntuforums.org/showthread.php?t=1161465)

but it turns out the card was being 'seen' by my router but the drivers for it are not in linux? its a tp-link tg-3269 card and i found people with similar problems here: [http://www.linuxquestions.org/questions/linux-networking-3/network-card-driver-installation-on-gutsy-tp-link-tg-3269-631288/](http://www.linuxquestions.org/questions/linux-networking-3/network-card-driver-installation-on-gutsy-tp-link-tg-3269-631288/) and here: [http://www.howtoforge.com/forums/archive/index.php/t-22047.html](http://www.howtoforge.com/forums/archive/index.php/t-22047.html)

following the above links i copied the .tgx driver file to my home dir and unpacked it. resulting in the following dir tree:

```
 tar -xzvf driver.tgz
r1000_v1.05/
r1000_v1.05/release_note.txt
r1000_v1.05/README
r1000_v1.05/src/
r1000_v1.05/src/Makefile_linux24x
r1000_v1.05/src/r1000_ioctl.c
r1000_v1.05/src/r1000.h
r1000_v1.05/src/Makefile
r1000_v1.05/src/r1000_n.c
r1000_v1.05/Makefile
```

next i ran ```
sudo apt-get install linux-headers-$(uname -r)
```

that updated the headers, i then cd to the driver dir and ran the following commands which came up with errors:

```
/r1000_v1.05$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/home/server/r1000_v1.05/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions
make[1]: Leaving directory `/home/server/r1000_v1.05/src'
make -C src/ modules
make[1]: Entering directory `/home/server/r1000_v1.05/src'
make -C /lib/modules/2.6.27-11-server/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-11-server'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-11-server'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/server/r1000_v1.05/src'
make: *** [modules] Error 2
```

to be honest i'm not great at unpacking and making stuff from src, being a bit of a noob i am used to relying on aptitude! And these errors don't mean much to me:( 

any ideas would be much appreciated, 

thanx!

Dan

---

### Post by gobbledigook on 2009-05-19
hey!

little 'bump' :) any ideas?

---

