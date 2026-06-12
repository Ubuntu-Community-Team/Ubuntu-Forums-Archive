---
title: "Installation help"
date: 2008-08-15
forum: Virtualisation
---

### Post by Drezard on 2008-08-15
Hey, 

Trying to install something (Vmware server) my ubuntu server 8.04 and Vmware server keeps asking for 'libX11.so.6' which isn't there supposedly. So instead of being a normal user (ewww) and running straight to this forum, i did a little research into what libX11.so.6 is... but, the only way I could find to replace it was to use this command and install a few libs:

```

sudo apt-get install ia32-lib-sdl ia32-libs ia32asound2

``` 

Only problem was it couldn't find ia32-lib-sdl (im guessing because im on a server edition and not a desktop edition). Are there any alternatives to installing this? Vmware wont let me enter a serial key (odd why it needs this for a serial key???) without it.

Daniel

---

### Post by overdrank on 2008-08-15
Moved :)

---

### Post by cknowlto on 2008-10-29
> **Drezard said:**
> Hey, 

Trying to install something (Vmware server) my ubuntu server 8.04 and Vmware server keeps asking for 'libX11.so.6' which isn't there supposedly. So instead of being a normal user (ewww) and running straight to this forum, i did a little research into what libX11.so.6 is... but, the only way I could find to replace it was to use this command and install a few libs:

```

sudo apt-get install ia32-lib-sdl ia32-libs ia32asound2

``` 

Only problem was it couldn't find ia32-lib-sdl (im guessing because im on a server edition and not a desktop edition). Are there any alternatives to installing this? Vmware wont let me enter a serial key (odd why it needs this for a serial key???) without it.

Daniel

Also having this problem.  Could use a hand. :confused:

---

### Post by bodhi.zazen on 2008-10-29
> **cknowlto said:**
> Also having this problem.  Could use a hand. :confused:

Take a look at the sticky at the top of the forum :)

---

### Post by cknowlto on 2008-10-29
I did.  This command does not work...

```
sudo apt-get install ia32-libs
Reading package lists... Done.
Building dependency tree
Reading state information ... Done.
E: Couldn't find package ia32-libs
```

...and yes, I checked sources.list to make sure that the universe and multiverse repositories are not commented out.

Is there a ia32-libs-server package of some sort?

---

### Post by bodhi.zazen on 2008-10-29
It is in Universe

Or you can download it from here :

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ia32-libs](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ia32-libs)

my only guess would be to update your package list ?

```
sudo apt-get update
```

---

### Post by cknowlto on 2008-10-29
ahhhh!  That might explain it.   My architecture is 64 bit intel xeon processors, not AMD.  There appears to be no support for those 32 bit libraries for 64bit intel, at least not that I can see.  I freely admit to my noobness where this is concerned though :)

---

### Post by cknowlto on 2008-10-29
hmmmm.... I wonder if I could build them...  This IS supposed to be a learning process for me.

---

### Post by bodhi.zazen on 2008-10-29
> **cknowlto said:**
> ahhhh!  That might explain it.   My architecture is 64 bit intel xeon processors, not AMD.  There appears to be no support for those 32 bit libraries for 64bit intel, at least not that I can see.  I freely admit to my noobness where this is concerned though :)

I have those libs installed from the Ubuntu repos on a xeon core, no problem.

"AMD" is a (poor) "generic" term for 64 bit arch (in Ubuntu-land) and does not mean it is only for AMD processors.

Did you install 64 bit or32 bit Ubuntu ?

---

### Post by cknowlto on 2008-10-30
64 bit server edition.  This will be a VMWare platform exclusively, so I wanted as small an ubuntu footprint as possible.  The VMWare bare metal install does not support my hardware unfortunately.  This is a prototype box to proof-of-concept an embedded software simulator, so however I get there is probably not as important as proving that it can be done.

---

### Post by cknowlto on 2008-10-30
OK ,after spending most of today struggling to get the damm usb ports to recognize my usb key and mount the fs on it (which I could not manage) I finally ftp'd that package to the machine and did the following:

sudo dpkg -i /tmp/ia32-libs_2.2ubuntu11_amd64.deb
dpkg: error processing /tmp/ia32-libs_2.2ubuntu11_amd64.deb (--install)
package architecture (amd64) does not match system (i386)
...

---

### Post by bodhi.zazen on 2008-10-30
What is the output of :

```
uname -a
```

---

### Post by cknowlto on 2008-10-30
Linux ubuntutest1 2.6.24-19-server #1 SMP Wed Aug 20 23:54:28 UTC 2008 i686 GNU/Linux

---

### Post by bodhi.zazen on 2008-10-30
You have 32 bit ubuntu, either install the 64 bit version ("amd i86_64") or install the 32 bit package on your current server.

Likewise with VMWare (you need the 32 bit package or install the 64 bit server and use VMware 64 bit).

---

### Post by cknowlto on 2008-10-30
ARRRGGGH!!  Noob sickness strikes again!  

TYVM!  

Unfortunately this means I have to start all over!  Dang it, I could swear I got the 64 bit version of server...

---

