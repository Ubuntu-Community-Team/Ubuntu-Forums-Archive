---
title: "help with chroot and imagemagick script"
date: 2008-02-08
forum: Server Platforms
---

### Post by dmizer on 2008-02-08
i am running apache in a chroot environment.  i want to run gallery which requires imagemagick in order to operate correctly.  this means that i must copy the imagemagick and it's dependencies into the chroot.

here is the howto i followed for chrooting apache:
[https://wiki.ubuntu.com/ModChroot](https://wiki.ubuntu.com/ModChroot)

chroot lands in /var/chroot/apache

i found a script for copying the executables for imagemagick:
[http://www.bamweb.nl/index.php?option=com_content&task=view&id=147&Itemid=3](http://www.bamweb.nl/index.php?option=com_content&task=view&id=147&Itemid=3)

to the best of my knowledge, i have adapted the script for my environment, but i need help with the portion highlighted in red:
```
#!/bin/sh
IMAGEMAGICK="/usr/bin/composite /usr/bin/convert /usr/bin/identify"

if [ ! -d /var/chroot/apache/usr/lib ]; then mkdir -p /var/chroot/apache/usr/lib ;fi
if [ ! -d /var/chroot/apache/lib/tls/i686/cmov ]; then mkdir -p /var/chroot/apache/lib/tls/i686/cmov ;fi
if [ ! -d /var/chroot/apache/lib ]; then mkdir -p /var/chroot/apache/lib ;fi
if [ ! -d /var/chroot/apache/usr/bin ]; then mkdir -p /var/chroot/apache/usr/bin ;fi

[COLOR="Red"]LOCALBIN=`ldd $IMAGEMAGICK | grep -v : | grep usr | awk '{print $7}' | grep lib`
LOCALLIB=`ldd $IMAGEMAGICK | grep -v : | grep usr | awk '{print $7}' | grep local | grep -v libexec | grep lib`
LIB=`ldd $IMAGEMAGICK | grep -v : | grep usr | awk '{print $7}' | grep -v local | grep -v libexec | grep lib`
LIBEXEC=`ldd $IMAGEMAGICK | grep -v : | grep usr | awk '{print $7}' | grep libexec`
[/COLOR]
for x in $LOCALBIN
do
  if [ ! -x /var/chroot/apache${x} ]; then
    cp -p $x /var/chroot/apache${x}
    echo Copied $x
  else
    echo /var/chroot/apache$x already executable
  fi
done

for x in $LOCALLIB
do
  if [ ! -r /var/chroot/apache${x} ]; then
    cp -p $x /var/chroot/apache${x}
    echo Copied $x
  else
    echo /var/chroot/apache$x already readable
  fi
done

for x in $LIB
do
  if [ ! -r /var/chroot/apache${x} ]; then
    cp -p $x /var/chroot/apache${x}
    echo Copied $x
  else
    echo /var/chroot/apache$x already readable
  fi
done

for x in $LIBEXEC
do
  if [ ! -r /var/chroot/apache${x} ]; then
    cp -p $x /var/chroot/apache${x}
    echo Copied $x
  else
    echo /var/chroot/apache$x already readable
  fi
done
```

also, please look this over and see if i've missed something.  thank you.

---

