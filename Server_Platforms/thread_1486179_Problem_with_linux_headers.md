---
title: "Problem with linux headers"
date: 2010-05-17
forum: Server Platforms
---

### Post by Nunners on 2010-05-17
I'm trying to reinstall asterisk pbx after the server went completely hay-wire, primarily caused by my error in removing something accidentally, and have hit a problem with making the dahdi drivers.

As you will see from the output below, the install can't "see" the linux-headers source. ```
root@asterisk:/usr/src/dahdi-linux-2.2.1.1# make clean
make -C drivers/dahdi/firmware clean
make[1]: Entering directory `/usr/src/dahdi-linux-2.2.1.1/drivers/dahdi/firmware                                                                             '
rm -f dahdi-fw-*.o
make[1]: Leaving directory `/usr/src/dahdi-linux-2.2.1.1/drivers/dahdi/firmware'
root@england:/usr/src/dahdi-linux-2.2.1.1# make
make -C drivers/dahdi/firmware firmware-loaders
make[1]: Entering directory `/usr/src/dahdi-linux-2.2.1.1/drivers/dahdi/firmware                                                                             '
make[1]: Leaving directory `/usr/src/dahdi-linux-2.2.1.1/drivers/dahdi/firmware'
You do not appear to have the sources for the 2.6.31-20-server kernel installed.
make: *** [modules] Error 1
```

I've tried "apt-get source linux-headers-2.6.31-20-server", but still no resolution.  Can anyone give me some advice?

Thanks
Nunners

PS: This is a copy of a thread from the "[Installation &  Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333")" section.

Many thanks
Nunners

---

### Post by arrrghhh on 2010-05-17
That was a pretty poor response over in the installation section...

Looks like you just need the proper command.  I would think this would do it:
```
sudo apt-get install linux-headers-`uname -r`
``` should do it.  


There may be some other dependencies for compiling, build-essentials and g++ come to mind.  Not sure what else is required to compile, let me know if you get stuck.

---

### Post by Nunners on 2010-05-17
Thanks for the response...
Had tried that, but done it again with the following response:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.31-20-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

```

So, don't think that gets me any further?!!!

---

### Post by arrrghhh on 2010-05-17
It says it's already installed/newest version.  So you're probably missing some other depenency required for compiling.

---

### Post by Zeosa on 2010-05-17
Whats the symlink /lib/modules/`uname -r`/build point to?

```

ls -la /lib/modules/`uname -r`/build

```

---

### Post by Nunners on 2010-05-18
```
root@england:/usr/src# ls -la /lib/modules/`uname -r`/build
lrwxrwxrwx 1 root root 39 2010-03-17 08:02 /lib/modules/2.6.31-20-server/build -> /usr/src/linux-headers-2.6.31-20-server
```

I've tried checking for dependancies, but apt-get doesn't come up with anything, so I'm not sure what I'm looking for....

---

### Post by Nunners on 2010-05-18
Looking at that ln though, /usr/src/linux-headers-2.6.31-20-server doesn't exist... so next step - download source etc etc...

---

### Post by Nunners on 2010-05-18
> **Nunners said:**
> Looking at that ln though, /usr/src/linux-headers-2.6.31-20-server doesn't exist... so next step - download source etc etc...

But where to get the source from?  The only thing I can find has a file extension of .deb which i don't think is right?

---

### Post by Zeosa on 2010-05-18
you can download the linux-headers-2.6.31-20-server .deb for your installation and install it with dpkg -i linux-headers-2.6.31-20-server.deb

Strange though, apt-get install linux-headers-`uname -r` should have installed it.

Maybe try removing/purging the package and re-installing before you download a deb ...ie
```

apt-get remove --purge linux-headers-`uname -r`

apt-get install linux-headers-`uname -r`

```

---

### Post by Nunners on 2010-05-20
This is really doing my head in now... what did I do when it all stopped working - god knows... but oh well...

Doing a full purge and reinstall doesn't seem to make any difference ([http://pastebin.com/VqidYeAp](http://pastebin.com/VqidYeAp))... the only difference now is the error is different!

I've also tried using the source from the .deb file - and again still the same problems...

Can anyone think what might be causing it?

Thanks
Nunners

---

### Post by arrrghhh on 2010-05-20
Do you have the other packages required to compile?  Build-essentials comes to mind, I think there's a few others...

---

### Post by Zeosa on 2010-05-20
What he said...

Also, whats the new error?

---

### Post by Nunners on 2010-05-21
> **Zeosa said:**
> What he said...

Also, whats the new error?

```
root@england:/usr/src/dahdi-linux-complete-2.3.0+2.3.0# make clean
make -C linux clean
make[1]: Entering directory `/usr/src/dahdi-linux-complete-2.3.0+2.3.0/linux'
make -C /lib/modules/2.6.31-20-server/build SUBDIRS=/usr/src/dahdi-linux-complete-2.3.0+2.3.0/linux/drivers/dahdi DAHDI_INCLUDE=/usr/src/dahdi-linux-complete-2.3.0+2.3.0/linux/include DAHDI_MODULES_EXTRA=" " HOTPLUG_FIRMWARE=yes clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-server'
make[2]: Makefile: No such file or directory
make[2]: *** No rule to make target `Makefile'. Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-server'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/usr/src/dahdi-linux-complete-2.3.0+2.3.0/linux'
make: *** [clean] Error 2
root@england:/usr/src/dahdi-linux-complete-2.3.0+2.3.0# make
make -C linux all
make[1]: Entering directory `/usr/src/dahdi-linux-complete-2.3.0+2.3.0/linux'
make -C drivers/dahdi/firmware firmware-loaders
make[2]: Entering directory `/usr/src/dahdi-linux-complete-2.3.0+2.3.0/linux/drivers/dahdi/firmware'
make[2]: Leaving directory `/usr/src/dahdi-linux-complete-2.3.0+2.3.0/linux/drivers/dahdi/firmware'
make -C /lib/modules/2.6.31-20-server/build SUBDIRS=/usr/src/dahdi-linux-complete-2.3.0+2.3.0/linux/drivers/dahdi DAHDI_INCLUDE=/usr/src/dahdi-linux-complete-2.3.0+2.3.0/linux/include DAHDI_MODULES_EXTRA=" " HOTPLUG_FIRMWARE=yes modules DAHDI_BUILD_ALL=m
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-server'
make[2]: Makefile: No such file or directory
make[2]: *** No rule to make target `Makefile'. Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-server'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/dahdi-linux-complete-2.3.0+2.3.0/linux'
make: *** [all] Error 2

```

Right, think I'm getting somewhere now... I need to download linux-headers-2.6.31-20 as in the -server it all points to that... hadn't noticed that before...

---

### Post by Nunners on 2010-05-21
Hooray... getting somewhere now...

Downloaded linux-headers-2.6.31-20 and that's done the trick... why wasn't it easy?  Should have been... but then hey, I was the one who messed it up???!!!

Thanks for your help guys...

---

### Post by arrrghhh on 2010-05-21
> **Nunners said:**
> Hooray... getting somewhere now...

Downloaded linux-headers-2.6.31-20 and that's done the trick... why wasn't it easy?  Should have been... but then hey, I was the one who messed it up???!!!

Thanks for your help guys...

So is it fixed?  Please mark thread 'SOLVED' thanks!

---

### Post by Nunners on 2010-05-21
Sure is fixed... thank goodness...

---

