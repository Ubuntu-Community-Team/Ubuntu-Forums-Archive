---
title: "Howto Setup Xbox360 Controller in Edgy Elft"
date: 2006-12-13
forum: Tutorials
---

### Post by redDEADresolve on 2006-12-13
**Getting the Xbox360 Controller Working Edgy**

This guide is meant to be really easy; giving you reasons why you're doing things and explaining how to do them in simple language. Don't be afraid it almost impossible to mess up your system. READ the directions.


**You need to have automake1.9 & kernel-headers for your kernel**
```
sudo apt-get install linux-headers-'uname -r' build-essential
sudo apt-get install automake1.9

```

[B]
First you need to download two files:[/B]
Use these links (right click save as)
```
xpad.c
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c]("http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c")
xpad.h
-[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h]("http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h")
```


**Then your going to make a folder in your home directory called .xpad360 (the dot is to make it hidden)**
```
mkdir ~/.xpad360
```


**Now you are going to place the two files you downloaded (xpad.c & xpad.x) into the folder (.xpad360) you just created.**
1. Go to places->home
2. Once in your home folder either press Ctrl H (control key & h at the same time) or go to view-> show hidden files
3. Paste the two files you downloaded into the folder the folder you created, .xpad360

[B]
Now your going to make a Makefile:[/B]
```
gedit ~/.xpad360/Makefile
```

**And add this to that file and save:**
```
KERNEL_DIR?=/usr/src/linux-headers-2.6.17-10-generic

obj-m := xpad.o

EXTRA_CFLAGS= -I$(shell pwd)

all:
	$(MAKE) modules -C $(KERNEL_DIR) SUBDIRS=$(shell pwd)
```
*It is import that there is an indentation (Tab) before $(Make) in the above file. It will not work without it.
*Note the first line of the make file: **KERNEL_DIR?=/usr/src/linux-headers-2.6.17-10-generic** is my kernel and about 90% of everyone else's. If you followed all these steps and still can't get the file to make. You want to check your folder /usr/src/ and see what kernel your are using and amend the script accordingly.

[B]
Now your going to run the Makefile you just made:[/B] (YOUR NAME should be replaced with your login name)
```
cd /home/<YOUR NAME>/.xpad360
sudo make
```


**Now Your going to add the xpad360 "driver" into the /usb/inputs**
```
sudo cp xpad.ko /lib/modules/$(uname -r)/kernel/drivers/usb/input
```
[B]
Now to finish up:[/B]
```
sudo depmod -a
sudo modprobe xpad
```


**And to reboot:**
```
sudo shutdown -r now
```

Enjoy!

---

### Post by russellchamp on 2007-01-13
Thanks! Great guide! :KS 
Only thing to add is where to find the device location thing whatever...
anyway, you can find the controller device in /dev/input/js0

---

### Post by ebs16 on 2007-02-08
Does this driver work for multiple controllers? I can't seem to get it to work with more than one.  Also, permissions are not set properly for the gamepads.  When I connect an XBOX 360 controller to the PC, it is assigned to the "plugdev" group with no read/write permissions for others.  I can reassign the permissions, but they reset when the computer reboots.  How can I change the default permissions?

Thanks!

---

### Post by po0f on 2007-02-09
ebs16,

I don't know about the multiple controller issue you are having (I only own one right now), but the easiest way to solve your other problem would be to add any users you want to be able to read the device to the plugdev group:

```
[FONT="Courier New"]$ sudo gpasswd -a <user> plugdev[/FONT]
```

Note that you'll have to logout and re-login for the changes to take effect.

There is another solution, but it requires writing your own udev rules.  This solution is definitely more involved, but it is actually easy.
[list]
[*][Create your own udev rules to control removable devices](http://ubuntuforums.org/showthread.php?t=168221):  Written specifically for removable drives, it also applies to any USB device.
[*][Writing udev rules](http://reactivated.net/writing_udev_rules.html):  Nice explanation, more in-depth.
[/list]

---

### Post by dabsan on 2007-02-10
Hope someone can help me ... when I entered the command :-
sudo modprobe xpad

I got this error message :-
FATAL: Error inserting xpad (/lib/modules/2.6.17-11-386/kernel/drivers/usb/input/xpad.ko): Invalid module format

Can anyone tell me what went wrong?  
Many Thanks

---

### Post by po0f on 2007-02-10
dabsan,

Can you post the output of the following command?

```
[FONT="Courier New"]$ uname -r[/FONT]
```

[EDIT]

Are you having any other kernel troubles?  People have been having problems with 2.6.17-11-* kernels.  Have you tried this with 2.6.17-10-*?

---

### Post by dabsan on 2007-02-10
Hi thanks for your message ...

The output was :-   
2.6.17-11-386

---

### Post by dabsan on 2007-02-11
when i execute this command :-
sudo apt-get install linux-headers-'uname -r' build-essential

I get this error :-
E: Couldn't find package linux-headers-uname -r

Hope someone can help. 
Many Thanks

---

### Post by po0f on 2007-02-11
dabsan,

Those are backticks, not single quotes.  On a QWERTY keyboard, the backtick is to the left of the 1 (the key you press with shift to get a tilde ~).

You could also just install linux-headers-2.6.17-11-386 since you know that's what kernel version you are running.

---

### Post by caecusum on 2007-02-16
I followed these instructions and everything seemed to work correctly.  After the reboot, however, not much is happening.  I plugged the controller in, turned it on, and fired up snes9express (the frontend for SNES9X emulator.)  I browed to the configure input section but the system doesn't seem to find any joysticks.  I tried both /dev/js0 (the program's default) and /dev/input/js0 as mentioned earlier in this thread.  Neither seem to exist.  What gives?

By the way, is there any particular USB cable that is necessary for this?  I have one that I bought as a charger for the controller that looked like just a standard USB connection, and it was.  Is this adequate?

edit:  By the way, upon browsing to my /dev/input directory, the only things listed are:
event0 event1 event2 mice mouse0 and ts0
not sure if that's meaningful, seems like there is definitely no joystick detected.

edit 2: Read a few more things online.  I didn't realize that there is an entirely separate wired controller available designed to be used with a PC.  Perhaps my USB charger attachment isn't going to cut it.

---

### Post by caecusum on 2007-02-16
Solved my own problem.  You definitely can't use the standard wireless xbox360 controller with the USB charger kit.  Using a wired controller did the trick, works well.  Thanks for the great HowTo!

---

### Post by dugan on 2007-03-05
Great guide, and great research too. I just bought my 360 controller and, with the help of this guide, got it working within five minutes.

I should really be investigating this myself, but does your guide still work with kernel 2.6.20?

---

### Post by po0f on 2007-03-05
dugan,

No, this is my current struggle with it.  I assume you mean a Feisty kernel when you say 2.6.20?  I got it to compile, but the kernel just does not recognize the Xbox360 controller as a gamepad.  A `sudo tail -fn0 /var/log/messages` will reveal that the kernel thinks of it as a basic USB device, nothing more.  On a side note, the regular Xbox controller works fine (besides the axis issue plagued by many gamepads, search the forum for details).

I would love to play my emulators, but not being able to use a gamepad makes it very frustrating to say the least.  If you uncover any information, please be kind enough to post it back here.  :)

---

### Post by mikeday116 on 2007-03-15
hi i followed your guide but when i rebooted, my controller doesn't seem to respond. None of the lights are on on the controller, but when i go to usb devices the controller definitely is there. when i go to /dev/input , i see that /js0 is present. 

Is there something i didn't do right?

Is there a program to test the controller?

Sorry if my linux lingo isn't too great, i started using ubuntu 3 weeks ago.

Any help would be greatly appreciated.

---

### Post by po0f on 2007-03-16
mikeday116,

You can test the controller with the following command executed from a terminal (Ctrl-C to exit when you're done):

```
$ cat /dev/input/js0
```

To calibrate it, use [jscalibrator](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=jscalibrator&searchon=names&subword=1&version=all&release=all), it has a GUI.  IIRC, the entry for it will show up in Applications->Games.

---

### Post by eaglesfan17 on 2007-03-16
GREAT job! Been looking for something like this. Worked immediately with ePSXe!

---

### Post by MaX on 2007-03-19
I couldn't get this to work at all... do I have to download the xpad from that site? Why isn't it included in the orignal xpad that comes with the kernel?

---

### Post by eaglesfan17 on 2007-03-21
> **MaX said:**
> I couldn't get this to work at all... do I have to download the xpad from that site? Why isn't it included in the orignal xpad that comes with the kernel?

You have to download the xpad files listed.

---

### Post by Nolander on 2007-03-23
hay all

when i type this:
```
 sudo cp xpad.ko /lib/modules/$(uname -r)/kernel/drivers/usb/input
```

I get this:
```
cp: cannot stat `xpad.ko': No such file or directory

```

HELP!!

ta,
Blake

ps while im here any know of any good consol emulators

---

### Post by mikeday116 on 2007-03-25
thanks for the info po0f. 

the controller works great. Just wondering, If I plug in a second controller will it work?

Anyway thanks again for all your help.

---

### Post by leomelo on 2007-03-27
leomelo@RLMeloPComputer:~$ cd /home/leomelo/.xpad360
[email]leomelo@RLMeloPComputer:~/.xpad[/email]360$ sudo make
Password:
make modules -C /usr/src/linux-headers-2.6.20-13-generic SUBDIRS=/home/leomelo/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-13-generic'
  CC [M]  /home/leomelo/.xpad360/xpad.o
/home/leomelo/.xpad360/xpad.c:54:26: error: linux/config.h: No such file or directory
/home/leomelo/.xpad360/xpad.c:62:29: error: linux/usb_input.h: No such file or directory
/home/leomelo/.xpad360/xpad.c: In function ‘xpad_process_packet’:
/home/leomelo/.xpad360/xpad.c:161: warning: implicit declaration of function ‘input_regs’
/home/leomelo/.xpad360/xpad.c: In function ‘xpad_probe’:
/home/leomelo/.xpad360/xpad.c:368: error: ‘SLAB_ATOMIC’ undeclared (first use in this function)
/home/leomelo/.xpad360/xpad.c:368: error: (Each undeclared identifier is reported only once
/home/leomelo/.xpad360/xpad.c:368: error: for each function it appears in.)
/home/leomelo/.xpad360/xpad.c:386: warning: implicit declaration of function ‘usb_to_input_id’
/home/leomelo/.xpad360/xpad.c:451: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
make[2]: *** [/home/leomelo/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/leomelo/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-13-generic'
make: *** [all] Error 2
I get those errors when i enter sudo make

---

### Post by leomelo on 2007-03-27
I change the kernel, and it happens the same as Nolander: cp: cannot stat `xpad.ko': No such file or directory.

---

### Post by EEVOL on 2007-04-16
I've tried this and haven't gotten it to work.  I tried kernel linux-headers-2.6.17-10-generic and linux-headers-2.6.17-11-generic and followed the steps thoroughly with no errors.  Yet when I plug my controller in (wired) the USB port, the light goes on for a second then turns  off.

This is what I get when I do 'sudo tail -fn0 /var/log/messages':
```

Apr 16 00:17:29 joe-laptop kernel: [17180008.624000] usb 2-1: new full speed USB device using uhci_hcd and address 4
Apr 16 00:17:29 joe-laptop kernel: [17180008.836000] usb 2-1: configuration #1 chosen from 1 choice
Apr 16 00:17:29 joe-laptop kernel: [17180008.840000] input: Microsoft Xbox 360 Controller as /class/input/input6
Apr 16 00:17:30 joe-laptop kernel: [17180009.384000] /home/joe/.xpad360/xpad.c: opening device
Apr 16 00:17:30 joe-laptop kernel: [17180009.384000] /home/joe/.xpad360/xpad.c: closing device
Apr 16 00:17:30 joe-laptop kernel: [17180009.440000] /home/joe/.xpad360/xpad.c: opening device
Apr 16 00:17:30 joe-laptop kernel: [17180009.440000] /home/joe/.xpad360/xpad.c: closing device

```

Someone help!

---

### Post by goonies on 2007-05-27
I tried this on Feisty, everything works until I plug in the controller, i get this when using the command mentioned above

```
May 27 10:05:21 oblivion kernel: [  302.150345] usb 5-2.4: USB disconnect, address 5
May 27 10:05:25 oblivion kernel: [  305.875543] usb 5-2.3: new full speed USB device using ehci_hcd and address 6
May 27 10:05:25 oblivion kernel: [  305.969482] usb 5-2.3: configuration #1 chosen from 1 choice
```

---

### Post by Apewall on 2007-06-14
Feisty recognizes my TSZ360Pad (Pelican 360 Controller) but after loading the xpad module, nothing occurs, and js0 is never present, the TSZ360Pad is still listed as an "unknown device."

I would have thought someone may have found an answer of how to fix the 360 controller for feisty (2.6.20-16 kernel). ?:(

---

### Post by Surkow on 2007-06-26
I also can't get this to work with the 2.6.20-16 kernel. My USB driver locked up and I had to manually remove the controller driver to be able to boot. Is there anyone who was able to get it to work with feisty?

---

### Post by Surkow on 2007-06-26
Is there anyone who was able to install the drivers with feisty?

---

### Post by Surkow on 2007-06-27
Bump

---

### Post by adam0509 on 2007-06-27
seems the drivers is integrated in Feisty...

```

$ modinfo xpad
filename:       /lib/modules/2.6.20-16-lowlatency/kernel/drivers/usb/input/xpad.ko
license:        GPL
description:    driver for Xbox controllers
author:         Marko Friedemann <mfr@bmx-chemnitz.de>, Oliver Schwartz <Oliver.Schwartz@gmx.de>, Georg Lukas <georg@op-co.de>, Thomas Pedley <Gentoox@shallax.com>, Edgar Hucek <hostmaster@ed-soft.at>
srcversion:     7EC4E48313512193C8A772E
alias:          usb:v*p*d*dc*dsc*dp*icFFisc5Dip01*
alias:          usb:v*p*d*dc*dsc*dp*ic03isc00ip00*
alias:          usb:v*p*d*dc*dsc*dp*ic58isc42ip00*
depends:        usbcore
vermagic:       2.6.20-16-lowlatency SMP preempt mod_unload 586 
parm:           debug:Debugging (ulong)

```

---

### Post by Surkow on 2007-06-28
> **adam0509 said:**
> seems the drivers is integrated in Feisty...

```

$ modinfo xpad
filename:       /lib/modules/2.6.20-16-lowlatency/kernel/drivers/usb/input/xpad.ko
license:        GPL
description:    driver for Xbox controllers
author:         Marko Friedemann <mfr@bmx-chemnitz.de>, Oliver Schwartz <Oliver.Schwartz@gmx.de>, Georg Lukas <georg@op-co.de>, Thomas Pedley <Gentoox@shallax.com>, Edgar Hucek <hostmaster@ed-soft.at>
srcversion:     7EC4E48313512193C8A772E
alias:          usb:v*p*d*dc*dsc*dp*icFFisc5Dip01*
alias:          usb:v*p*d*dc*dsc*dp*ic03isc00ip00*
alias:          usb:v*p*d*dc*dsc*dp*ic58isc42ip00*
depends:        usbcore
vermagic:       2.6.20-16-lowlatency SMP preempt mod_unload 586 
parm:           debug:Debugging (ulong)

```
I get the following message:

```
modinfo: could not find module xpad
```

Did you install the drivers before with an older kernel?

---

### Post by Surkow on 2007-06-30
Bump

---

### Post by Surkow on 2007-07-28
It seems I my version of the module is borked. My other pc's running Ubuntu do support it. How am I supped to configure the controller? I want to try and use it with [Mupen64]("http://mupen64.emulation64.com/down.htm") but there is no way the controller is recognized.

---

### Post by Surkow on 2007-08-01
Any suggestion how to work with controllers and gamepads in Ubuntu?

---

### Post by Surkow on 2007-08-09
Bump

Edit: five in a row is a bit...not done I think. xD

---

### Post by EXCiD3 on 2007-08-18
Nice work on the thread, however your first command is incorrect, please replace that command with:
```
sudo aptitude install linux-headers-`uname -r` build-essential
```

Just a lil typo you had, using ' instead of `
Makes a big difference though ;)

---

### Post by Surkow on 2007-08-28
I'm running Feisty Fawn and upgraded to the latest Gutsy kernel and still no /dev/input/js0 entry. I tried multiple USB controllers on the front and the back of my  PC. I can't believe that something as simple as this is not recognized.

Edit: all other input devices like gamepads from Piranha seem to work. I guess this is just a driver issue.

---

### Post by Surkow on 2007-09-09
I tried the exact same controller on a different PC and still have the same issues. It's correct that the newer kernels have support included for the xbox(360) controllers. But there are no devices created. After following the guide on the first page of this topic a device node seems to respond on "cat /dev/input/js0". Sadly enough after manually changing the drivers the PC no longer boots till I remove the xbox360 controller. I have posted this many times in this thread that I'm just tired...Can someone explain EXACTLY what they did to make it work?

---

### Post by loctorn on 2007-09-11
Yes I too would like to see a guide on exactly how someone got this to work, I followed the directions that were given on this post and another I found and still haven't gotten my controller to work at all. 

The calibrator program recognizes there is something plugged in, but when I move the sticks it does nothing nor does my controller light up at anytime other then when I first plug it into the USB ports.

This is getting so frustrating that something as simple as this won't work.

Well enough venting.....if someone could please get something up that makes sense and will allow me to use my xbox360 controller on my pc (for ZSNES) I would ever so greatly appreciate it.

Thanks again

---

### Post by Surkow on 2007-09-11
After searching with google for a solution I found a page on ubuntuforums I couldn't find with the lousy search function of vBulletin itself. An edited driver for newer kernels can be found here: [http://ubuntuforums.org/showpost.php?p=2512158&postcount=6](http://ubuntuforums.org/showpost.php?p=2512158&postcount=6)

It solves my boot problem and a device entry is created in /dev/input/js0. I haven't been able to test it yet.

---

### Post by ouellettesr on 2007-10-07
I would like to know if anyone has got this working with gutsy yet. I compiled with the new xpad files as well as the old one and got no errors while installing, but to no avail. I plug my controller in after a reboot and all it does is constantly blink, Also there is no js0. Thanks

---

### Post by dracule on 2007-10-30
> **ouellettesr said:**
> I would like to know if anyone has got this working with gutsy yet. I compiled with the new xpad files as well as the old one and got no errors while installing, but to no avail. I plug my controller in after a reboot and all it does is constantly blink, Also there is no js0. Thanks

same here, 

bob@bob-laptop:~$ cat /dev/input/js0
cat: /dev/input/js0: No such file or directory


no errors when installing, i can modprobe xpad, but still nothing working.

im using wireless btw.

---

### Post by Zauberer on 2007-11-12
Hi everyone!!
For Gutsy, just use: ```
sudo cp -f xpad.ko /lib/modules/$(uname -r)/kernel/drivers/input/joystick/

``` instead of ```
sudo cp -f xpad.ko /lib/modules/$(uname -r)/kernel/drivers/usb/input/

```

---

### Post by Vitamin-Carrot on 2007-11-13
:-(

```

cp: target `/lib/modoles/2.6.22-14-generic/kernel/drivers/input/joystick/' is not a directory: No such file or directory

```

I think i borked it

:-(

---

### Post by Pro75357 on 2007-11-13
> **Vitamin-Carrot said:**
> :-(

```

cp: target `/lib/modoles/2.6.22-14-generic/kernel/drivers/input/joystick/' is not a directory: No such file or directory

```

I think i borked it

:-(

Dude you just spelled modules wrong.

I put the xpad.ko file in that directory, however, and still just get flashing lights.

EDIT: Restarted the machine and no more flashing lights.

---

### Post by Vitamin-Carrot on 2007-11-13
> **Pro75357 said:**
> Dude you just spelled modules wrong.

I put the xpad.ko file in that directory, however, and still just get flashing lights.

EDIT: Restarted the machine and no more flashing lights.

BWAHAHAHAHAHAHAHAHA
I Guess I R Borked
Me Am Bad

---

### Post by Jojo12a on 2007-11-13
see [http://ubuntuforums.org/showthread.php?p=3710762]("http://ubuntuforums.org/showthread.php?p=3710762")

This was actually for gutsy and should work for feisty and gutsy, I just used the wrong thread. Here's the How-To:

To easify the creation of new compiles after kernel updates, I have created a basic module-assistant package. Install it as follows:

```

# first, download [ATTACH]49205[/ATTACH]
# install prerequisites and package (has to be executed wherever you have put the deb
sudo apt-get install module-assistant
sudo dpkg -i xpad360-source_0.0.7_all.deb
# go to the compilation directory
cd /usr/src
# this compiles and installs a new module package
sudo m-a a-i xpad360
```

I also attached the source package ([ATTACH]49206[/ATTACH]) from which I created this. This package could damage your system, kill your cat or set your house on fire, so I don't guarantee anything. It works for me anyway.

---

### Post by HIM_Tattoos on 2008-01-05
bump as xpad.h isn't available to download and if anyone has it I would greatly appreciate it.

---

### Post by EnsignR on 2008-01-05
There is an xpad.h in the archive posted here:
[http://ubuntuforums.org/showpost.php?p=2512158](http://ubuntuforums.org/showpost.php?p=2512158)

I think it's from Feisty though, not sure if there is any difference.

I have been playing around with the source in there trying to get my X360 Controller Wireless Adapter ( 045e:0719 ) working in Gutsy. As yet without any luck.

If anyone has any ideas for that one I'd really appreciate it.



EDIT: I have finally managed to get my WIRELESS controller working under Gutsy by following the instructions (Nicolae's in particular) in this thread: [http://ubuntuforums.org/showthread.php?t=570642](http://ubuntuforums.org/showthread.php?t=570642)

---

### Post by Amirith on 2008-02-04
Ok, how do I do this. I don't understand what you mean by code. Anyone know how to put this into terms where the computer illiterate can under stand?

---

### Post by morse on 2008-12-20
I have recently been given by my cousin a spare x box 360 wireless controller which was on his x box, how do i re -register it to mine, its not currently linked to the internet

---

### Post by cliffemall502 on 2009-03-17
I am confused :-/ 
I cannot get past this part

cd /home/pouesum/.xpad360
sudo make

for some reason my kernel linux headers are 2.6.27-7-generic, 2.6.27-9-generic, 2.6.27-10-generic, and 2.6.27-11-generic

How can I have so many different ones?

[email]pouesum@pouesum-desktop:~/.xpad[/email]360$ sudo make
make modules -C /usr/src/linux-headers-2.6.27-11-generic SUBDIRS=/home/pouesum/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/pouesum/.xpad360/xpad.o
/home/pouesum/.xpad360/xpad.c: In function ‘xpad_open’:
/home/pouesum/.xpad360/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/pouesum/.xpad360/xpad.c: In function ‘xpad_close’:
/home/pouesum/.xpad360/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/pouesum/.xpad360/xpad.c: In function ‘xpad_probe’:
/home/pouesum/.xpad360/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/pouesum/.xpad360/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/pouesum/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/pouesum/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2
[email]pouesum@pouesum-desktop:~/.xpad[/email]360$ 

:-/ Any ideas?

---

### Post by Prof_NARF on 2009-10-05
Change the lines 382 and 408 in xpad.c from
```
struct usb_xpad *xpad = dev->private;
```
to
```
struct usb_xpad *xpad = input_get_drvdata(dev);
```


line 496 from
```
input_dev->cdev.dev = &intf->dev;
```
to
```
input_dev->dev.parent = &intf->dev;
```


and line 497 from
```
input_dev->private = xpad;
```
to
```
input_set_drvdata(input_dev, xpad);
```

I hope this works for you.

This way I made the Microsoft XBox360 Gamepad work under Ubuntu 9.04 - Jaunty Jackalope x64.

---

### Post by Je Et on 2009-11-01
When I try and run:

sudo apt-get install linux-headers-'uname -r' build-essential

I get this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r


Real new @ linux and trying to get away from windoze. Been trying to get my xbox360 (from GameStop) to work with epsxe160. The emulator is working great...please HELP!!!

---

### Post by Je Et on 2009-11-03
found the answer, and I see I posted in the wrong place.  See you in [**Absolute Beginner Talk.**]("http://ubuntuforums.org/forumdisplay.php?f=326")

Je Et

---

### Post by farna on 2009-12-24
I went through the steps with the changes for Jaunty as described by Prof_NARF. I still get an error:

swygert@Living-Room ~/.xpad360 $ sudo make
[sudo] password for swygert: 
make modules -C /usr/src/linux-headers-2.6.17-10-generic SUBDIRS=/home/swygert/.xpad360
make: *** /usr/src/linux-headers-2.6.17-10-generic: No such file or directory.  Stop.
make: *** [all] Error 2


If it makes any difference I am using Mint 8 x64, which is based on Ubuntu Karmic. So what's wrong?

---

### Post by KEE on 2010-11-21
I get this. im using ubuntu 10-04 and also my xpad.ko is under /lib/modules/2.6.32-25-generic/kernel/drivers/input/joystick/lib/modules/2.6.32-25-generic/kernel/drivers/input/joystick ```
sudo make
make modules -C /usr/src/linux-headers-2.6.32-25-generic SUBDIRS=/home/goat/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /home/goat/.xpad360/xpad.o
/home/goat/.xpad360/xpad.c: In function ‘xpad_wireless_connect’:
/home/goat/.xpad360/xpad.c:291: error: implicit declaration of function ‘info’
/home/goat/.xpad360/xpad.c: In function ‘xpad_open’:
/home/goat/.xpad360/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/goat/.xpad360/xpad.c: In function ‘xpad_close’:
/home/goat/.xpad360/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/goat/.xpad360/xpad.c: In function ‘xpad_probe’:
/home/goat/.xpad360/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/goat/.xpad360/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/goat/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/goat/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [all] Error 2
```

---

### Post by skyf3r on 2011-10-24
Mine doesn't want to make due to absence of smp_lock.h in the very recent Oneiric Ocelot. What should I do?

---

