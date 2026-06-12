---
title: "HOWTO: logitech, labtec webcams with qc-usb driver"
date: 2005-08-02
forum: Tutorials
---

### Post by trollzor on 2005-08-02
This is a HOWTO guide to install the logitech webcam drivers from this
sourceforge project [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)


**==Quick n Dirty guide for the brave==**

#kernel headers, compilers and v4l1 for gnome
```
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install build-essential
sudo apt-get install libpt-plugins-v4l
```

#get the driver
```
wget http://optusnet.dl.sourceforge.net/sourceforge/qce-ga/qc-usb-0.6.3.tar.gz
tar zxvf qc-usb-0.6.3.tar.gz
cd qc-usb-0.6.3
```

#become root because script doesn't understand sudo, it whinges a lot about not working, but then it does.
```
sudo -s -H
./quickcam.sh
```



**==Longer Guide==**


**==Checking you have the right webcam==**

you can do this with the command:

```
lsusb
```

Which should give you a couple of lines, one looking like this:

[COLOR=DarkOrange]Bus 002 Device 003: ID 046d:0870 Logitech, Inc. QuickCam Express[/COLOR]

According to the website:

> Generally any USB camera with Vendor Id 0x46d and Product Id 0x840,
0x850, or 0x870 should work

There are other links on [the page](http://qce-ga.sourceforge.net/)  to check out if your camera ID is different. Also there are some other threads on the forums that concern another driver which might work for you if this one doesn't [here](http://ubuntuforums.org/showthread.php?t=44364) and [here](http://ubuntuforums.org/showthread.php?t=46092&page=1&pp=10&highlight=software+webcam). 



**==Extras you need==**

Ok before you can install the driver you need these things and I
describe how to get them next:
[list]
[*]kernel headers for your kerne
[*]compilers to.... compile
[*]video for linux ver 1 interface if you want to use gnomemeeting
[/list] 



**==Installing Kernel Headers==**

Ok if you know how to do this, or have them installed, skip to the next
section.

*the apt-get way*

To make sure they are there:

```
sudo apt-cache search linux-headers-$(uname -r)
```

To install them:

```
sudo apt-get install linux-headers-$(uname -r)
```


*the synaptic way*

Type "uname -r" in a terminal

Then go into synaptic and type "headers"

Grab the package labeled "linux-headers-2.6.10-5-***" that matches your
machine. I don't think it hurts to grab others if you need them.


**==Installing compilers==**

This is a series of compilers your ubuntu distro doesn't come with by default, but are used to make programs from source.

```
sudo apt-get install build-essential
```

OR search synaptic for "build-essential"


**==Installing video for linux ver 1==**

Ubuntu comes with V4L2, but that won't work for gnomemeeting with this driver.

```
sudo apt-get install libpt-plugins-v4l
```

OR search synaptic for "v4l" and tick 'em.




**==Installing the Driver==**

Now that you have the prerequisites go to the quickcam express driver sourceforge page:

[http://sourceforge.net/projects/qce-ga/](http://sourceforge.net/projects/qce-ga/)

Download the qc-usb package to your home folder (~150kb):

```
wget [http://optusnet.dl.sourceforge.net/sourceforge/qce-ga/qc-usb-0.6.3.tar.gz](http://optusnet.dl.sourceforge.net/sourceforge/qce-ga/qc-usb-0.6.3.tar.gz)

```
(N.B. the driver might update in the course of this HOWTO being on the
forums, check the page to make sure.)

uncompress the package:

```
tar zxvf qc-usb-0.6.3.tar.gz
```

enter the folder:

```
cd qc-usb-0.6.3
```

Now the script in the folder doesn't understand sudo, so we have to
become root.

```
sudo -s -H
```

Now run the script, accepting the defaults should be ok, read what
it says, it may give errors, but soldier on because it worked anyway for
me (that said, have you backed up your files?):

```
./quickcam.sh
```


**==Testing==**

Open gnomemeeting, make sure you select v4l and not v4l2 in setup. Should be working. My Labtec cam (which registers as a logitech) is washed out and shifted to the yellow/red side of the spectrum, other cameras should not be, if anyone has a fix for this problem, post it here.


**==Last notes==**

Camera works on reboot without adding "quickcam" to /etc/modules, so you are done. Hope this helps people, I will check in on the guide to correct any typos etc.

good luck, 

Trollzor

---

### Post by Raj on 2005-09-30
Absolute genius

I love you!!! :)

Cheers man. Now all I have to do is find people to chat with, lol

Raj

---

### Post by globalman on 2005-11-18
ok
iam using qc-usb-messenger-0.8
but i follow these steps
everything went fine.. but got missing gcc.
this error

./quickcam.sh
....
Warning: gcc missing

i installed gcc-3.4
and 4.0 is already installed i think by defult
(Ubuntu 5.10 'Breezy Badger')
(kernel-2.6.12-9-386)

what else is missing ?

---

### Post by CarbonPlexus on 2005-11-25
Ok I get to the end of the installer and it says

> Now I finally will try to load the module.
If you're unlucky, your computer might crash right now!!!!
Consider long if you really want to continue.
Press Ctrl+C to quit, Enter to continue --->

You decided to do it, here we go...
=== Leaving root mode ===
The driver detected the following supported cameras:
[!] No cameras detected.
Try unloading and reloading the driver manually with
        rmmod quickcam; insmod ./quickcam.ko debug=-1
and then checking whether there are any messages indicating
problems with command
        dmesg
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.

so then I tried the 2 commands it showed

> k---@M-------:~/Desktop/qc-usb-0.6.3$ rmmod quickcam; insmod ./quickcam.ko debug=-1
insmod: error inserting './quickcam.ko': -1 Operation not permitted
k---@M-------:~/Desktop/qc-usb-0.6.3$ dmesg
[4297560.236000] usbcore: registered new driver quickcam
[4297576.374000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297576.374000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297576.462000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297576.462000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297699.500000] usbcore: deregistering driver quickcam


Any idea what this is about?  I have a Logitech Quickcam Messenger but I got the special driver for it that was moddified from the other Logitech webcams because it's supposed to be slightly different.  Also I see a camera in the Device Manager so it shows up but it's not registering with the driver :confused:  Any thoughts/help would be appreciated ^_^

---

### Post by sabitha on 2005-11-26
how about my webcam driver 

Bus 004 Device 006: ID 0c45:612f Microdia

anybody knows :(

---

### Post by Turtle.net on 2005-11-26
Here is an alternate method :p 
In fact I simply followed the instructions on this site [http://home.mag.cx/messenger/]("http://home.mag.cx/messenger/")

This method should work for 
[LIST]
[*]Quickcam Messenger (0x046D, 0x08F0) & (0x046D, 0x08F6)
[*]Quickcam Communicate (0x046D, 0x08F5)
[/LIST]

I downloaded from this page the driver qc-usb-messenger-0.9.tar.gz (2005-11-21) and untarred this archive in /usr/src/

```
# cd /usr/src/qc-usb-messenger-0.9/
# sudo apt-get install linux-headers-$(uname -r)
# sudo apt-get install build-essential
# sudo apt-get install libpt-plugins-v4l
# make install
# modprobe videodev
# modprobe quickcam

```

And after that I was able to use my Quickcam messenger in Gnomemeeting (automatic detection of the webcam).

According to the same site the button on the webcam should work with special configuration of the kernel (I do not use this function so I never tried...)

Enjoy :razz:

---

### Post by dixonstalbert on 2005-12-10
Thanks Trollzer for very clearly written HOWTO and also to Turtle.net for his alternative method

I ran into some problems trying to replace my old logitech webcam with a new Logitech Quickcam Communicate.

The old drivers prevented installing new ones. I found the answer here 

[http://wiki.ubuntu-fr.org/materiel/webcam_logitech_msn]("http://wiki.ubuntu-fr.org/materiel/webcam_logitech_msn")

on the french ubuntu wiki- very good HOWTO if you speak french

the guide recommends making sure you start by checking to see if any old drivers are loaded  and cleaning them out by typing:

```
lsmod | grep videodev
sudo rmmod quickcam
sudo rmmod videodev
```

after this I was able to successfully install my Quickcam Communicate driver using procedure outlined by turtle.net above

My next problem was that the webcam stopped working after rebooting computer

The french ubuntu wiki page  also gave an answer to that. You have  to put in a startup script in your /etc/init.d directory so driver will unload/reload at startup. you create one by typing:

```
sudo touch /etc/init.d/quickcam && sudo chmod 755 /etc/init.d/quickcam

sudo gedit /etc/init.d/quickcam
#! /bin/sh
# /etc/init.d/quickcam: reload the Logitech Quickcam Communicate driver.
rmmod quickcam
modprobe quickcam

``` 

save and exit out of gedit text editor and type this to put the same script in your /etc/rcS.d/ directory

```
sudo ln -s /etc/init.d/quickcam /etc/rcS.d/S99quickcam
```


after I did this Quickcam Communicate worked without a problem in camorama, xawtv and amsn

hope this helps someone

---

### Post by Neo40 on 2006-01-03
Hi,

I have Breezy installed and it seems my usb quickcam camera is not detected.
If I type lsusb, I got this:

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


Someone can help me?

Thanks

---

### Post by gosh on 2006-01-07
I also have a problem with recoginizing my webcam.

lsusb says:

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:08c5 Logitech, Inc.
Bus 001 Device 002: ID 046d:c01a Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

One logitech device is my mouse, the other should be my quickcam

---

### Post by alinuxfan on 2006-05-31
I get...i did the howto exactly (even copied and pasted)...j
[PHP]./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
Warning: gcc missing
Warning: gcc missing
Warning: make missing
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
Warning: ld missing
/bin/uname
/usr/bin/tr
Warning: xawtv missing
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
[!] Some important programs can not be found on default path.
Probably they aren't installed.
You should install them, for example, by using apt-get or rpm.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->
[/PHP]

ust curious where to go from here...thanks

---

### Post by Turtle.net on 2006-06-01
Hi,
Just looking at the Warning you get I'm wondering : do you installed build-essential ?

---

### Post by shamrock_uk on 2006-07-30
sudo apt-get install xawtv will fix it.

---

### Post by noizatu on 2006-09-25
a cool link to an automatic software for configuring the webcam. I have a Logitech QuickCam Messenger and it's working :-D

[https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)


Thanks to chele for this link!

---

### Post by uboltun on 2007-02-14
I am running a Logitech Quickcam, and I had some problems making it work. I have seen many people having the same exact problem. When running Kopete or Ekiga the progrem just froze. I tried to instal qc-usb driver but that did not fixed the problem. Then I tried something else. I switch the USB port from the one on my monitor to the port on the box and BUM ! It worked ! I hope for some of you thet might help.

lsusb | grep Quick
Bus 004 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express

This is what I had ind dmesg when ekiga froze:
quickcam: Control URB error -2

---

### Post by drummerJOE4036 on 2008-11-18
I'm having some trouble compiling the module with the script. Here are all the error messages I get as I run the script.

I'm running 8.04 hardy, and trying to install a logitech quickcam web (lego camera).

```
I can find the following probably compatible devices:
Bus 001 Device 004: ID 046d:0850 Logitech, Inc. QuickCam Web

```

Please help, thanks.
perhaps relavent system info put out during script
```
Kernel source directory: /lib/modules/2.6.24-21-generic/build
Detected kernel version is 2.6.x.
Kernel version name: 2.6.24-21-generic
Kernel source version code: 132632
Driver file name: quickcam.ko
Module install directory: /lib/modules/2.6.24-21-generic
Driver source directory (PWD):         /home/joe/qc-usb-0.6.6
Kernel source directory (LINUX_DIR):   /lib/modules/2.6.24-21-generic/build
Module install directory (MODULE_DIR): /lib/modules/2.6.24-21-generic
Utility install directory (PREFIX):    /usr/local
User options (USER_OPT):               -DHAVE_UTSRELEASE_H=1
Driver file name (use with insmod):    quickcam.ko	
Kernel version code:                   132632

```




```
gcc version: gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
gcc version: gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Make version: GNU Make 3.81
Linker version: GNU ld (GNU Binutils for Ubuntu) 2.18.0.20080103
Kernel compiler: gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
	export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).

```

later on

```
In file included from /home/joe/qc-usb-0.6.6/qc-driver.c:47:
/home/joe/qc-usb-0.6.6/quickcam.h:129:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/cache.h:4,
                 from include/linux/time.h:7,
                 from include/linux/videodev2.h:59,
                 from include/linux/videodev.h:15,
                 from /home/joe/qc-usb-0.6.6/quickcam.h:95,
                 from /home/joe/qc-usb-0.6.6/qc-driver.c:47:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/joe/qc-usb-0.6.6/qc-driver.c: In function ‘qc_i2c_init’:
/home/joe/qc-usb-0.6.6/qc-driver.c:824: error: ‘struct urb’ has no member named ‘lock’
/home/joe/qc-usb-0.6.6/qc-driver.c:825: warning: assignment from incompatible pointer type
/home/joe/qc-usb-0.6.6/qc-driver.c: In function ‘qc_isoc_start’:
/home/joe/qc-usb-0.6.6/qc-driver.c:1867: warning: assignment from incompatible pointer type
/home/joe/qc-usb-0.6.6/qc-driver.c: At top level:
/home/joe/qc-usb-0.6.6/qc-driver.c:3009: error: unknown field ‘hardware’ specified in initializer
make[2]: *** [/home/joe/qc-usb-0.6.6/qc-driver.o] Error 1
make[1]: *** [_module_/home/joe/qc-usb-0.6.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [quickcam.ko] Error 2
ls: cannot access quickcam.ko: No such file or directory
[!] Looks like the driver compilation failed.

```


Thanks

---

### Post by strN00B on 2008-11-20
i get so many errors!

kernal and gcc are different versions

failed to compile driver
failed to load driver

ahhhh! help

EDIT: The exact as DrummerJOE!! But Im using 8.10

---

### Post by prasopsuk on 2008-11-23
i had try to enable my logitech webcam for couple weeks. but can't working for all of suggestion above. how to correct this problem on ubuntu 8.10?
Thank you.

---

### Post by bluelightav on 2009-01-02
Hi, does anybody know how to get around this one?

./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc version: Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu11' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
gcc version: Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu11' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
Make version: GNU Make 3.81
Linker version: GNU ld (GNU Binutils for Ubuntu) 2.18.93.20081009
Kernel compiler: gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
	export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> ^C

---

### Post by bluelightav on 2009-01-03
Hi Utube,

I am able to read forums. What exactly do you want to suggest? I have a problem with the above instructions. Still no solution. I don't see that my kernel, header and compiler are of different versions.

---

### Post by Doug11 on 2009-01-31
You must remember that guide is about 4 years old.

---

### Post by Veratyr9 on 2009-02-13
yea i just noticed the date AFTER installing all this stuff. none of it worked (for my quickcam pro, oldschool cam).  and i just switched back to my newer quickcam that works fine with ubuntu default drivers.

now my new question, how do i uninstall all this junk i just put on my intrepid box? lol

---

### Post by bbrout on 2012-05-06
I go:

sudo apt-get install libpt-plugins-v4l

and I get:


Unable to locate package libpt-plugins-v4l
 
after running quickcam.sh as according to instruction I get:


Kernel source directory: /lib/modules/3.0.0-16-generic/build
[!] Can not find kernel source or even headers.
Make sure that they are installed (install with e.g. rpm or apt-get
if necessary) and ensure that you have read rights to the files.

and later:

Detected kernel version is 3.0.x.
[!] Kernel major version is not 2, which is completely something
not expected. Either it was misdetected or you are using
not supported kernel version.

[!] Kernel source is not configured properly.
[: 435: y: unexpected operator
You have only kernel headers but they are not configured
properly. It's pointless trying to continue, this won't work.
Either install properly configured kernel headers or full
source with kernel configuration file. In the latter case
I can configure the kernel source using the configuration
file automatically.

and:

Couldn't find KERNEL_UTS version


needless to say, it didn't work. I note it is looking for a different gcc version, but that shouldn't stop it. I think it is the v4l plugin causing the problem. Any suggestions. I'm in KDE with Ubuntu.

---

