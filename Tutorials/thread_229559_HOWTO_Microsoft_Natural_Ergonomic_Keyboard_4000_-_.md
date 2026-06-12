---
title: "HOWTO: Microsoft Natural Ergonomic Keyboard 4000 - enabling special keys"
date: 2006-08-04
forum: Tutorials
---

### Post by zerwas on 2006-08-04
[CENTER][SIZE="4"]How to get Microsoft Natural Ergonomic Keyboard 4000 (MSNEK4K) to work **completely** with Ubuntu[/SIZE]
[IMG]http://www.notebooksbilliger.de/image.php/microsoft_natural_ergonomic_keyboard_4000[/IMG][/CENTER]

*Please note*: Information in this posting may be outdated as i don't own this keyboard anymore. Have a look at the rest of this thread. For example, abid_naqvi83 managed to get the slider [working]("http://ubuntuforums.org/showpost.php?p=11336640&postcount=178").

Second note: The zoom wheel currently only works by applying another patch to the kernel. I can't test it at the moment so i need some acknowledge that it works. See *Appendix*[3].

**[CENTER][SIZE="5"]= Solution 1 =[/SIZE]**(use a newer kernel)[/CENTER]

Upgrade to kernel 2.6.24 or higher (included in Ubuntu 8.04 already for example) which includes the drivers for MSNEK4K. In order to do that, follow [this]("http://ubuntuforums.org/showthread.php?t=646755") tutorial. This solution should not be riskier than compiling the kernel by yourself. You should always be cautious when it comes to the kernel, whether you use solution 1 or 2.



**[CENTER][SIZE="5"]= Solution 2 =[/SIZE]**(recompile your old kernel)[/CENTER]

[LIST=1]
[*]Follow the [*_HOWTO_*]("http://ubuntuforums.org/showthread.php?t=311158") for compiling the kernel from kernel.org. Instead of step 6 and 7 of the kernel howto, perform this: ```
sudo cp /boot/config-`uname -r` .config && sudo make oldconfig
```
After this command, the kernel will be patched like this:


[*]Download the attachment of this post


[*]Unpack the package:
```
unzip msnek4k-patchset.zip -d /tmp
```


[*]Patch the kernel:```
sudo patch -p1 < /tmp/msnek4k-patchset
```


[*]Now, type ```
make xconfig
```A configuration window pops up. Now, follow the [performance tips]("http://ubuntuforums.org/showpost.php?p=1174954&postcount=507"). After this, go to *Device Drivers* --> *USB*, activate *"HID Simple Driver Interface"*" and change *Microsoft Natural Ergonomic Keyboard 4000 Driver*" to "**m**". If you can't find it in the configuration hierarchy, you can also press CTRL+F and type *simple* in the search box.


[*]Go ahead with the howto (step 10 is the next). After all steps are done, the keyboard should work.
[/LIST]

[CENTER][SIZE="4"]= Appendix =[/SIZE][/CENTER]
[SIZE="1"][LIST]
[*][1] [HOWTO for Slackware 12.0 users]("http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Natural_Ergonomic_Keyboard_4000_in_X_on_Slackware_12_0") (including nice Xmodmap file)
[*][2] [Launchpad bug entry]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84965")
[*][3] [Launchpad bug entry for zoom wheel]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264287")
[*][4] There is a good resource for information on getting this keyboard "working" under Linux in general in the [Gentoo MSNEK4K HOWTO]("http://gentoo-wiki.com/HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000")
[/LIST][/SIZE]

*Thanks:*
[LIST]
[SIZE="1"]
[*]Thank you [alsuren]("http://ubuntuforums.org/member.php?u=325394") for pointing me to the fact that 2.6.24 now supports it.
[*]Credit for the kernel-howto goes to [_master_kernel_]("http://ubuntuforums.org/member.php?u=201430")
[*]I'd also like to thank trantorvega for the Gentoo-Page.
[*][_strabes_]("http://ubuntuforums.org/member.php?u=127592") for clarifying a few things.
[*]And, most of the work to get your keyboard working did [_Liyu_]("http://ubuntuforums.org/member.php?u=150309") for you! [SIZE="1"](the Patch is also available at [_http://lkml.org/_]("http://lkml.org/") from [_liyu_]("http://groups.google.de/groups/profile?enc_user=t81lOhQAAACCDIdHxTwHAJ5EM1tIJ6nKOPANdqfI6prRsqjc7uCt1A&hl=de"))[/SIZE][/SIZE]
[/LIST]

---

### Post by zerwas on 2006-08-05
This should be the correct instructions to install the patch. On my pc, the Favorites-Buttons still doesn't work with version 0.3.0. :( (they don't give a keycode)
Perhaps anybody has ideas or can tell me that it works for him :)

Greetings,
zerwas

---

### Post by boom2k1 on 2006-08-10
Thanks!!!!

Question though.
When I do:

sudo patch -pl /home/charles/installing/4000/msnek4k.patch
patch: **** strip count l is not a number


What does it mean?
Thanks!

---

### Post by boom2k1 on 2006-08-10
eh.. i think i forgot to change the Ergonomic 4000 to "m"

what will happen?

---

### Post by zerwas on 2006-08-11
> **boom2k1 said:**
> sudo patch -pl /home/charles/installing/4000/msnek4k.patch
patch: **** strip count l is not a number

What does it mean?
You typed the letter "l" instead of the number "1". That's what the program patch is complaining about ;)
At best you copy and paste these lines into your terminal:
```
sudo patch -p1 < /home/charles/installing/4000/simple.patch
sudo patch -p1 < /home/charles/installing/4000/msnek4k.patch
```

> eh.. i think i forgot to change the Ergonomic 4000 to "m"
Changing to "m" means to compile the driver for your keyboard as a module.
If you don't do this, it won't work.

---

### Post by unixfudotnet on 2006-08-11
The patches don't seem to apply cleanly anymore.
> 
root@chris-desktop:/usr/src# ls -l
total 40364
lrwxrwxrwx  1 root src        14 2006-08-11 06:49 linux -> linux-2.6.17.7
drwxrwxrwx 19 root root     4096 2006-07-24 23:36 linux-2.6.17.7
-rw-r--r--  1 root src  41283287 2006-07-24 23:40 linux-2.6.17.7.tar.bz2

root@chris-desktop:/usr/src# patch -p0 < /tmp/simple.patch
patching file linux-2.6.17.7/drivers/usb/input/hid-core.c
Hunk #1 FAILED at 4.
Hunk #4 FAILED at 49.
Hunk #5 FAILED at 797.
Hunk #6 FAILED at 853.
Hunk #7 FAILED at 1997.
Hunk #8 FAILED at 2013.
Hunk #9 FAILED at 2048.
Hunk #10 FAILED at 2195.
Hunk #11 FAILED at 2291.
Hunk #12 FAILED at 2307.
10 out of 12 hunks FAILED -- saving rejects to file linux-2.6.17.7/drivers/usb/input/hid-core.c.rej
patching file linux-2.6.17.7/drivers/usb/input/hid.h
Hunk #2 FAILED at 381.
Hunk #3 succeeded at 449 with fuzz 2.
1 out of 3 hunks FAILED -- saving rejects to file linux-2.6.17.7/drivers/usb/input/hid.h.rej
patching file linux-2.6.17.7/drivers/usb/input/hid-input.c
Hunk #2 succeeded at 37 with fuzz 2.
Hunk #3 FAILED at 65.
Hunk #4 succeeded at 853 with fuzz 1.
1 out of 4 hunks FAILED -- saving rejects to file linux-2.6.17.7/drivers/usb/input/hid-input.c.rej
patching file linux-2.6.17.7/drivers/usb/input/hid-simple.h

root@chris-desktop:/usr/src# patch -p0 < /tmp/msnek4k.patch
patching file linux-2.6.17.7/drivers/usb/input/usbnek4k.c
patching file linux-2.6.17.7/drivers/usb/input/Kconfig
Hunk #1 FAILED at 326.
1 out of 1 hunk FAILED -- saving rejects to file linux-2.6.17.7/drivers/usb/input/Kconfig.rej
patching file linux-2.6.17.7/drivers/usb/input/Makefile
Hunk #1 FAILED at 44.
1 out of 1 hunk FAILED -- saving rejects to file linux-2.6.17.7/drivers/usb/input/Makefile.rej



---

### Post by liyu on 2006-08-18
I am "liyou", but should be "liyu". :) 
Regarding to 5 my favorites keys,  I also found they can not work under default XKB configuration (XkbModel pc105 for
 me at least), in other words, I think this is a problem of XKB configuration, if you insert evbug.ko into kernel, you can see
the keycode is yield in system log or dmesg when we press and release these five keys. I still am beginner of the XKB
 configuration, I will reply here at once if I configure them successfully.;) 

I can not sure what problem the friend unixfudotnet have](*,) , this patch both should be can apply on 2.6.17.7 and 2.6.17.8
kernel code tree. but not 2.6.18.x so far. Do you eager to try new 2.6.18 kernel? if so, I also will release them.
The latest patch can be downloaded from linux-usb-devel maillist. I use them as example. Follow is my
process of playing this patch.

I recommend you use 0.3.1, the reason is not only it add force-feedback support, but also include some bugfixes.

[root@liyu tmp]# ls -l linux-2.6.17.7.tar.bz2 linux-2.6.17.8.tar.bz2
-rw-rw-r--  1 sailor sailor 41283287  8&#26376;  5 13:23 linux-2.6.17.7.tar.bz2
-rw-rw-r--  1 sailor sailor 41276096  8&#26376;  7 17:34 linux-2.6.17.8.tar.bz2
[root@liyu tmp]# tar jxf linux-2.6.17.8.tar.bz2
[root@liyu tmp]# mv linux-2.6.17.8 linux-2.6.17.7
[root@liyu tmp]# patch -p0 < patches/hid-simple-0.3.1.patch
patching file linux-2.6.17.7/drivers/usb/input/hid-core.c
patching file linux-2.6.17.7/drivers/usb/input/hid.h
patching file linux-2.6.17.7/drivers/usb/input/hid-input.c
patching file linux-2.6.17.7/drivers/usb/input/hid-simple.c
patching file linux-2.6.17.7/drivers/usb/input/hid-simple.h
[root@liyu tmp]# patch -R -p0 < patches/hid-simple-0.3.1.patch
patching file linux-2.6.17.7/drivers/usb/input/hid-core.c
patching file linux-2.6.17.7/drivers/usb/input/hid.h
patching file linux-2.6.17.7/drivers/usb/input/hid-input.c
patching file linux-2.6.17.7/drivers/usb/input/hid-simple.c
patching file linux-2.6.17.7/drivers/usb/input/hid-simple.h
[root@liyu tmp]# mv linux-2.6.17.7 linux-2.6.17.8
[root@liyu tmp]# tar jxf linux-2.6.17.7.tar.bz2
[root@liyu tmp]# patch -p0 < patches/hid-simple-0.3.1.patch
patching file linux-2.6.17.7/drivers/usb/input/hid-core.c
patching file linux-2.6.17.7/drivers/usb/input/hid.h
patching file linux-2.6.17.7/drivers/usb/input/hid-input.c
patching file linux-2.6.17.7/drivers/usb/input/hid-simple.c
patching file linux-2.6.17.7/drivers/usb/input/hid-simple.h
[root@liyu tmp]# patch -p0 -R < patches/hid-simple-0.3.1.patch
patching file linux-2.6.17.7/drivers/usb/input/hid-core.c
patching file linux-2.6.17.7/drivers/usb/input/hid.h
patching file linux-2.6.17.7/drivers/usb/input/hid-input.c
patching file linux-2.6.17.7/drivers/usb/input/hid-simple.c
patching file linux-2.6.17.7/drivers/usb/input/hid-simple.h
[root@liyu tmp]# LANG=C rpm -qi patch
Name        : patch                        Relocations: (not relocatable)
Version     : 2.5.4                             Vendor: Red Hat, Inc.
Release     : 19                            Build Date: Wed Feb 18 00:12:33 2004
Install Date: Mon Feb 13 15:06:14 2006      Build Host: tweety.devel.redhat.com
Group       : Development/Tools             Source RPM: patch-2.5.4-19.src.rpm
Size        : 102492                           License: GPL
Signature   : DSA/SHA1, Fri May  7 05:33:41 2004, Key ID b44269d04f2a6fd2
Packager    : Red Hat, Inc. <http://bugzilla.redhat.com/bugzilla>
URL         : [http://www.gnu.org/software/patch/patch.html](http://www.gnu.org/software/patch/patch.html)
Summary     : The GNU patch command, for modifying/upgrading files.
Description :
The patch program applies diff files to originals.  The diff command
is used to compare an original to a changed file.  Diff lists the
changes made to the file.  A person who has the original file can then
use the patch command with the diff file to add the changes to their
original file (patching the file).
 
Patch should be installed because it is a common way of upgrading
applications.


I hope this can help you a bit.

---

### Post by liyu on 2006-08-19
You can find this patch for 2.6.18-rc4 here: 

[http://marc.theaimsgroup.com/?l=linux-usb-devel&m=115597610700839&w=2](http://marc.theaimsgroup.com/?l=linux-usb-devel&m=115597610700839&w=2)

---

### Post by Lunar_Lamp on 2006-08-25
I had the same problem as previously when trying to get the patch to apply...

---

### Post by skaramanger on 2006-09-03
> **liyu said:**
> You can find this patch for 2.6.18-rc4 here: 

[http://marc.theaimsgroup.com/?l=linux-usb-devel&m=115597610700839&w=2](http://marc.theaimsgroup.com/?l=linux-usb-devel&m=115597610700839&w=2)

Greetings Liyu,


I too get patch errors. So, I cut and pasted the text from the above link.  I am attempting to compile the 2.6.17.7  kernel. Do I need to modify the diff line before I proceed? The comments in the post state that file is also a patch for my kernel. I have come over from Mandriva earlier this year, I have compiled my own kernel before just not used/modified patch files. I just know enough to be dangerous :>.

```
diff -Naurp linux-2.6.18-rc4/drivers/usb/input.orig/hid-core.c linux-2.6.18-rc4/drivers/usb/input/hid-core.c
--- linux-2.6.18-rc4/drivers/usb/input.orig/hid-core.c	2006-08-19 15:53:28.000000000 +0800
+++ linux-2.6.18-rc4/drivers/usb/input/hid-core.c	2006-08-19 15:49:24.000000000 +0800
```

Thanx

---

### Post by remmelt on 2006-09-11
No go for me either. Patch files from the first post throw hunk errors (10 out of 12 went wrong.) Could you please create a zipfile with working patches. That would be great! I'm looking forward to having these buttons work again.

Under Gnome at least some of them work, like calculator, play, volume, mail. Not bad for a start. Under KDE, nothing goes.

---

### Post by ydef on 2006-09-21
Had no problems applying the patch to 2.6.17 kernel using the beyond3 patchset.

Thanks liyu!

I've noticed the improvements, like the un-flocked keys are mostly functional now, plus all the other keys except the five my favorite keys at the center top and the my favorites key itself still don't work as you had mentioned in your message here, however neither does the zoom switch.  However, the back and forward buttons DO work!

But of the 12 new un-flocked keys, my F5 and F10 keys don't register at all using xev.

So in total the zoom switch, Open and Spell button (aka un-flocked F5 and F10), MyFav button and Five buttons above it, totaling 8 still non-working buttons plus zoom switch.

But good going getting the other un-flocked buttons finally working, plus the forward and back keys with your latest 0.3.1 update Liyu!

Anyone else have this issue?

---

### Post by Angafirith on 2006-09-21
You might want to check your xmodmap settings to see if the zoom switch has a defined function. I had to set mine manually.

The relevant settings:
```
keycode 182 = XF86ZoomIn
keycode 183 = XF86ZoomOut
```

I configured the compiz zoom plugin to use these keys for zooming in and out. This means that when I use the slider, it actually zooms into the screen. The attached screenshot shows exactly what I see when I zoom part of the way.

Under windows, all I ever saw it do was increase or decrease the text size, but I only really tried it in Internet Explorer.

---

### Post by skaramanger on 2006-09-22
Greetings Angafirith;

I've seen links for using xmodmap settings in these forums. However, it gets confusing, regarding the difference between patching and compiling a kernel and using xmodmap.  Could you post some details of your configuration.  I'm using Xfce with gnome services.

[QUOTE=Angafirith;1527875]You might want to check your xmodmap settings to see if the zoom switch has a defined function. I had to set mine manually.

How does the kernel method work differently that using xmodmap?  Are there any issues regarding complexity/reliability.

The relevant settings:
```
keycode 182 = XF86ZoomIn
keycode 183 = XF86ZoomOut
```

I configured the compiz zoom plugin to use these keys for zooming in and out. This means that when I use the slider, it actually zooms into the screen. The attached screenshot shows exactly what I see when I zoom part of the way.

What is the compiz plugin? Please elaborate a little.  

Thanks,
:) 
<snip>

---

### Post by ydef on 2006-09-23
Sweet, thanks angafarith for the tip on the zoom angle.  After a recompile I also got my open and spell buttons working too.

So now I've got my back and forward buttons set as shortcuts to flip between desktops and I've set shortcuts for my zoom buttons to flip focus control between windows on a desktop.   And I can still use my zoom stick to increase and decrease text size in my browser by using the 'block global shortcuts' shortcut.  Righteous!

Hard to imagine how evolved keyboards will be in a hundred years time, likely putting every finger to work with as little motion as possible.  Still got a long way to go, but this keyboard is definitely an improvement once you have all the details working.

Now if we could just get those favorite buttons working. ;)

---

### Post by trantorvega on 2006-09-26
In these last hours I've written a Howto on th Gentoo Wiki including all the steps to get the keybard working, including a method I found to get ALL the keys events reported by X, along with my modification to several xkb files, geometry included.
I believe it might interest those of you struggling with the big numbered keys:
[http://gentoo-wiki.com/HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000]("http://gentoo-wiki.com/HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000")
Feel free to add comments or pm me.
Btw thanks again liyu for your work!!

---

### Post by liyu on 2006-09-26
I am really not familiar with the X configuration. Thanks trantorvega for your great work. :KS so we can enjoy all fun from this keyboard. 

Also, Welcome to China. :) 

Goodluck.

---

### Post by trantorvega on 2006-09-26
I've some questions liyu. Not being a kernel hacker I've not understood how keycodes are actually generated and if their values are hardwired into the keyboard. Is differentiating the codes generated by Favorites/Down Arrow and One/Print (so that each key generates a different keycode) possible?

---

### Post by Angafirith on 2006-09-27
> **skaramanger said:**
> 
How does the kernel method work differently that using xmodmap?  Are there any issues regarding complexity/reliability.

There is no difference. You have to patch the kernel for the xmodmap settings to work properly. My post was really intended to help ydef with his zoom slider.

Regarding your problem, I have no idea what to say. I was able to apply the patch to a vanilla kernel without any trouble at all.
> 
What is the compiz plugin? Please elaborate a little. 
Compiz is a window manager designed for use with XGL or AIGLX. It has plugins that allow you to do some cool things, like have wobbling windows or zoom into the screen. I configured the zoom slider with this plugin so that it actually zooms in and out of the screen, rather than just enlarge the text size.

---

### Post by Lunar_Lamp on 2006-09-27
For those who are having trouble applying this patch what you need to do is get the THREE files that are linked to on the gentoo page and apply them in order.  Also, there are text bits at the start and end of those files that need to be deleted.  The stuff at the end is fairly obvious, but at the start you need to remove the stuff up (but not including) the "diff..." part.  This is usually preceded by something like "signed off by liyu".

I've attached the 3 files I used to get it to patch on 2.6.17.7 - I don't know if order is important but I did "core" "simple" "msek" files in that order.

I'm not sure but I think you may need to edit the top part of the files in the "diff" statement to suit your kernel version if you're using a kernel other than 2.6.17.7.

---

### Post by trantorvega on 2006-09-27
In order tho apply the patches you only need to cd /path/of/kernel_sources 
(cd /usr/src/linux for example) and then patch -p1 < /path/of/your/patch .

P.S.

The howto on gentoo-wiki is still a work in progress. I keep adding informations or notes. Several problems and possible solutions have come up, along with suggestions and questions. If you have any of these feel free to comment here: [http://gentoo-wiki.com/Talk:HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000]("http://gentoo-wiki.com/Talk:HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000")

---

### Post by liyu on 2006-09-27
> **trantorvega said:**
> I've some questions liyu. Not being a kernel hacker I've not understood how keycodes are actually generated and if their values are hardwired into the keyboard. Is differentiating the codes generated by Favorites/Down Arrow and One/Print (so that each key generates a different keycode) possible?

You are welcome.

No, as we want:D, these keycodes are not hardwired into this keyboard. they are defined in the ${KERNEL_SOURCE_TREE}/include/linux/input.h, I think they are a part of the Linux input interface. so, in principle, we can let one key generate more than one keycodes. Well, I am going to experiment with this.

And, yes, as the guess in your email, I am chinese.

Thanks.

---

### Post by liyu on 2006-09-28
This is  you want to get. The My Favorites, Redo, and five custom keys can yield two keycodes,  and one of both is less than 255, follow is the mapping:

KEY_FAVORITES ==> KEY_F16 (186)
KEY_REDO ==> KEY_F17 (187)
KEY_CUSTOM1  ==> KEY_F18 (188)
KEY_CUSTOM2  ==> KEY_F19 (189)
KEY_CUSTOM3  ==> KEY_F20 (190)
KEY_CUSTOM4  ==> KEY_F21 (191)
KEY_CUSTOM5  ==> KEY_F22 (192)

Here is the source, and I found there is a problem in the hid simple driver layer,  I will release these sources/patches for 2.6.18 vanilla kernel later, however, I should go home now. :-D 

/*
 *  Microsoft Natural Ergonomic Keyboard 4000 Driver
 *
 *  Version:	0.3.2
 *
 *  Copyright (c) 2006 Li Yu <raise.sail@gmail.com>
 */

/*
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of the GNU General Public License as published by the Free
 * Software Foundation; either version 2 of the License, or (at your option)
 * any later version.
 */

#include <linux/kernel.h>
#include <linux/input.h>
#include "hid.h"
#include "hid-simple.h"

#define USAGE_ZOOM_IN 0x22d
#define USAGE_ZOOM_OUT 0x22e
#define USAGE_HOME	0x223
#define USAGE_SEARCH	0x221
#define USAGE_EMAIL	0x18a
#define USAGE_FAVORITES	0x182
#define USAGE_MUTE	0xe2
#define USAGE_VOLUME_DOWN	0xea
#define USAGE_VOLUME_UP	0xe9
#define USAGE_PLAY_PAUSE	0xcd
#define USAGE_CALCULATOR	0x192
#define USAGE_BACK	0x224
#define USAGE_FORWARD	0x225
#define USAGE_CUSTOM	0xff05

#define USAGE_CUSTOM_RELEASE	0x0
#define USAGE_CUSTOM_1	0x1
#define USAGE_CUSTOM_2	0x2
#define USAGE_CUSTOM_3	0x4
#define USAGE_CUSTOM_4	0x8
#define USAGE_CUSTOM_5	0x10

#define USAGE_HELP	0x95
#define USAGE_UNDO	0x21a
#define USAGE_REDO	0x279
#define USAGE_NEW	0x201
#define USAGE_OPEN	0x202
#define USAGE_CLOSE	0x203

#define USAGE_REPLY	0x289
#define USAGE_FWD	0x28b
#define USAGE_SEND	0x28c
#define USAGE_SPELL	0x1ab
#define USAGE_SAVE	0x207
#define USAGE_PRINT	0x208

#define USAGE_KEYPAD_EQUAL 0x67
#define USAGE_KEYPAD_LEFT_PAREN 0xb6
#define USAGE_KEYPAD_RIGHT_PAREN 0xb7

#define MSNEK4K_ID_VENDOR	0x045e
#define MSNEK4K_ID_PRODUCT	0x00db

static struct usb_device_id nek4k_id_table[] = {
	{
		USB_DEVICE(MSNEK4K_ID_VENDOR, MSNEK4K_ID_PRODUCT)
	},
	{}
};

MODULE_DEVICE_TABLE(usb, nek4k_id_table);

static char driver_name[] = "Microsoft Natural Ergonomic Keyboard 4000";

struct usage_block consumer_usage_block[] = {
	USAGE_BLOCK(USAGE_ZOOM_IN, 0, EV_KEY, KEY_F13, 0),
	USAGE_BLOCK(USAGE_ZOOM_OUT, 0, EV_KEY, KEY_F14, 0),
	USAGE_BLOCK(USAGE_HOME, 0, EV_KEY, KEY_HOMEPAGE, 0),
	USAGE_BLOCK(USAGE_SEARCH, 0, EV_KEY, KEY_SEARCH, 0),
	USAGE_BLOCK(USAGE_EMAIL, 0, EV_KEY, KEY_EMAIL, 0),
	USAGE_BLOCK(USAGE_FAVORITES, 0, EV_KEY, KEY_F16, 0),
	USAGE_BLOCK(USAGE_FAVORITES, 0, EV_KEY, KEY_FAVORITES, 0),
	USAGE_BLOCK(USAGE_MUTE, 0, EV_KEY, KEY_MUTE, 0),
	USAGE_BLOCK(USAGE_VOLUME_DOWN, 0, EV_KEY, KEY_VOLUMEDOWN, 0),
	USAGE_BLOCK(USAGE_VOLUME_UP, 0, EV_KEY, KEY_VOLUMEUP, 0),
	USAGE_BLOCK(USAGE_PLAY_PAUSE, 0, EV_KEY, KEY_PLAYPAUSE, 0),
	USAGE_BLOCK(USAGE_CALCULATOR, 0, EV_KEY, KEY_CALC, 0),
	USAGE_BLOCK(USAGE_BACK, 0, EV_KEY, KEY_BACK, 0),
	USAGE_BLOCK(USAGE_FORWARD, 0, EV_KEY, KEY_FORWARD, 0),
	USAGE_BLOCK(USAGE_HELP, 0, EV_KEY, KEY_HELP, 0),
	USAGE_BLOCK(USAGE_UNDO, 0, EV_KEY, KEY_UNDO, 0),
	USAGE_BLOCK(USAGE_REDO, 0, EV_KEY, KEY_F17, 0),
	USAGE_BLOCK(USAGE_REDO, 0, EV_KEY, KEY_REDO, 0),
	USAGE_BLOCK(USAGE_NEW, 0, EV_KEY, KEY_NEW, 0),
	USAGE_BLOCK(USAGE_OPEN, 0, EV_KEY, KEY_OPEN, 0),
	USAGE_BLOCK(USAGE_CLOSE, 0, EV_KEY, KEY_CLOSE, 0),
	USAGE_BLOCK(USAGE_REPLY, 0, EV_KEY, KEY_REPLY, 0),
	USAGE_BLOCK(USAGE_FWD, 0, EV_KEY, KEY_FORWARDMAIL, 0),
	USAGE_BLOCK(USAGE_SEND, 0, EV_KEY, KEY_SEND, 0),
	USAGE_BLOCK(USAGE_SPELL, 0, EV_KEY, KEY_F15, 0),
	USAGE_BLOCK(USAGE_SAVE, 0, EV_KEY, KEY_SAVE, 0),
	USAGE_BLOCK(USAGE_PRINT, 0, EV_KEY, KEY_PRINT, 0),
	USAGE_BLOCK_NULL
};

struct usage_block msvendor_usage_block[] = {
	USAGE_BLOCK(USAGE_CUSTOM, USAGE_CUSTOM_1, EV_KEY, KEY_FN_F1, 0),
	USAGE_BLOCK(USAGE_CUSTOM, USAGE_CUSTOM_2, EV_KEY, KEY_FN_F2, 0),
	USAGE_BLOCK(USAGE_CUSTOM, USAGE_CUSTOM_3, EV_KEY, KEY_FN_F3, 0),
	USAGE_BLOCK(USAGE_CUSTOM, USAGE_CUSTOM_4, EV_KEY, KEY_FN_F4, 0),
	USAGE_BLOCK(USAGE_CUSTOM, USAGE_CUSTOM_5, EV_KEY, KEY_FN_F5, 0),
	USAGE_BLOCK_NULL
};

struct usage_block keyboard_usage_block[] = {
	USAGE_BLOCK(USAGE_KEYPAD_EQUAL, 0, EV_KEY, KEY_KPEQUAL, 0),
	USAGE_BLOCK(USAGE_KEYPAD_LEFT_PAREN, 0, EV_KEY, KEY_KPLEFTPAREN, 0),
	USAGE_BLOCK(USAGE_KEYPAD_RIGHT_PAREN, 0, EV_KEY, KEY_KPRIGHTPAREN, 0),
	USAGE_BLOCK_NULL
};

struct usage_page_block nek4k_usage_page_blockes[] = {
	USAGE_PAGE_BLOCK(HID_UP_CONSUMER, consumer_usage_block),
	USAGE_PAGE_BLOCK(HID_UP_MSVENDOR, msvendor_usage_block),
	USAGE_PAGE_BLOCK(HID_UP_KEYBOARD, keyboard_usage_block),
	USAGE_PAGE_BLOCK_NULL
};

static int nek4k_pre_event(const struct hid_device *hid, 
						const struct hid_field *field,
						const struct hid_usage *usage,
						const __s32 value,
						const struct pt_regs *regs)
{
	struct hid_input *hidinput = field->hidinput;
	struct input_dev *input = hidinput->input;
	int code = 0, ascii_keycode = 0, ev_value;

	ev_value = value?1:0;

        switch (usage->hid&HID_USAGE) {
	case USAGE_FAVORITES:
		code = KEY_FAVORITES;
		ascii_keycode = KEY_F16;
		goto exit;
	case USAGE_REDO:
		code = KEY_REDO;
		ascii_keycode = KEY_F17;
		goto exit;
	};

        if ((usage->hid&HID_USAGE) != USAGE_CUSTOM)
		/* let hid core continue to process them */
		return (!0);
	
	switch (value) {
	case USAGE_CUSTOM_RELEASE:
		code = get_keycode(hidinput->private);
		ascii_keycode = KEY_F18+(code-KEY_FN_F1);
		break;
	case USAGE_CUSTOM_1:
		code = KEY_FN_F1;
		ascii_keycode = KEY_F18;
		break;
	case USAGE_CUSTOM_2:
		code = KEY_FN_F2;
		ascii_keycode = KEY_F19;
		break;
	case USAGE_CUSTOM_3:
		code = KEY_FN_F3;
		ascii_keycode = KEY_F20;
		break;
	case USAGE_CUSTOM_4:
		code = KEY_FN_F4;
		ascii_keycode = KEY_F21;
		break;
	case USAGE_CUSTOM_5:
		code = KEY_FN_F5;
		ascii_keycode = KEY_F22;
		break;
	}
exit:
	if (code) {
		hidinput->private = (void*)code;
		input_event(input, EV_KEY, code, ev_value);
		input_sync(input);
	}
	if (ascii_keycode) {
		input_event(input, EV_KEY, ascii_keycode, ev_value);
		input_sync(input);
	}
	return 0; 
}

static struct hidinput_simple_driver nek4k_driver = {
	.owner = THIS_MODULE,
	.name = driver_name,
	.pre_event = nek4k_pre_event,
	.id_table = nek4k_id_table,
	.usage_page_table = nek4k_usage_page_blockes,
	.private = NULL
};

static int __init nek4k_init(void)
{
	return hidinput_register_simple_driver(&nek4k_driver);
}

static void __exit nek4k_exit(void)
{
	hidinput_unregister_simple_driver(&nek4k_driver);
}

module_init(nek4k_init);
module_exit(nek4k_exit);

MODULE_LICENSE("GPL");

---

### Post by ydef on 2006-09-28
> **trantorvega said:**
> 
The howto on gentoo-wiki is still a work in progress. I keep adding informations or notes. Several problems and possible solutions have come up, along with suggestions and questions. If you have any of these feel free to comment here: [http://gentoo-wiki.com/Talk:HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000]("http://gentoo-wiki.com/Talk:HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000")

How weird.  I'm not able to pull up anything from gentoo-wiki.com at the moment even though the site's pingable.  Surprised there's no mirror.

---

### Post by Angafirith on 2006-09-29
> 
The howto on gentoo-wiki is still a work in progress. I keep adding informations or notes. Several problems and possible solutions have come up, along with suggestions and questions. If you have any of these feel free to comment here: [http://gentoo-wiki.com/Talk:HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000](http://gentoo-wiki.com/Talk:HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000) 

Thanks for putting that up there. I upgraded to Edgy the other day, and I was able to successfully apply those three patches to the ubuntu kernel sources. I did have to apply one patch manually (the one with the Makefile and Kconfig changes), but it was quite easy to do.

---

### Post by amitm02 on 2006-09-30
hello, i have a kernel newbie question (a bit off-topic),

who and how one decides if a patch should be included in future releases?
will this keybaord patch for example will be included?

is it realy nessery to comipile all of the kerenl, souldn't modules allow you to add it dynamicly to a working kernel?

thanks
amit

---

### Post by nmarshall on 2006-09-30
I could not get the patches to apply, on 2.6.17.8 or 2.6.17.7 ](*,) 

I am running dapper drake with kernel 2.6.15-27-386, and some of the buttons do work. only the "My Favorites" and star buttons, and the zoom thing do not work.

---

### Post by eprparadocs on 2006-11-09
I couldn't get usbnek4k.c 0.3.2 to work. When I modprobe it the kernel complains about get_keycode() not being found. I am missing a file or something?

Chaz.

---

### Post by wren42 on 2006-11-17
I had the same problem. It's because only part of the required patches were posted to this thread! I contacted the developer, and he told me that the most current version can be found here:

[http://lkml.org/lkml/2006/10/12/18](http://lkml.org/lkml/2006/10/12/18)

---

### Post by zerwas on 2006-11-22
I updated the instructions.

---

### Post by alanfranz on 2006-12-05
2.6.19 is out and it seems the patch by Liyu hasn't made it in the official tree.

Also, I don't know if it's an issue related to this driver, but I found out that you must disable 'Powerbook keys' in 'Full HID support' in order for the kernel 2.6.18 to compile cleanly using the 0.4.0 ubuntu patch.

I have plans for integrating all this piece of info in the wiki... if anybody else has something to add (e.g. any workaround, anything that doesn't work, etc) please tell me!

---

### Post by bodhi.zazen on 2006-12-06
Nice How-to

This thread has been added to the UDSF wiki.

[Microsoft_Natural_Ergonomic_Keyboard_4000](http://doc.gwos.org/index.php/Microsoft_Natural_Ergonomic_Keyboard_4000)

---

### Post by rko618 on 2006-12-21
This might be a dumb question but is there any way to get the favorites keys to work WITHOUT recompiling my kernel?

---

### Post by ydef on 2006-12-24
[FONT="Verdana"][SIZE="4"]

It looks like the latest 0.4.1 hid-simple all in  one patch from liyu allows everything to work using merely the kbd driver in X and not having to go through the drama of setting up two separate evdev sections in xorg.conf.

When enabling the usbnek4k module it requires the ascii_keycode parameter to be set:

# modprobe usbnek4k ascii_keycode=1

or just put a line in your /etc/modules file:

usbnek4k ascii_keycode=1

The only button that doesn't work out of the box in this case is the **My Favorites** button.  To get this working, you must change the hex code in usbnek4k.c and recompile.  You can do this in the patch before applying it, or if you've already compiled it go to the drivers/usb/input subdirectory within your source directory and at the top of usbnek4k.c where it defines it as:

#define USAGE_FAVORITES	0x182

changing the 0x182 (which translates to keycode 386 in decimal, which is obviously out of the 256 key range of X), to an unused keysym of your choice that appears in /usr/include/linux/input.h.  I use the UNKNOWN symbol from input.h which lists as keycode 240 and translates to 0xF0 in hex.  So I replace the above define with:

#define USAGE_FAVORITES 0xF0

before recompiling to get it all working perfectly with the kbd driver and don't need to bother using the evdev driver at all.

My xkb section in xorg.conf looks like this:

Section "InputDevice"
  Identifier "Keyboard1"
  Driver "kbd"
  option "AutoRepeat" "250 50"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbLayout" "en_US"
  option "XkbModel" "microsoftnek4k"
  option "XkbCompat" "complete+pc+keypad"
  option "XkbSymbols" "inet(microsoftnek4k)+us+capslock+srvr_ctrl+level3+level5"
  option "XkbTypes" "complete+caps(internal_nocancel)"
  option "XkbOptions" "caps:internal_nocancel+compose(menu)+lv3(switch)"
EndSection

All the other sections in the HOWTO still apply, like adding the extra sections to the various files in /usr/share/X11/xkb in order to create the new model type microsoftnek4k and the respective symbol type that is a subset of the microsoft inet keyboards in the symbols directory.

I would assume liyu will probably fix the skewered out of range favorites key that maps to 386 in the next release so keep that in mind if upgrading the patch in future.

And to whoever asked, NO, there is no way to get the extra buttons working without recompiling the kernel ALTHOUGH i believe that some of the variations of the precompiled debs of the 2.6.18 kernel include an earlier version of the usbnek4k driver out of the box so you would need to install the 2.6.18 image and look for that module.  It isn't included in the 2.6.19 and 2.6.20 deb images that I've seen so unless you want to wait for the patch to be incorporated into the main tree or forever use 2.6.18 it's still in your best interests to get off your lazy *** and learn how to recompile.  :( 


[/SIZE][/FONT]

---

### Post by bsdboy on 2006-12-27
Greetings and salutations! 

Have some trouble finding where to change the Microsoft Ergonomic Natrural Keyboard 4000 to m (Step 5). I've done the first three steps from the Master Kernel Thread - howto, then patched the kernel with the patch 'msnek4k-patchset', then returned to Master Kernel Thread - howto and done steps 4 and 5. When I ran step 6 the qconf window appears and I thougt, now is the time to change "Microsoft Natural Ergonomic Keyboard 4000 Driver" to "m". The problem is I can't find it under USB, anywhere?!

Help someone please, where did I go wrong? I'm an Kernel-configuration-newbee.

BTW: I also have SATA drives, which driver should I use?

---

### Post by Lunar_Lamp on 2006-12-27
I remember ages ago playing around with this (couldn't get it to work for whatever reason).  However, I do remember that the module was there, it was jut REALLY well hidden.  Even when I knew where it was it was hard to find.  You'll probably have to look on every single menu - if I recall correctly (and I could be waaay off) here, I remember it being hidden in with some apple stuff.  It was there, just well hidden.  Sorry I can't be more help, but don't give up!

---

### Post by bsdboy on 2006-12-27
Lunar_Lamp I found it, as you said , it was hidden. Thank you. It was under the USB, and HID Simple Driver Interface had to be checked, then the Microsoft Ergonomic Natural Keyboard 4000 option was avaliable. But get error when I compile the kernel:

drivers/usb/input/hid-input.c: In function &#8216;hidinput_pb_event&#8217;:
drivers/usb/input/hid-input.c:202: error: &#8216;input&#8217; undeclared (first use in this function)
drivers/usb/input/hid-input.c:202: error: (Each undeclared identifier is reported only once
drivers/usb/input/hid-input.c:202: error: for each function it appears in.)
make[4]: *** [drivers/usb/input/hid-input.o] Error 1
make[3]: *** [drivers/usb/input] Error 2
make[2]: *** [drivers/usb] Error 2
make[1]: *** [drivers] Error 2

If anyone could shed some light over this, I would be grateful

---

### Post by aresek on 2007-01-02
Same problem here, could anyone help?

---

### Post by aresek on 2007-01-03
I tried kernel 2.6.18.6 and patches from gentoo wiki and it worked for me :) now it works.

---

### Post by phill on 2007-01-14
I'm in the same position as bsdboy and aresek, 2.6.19 will just not compile.

Has anyone managed to get it working?

---

### Post by vetik32 on 2007-02-09
hello, anybody knows where I can get  msnek4k-patchset for 2.6.20?
Thanks!
p.s. google doesn't know :(

---

### Post by zerwas on 2007-02-11
> **vetik32 said:**
> hello, anybody knows where I can get  msnek4k-patchset for 2.6.20?
Thanks!
p.s. google doesn't know :(

Google is our god. There is no patchset for codebase 2.6.20. Liyus last post can be found [here]("http://groups.google.de/group/linux.kernel/browse_thread/thread/3960dc2d6009a332/93e6c9ff40090c4d?lnk=gst&q=Microsoft+Natural+Ergonomic+Keyboard+4000+Driver&rnum=1&hl=de#93e6c9ff40090c4d").

Regards,
zerwas

---

### Post by nct on 2007-02-13
I've filled a bug for complete support of this keyboard at [https://launchpad.net/ubuntu/+bug/84965]("https://launchpad.net/ubuntu/+bug/84965").

---

### Post by kat_ams on 2007-02-26
I've slightly modified Liyu's patch to try to make it compatible with kernel 2.6.20.1 but I keep getting the following error in line 40. 

Here is what I did...

I put a simlink to my kernel source /usr/src/linux-2.6.20.1 is linked to /usr/src/linux and modified liyu's code as such to make it kernel independent. just changed all reference to 2.6.19 to linux...

I modified the code from liyu's last post to 
[http://marc.theaimsgroup.com/?l=linux-usb-devel&m=116539956331436&w=2](http://marc.theaimsgroup.com/?l=linux-usb-devel&m=116539956331436&w=2)

When I test the patch with the command:

```
 sudo patch -p1 --dry-run < msnek4-patch
```I get the following error:

```

patching file drivers/usb/input/hid-core.c
Hunk #1 succeeded at 27 (offset 1 line).
Hunk #2 FAILED at 35.
Hunk #3 succeeded at 50 (offset 2 lines).
**patch: **** malformed patch at line 40: struct hid_usage *usage, __s32 value, int interrupt)  {**
```any idea's why Kernel 2.6.20.1 does not like line 40?? :confused:

---

### Post by istaon on 2007-03-03
Hi,

I think I'm too stupid to get theses keyboard to work.:confused: 
I tryed with a lot of differnt Kernel sources (2.6.17 - 2.6.20.1) But with none of them the patch (Yes I looked for the korrekt version number) would work correctly. Everytime I got an compiling error. 
So now I think its to difficult for me and I like to ask if someone has an precompiled ubuntukernel with this patch and can give me that packaged? :?:

He/she would help me a lot....

Or a really working howto with the correct files....

Br
Dominik

---

### Post by liyu on 2007-03-05
The hid core is split from USB since kernel 2.6.20. So we can not port this driver to it easier.

I already have ported it to 2.6.21-rc2. see this URL:

version 0.5.0 [http://lkml.org/lkml/2007/3/5/18](http://lkml.org/lkml/2007/3/5/18)

Well, I think it also can use it in 2.6.20 kernel, however it may need some little changes ( adjust the offset of some lines ).

---

### Post by liyu on 2007-03-05
Regarding to the problem hidinput_pb_event(), you can use this patch,  the 0.5.0 already fixed this.

--- linux-2.6.19.2/drivers/usb/input/hid-input.c        2007-02-02 17:12:58.000000000 +0800
+++ linux-2.6.19.2.new/drivers/usb/input/hid-input.c    2007-02-02 17:18:00.000000000 +0800
@@ -199,7 +199,7 @@
                if (hidinput_trylock_simple(hidinput))
                        return 0;
                if (test_bit(usage->code, hid->pb_pressed_numlock) ||
-                   test_bit(LED_NUML, input->led)) {
+                   test_bit(LED_NUML, hidinput->input->led)) {
                        trans = find_translation(powerbook_numlock_keys, usage->code);
  
                        if (trans) {
@@ -219,7 +219,7 @@
        if (hid->quirks & HID_QUIRK_POWERBOOK_ISO_KEYBOARD) {
                trans = find_translation(powerbook_iso_keyboard, usage->code);
                if (trans) {
-                       input_event(input, usage->type, trans->to, value);
+                       input_event(hidinput->input, usage->type, trans->to, value);
                        return 1;
                }
        }

---

### Post by vetik32 on 2007-03-05
> **liyu said:**
> 
...
Well, I think it also can use it in 2.6.20 kernel, however it may need some little changes ( adjust the offset of some lines ).

I've got rejects for 
drivers/hid/hid-core
drivers/hid/hid-input
drivers/usb/input/Kconfig
drivers/usb/input/Makefile
drivers/usb/input/hid-core.c
include/linux/hid.h
apparently 
hidinput_input_init needs:       
+       input_dev->open = hid->hidinput_open; 
+       input_dev->close = hid->hidinput_close; 
and not
+       input_dev->open = hidinput_open; 
+       input_dev->close = hidinput_close; 

and those methods are from 
drivers/usb/input/hid-core
and not drivers/hid/hid-input.c

other rejects have successfully been fixed with
rej -m meld XXX.y XXX.y.rej

p.s. I am a simple guy who don't know nothing about c or c++ 
p.p.s.: make shows some warnings :

include/linux/hid-simple.h:139: warning: previous implicit declaration of 'schedule' was here
drivers/usb/input/usbnek4k.c: In function 'nek4k_pre_event':
drivers/usb/input/usbnek4k.c:211: warning: cast from pointer to integer of different size
drivers/usb/input/usbnek4k.c:221: warning: cast to pointer from integer of different size

In file included from drivers/usb/input/usbnek4k.c:20:
include/linux/hid-simple.h: In function 'hidinput_lock_simple':
include/linux/hid-simple.h:139: warning: implicit declaration of function 'schedule'

used: gentoo-sources (vanilla + gentoo patches) (gentoo distro)

---

### Post by liyu on 2007-03-05
I guess your machine is 64bit, is it true? if so, you can redefine code variable in 
nek4k_pre_event() as long type, and replace (int) at line usbnek4k.c:211 with (long), I think this can remove the warnings.

The implicit declaration of 'schedule', well, I lost linux/sched.h header file, sorry.

---

### Post by istaon on 2007-03-06
I tried your 0.5 patch and this will work, but LUKS won't work anymore :(
So is there a way to patch the ubuntu-kernel? because I thing its something with the kernelmodifikations they did....

Br
Dominik

---

### Post by vetik32 on 2007-03-09
yeah, you've right, the warnings are gone
thanks a lot

---

### Post by istaon on 2007-03-11
Hi

if I try to patch the 2.6.21-rc2 kernel, I go the following error:

patching file include/linux/hid.h
patching file include/linux/hid-simple.h
patching file drivers/hid/hid-core.c
patching file drivers/hid/hid-input.c
patching file drivers/hid/hid-simple.c
patching file drivers/hid/Kconfig
patching file drivers/hid/Makefile
patching file drivers/usb/input/hid-core.c
patching file drivers/usb/input/Kconfig
patching file drivers/usb/input/Makefile
patching file drivers/usb/input/usbnek4k.c
patch unexpectedly ends in middle of line
patch unexpectedly ends in middle of line

Any ideas?

Br
dominik

---

### Post by istaon on 2007-03-11
or with verbose msg:

Hmm...  Looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naurp linux-2.6.21-rc2.orig/include/linux/hid.h linux-2.6.21-rc2/include/linux/hid.h
|--- linux-2.6.21-rc2.orig/include/linux/hid.h  2007-03-05 09:09:35.000000000 +0800
|+++ linux-2.6.21-rc2/include/linux/hid.h       2007-03-05 11:17:22.000000000 +0800
--------------------------
Patching file include/linux/hid.h using Plan A...
Hunk #1 succeeded at 35.
Hunk #2 succeeded at 398.
Hunk #3 succeeded at 437.
Hunk #4 succeeded at 493.
Hmm...  The next patch looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naurp linux-2.6.21-rc2.orig/include/linux/hid-simple.h linux-2.6.21-rc2/include/linux/hid-simple.h
|--- linux-2.6.21-rc2.orig/include/linux/hid-simple.h   1970-01-01 08:00:00.000000000 +0800
|+++ linux-2.6.21-rc2/include/linux/hid-simple.h        2007-03-05 13:37:42.000000000 +0800
--------------------------
Patching file include/linux/hid-simple.h using Plan A...
Hunk #1 succeeded at 1.
Hmm...  The next patch looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naurp linux-2.6.21-rc2.orig/drivers/hid/hid-core.c linux-2.6.21-rc2/drivers/hid/hid-core.c
|--- linux-2.6.21-rc2.orig/drivers/hid/hid-core.c       2007-03-05 09:09:32.000000000 +0800
|+++ linux-2.6.21-rc2/drivers/hid/hid-core.c    2007-03-05 11:17:26.000000000 +0800
--------------------------
Patching file drivers/hid/hid-core.c using Plan A...
Hunk #1 succeeded at 26.
Hunk #2 succeeded at 43.
Hunk #3 succeeded at 822.
Hunk #4 succeeded at 852.
Hunk #5 succeeded at 1011.
Hmm...  The next patch looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naurp linux-2.6.21-rc2.orig/drivers/hid/hid-input.c linux-2.6.21-rc2/drivers/hid/hid-input.c
|--- linux-2.6.21-rc2.orig/drivers/hid/hid-input.c      2007-03-05 09:09:32.000000000 +0800
|+++ linux-2.6.21-rc2/drivers/hid/hid-input.c   2007-03-05 11:17:26.000000000 +0800
--------------------------
Patching file drivers/hid/hid-input.c using Plan A...
Hunk #1 succeeded at 30.
Hunk #2 succeeded at 67.
Hunk #3 succeeded at 78.
Hunk #4 succeeded at 157.
Hunk #5 succeeded at 166.
Hunk #6 succeeded at 191.
Hunk #7 succeeded at 209.
Hunk #8 succeeded at 246.
Hunk #9 succeeded at 257.
Hunk #10 succeeded at 287.
Hunk #11 succeeded at 708.
Hunk #12 succeeded at 720.
Hunk #13 succeeded at 730.
Hunk #14 succeeded at 747.
Hunk #15 succeeded at 759.
Hunk #16 succeeded at 786.
Hunk #17 succeeded at 825.
Hunk #18 succeeded at 911.
Hunk #19 succeeded at 943.
Hmm...  The next patch looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naurp linux-2.6.21-rc2.orig/drivers/hid/hid-simple.c linux-2.6.21-rc2/drivers/hid/hid-simple.c
|--- linux-2.6.21-rc2.orig/drivers/hid/hid-simple.c     1970-01-01 08:00:00.000000000 +0800
|+++ linux-2.6.21-rc2/drivers/hid/hid-simple.c  2007-03-05 11:17:26.000000000 +0800
--------------------------
Patching file drivers/hid/hid-simple.c using Plan A...
Hunk #1 succeeded at 1.
Hmm...  The next patch looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naurp linux-2.6.21-rc2.orig/drivers/hid/Kconfig linux-2.6.21-rc2/drivers/hid/Kconfig
|--- linux-2.6.21-rc2.orig/drivers/hid/Kconfig  2007-03-05 09:09:32.000000000 +0800
|+++ linux-2.6.21-rc2/drivers/hid/Kconfig       2007-03-05 11:17:26.000000000 +0800
--------------------------
Patching file drivers/hid/Kconfig using Plan A...
Hunk #1 succeeded at 36.
Hmm...  The next patch looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naurp linux-2.6.21-rc2.orig/drivers/hid/Makefile linux-2.6.21-rc2/drivers/hid/Makefile
|--- linux-2.6.21-rc2.orig/drivers/hid/Makefile 2007-03-05 09:09:32.000000000 +0800
|+++ linux-2.6.21-rc2/drivers/hid/Makefile      2007-03-05 11:17:26.000000000 +0800
--------------------------
Patching file drivers/hid/Makefile using Plan A...
Hunk #1 succeeded at 3.
Hmm...  The next patch looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naurp linux-2.6.21-rc2.orig/drivers/usb/input/hid-core.c linux-2.6.21-rc2/drivers/usb/input/hid-core.c
|--- linux-2.6.21-rc2.orig/drivers/usb/input/hid-core.c 2007-03-05 09:09:34.000000000 +0800
|+++ linux-2.6.21-rc2/drivers/usb/input/hid-core.c      2007-03-05 13:40:58.000000000 +0800
--------------------------
Patching file drivers/usb/input/hid-core.c using Plan A...
Hunk #1 succeeded at 33.
Hunk #2 succeeded at 1287.
Hunk #3 succeeded at 1338.
Hunk #4 succeeded at 1442.
Hunk #5 succeeded at 1512.
Hmm...  The next patch looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naurp linux-2.6.21-rc2.orig/drivers/usb/input/Kconfig linux-2.6.21-rc2/drivers/usb/input/Kconfig
|--- linux-2.6.21-rc2.orig/drivers/usb/input/Kconfig    2007-03-05 09:09:34.000000000 +0800
|+++ linux-2.6.21-rc2/drivers/usb/input/Kconfig 2007-03-05 11:17:28.000000000 +0800
--------------------------
Patching file drivers/usb/input/Kconfig using Plan A...
Hunk #1 succeeded at 357.
Hmm...  The next patch looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naurp linux-2.6.21-rc2.orig/drivers/usb/input/Makefile linux-2.6.21-rc2/drivers/usb/input/Makefile
|--- linux-2.6.21-rc2.orig/drivers/usb/input/Makefile   2007-03-05 09:09:34.000000000 +0800
|+++ linux-2.6.21-rc2/drivers/usb/input/Makefile        2007-03-05 11:17:28.000000000 +0800
--------------------------
Patching file drivers/usb/input/Makefile using Plan A...
Hunk #1 succeeded at 48.
Hmm...  The next patch looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naurp linux-2.6.21-rc2.orig/drivers/usb/input/usbnek4k.c linux-2.6.21-rc2/drivers/usb/input/usbnek4k.c
|--- linux-2.6.21-rc2.orig/drivers/usb/input/usbnek4k.c 1970-01-01 08:00:00.000000000 +0800
|+++ linux-2.6.21-rc2/drivers/usb/input/usbnek4k.c      2007-03-05 11:17:28.000000000 +0800
--------------------------
Patching file drivers/usb/input/usbnek4k.c using Plan A...
Hunk #1 succeeded at 1.
patch unexpectedly ends in middle of line
Hmm...patch unexpectedly ends in middle of line
  Ignoring the trailing garbage.
done

---

### Post by istaon on 2007-03-11
Ok I've patcht the last section usbnek4k manually. After that, I can compile my kernel.
But how to setup the keybord for kde now?

Br
Dominik

---

### Post by liyu on 2007-03-12
Please see here:

[http://gentoo-wiki.com/HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000](http://gentoo-wiki.com/HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000)

May be, Well, O, You should search google.com first.

---

### Post by istaon on 2007-03-12
Hi,

so after compiling the kernel and setup my keybord I try to install the nvidia kernel modules, but they dont't compile anymore?!

I tried a lot of howtos but none of them helps. So isn't there a way to get the hid patch into the "normal" Ubuntu-kernel.?

Or is there a way to patch the ubuntukernel itself, so that the "normal" restricted modules can be used?!

---

### Post by ydef on 2007-03-14
Hm ... so it sounds like what you are saying is that the patch will work with 2.6.21 but not 2.6.20.  That is highly unfortunate.

If anyone gets it to work on 2.6.20 please post how you did it.  

Thanks!

---

### Post by liyu on 2007-03-14
I have a patch for 2.6.20.1,  but not for 2.6.20. this may have a bit of help for you.

---

### Post by istaon on 2007-03-19
Hi,

a good message for all people who doesn't want to recompile the kernel:

The patch is now implemented in the offical kernel form ubuntu.

=D>

---

### Post by zerwas on 2007-03-21
> **istaon said:**
> 
The patch is now implemented in the offical kernel form ubuntu.

I have no access to my computer these weeks. Do you mean the Feisty-kernel?

---

### Post by istaon on 2007-03-22
As far as I know: "Yes"

---

### Post by ogryn on 2007-03-25
> **istaon said:**
> Hi,

a good message for all people who doesn't want to recompile the kernel:

The patch is now implemented in the offical kernel form ubuntu.

=D>

What do Feisty users have to do to take advantage of this?

I can't even seem to get my NumLock, CapsLock and ScrollLock lights to work at the moment!

Thanks :)

---

### Post by db9s on 2007-03-25
this **** is sooooooooo complicated. Seriously ...the only way to fix the zoom button is thru the kernel?

Can't someone (yes I mean you) make a simple program that can map the keys or something? It would be great if the zoom button worked with beryl's zoom function.

---

### Post by zerwas on 2007-03-28
> Can't someone (yes I mean you) make a simple program that can map the keys or something? It would be great if the zoom button worked with beryl's zoom function.

It's true, that these keys can only be mapped with a kernel driver (you bought a microsoft product).
When Ubuntu 7.04 gets out, we will be able to make this program :)

---

### Post by earlycj5 on 2007-03-30
> **istaon said:**
> Hi,

a good message for all people who doesn't want to recompile the kernel:

The patch is now implemented in the offical kernel form ubuntu.

=D>

It is?  I'm running 7.04, when I modprobe usbnek4k I get an error that the module wasn't found.  :confused:

---

### Post by luxerama on 2007-04-19
Im running Feisty and have the same problem as earlycj5. 
```
modprobe usbnek4k
FATAL: Module usbnek4k not found.

```
istaon are you sure it has been included?

---

### Post by zerwas on 2007-04-19
it is not implemented.
For information look here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84965](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84965)

---

### Post by atlantis_ on 2007-05-02
Hi,

the mentioned patch does not work for feisty (kernel  2.6.20).
Is there a patch availble that kernel?

---

### Post by kiranlightpaw on 2007-05-03
I posted this in a separate thread, but figured I'd post it here also.

 I have a Microsoft Natural Ergonomic Keyboard 4000 v1.0 USB keyboard. The volume controls (at the top) work in the Live CD environment, but refuse to work on the install. I've checked the Keyboard Bindings between the Live CD and the install and they're the same.

When I click it in the Live CD enviro, I get the popup volume control as would be expected, but when I click it in the installed enviro, I get a weird thing happening to the screen that looks like something crashing and all the widgets reverting to what looks like a default GTK appearance. It lasts for about two or three seconds, then reverts to standard Ubuntu theme.

Any thoughts? It just seems odd to me that this would work in the Live enviro and not in the installed enviro. Would the driver solution mentioned above fix this? Does it even work in Feisty yet?

EDIT: I'm using Feisty on an AMD Athlon 64 Processor 3700. All updates (at least from the manager) have been installed. A8N-SLI motherboard.

---

### Post by StratosL on 2007-05-05
On a Feisty install, the volume buttons worked out of the box, as well as the mute button and the calculator button.

Through the keyboard shortcuts menu in gnome, I have also the top left home, search and mail buttons working.

What is not working is the five "raw" button top middle, the "my favorites", the multimedia "start/stop" (or at least I don't know how to pass that command to amarok), the "zoom" (but zoom is not desperately needed if you have beryl effects) and the twelve alter-ego function keys.

Of the missing functionality, the most wanted to work would be:
1) the five "raw" buttons would be the most useful, as they could be "wildcard" application launchers.
2) the alter-ego function keys, enabled by turning off the "F-Lock" key. I wish they could be assigned their advertised function...

BTW, recompiling the kernel is out of the question for 99.5% of the users, including myself.

---

### Post by kiranlightpaw on 2007-05-05
I actually fixed the problem. It wasn't the keyboard, but actually gnome-settings-daemon crashing when in combination with Xinerama and nVidia drivers. The volume was actually changing, but the little popup window wasn't working.

[This bug](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232) describes the fix.

The only ways I've seen to get the favorite keys working is to apply the patches as specified above. It's not difficult, but low on my priority list right now since I never use them under Windows anyways. :P

---

### Post by liyu on 2007-05-10
Here is the latest version:

[http://lkml.org/lkml/2007/4/30/33](http://lkml.org/lkml/2007/4/30/33)

So, we can use zoom handler as mouse wheel. Thanks for this interesting idea.

And, ascii_code is on default from now on.

(It is for 2.6.21.1)

---

### Post by zerwas on 2007-05-12
Hello Liyu,

Thank you very much for this new version. I have a question: I am not able to use the module usbhid. So when i am using this keyboard only with usbkbd and your driver, will it work?
EDIT: Worked perfectly.

**Which function do you guys use for the zoom scroll wheel?**


Regards,
zerwas

---

### Post by woifi on 2007-05-15
hi!

> **liyu said:**
> Here is the latest version:
(It is for 2.6.21.1)

will this patch work for edgy (and it's default kernel) too?

tia

woifi

---

### Post by johnnyphive on 2007-05-17
Just got 7.04 64bit installed and my "F" keys don't seem to be working.  I'm not too worried about all the "special" keys, but the "F" keys seem to be a must from what i've been reading.  Do i need to follow all these steps in order to get those to work?  Also, i noticed this thread started over a year ago.  Where can i find the most up to date info?

---

### Post by zerwas on 2007-05-18
Hello johnnyphive,

This thread may have started a year ago but as you see, the driver developer and me are still writing :).

The F-keys should work by default. Next to the F12 key, there is a key with which you can switch between F-keys and the other option. Try pressing it.

If that doesn't work: Are you using the usbkbd driver? The F-keys won't work with it. usbhid is the better alternative.

And, if you start the program xev, go with the mouse into the white window and press a F-key, is there any reaction in the terminal?

Regards,
zerwas

---

### Post by johnnyphive on 2007-05-18
> **zerwas said:**
> Hello johnnyphive,

This thread may have started a year ago but as you see, the driver developer and me are still writing :).

The F-keys should work by default. Next to the F12 key, there is a key with which you can switch between F-keys and the other option. Try pressing it.

If that doesn't work: Are you using the usbkbd driver? The F-keys won't work with it. usbhid is the better alternative.

And, if you start the program xev, go with the mouse into the white window and press a F-key, is there any reaction in the terminal?

Regards,
zerwas

D@mn, never even saw that key before.  That did the trick.  Now my next question, what about my "windows" key.  Any way to get that working?

---

### Post by zerwas on 2007-05-19
> **johnnyphive said:**
> D@mn, never even saw that key before.  That did the trick.  Now my next question, what about my "windows" key.  Any way to get that working?

The question is what you want to do with this key. So you can't use it in the shortcut-dialog of GNOME?

Try, if xev gives a keycode back.

---

### Post by johnnyphive on 2007-05-19
Here are the results of xev, Not real sure what to do with them though

KeyPress event, serial 29, synthetic NO, window 0x3c00001,
    root 0x156, subw 0x0, time 47937192, (-1098,-73), root:(260,13),
    state 0x10, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x3c00001,
    root 0x156, subw 0x0, time 47938999, (-1098,-73), root:(260,13),
    state 0x50, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

---

### Post by remmelt on 2007-05-22
A few weeks ago a new kernel came out. Still, the 4000 is not supported. Why is that? The patch is out and submitted, people use the keyboard and it's still for sale. I just don't understand. Is it personal preference?

Compiling the kernel, although technically feasible, is out of the question. This is not Gentoo, this is Ubuntu: I love and use apt. When there is a new kernel version, I'd like to be able to upgrade to it without any bullshit or recompiling or other problems.

Sorry for the rant, but this is one of the first big disappointments for me. I understand that some hardware can be troublesome, but this thing is documented and dealt with. Get with the program, Kernel.

---

### Post by Hadret on 2007-05-30
Is there any chance at the moment, to compile it on an 2.6.22 kernel?

---

### Post by Hadret on 2007-06-05
Well, basically there is good HID support already in 2.6.22. All what is needed right now, is driver for mnek4k ;]

---

### Post by ydef on 2007-06-15
Dear Liyu,

At present some of us are breathlessly awaiting your release of the usbnek4k/hid-simple patch for kernel version 2.6.22.

This most recent kernel version is fundamentally different from 2.6.21 in the way the driver directories hierarchies have changed, having done away with the usb/input directory where the usbnek4k module lived in 2.6.21 and classified all usb input drivers into more specific categories 
based on the type of input device it is so unfortunately there's not a quick and dirty port from the earlier kernel.  Are you going to create a specific hid/usbhid parent for the usbnek4k.ko module?  Haven't seen any release of the latest patch on lkml and we're hoping you post one soon.

---

### Post by strabes on 2007-06-15
I am one of those breathlessly waiting for an easy way to get all of the buttons working. Since this patch did not make it into the feisty kernel, perhaps it will be in the gutsy one?

Anyway, I don't understand step 5: > After following the performance tips, also go to Device Drivers --> USB and change "Microsoft Natural Ergonomic Keyboard 4000 Driver" to "m"

What performance tips? In the config window that pops up I could find nothing like "Microsoft Natural Ergonomic Keyboard 4000 Driver"

Where exactly is this? Is it 100% necessary? I used the patch liyu posted on page 4 of this thread. My kernel is compiling right now and I'll let ya'll know if it works, but for some reason I'm skeptical.

---

### Post by strabes on 2007-06-16
dupe

---

### Post by zerwas on 2007-06-17
Hello Alex,

> Since this patch did not make it into the feisty kernel, perhaps it will be in the gutsy one?
Follow [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84965") report. I hope it will make it into gutsy.
> What performance tips?
Click on "performance tips" in the howto and you will see :-)

I updated the howto, so i hope you can get this keyboard working now :). You should be able to apply it to 2.6.21 (which is not the latest kernel version).

Compiling a kernel is never easy if you have never done that before.

Regards,
zerwas

---

### Post by strabes on 2007-06-17
I have 2.6.20-16-generic installed and do not see 2.6.21 in the ubuntu repos, will it work? Or am I patching the kernel that is downloaded in the howto?

I cannot find "Microsoft Natural Ergonomic Keyboard 4000 Driver" in the qconf window. The attached screenshot is what comes up when I search for "Keyboard" 

Nothing comes up when I search for "microsoft"

Also, when I run this command (sudo cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make xconfig) from the howto you linked to, it asks me a bunch of questions about stuff that is way over my head so I just held enter through the whole thing until the configuration window popped up.

Why is this not working for me? What should I do?

---

### Post by zerwas on 2007-06-17
You should simply do what the kernel-howto says (and it says to manually download 2.6.21 (step 2), combined with my howto. 2.6.21 is not in the Ubuntu repos, that's ok. It's because normally there is no need to change the kernel. Gutsy will have 2.6.22 :-). And i hope Li Yu will make his patch also for 2.6.22.

Holding enter for the questions was ok.


[size=1]Another solution could be to
try it again, but this time, instead of:
```
sudo cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make xconfig
```simply do 
```
sudo make xconfig
```[/size]

---

### Post by strabes on 2007-06-17
I finally got it to work. I'm running kubuntu feisty fully upgraded (my kernel was 2.6.20 before following this howto). Here are some of the steps that were confusing to me, mostly because I have never compiled my own kernel before. I hope that these tips help others to be sucessful in getting their Microsoft Natural Ergonomic Keyboard 4000 working.

1) I used the patch that liyu posted on page four of this thread, located [here](http://ubuntuforums.org/showpost.php?p=2626882&postcount=72). This patch lets you use the zoom slider to scroll up and down, which is far more useful than zooming.

2) As zerwas posted on page 5 of this thread, ([post](http://ubuntuforums.org/showpost.php?p=2861752&postcount=88)), for step 5 of the master_kernel thread, instead of running ```
sudo cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make xconfig
``` I had to run ```
sudo make xconfig
```

3) As bsdboy posted on page 2 of this thread, ([post](http://ubuntuforums.org/showthread.php?p=1936072&highlight=hidden#post1936072)) the location of the "Microsoft Ergonomic Natural Keyboard 4000 Driver" option is really hidden in the config window, and HID Simple Driver Interface has to be checked in order for it to appear. An easy way to find both of them is to just search (Ctrl+F) for "simple" and they should both appear.

After these steps are cleared up you should be able to continue with step 7 of the master_kernel thread.

Perhaps some of these clarifications should be added to the main how to? (the first post in this thread) Especially the third one.

---

### Post by zerwas on 2007-06-17
> 1) I used the patch that liyu posted on page four of this thread, located [here](http://ubuntuforums.org/showpost.php?p=2626882&postcount=72). This patch lets you use the zoom slider to scroll up and down, which is far more useful than zooming.
That's the same patch as in the howto :-)

> Perhaps some of these clarifications should be added to the main how to?
Done. Thank you very much for helping out. I don't have the time now for trying the updated instructions. :(

Regards,
zerwas

---

### Post by strabes on 2007-06-17
Alrighty ya'll, any ideas on getting the back/forward keys working with firefox? Using the [current version](http://lkml.org/lkml/2007/4/30/33) of the liyu's patch, their keycodes/names are 234, XF86Back and 233, XF86Forward

Right now I'm using them as the global shortcuts for next/previous track in amarok.

---

### Post by ydef on 2007-06-17
> **strabes said:**
> Alrighty ya'll, any ideas on getting the back/forward keys working with firefox? Using the [current version]("http://lkml.org/lkml/2007/4/30/33") of the liyu's patch, their keycodes/names are 234, XF86Back and 233, XF86Forward

Right now I'm using them as the global shortcuts for next/previous track in amarok.

Yeah, it's really simple really.  There are actually multiple ways to do it.  You can set keycodes 233 and 234 in your Xmodmap file to also alias to alt-right and alt-left.  You could also use a window manager based app to set keyboard shortcuts.  For instance I use kde, so in the kde control manager I could set backward and forward under keyboard shortcuts under regional and accessibility to XF86Back and XF86Forward.  

I use these keys to allow me to flip right and left between tabs, and use a shift-XF86Back and shift-XF86Forward to allow me to go back and forward in pages.  It's infinitely nicer.

---

### Post by strabes on 2007-06-18
In the KDE control module I have set XF86Back and XF86Forward to Back and Forward respectively and have also removed them from the amarok global shortcuts. They still do not affect anything in firefox, but they do work in KDE apps like konqueror. 

I also noticed that the =, (, and ) keys in the top right of the keyboard also don't work. How would I bind these keys to their respective characters in my ~/.Xmodmap file?

My favorite part about this patch so far is being able to use the zoom slider to scroll.

---

### Post by ydef on 2007-06-18
> **strabes said:**
> In the KDE control module I have set XF86Back and XF86Forward to Back and Forward respectively and have also removed them from the amarok global shortcuts. They still do not affect anything in firefox, but they do work in KDE apps like konqueror. 

Hm.  All I can think of is you might want to try hitting your 'block global shortcuts' key then see if the forward and back work.  If you haven't assigned it yet, assign it in the same kde shortcuts gui. 

> I also noticed that the =, (, and ) keys in the top right of the keyboard also don't work. 

Those keys work fine for me and should work out of the box.  Make sure you're using the latest liyu driver which should be 0.5.1 hid-simple which is an all-in-one patch.  you can always find them on lkml.org

---

### Post by strabes on 2007-06-18
> I also noticed that the =, (, and ) keys in the top right of the keyboard also don't work.

Well I couldn't get them working by default so I just used the keycodes from xev to name them F14, F15, and F16 and then use the Input Actions section of the KDE Control Center to make them output their respective characters when pressed.

---

### Post by strabes on 2007-06-19
I also just realized that my wireless card in my laptop is no longer being recognized by ubuntu. Could this possibly be because I disabled its driver in the config window by mistake? Is it possible to load a module manually to enable it?

Another issue I'm noticing is that if you unplug the keyboard and then plug it back in, the extra buttons stop working and to get them working again you have to manually run ```
sudo rmmod usbnek4k
sudo modprobe usbnek4k
```

---

### Post by ydef on 2007-06-24
> **strabes said:**
> I also just realized that my wireless card in my laptop is no longer being recognized by ubuntu. Could this possibly be because I disabled its driver in the config window by mistake? Is it possible to load a module manually to enable it?

You can always force remove a driver (rmmod -f) and reload it again with modprobe.  But if your wireless card isn't being recognized, then it sounds like the driver was never loaded to begin with.  Check your debug messages with dmesg to see if/when your wireless card is recognized by ubuntu during bootstrap.

> **strabes said:**
> 
Another issue I'm noticing is that if you unplug the keyboard and then plug it back in, the extra buttons stop working and to get them working again you have to manually run ```
sudo rmmod usbnek4k
sudo modprobe usbnek4k
```

Yep.  Due to some bugginess, I reset the driver upon the startup and initialization of X by putting the lines:

sudo rmmod -f usbnek4k
sudo modprobe usbnek4k

in my .xsession file or else some buggy issues seem to occur with regards to the holdover of usbnek4k functionality when in use with the console only.

Of course, I always startx manually aftering booting into a default rc2 using console.  Anyone that boots straight into X shouldn't need to do that, but anyone using startx I would recommend inserting the above lines in your .xsession

---

### Post by liyu on 2007-06-25
> **ydef said:**
> Dear Liyu,

At present some of us are breathlessly awaiting your release of the usbnek4k/hid-simple patch for kernel version 2.6.22.



Thank you for care this driver.

The 2.6.22 vanilla kernel have not release yet (RC5 now). however, use this driver for current preview version kernel also are welcome.

The attachment is the patch that you want. this should can be apply on 2.6.22-rc5.

Any suggestion send my email please. 

Good luck.

---

### Post by zerwas on 2007-06-26
Thanks. Also works perfectly with 2.6.22-rc**6**

---

### Post by strabes on 2007-06-27
There is nothing in dmesg about any sort of wireless card. I grep'd "pro" (for intel/pro wireless) "wireless," etc, all with -i.

Looks like I'm in trouble.

EDIT: I have compiled the kernel several times, each time making sure everything relating to "intel/pro wireless" is enabled but for some reason my wireless card is not recognized with this new kernel.

---

### Post by ydef on 2007-06-28
Liyu:  Thank you!  Works perfectly with 2.6.22-rc3-light1 viper patchset.

Strabes:  Dunno.  Mine work perfectly in firefox.

---

### Post by akincisor on 2007-07-09
The patch works perfectly on 2.6.22. Is this patch going to be incorporated into the kernel soon?

akincisor

---

### Post by plato4me on 2007-07-17
I note that there are two distinct patches attached to this HOWTO.  

    msnek4k-patchset-for-2.6.22.zip 

and

    msnek4k-patchset.zip 

The former unzips to "hid.patch", the latter to "msnek4k-patchset".

I downloaded and unzipped linux-2.6.22 and followed the instructions up to the point where I was supposed to apply the patch.  The HOWTO says to use "msnek4k-patchset".  However, that one produces lots of errors.  "hid.patch", on the other hand runs flawlessly.

Which one to use?  Both?

Well, I'm trying it out with just "hid.patch", and am compiling the kernel now.  However....  I couldn't find anything about "Microsoft Natural Ergonomic 4000" when I configured the thing.  Nothing I had any chance to check as a module to be compiled.  So I'm not optimistic about the result.

Any suggestions?

---

### Post by strabes on 2007-07-17
> **plato4me said:**
> Well, I'm trying it out with just "hid.patch", and am compiling the kernel now.  However....  I couldn't find anything about "Microsoft Natural Ergonomic 4000" when I configured the thing.  Nothing I had any chance to check as a module to be compiled.  So I'm not optimistic about the result.

Any suggestions?

From the 1st post in this thread:

After this, go to Device Drivers --> USB, activate "HID Simple Driver Interface"" and change Microsoft Natural Ergonomic Keyboard 4000 Driver" to "m". **If you can't find it in the configuration hierarchy, you can also press CTRL+F and type "simple" in the search box.**

---

### Post by plato4me on 2007-07-18
Thanks.  That worked for me.

---

### Post by salnet on 2007-07-21
One silly question: What for a driver do I have to load in xorg.conf? At the moment kdb is loaded and the 5 Fav-keys aren't working (plus the Zoom-Slider, the *, and the first three buttons above the numpad). But I read in this thread that someone got them working.
Kernel is 2.6.22.1 from kernel.org with the correct patch (msnek4k-patchset-for-2.6.22)

Thanks in advance for help,
salnet

---

### Post by strabes on 2007-07-21
You have to patch & recompile the kernel to get those buttons to work. See the first post of this thread.

---

### Post by salnet on 2007-07-22
> **strabes said:**
> You have to patch & recompile the kernel to get those buttons to work. See the first post of this thread.I have patched the kernel and recompiled it. So I'm very confused that the buttons still don't work.

Only buttons I got to work are Browser, Search, Mail, Mute, Volume +/-, Play, Calculator, Back, Foraward.
The other extra-keys don't even send a keycode. I think it has something to do that there are only 255 keycodes allowed (see dumpkeys)

---

### Post by Buchinho on 2007-07-22
same problem here!

> **salnet said:**
> I have patched the kernel and recompiled it. So I'm very confused that the buttons still don't work.

Only buttons I got to work are Browser, Search, Mail, Mute, Volume +/-, Play, Calculator, Back, Foraward.
The other extra-keys don't even send a keycode. I think it has something to do that there are only 255 keycodes allowed (see dumpkeys)

---

### Post by liyu on 2007-09-07
This is the patch for 2.6.23-rc5.

Enjoy.

---

### Post by ydef on 2007-09-08
Liyu,

Mucho Gracias! :)  Driver works perfectly in 2.6.23.  Very much appreciate your instant response to my PM request.

Buchinos:  Sucks that it's only happening to you and not the rest of us.  I bet if you read really carefully through this thread you could probably figure out what you're doing wrong.  

Ydef

---

### Post by bluescreen303 on 2007-09-20
Hi, I'm a gentoo user but I have access to an ubuntu box in case I need some files from there.

I'm using the kernel patch for 2.6.22
furthermore I followed the instructions from [http://gentoo-wiki.com/HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000](http://gentoo-wiki.com/HOWTO_Microsoft_Natural_Ergonomic_Keyboard_4000) which I believe was the starting point for ubuntu users too for this keyboard.

I did all the stuff in /usr/share/X11/xkb and I am using 2 evdev's in xorg.conf.

Is this still the way to go?
I've read some stuff about not needing 2 dev's anymore and about using an option to modprobe usbnek4k.
Also I saw some suggestions about using xmodmap instead of fiddling in /usr/share/X11/xkb.

So, after installing the kernel-module, what's the best way to go forward? (xorg.conf / modmaps / other) 

The reason I ask is because I have a few strange issues atm, and before posting them one by one, I'd like to make sure I did follow the right path...

thanks,
Mathijs

---

### Post by measekite on 2007-10-02
> **aresek said:**
> I tried kernel 2.6.18.6 and patches from gentoo wiki and it worked for me :) now it works.

When you upgrade to the next version of Ubuntu what will you have to do to get it working again?

---

### Post by atomic_turtle on 2007-10-10
Hi,

is there any new article/ manual/ howto for Ubuntu or will I have to go by the Howto in the Gentoo-Wiki?
If no separate Howto for Ubuntu systems exists yet - and if the method to do this is sufficiently different to warrant one - I'll happily write an article and put it in the UU Wiki - in German as I am. But of course, to be able to write an article, I first have to get it going myself.
Furthermore, I'm using Edgy and I guess I'll have to upgrade to Feisty at some point. I'm a bit nervous about that bc I don't feel like working this out and then doing it all again after upgrading. Is it possible to carry over kernel-patches?
Regards,

atomic_turtle

P.S.: Oh, I'll have to upgrade anyway. I've now downloaded a patch for kernel 2.6.23 and I have 2.6.17, so...

---

### Post by zerwas on 2007-10-11
> Is it possible to carry over kernel-patches?
No, not that easy.

The HOWTO should also work for you with Edgy. :-)

The only reason i didn't write an article about this was the hope, that this driver would get into Gutsy kernel. But:

"Unfortunately, this driver depends on hid simple driver interface which is not included in the kernel proper. Unless the simple driver interface is included upstream I cant include this driver into gutsy."
-- [Launchpad.net Bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84965")

Best regards,
zerwas

---

### Post by atomic_turtle on 2007-10-12
Okay.
I'll try it out myself.
Maybe you could help me a little bit along the way with this keyboard? Then you could write an article for this Wiki if you want to, I'll write one in German for ubuntuusers.de and I can just give you a translation when I'm done.
I have already made a little progress with the keyboard, but it's really very shaky. I've only rearranged some of the >regular< qwerty keys - but not even that seems to be very reliable, it seems to sometimes work and sometimes not, weird as it sounds...
In the meantime I've upgraded my system to Feisty. I now have Kernel 2.6.20-youknowhat, so I guess getting the right Patch for that Kernel would be a good start ;-)
I'm away for the weekend and if I as much as sit down in front of a computer during that short time, my wife will probably hang, shoot and drown me. But on Monday I can go to work on this.
Regards,

atomic_turtle

---

### Post by vancheese on 2007-10-15
Is this still the only way to enable the special keys for gusty??

---

### Post by ydef on 2007-11-10
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by ydef on 2007-11-10
The only difference now from the HOWTO is that the usbnek4k driver is now compatible with the kbd driver so you no longer need to dick around setting up two devices that use evdev, actually this has been the case for a while.
Here is an example of my input device entry in xorg.conf that I'm using with the present debian unstable version 1:7.3+3 :

 Section "InputDevice"
  Identifier "msnek4k"
  Driver "kbd"
  option "AutoRepeat" "250 50"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbLayout" "en_US"
  option "XkbModel" "microsoftnek4k"
  option "XkbOptions" "caps:internal_nocancel+lv3(switch)+compose(menu)"
EndSection 

 
Then just make sure the identifier appears in the ServerLayout.  Again, from my xorg.conf:

Section "ServerLayout"
  Identifier "default"
  screen 0 "Screen0" 0 0
  InputDevice "mx1000" "CorePointer"
  InputDevice "msnek4k" "CoreKeyboard"
EndSection

---

### Post by ydef on 2007-11-10
Here are all the modified files you need to get it working, just drop the replacements in /usr/share/X11/xkb where they belong.  I've also included my xorg.conf if it helps anyone.

Plug and play.

---

### Post by ydef on 2007-11-10
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by biodiesel-bri on 2007-11-24
Thanks a lot for posting this - I've had one of these keyboards for a long time and never been able to use the special keys.

However, I use this keyboard with a laptop - how do I configure xorg.conf to only use the MS keyboard when it is plugged in and still be able to use the special keys on my laptop?  I'm reluctant to just overwrite the /etc/X11/xkb files that are already there.

---

### Post by ydef on 2007-11-25
You need to add the extra InputDevice section for the MS keyboard in xorg.conf as it shows in my sample.  

Also, you don't have to worry about the drop in replacements, since nothing has been removed.  All the files I've provided have just been augmented to account for the ms 4000 keyboard.

If you're that worried about it you can always make a backup of the files in question.

---

### Post by biodiesel-bri on 2007-11-25
So I added the extra InputDevice section, made backups, dropped in the files and rebooted.  And then neither the laptop nor the USB keyboard would work.  When I commented out the line:
```
    InputDevice           "msnek4k"
```
in /etc/X11/xorg.conf I regained use of both keyboards.  I pulled out the "CoreKeyboard" option because my laptop keyboard already and Xorg complained about it.

Any ideas?

---

### Post by liyu on 2007-11-25
Hi, this is nek4k driver for 2.6.24-rc2, it can apply on 2.6.24-rc3 too. Ydef, I am sorry for this delay so long time since you noticed me. ;-)

---

### Post by ydef on 2007-11-29
Liyu, thank you!  I'm relieved that you are still around. :)

Biodeisel:

You need two entries for InputDevice, one for your native laptop keyboard and one for msnek4k.  And make sure your native keyboard is the core keyboard since its the builtin.  And just for clarification, the geom.microsoft.gz file that I posted in my message should be uncompressed and dropped into the /usr/share/X11/xkb/geometry as the plain text file called microsoft.

If you're still having problems, include a copy of your Xorg.0.log and the xorg.conf you're using in your post.

---

### Post by tukanos on 2007-12-08
I'm a gentooer, but I want to thank you for this amazing thread.  It took me some hours to tune everything (have to map the 1-5 & My Favourites), but now it works just fine :)).

Want to thank you Liyu for writing this patch (cruised through the source :), nice work.

Ydef for the work & the last definition which doesn't need the the udev entries.  I had hard time with the overlapping of the keys (with the mod).

Thanks everyone

p.s. nice to have control for Amarok like
dcop amarok player playPause
dcop amarok player stop
dcop amarok player prev
dcop amarok player next

---

### Post by vda on 2007-12-26
> **zerwas said:**
> [SIZE="1"]Thanks:
Credit for the kernel-howto goes to [master_kernel]("http://ubuntuforums.org/member.php?u=201430")
I'd also like to thank trantorvega for the Gentoo-Page.
[strabes]("http://ubuntuforums.org/member.php?u=127592") for clarifying a few things.
And, most of the work to get your keyboard working did [Liyu]("http://ubuntuforums.org/member.php?u=150309") for you! :-) And, he is still working! [SIZE="1"](the Patch is also available at [http://lkml.org/]("http://lkml.org/") from [liyu]("http://groups.google.de/groups/profile?enc_user=t81lOhQAAACCDIdHxTwHAJ5EM1tIJ6nKOPANdqfI6prRsqjc7uCt1A&hl=de"))[/SIZE][/SIZE]

Any plans to push it into mainstream kernel?

From the cursory llok at the code it seems to need some style polishing and a bit on English language fixes, but overall it doesn't seem to be badly written.

---

### Post by arbrandes on 2007-12-27
> **vda said:**
> Any plans to push it into mainstream kernel?

Apparently, it already has:

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=1fe8736da695c2b14961438c73d5600538bd92d9;hp=4dc21a8005216ee3784df545f028775242c6f499](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=1fe8736da695c2b14961438c73d5600538bd92d9;hp=4dc21a8005216ee3784df545f028775242c6f499)

---

### Post by ydef on 2008-01-08
> **arbrandes said:**
> Apparently, it already has:

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=1fe8736da695c2b14961438c73d5600538bd92d9;hp=4dc21a8005216ee3784df545f028775242c6f499](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=1fe8736da695c2b14961438c73d5600538bd92d9;hp=4dc21a8005216ee3784df545f028775242c6f499)

This link you provided arbrandes is NOT the patch for msnek4k.

---

### Post by big dizzle on 2008-01-08
Going through this walkthrough.  I did the first five steps of the howto that was linked, then I did the first three steps on this howto.  On the first step of the howto on this page:
> sudo cp /boot/config-`uname -r` .config && sudo make oldconfig
I get the following:
> scripts/kconfig/conf -o arch/x86_64/Kconfig
.config:34:warning: trying to assign nonexistent symbol ACPI_CUSTOM_DSDT_INITRD
.config:46:warning: trying to assign nonexistent symbol ACPI_SLEEP_PROC_FS
.config:47:warning: trying to assign nonexistent symbol ACPI_SLEEP_PROC_SLEEP
.config:596:warning: symbol value 'm' invalid for EDAC
.config:600:warning: trying to assign nonexistent symbol EDAC_POLL
.config:708:warning: symbol value 'm' invalid for FB_VESA
.config:887:warning: trying to assign nonexistent symbol I2C_ISA
.config:893:warning: trying to assign nonexistent symbol I2C_POULSBO
.config:1120:warning: trying to assign nonexistent symbol IP_ROUTE_MULTIPATH_CACHED
.config:1357:warning: trying to assign nonexistent symbol MSS
.config:1541:warning: trying to assign nonexistent symbol NET_ESTIMATOR
.config:1619:warning: trying to assign nonexistent symbol NIU
.config:1677:warning: trying to assign nonexistent symbol OSS_OBSOLETE
.config:1807:warning: trying to assign nonexistent symbol PM_DISABLE_CONSOLE
.config:1810:warning: trying to assign nonexistent symbol PM_SYSFS_DEPRECATED
.config:2228:warning: trying to assign nonexistent symbol SOFTWARE_SUSPEND
.config:2277:warning: trying to assign nonexistent symbol SUSPEND_SMP
.config:2553:warning: trying to assign nonexistent symbol VERSION_SIGNATURE
.config:2694:warning: trying to assign nonexistent symbol WRAPPER_PRINT
.config:2758:warning: trying to assign nonexistent symbol IPC_NS
.config:2766:warning: trying to assign nonexistent symbol UTS_NS
*
* Linux Kernel Configuration
*
*
* General setup
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [Y/n/?] y
Local version - append to kernel release (LOCALVERSION) [] 
Automatically append version information to the version string (LOCALVERSION_AUTO) [N/y/?] n
Support for paging of anonymous memory (swap) (SWAP) [Y/n/?] y
System V IPC (SYSVIPC) [Y/n/?] y
POSIX Message Queues (POSIX_MQUEUE) [Y/n/?] y
BSD Process Accounting (BSD_PROCESS_ACCT) [Y/n/?] y
  BSD Process Accounting version 3 file format (BSD_PROCESS_ACCT_V3) [Y/n/?] y
Export task/process statistics through netlink (EXPERIMENTAL) (TASKSTATS) [N/y/?] n
User Namespaces (EXPERIMENTAL) (USER_NS) [N/y/?] (NEW) unzip msnek4k-patchset.zip -d /tmp
User Namespaces (EXPERIMENTAL) (USER_NS) [N/y/?] (NEW) sudo patch -p1 < /tmp/msnek4k-patchset
User Namespaces (EXPERIMENTAL) (USER_NS) [N/y/?] (NEW) 


This is where it ends.  I may be a newb, but I'm guessing that this isn't the command prompt that the person who wrote this thread had in mind when they had step three
> unzip msnek4k-patchset.zip -d /tmp
in mind.

What should I do with this?  Should I hit enter/y/n until I get the command prompt again?  

Also, from the following command
> unzip msnek4k-patchset.zip -d /tmp 
it looks the the thread author meant for the file to be downloaded to /tmp, is that correct?

---

### Post by Andrew Pape on 2008-01-17
Hi ydef,

I've tried several times, with several boots, to get the extra keys to work on Feisty Fawn 7.04, following all the advice given with the 5 zipped files, and hopefully putting them in the right place. The new keyboard still works, but the extra keys don't, except for mail and calculator, but I know mail always worked out of the box, and probably calculator too. I have renamed the geometry file as "microsoft" as suggested, and inspected that file, which seems to set up the multimedia keys. But no go. With several dirs involved and a great chance I've put the wrong file somewhere, maybe I should post the contents of the files, like xorg.conf, microsoft, etc, along with the full directory names?  I don't have a laptop, so shouldn't have laptop issues, but there is different info in a similar thread: [http://ubuntuforums.org/showthread.php?p=3834452#post3834452]("http://ubuntuforums.org/showthread.php?p=3834452#post3834452")
which says that a patch zip file must be run. I downloaded a patch and ran it as an executable, after viewing it first as a text file, but executing it didn't help.

Any help greatly appreciated.

Cheers,

Andrew.

---

### Post by Andrew Pape on 2008-01-17
Hi,

after experimentation with System->Preferences->Keyboard Shortcuts, I was quickly able to get the Web/Home button working on my keyboard. I still haven't achieved everything, as I want to be able to use the My Documents Button and the 5 My Favorurites Buttons at the top. Nor does the Log Off button respond. It seems my tinkering in the last post hasn't achieved much, except the system still works.

I then tried System->Prefs->Keyboard, which had a basic, not ms keyboard set up, despite my tinkering with system files at the command line in the last post. I looked at the list of Microsoft keyboards, and none matched mine. I tried a couple and then tried remapping keys, but no more success. I'd like to get the "*" and My Favoruites working most of all. Surely you'd need some extra software to provide a user interface to set up the My Favorurites, like when using Windows?

Any help much appreciated.

Thanks,

Andrrew.

---

### Post by ydef on 2008-01-26
> **Andrew Pape said:**
> Hi,

after experimentation with System->Preferences->Keyboard Shortcuts, I was quickly able to get the Web/Home button working on my keyboard. I still haven't achieved everything, as I want to be able to use the My Documents Button and the 5 My Favorurites Buttons at the top. Nor does the Log Off button respond.

Well, if some of the special keys work that's a good sign.  Test the keys that don't work with the xev utility.  execute it from a shell from a terminal window and a box will show up.  Place your pointer on it and try pressing the keys that don't work for you.

If the driver's working, which it sounds like it is if you have 'some' of the keys working, you'll see that each key you press will provide a keycode in the term window.  If that works then you're in business.  Run kcontrol and go to accessibility -> keyboard shortcuts and map the keys you want to the apps you want to fire up when pressing them.  It's as simple as that.

Also, make sure that if you're updating packages that an upgraded version of xkb-data doesn't wipe out the customized files I provided.  If it does, you'll need to replace them.  What I've done to avoid that hassle is use dpkg-divert to divert the original files into one of a different name like dpkg-divert --add --rename --divert /usr/share/X11/xkb/geometry/microsoft.old /usr/share/X11/xkb/geometry/microsoft

That will move the original file to the new file microsoft.old.  Then just drop the modified microsoft file that I provided in the directory to replace the diverted one.  Do that for each modified file I provided.  That way any new apt-get upgrades you do won't overwrite modified files and instead will replace the diverted files.

Hope that helps.

---

### Post by ydef on 2008-01-26
In one of my prior posts I posted four drop in replacement files including my xorg.conf files.  The drop in replacements were geometry.dir,keycodes.dir,symbols.dir, and geometry/microsoft.  These are NOT the only files that need to be modified so if you were thinking that was it without following the FAQ it's little wonder why you haven't gotten all the buttons working.

I've made it simpler by uploading a tar.gz file with ALL the modified files required to get the driver working properly plus a .txt file that will direct you where to place them.

These files have been modded from the latest xkb-data package version 1.1~cvs.20080104.1-1 or 1.1~cvs.20080104.1-1ubuntu1 

Don't forget that you still need to recompile the kernel with liyu's patch to get things working.  These files just save you the extra hassle of having to modify anything.  You can just recompile, drop in the file replacements, and assuming the keyboard section of your xorg.conf is configured properly all should be well.

One other snag I discovered on the patch for the 2.6.24 kernel is that you MUST have the kernel option set to CONFIG_HID=y , you CANNOT have it set as a module since it has a dependency on the usb_hid module, and as co-existing modules they hose into an infinite loop.

---

### Post by alsuren on 2008-01-31
> **ydef said:**
> <snip>

While that kind of attitude may be welcome on the Debian lists, I don't think there's room for it (rudeness)* here. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84965/comments/19](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84965/comments/19)
seems to report that it works on red hat (I assume without recompilation), so re-compiling the kernel is *not* required for those wanting to use linux.

Also, support was committed to Linus'  kernel tree on 9 Aug 2007, and is included in the 2.6.24 kernel. Upgrading to Hardy should fix this. I will probably wait until march before doing that. Upgrading just the kernel is also possible: [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755) but also might eat your babies (though no more so than using unsigned executable installers on windows).

---

### Post by jstgtpaid on 2008-03-12
I upgraded ubuntu to Hardy.  Could someone post instructions on how to get this keyboard working with Hardy?  

Supposedly this kernel supports the ms4k keyboard, but it still shows as generic in the keyboard preferences.  Using the files various conf files supplied by Ydef (thanks for taking the time to make them btw) did not work for me either.

I copied all the files supplied by Ydef except for the xorg.conf and there was no change in functionality.  When I made the changes to the keyboard components of the xorg.conf to match the Ydef xorg.conf keyboard components, then gnome would not start.  I was able to get into a command line and put the old files back, but I would like to get this running.

Can someone provide Hardy friendly instructions?

Thanks in advance...
Steven

---

### Post by linuxpenguin on 2008-03-15
This is stupid. . . but could anyone tell me where this "xmodmap" file would be for Debian Lenny?  Can't find it. . . it's not in my home directory, and it's not in /etc/X11/xmodmap (as this forum post suggests it is in Gentoo: [http://forums.gentoo.org/viewtopic-p-3607844.html#3607844](http://forums.gentoo.org/viewtopic-p-3607844.html#3607844)).

I need to find it (and you do too) to make some of the keys work - they spit out a keycode which is fine for some apps. . . but I want to, for example, use the Zoom thing for Compiz, and use some of the other keys.  Compiz doesn't seem to want to let me do this if it doesn't have a key name to refer to (but GNOME's "System > Preferences > Keyboard Shortcuts" program has no problem if I want to use any of these special keys - but it only shows their keycode to refer to them, for example "Play/Pause" is 0xac).

I know this is Ubuntu not Debian, but I figure they are very similar.  I tried searching, but this file didn't come up. . . is it something I have to create?  I'm just guessing that there's some file already setting up the keybindings for xmodmap - since xmodmap -pke spits out a bunch of info:
```
@darkwing:~$ xmodmap -pke
keycode   8 =
keycode   9 = Escape
keycode  10 = 1 exclam
keycode  11 = 2 at
keycode  12 = 3 numbersign
keycode  13 = 4 dollar
keycode  14 = 5 percent
keycode  15 = 6 asciicircum
keycode  16 = 7 ampersand
keycode  17 = 8 asterisk
keycode  18 = 9 parenleft
keycode  19 = 0 parenright
keycode  20 = minus underscore
keycode  21 = equal plus
keycode  22 = BackSpace Terminate_Server
keycode  23 = Tab ISO_Left_Tab
keycode  24 = q Q
keycode  25 = w W
keycode  26 = e E
keycode  27 = r R
keycode  28 = t T
keycode  29 = y Y
keycode  30 = u U
keycode  31 = i I
keycode  32 = o O
keycode  33 = p P
keycode  34 = bracketleft braceleft
keycode  35 = bracketright braceright
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = a A
keycode  39 = s S
keycode  40 = d D
keycode  41 = f F
keycode  42 = g G
keycode  43 = h H
keycode  44 = j J
keycode  45 = k K
keycode  46 = l L
keycode  47 = semicolon colon
keycode  48 = apostrophe quotedbl
keycode  49 = grave asciitilde
keycode  50 = Shift_L
keycode  51 = backslash bar
keycode  52 = z Z
keycode  53 = x X
keycode  54 = c C
keycode  55 = v V
keycode  56 = b B
keycode  57 = n N
keycode  58 = m M
keycode  59 = comma less
keycode  60 = period greater
keycode  61 = slash question
keycode  62 = Shift_R
keycode  63 = KP_Multiply XF86_ClearGrab
keycode  64 = Alt_L Meta_L
keycode  65 = space
keycode  66 = Caps_Lock
keycode  67 = F1 XF86_Switch_VT_1
keycode  68 = F2 XF86_Switch_VT_2
keycode  69 = F3 XF86_Switch_VT_3
keycode  70 = F4 XF86_Switch_VT_4
keycode  71 = F5 XF86_Switch_VT_5
keycode  72 = F6 XF86_Switch_VT_6
keycode  73 = F7 XF86_Switch_VT_7
keycode  74 = F8 XF86_Switch_VT_8
keycode  75 = F9 XF86_Switch_VT_9
keycode  76 = F10 XF86_Switch_VT_10
keycode  77 = Num_Lock Pointer_EnableKeys
keycode  78 = Scroll_Lock
keycode  79 = KP_Home KP_7
keycode  80 = KP_Up KP_8
keycode  81 = KP_Prior KP_9
keycode  82 = KP_Subtract XF86_Prev_VMode
keycode  83 = KP_Left KP_4
keycode  84 = KP_Begin KP_5
keycode  85 = KP_Right KP_6
keycode  86 = KP_Add XF86_Next_VMode
keycode  87 = KP_End KP_1
keycode  88 = KP_Down KP_2
keycode  89 = KP_Next KP_3
keycode  90 = KP_Insert KP_0
keycode  91 = KP_Delete KP_Decimal
keycode  92 =
keycode  93 = Mode_switch
keycode  94 = less greater bar brokenbar bar brokenbar
keycode  95 = F11 XF86_Switch_VT_11
keycode  96 = F12 XF86_Switch_VT_12
keycode  97 = Home
keycode  98 = Up
keycode  99 = Prior
keycode 100 = Left
keycode 101 =
keycode 102 = Right
keycode 103 = End
keycode 104 = Down
keycode 105 = Next
keycode 106 = Insert
keycode 107 = Delete
keycode 108 = KP_Enter
keycode 109 = Control_R
keycode 110 = Pause Break
keycode 111 = Print Sys_Req
keycode 112 = KP_Divide XF86_Ungrab
keycode 113 = Alt_R Meta_R
keycode 114 =
keycode 115 = Super_L
keycode 116 = Super_R
keycode 117 = Menu
keycode 118 =
keycode 119 =
keycode 120 =
keycode 121 =
keycode 122 =
keycode 123 =
keycode 124 = ISO_Level3_Shift
keycode 125 = NoSymbol Alt_L
keycode 126 = KP_Equal
keycode 127 = NoSymbol Super_L
keycode 128 = NoSymbol Hyper_L
keycode 129 =
keycode 130 =
keycode 131 =
keycode 132 =
keycode 133 =
keycode 134 =
keycode 135 =
keycode 136 =
keycode 137 =
keycode 138 =
keycode 139 =
keycode 140 =
keycode 141 =
keycode 142 =
keycode 143 =
keycode 144 =
keycode 145 =
keycode 146 =
keycode 147 =
keycode 148 =
keycode 149 =
keycode 150 =
keycode 151 =
keycode 152 =
keycode 153 =
keycode 154 =
keycode 155 =
keycode 156 = NoSymbol Meta_L
keycode 157 =
keycode 158 =
keycode 159 =
keycode 160 =
keycode 161 =
keycode 162 =
keycode 163 =
keycode 164 =
keycode 165 =
keycode 166 =
keycode 167 =
keycode 168 =
keycode 169 =
keycode 170 =
keycode 171 =
keycode 172 =
keycode 173 =
keycode 174 =
keycode 175 =
keycode 176 =
keycode 177 =
keycode 178 =
keycode 179 =
keycode 180 =
keycode 181 =
keycode 182 =
keycode 183 =
keycode 184 =
keycode 185 =
keycode 186 =
keycode 187 =
keycode 188 =
keycode 189 =
keycode 190 =
keycode 191 =
keycode 192 =
keycode 193 =
keycode 194 =
keycode 195 =
keycode 196 =
keycode 197 =
keycode 198 =
keycode 199 =
keycode 200 =
keycode 201 =
keycode 202 =
keycode 203 =
keycode 204 =
keycode 205 =
keycode 206 =
keycode 207 =
keycode 208 =
keycode 209 =
keycode 210 =
keycode 211 =
keycode 212 =
keycode 213 =
keycode 214 = XF86Display
keycode 215 =
keycode 216 =
keycode 217 =
keycode 218 =
keycode 219 =
keycode 220 =
keycode 221 =
keycode 222 =
keycode 223 =
keycode 224 =
keycode 225 =
keycode 226 =
keycode 227 =
keycode 228 =
keycode 229 =
keycode 230 =
keycode 231 =
keycode 232 =
keycode 233 =
keycode 234 =
keycode 235 =
keycode 236 =
keycode 237 =
keycode 238 =
keycode 239 =
keycode 240 =
keycode 241 =
keycode 242 =
keycode 243 =
keycode 244 =
keycode 245 =
keycode 246 =
keycode 247 =
keycode 248 =
keycode 249 =
keycode 250 =
keycode 251 =
keycode 252 =
keycode 253 =
keycode 254 =
keycode 255 =

```

---

### Post by StratosL on 2008-03-22
> **jstgtpaid said:**
> I 

Can someone provide Hardy friendly instructions?

Thanks in advance...
Steven

Yes please, could someone?

Thx!

---

### Post by ydef on 2008-04-06
> **alsuren said:**
> While that kind of attitude may be welcome on the Debian lists, I don't think there's room for it here.

Sure.  Whatever you say.  I was trying to make the statement for your benefit and apologize if it came across as too harsh.

> 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84965/comments/19](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84965/comments/19)
seems to report that it works on red hat (I assume without recompilation), so re-compiling the kernel is *not* required for those wanting to use linux.
Then I would encourage you to use Redhat if you really want it working.

> 
Also, support was committed to Linus'  kernel tree on 9 Aug 2007, and is included in the 2.6.24 kernel. Upgrading to Hardy should fix this. I will probably wait until march before doing that. Upgrading just the kernel is also possible: [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755) but also might eat your babies (though no more so than using unsigned executable installers on windows).Good luck on that account.  I'm at present running 2.6.24-rc8 and it required compilation of the patch into the kernel so Linus hasn't integrated it yet.  The most you could hope for if you don't want to recompile is for the ubuntu packagers to include the module in a pre-compiled ubuntu kernel, but I would strongly urge you to learn how to recompile the kernel since you can totally customize and cater it specifically to your hardware and the performance difference can be profound.

On another note, there is a new debian/ubuntu package that *might* simplify it for you called 'keytouch'.  You might want to apt-get it and see if you can get it working with the GUI it provides.

---

### Post by ydef on 2008-04-06
> **jstgtpaid said:**
> I upgraded ubuntu to Hardy.  Could someone post instructions on how to get this keyboard working with Hardy?  

Supposedly this kernel supports the ms4k keyboard, but it still shows as generic in the keyboard preferences.  Using the files various conf files supplied by Ydef (thanks for taking the time to make them btw) did not work for me either.

I copied all the files supplied by Ydef except for the xorg.conf and there was no change in functionality.  When I made the changes to the keyboard components of the xorg.conf to match the Ydef xorg.conf keyboard components, then gnome would not start.  I was able to get into a command line and put the old files back, but I would like to get this running.

Can someone provide Hardy friendly instructions?

Thanks in advance...
Steven

Out of curiosity, did you apply LiYu's patch and recompile the kernel as I mentioned is an absolute requirement in my last post?  You didn't mention what kernel version you 'upgraded' to when you upgraded to hardy.  
Did you have it working *before* you upgraded to hardy?

---

### Post by ydef on 2008-04-08
> **linuxpenguin said:**
> This is stupid. . . but could anyone tell me where this "xmodmap" file would be for Debian Lenny?  Can't find it. . . it's not in my home directory, and it's not in /etc/X11/xmodmap 

You need to create your own .Xmodmap hidden file in your home directory by using the output of 'xmodmap -pke', which your X startup script *should* run the xmodmap binary on in here when X starts up:

/etc/X11/Xsession.d/80ubuntu-xmodmap

After creating your .Xmodmap file in your home directory, customize it to your heart's content.  Also, for good measure add your .Xmodmap file to the system's /etc/X11/xinit directory as well. 

If for whatever reason it doesn't xmodmap your .Xmodmap file when X starts up, you need to add it to your startup scripts for X.  For instance, since I prefer to boot into a console before running startx, I've included in my .xsession file the line:

xmodmap ~/.Xmodmap &

I've attached my customized gzipped .Xmodmap file so you can see how I've customized it, including my customizations for the pointer (My mouse is a logitech mx1000) and also the 8 modifier keys at the end.

You can tell the custom keys that I've added to the proper keycodes because their names are prefixed by the 'XF86'.

Good luck!

---

### Post by jstgtpaid on 2008-04-08
> **ydef said:**
> Out of curiosity, did you apply LiYu's patch and recompile the kernel as I mentioned is an absolute requirement in my last post?  You didn't mention what kernel version you 'upgraded' to when you upgraded to hardy.  
Did you have it working *before* you upgraded to hardy?

I apologize.  I was under the impression that simply upgrading to Hardy was going to address my concerns.  I must have got that impression from a different post and saw what I wanted to when I read yours.

However, by installing Hardy, I do have a measure of success now with this keyboard.  Most of the buttons work automatically; which is fantastic.  However, the zoom key does not appear to do anything.  It is probably just a matter of mapping the key to an action ( I hope) but I will research that one.

Thanks for your assistance and guidance!

---

### Post by alsuren on 2008-04-09
> **jstgtpaid said:**
> I apologize.  I was under the impression that simply upgrading to Hardy was going to address my concerns.  I must have got that impression from a different post and saw what I wanted to when I read yours.
Hrrrrm... I never actually upgraded before I posted. Sorry if I got people's hopes up too high. I'm using 2.6.24-12-generic, on hardy and zoom and spell are still broken but all of the rest of the buttons seem to have started working (using xev to test), which is good enough for me. 

I might take another look at what ydef is talking about when I get more time. While I was constantly tweaking my kernel back on Gentoo, I prefer to let my package manager handle kernel stuff these days. That way I don't have to think about security updates.

---

### Post by ydef on 2008-04-24
Since recompiling up to kernel 2.6.25-rc9, I can confirm that at least from this version (any of the 2.6.25 run control revisions) that it no longer requires LiYu's additional patch to the source + recompile.  From Alsuren's post, it looks like support was provided as early as the later revisions of 2.6.24 and is available in the present linux-image-2.6.24-16-generic hardy package.  

The only major issues unaccounted for in my present kernel seem identical to what Alsuren reported with the zoom controller and the spell key being the only deadbeats.  It also required me to reconfigure my .Xmodmap file, as most of the XF86 specialty keys require different keycodes than the ones used by the earlier extraneous patch. (The entire top row, and F-unlocked second row required reconfiguration via xev.) 

I, however, found no source code in this kbd X driver that will support the Zoom Scroller out of the box, a fact that I confirmed with Liyu to which he replied he might provide a patch for.

Using event device IRQ's, I discovered these keys to be 432 (Spell), 418 (Zoom Up), and 419 (Zoom Down) ... so these signals have yet to be transposed to numbers 255 and below and will not be recognized in X until they are.  So the focus of another msnek4k patch release would be on these three keys (or one key and the zoomer sounds better).

---

### Post by tedtlogan on 2008-06-28
Hi,

I have 2.6.25 kernel, so I shouldn't need any patches, right?

The only thing I don't have working on my keyboard is the zoom scroll thing
[http://i.testfreaks.com/images/products/600x400/159/microsoft-natural-ergonomic-keyboard-4000.205983.jpg](http://i.testfreaks.com/images/products/600x400/159/microsoft-natural-ergonomic-keyboard-4000.205983.jpg)

#1 there.

What do I need to do to enable that, like for firefox to go up and down?

---

### Post by enigma20 on 2008-07-09
Hi :)
I have one question just to be sure. So if I have Ubuntu 8.04 this keybord will be work correct without any configurations [of course I mean basic keys, without multimedia-keys] - just plug & play ?

---

### Post by dboot on 2008-07-09
> **enigma20 said:**
> Hi :)
I have one question just to be sure. So if I have Ubuntu 8.04 this keybord will be work correct without any configurations [of course I mean basic keys, without multimedia-keys] - just plug & play ?

Yes, the keyboard works without any configuration with Hardy (and latest kernel that Hardy comes with). However, some extra functionality of the keyboard may or may not work for you such as the Zoom or My Favorites buttons.

For me, neither Zoom nor Back/Forward buttons work but Web/Home, Search, Mail, My Favorites, Mute, Volume up/down, Start/Pause, and Calculator work perfectly with no extra configuration.

---

### Post by enigma20 on 2008-07-14
I buy this keybord. I have Ubuntu 8.04.1, kernel 2.6.24-19, gnome 2.22.3
Work fine:
- web/home
- search
- mail
- My Favourites
- Calculator
- Back/Forward

Other buttons doesn't work. Buttons to change volume only shows pop'up with bar showing that volume was changed, but it isn't.
Are you set special keybord from Menu System-Administration-Keyboard ?

---

### Post by raccoonone on 2008-07-18
How did you get the Back/Forward buttons to work for a web browser? Everything is working for me except for the Zoom and the Back/Forward buttons.

---

### Post by enigma20 on 2008-07-24
**To configure Back/Forward**: I set in System/Preferences/Keyboard -> and second tab [I don't know how it was called in english :P I use polsih version of ubuntu]
and next _keyboard model_ - and I choose _Microsoft Inc._ and model _Microsoft Natural Keyboard Pro OEM_
thats all, Back/Forward works fine


I configure buttons (mute, volume change, play/pause) :) If I set it in system configuration then doesn't work for Amarok. To use it in Amarok we must remove it from system configuration and in Amarok go to "Settings -> Global shortcuts..." and it works fine :)


Have you got any idea how run other applications by buttons form 1-5, for example how to connect them with liferea, pidgin, eclipse :?:

---

### Post by sandos on 2008-07-28
I am using this keyboard on 8.04, and everything is working, EXCEPT the numeric keypad??

I've set my keyboard layout to Microsoft Natural OEM. Evtest shows events for my keypad, and numlock.

---

### Post by sandos on 2008-08-02
I solved my problem: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/197589](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/197589)

I just enabled, and then disabled the mouse emulation thingy for numeric keypad.

---

### Post by dhbabey on 2008-08-13
Sorry to be thick (if I missed something), but from perusing the thread I have been unable to tell whether its possible to make the zoom slider (zoomer) work...

I don't really care about any of the other "special" buttons, but having the zoomer act as a scroll wheel would be REALLY useful.

I'm currently running 8.04, with kernel 2.6.24 and the keyboard works fine out of the box, except for the zoom (as other people have reported)

If I apply the patches and recompile the kernel will the zoom button work???

What is the easiest way to get the zoom button to work.

thanks!

---

### Post by folke on 2008-09-15
> **dhbabey said:**
> Sorry to be thick (if I missed something), but from perusing the thread I have been unable to tell whether its possible to make the zoom slider (zoomer) work...

I don't really care about any of the other "special" buttons, but having the zoomer act as a scroll wheel would be REALLY useful.

I'm currently running 8.04, with kernel 2.6.24 and the keyboard works fine out of the box, except for the zoom (as other people have reported)

If I apply the patches and recompile the kernel will the zoom button work???

What is the easiest way to get the zoom button to work.

thanks!

Hi, did you get any answer on this?
I am interested in this to, Microsoft can at least go good hw :)

---

### Post by zerwas on 2008-09-21
> **folke said:**
> Hi, did you get any answer on this?
I am interested in this to, Microsoft can at least go good hw :)

Have a look at my updated HOWTO. Especially Appendix [3]. Good luck with it and i would be happy about feedback if it works.

---

### Post by brnetonboy on 2008-09-29
> **zerwas said:**
> Have a look at my updated HOWTO. Especially Appendix [3].

Sorry: where exactly is your howto?

---

### Post by zerwas on 2008-10-02
> **brnetonboy said:**
> Sorry: where exactly is your howto?

It's right [in front of you]("http://ubuntuforums.org/showpost.php?p=1339131&postcount=1"). ;-)

---

### Post by brnetonboy on 2008-10-02
d'oh!!! thanks... 	:oops:

---

### Post by roachmmflhyr on 2008-11-01
Keybaord no longer works in Ubuntu 8.10 w/ 2.6.27-generic kernel...:(

---

### Post by raccoonone on 2008-11-01
it still works for me, however the Back and Forward buttons have stopped working since upgrading to Intrepid

---

### Post by euphgeek on 2008-11-08
Hi,
I just bought this keyboard and plugged it in.  It works fine, except for a few keys.  The right control, end and the =, (, ) keys in the upper right-hand corner.  I'm running Ubuntu 8.04 with kernel 2.6.24-21-generic.  Here's an output of the relevant lines from dmesg:

```
[   30.098314] input: Microsoft Natural<AE> Ergonomic Keyboard 4000 as /devices/
pci0000:00/0000:00:13.0/usb1/1-2/1-2:1.0/input/input1
[   30.129898] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Natural<AE> Ergo
nomic Keyboard 4000] on usb-0000:00:13.0-2
[   30.143173] input: Microsoft Natural<AE> Ergonomic Keyboard 4000 as /devices/
pci0000:00/0000:00:13.0/usb1/1-2/1-2:1.1/input/input2
[   30.165854] input,hidraw1: USB HID v1.11 Device [Microsoft Natural<AE> Ergono
mic Keyboard 4000] on usb-0000:00:13.0-2
```

Any suggestions?

---

### Post by cynoclast on 2008-11-17
How do I make the favorites keys work with amarok?

Or perhaps more usefully:  How do I make them work to launch a command?

I got it working with Rythmbox by binding them in keyboard shorcuts.  It was remarkably easy that way.

But what if I wanted to use amarok?

the commands: ```
dcop amarok player next
dcop amarok player prev
```

do the trick, but it would be nice to be able to bind the keys to arbitrary commands.

---

### Post by craig100 on 2009-01-25
How did you map your + - stop/pause and mute keys?  Also the calculator key?  I'm finding the +- keys show a speaker icon on the screen and the bar beneath increases and decreases but the volume stays the same. Using RythmBox.

Thanks,

Craig

---

### Post by lkilcher on 2009-02-13
> **euphgeek said:**
> Hi,
I just bought this keyboard and plugged it in.  It works fine, except for a few keys.  The right control, end and the =, (, ) keys in the upper right-hand corner.  I'm running Ubuntu 8.04 with kernel 2.6.24-21-generic.  Here's an output of the relevant lines from dmesg:

```
[   30.098314] input: Microsoft Natural<AE> Ergonomic Keyboard 4000 as /devices/
pci0000:00/0000:00:13.0/usb1/1-2/1-2:1.0/input/input1
[   30.129898] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Natural<AE> Ergo
nomic Keyboard 4000] on usb-0000:00:13.0-2
[   30.143173] input: Microsoft Natural<AE> Ergonomic Keyboard 4000 as /devices/
pci0000:00/0000:00:13.0/usb1/1-2/1-2:1.1/input/input2
[   30.165854] input,hidraw1: USB HID v1.11 Device [Microsoft Natural<AE> Ergono
mic Keyboard 4000] on usb-0000:00:13.0-2
```

Any suggestions?

I am having a very similar problem, except that the keys listed above work for me.  The ones that do not are keypad 2,3,5,6,8,9 (the middle six in the keypad).  I ran xev, and there was absolutely no events on the pressing of any of these keys.  What does this mean?

I have the MS Natural Ergo. 4000 v1.0 (KU-0462, Part No. X802610-001).

thanx,
lk

---

### Post by diegotorquemada on 2009-02-17
Configuring the "Microsoft Ergonomic Natural Keyboard 4000" under [B][SIZE="5"]Debian 5 Lenny
[/SIZE][/B]

In order that they USB keyboard works in the GRUB screen, enable from the bios setup the
"Legacy USB keyboard support" option

Install the unstable package xkb-data_1.5-2_all.deb (available at: [http://packages.debian.org/search?keywords=xkb-data](http://packages.debian.org/search?keywords=xkb-data) )

In the kcontrol (control center) -> keyboard layout: activate the keyboard model "Microsoft Natural Wireless Ergonomic Keyboard 7000".

And voila!

If you want to test the keys use the
[FONT="Courier New"]$ xev[/FONT]
command, and run
[FONT="Courier New"]$ modmap -pke[/FONT]
in order to see all the keycode associations.

I also changed my /etc/X11/xorg.conf to
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "**microsoft7000**"
        Option          "XkbLayout"     "latam"
EndSection

```

---

### Post by CodeNosher on 2009-04-07
I just upgraded from 7.10 to 8.04.  On 7.10 the mute and +/- vol keys worked fine.  Now I get a picture that changes, but the volume stays the same.  I see others have the same problem.

Does anyone have a good fix for it?

---

### Post by CodeNosher on 2009-04-07
FINALLY!!  After lots of digging I found this old post:

[http://ubuntuforums.org/archive/index.php/t-377740.html](http://ubuntuforums.org/archive/index.php/t-377740.html)

"Navigate to System->Preferences->Sound. In the bottom combo-box, Ctrl-Left Click all the sound "devices" you want controlled by the volume keys."

Why it changed from Master to Capture I don't know, but it works now!!

The mute key is very handy in the office :D

---

### Post by LinusX on 2009-07-05
Hello,
I found a link to this thread on the german forum ubuntuusers.de.
I am using Ubuntu 9.04 64bit (german version) and the MS Ergonomic Keyboard 4000. Some of the extra keys like calculator, mute, volume+/-, e-mail, back/forward work fine, but some don't, like 1-5, the special f-keys and the zoom "wheel" and some don't work the way I want, like the browser button (opening nautilus instead of firefox) and play/pause (not working in audacious).
Could you tell me a way to fix these without having to read the whole 17 pages thread or being a professional programmer?
Thanks in advance!
Linus X.

---

### Post by jeje2a on 2009-11-21
Hi everybody
I am a french Linux Ubuntu user
I have a M$ Ergonomic Natural Keyboard 4000 over Ubuntu 8.04 with Kernel 2.6.24-25
i follow the instructions but it seems the patchset is for Kernel  2.6.21.1 or 2.6-22
it doesn't work for me...
Please , anyone have an idea ?
Thank you in advance

---

### Post by Jens Getreu on 2010-01-18
I just bought a "Microsoft Natural Ergonomic Keyboard 4000"

I am running ubuntu 9.10 with kernel 2.6.31-17-generic (amd64).

In the keyboard configuration tool I did not find the 4000 model so I tried out
all the other ones. 

My problem: all keys work fine except the function keys F1-F12 which I use 
very frequently (the zoom wheel does not work either). 
Furthermore it is not possible to switch with cntl-alt-F1 to a text console.

As I understand from this thread, there should exist a driver module for this 
keyboard. How can I enable it?

---

### Post by Samage on 2010-01-22
You may want to investigate the 'F Lock' key right at the end of the 'F' keys. Make sure it is on.

---

### Post by johnswb on 2010-01-27
Just installed this keyboard today.  Did anyone get the "favorites keys" working along with the "zoom"?  I'm running Ubuntu 9.10 and everything works except for favorites and zoom, nor the F-Lock key. 

~$ uname -a
Linux Ubuntu-9-10 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

---

### Post by Jens Getreu on 2010-02-06
> **Samage said:**
> You may want to investigate the 'F Lock' key right at the end of the 'F' keys. Make sure it is on.

Thanks!  Sometimes the solution is so easy! I would had never expected a special key blocking the other function keys. Especially not after 18 pages of discussion about drivers. :D

---

### Post by Jens Getreu on 2010-02-06
> **johnswb said:**
> Just installed this keyboard today.  Did anyone get the "favorites keys" working along with the "zoom"?  I'm running Ubuntu 9.10 and everything works except for favorites and zoom, nor the F-Lock key. 

~$ uname -a
Linux Ubuntu-9-10 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

To zoom the "visual effects" must be set to "Normal" in "System -> Preferences -> Appearance".

Then you need to bound in System->Preferences -> Keyboard Shortcuts 
"Zoom In" to "XF86Forward" (which are the 2 keys under the space key) and 
"Zoom out" to "XF86Back".

The zoom kind of joystick does not work for me.

---

### Post by xhaos on 2010-02-23
Hello, since 2 weeks ago my keyboard started sending random key presses to my system. Usually it reduces or increases the volume rapidly. Once in console I managed to catch one of the signals and it was " [26~ ". Does anyone else have this problem? Changing USB port seems to correct it for some time, but usually PC is unusable cause I constantly have to fix sound volume.

Thank you for your time.

---

### Post by burbilog on 2010-05-21
I made a quick fix for this problem.  It's based on kbd's showkey that DOES show scancodes. It looks into  configuration table and stuffs required keysyms into X via Xtst package.  Ugly, buggy and setuid (to read console under X you have to be setuid),  but it works (at least for me) and requires only installation of the  deb package. Lucid package is here:

 ```
sudo add-apt-repository ppa:rm-isaev/rawkeybind
sudo apt-get update
sudo apt-get install rawkeybind
```Then restart X.

Source code: [http://www.isaev.ru/rawkeybind/](http://www.isaev.ru/rawkeybind/)
 By default zoom up and down are bound to up arrow and down arrow but  you can change it in /etc/rawkeybind.conf

---

### Post by OlympicSoftworks on 2011-05-13
I just purchased the Microsoft "Natural Ergonomic Keyboard 4000"

I'm using 10.04 and pretty much everything works right out of the box.  Gotta love not needing drivers!

The only things that didn't are the variable zoom in the middle of the keyboard, the Back/Forward keys at the bottom of the keyboard, and the 5 special keys at the top.

Not too bad considering every other specially labeled key was detected and 'just works'.

I set the bottom Back/Forward keys as Jens Getreu said and they now work.  I may reset them to actually do the firefox backward/forward functions they were designed for but for now I'm good.

However those 5 special keys are not detected and there is no selection for the '4000' series in the keyboard selection utility...so I used the  xev  command from the terminal and here are the keycodes.

**Key 1**
KeyPress event, serial 36, synthetic NO, window 0x8a00001,
    root 0x1ad, subw 0x8a00002, time 1478036053, (31,45), root:(1213,101),
    state 0x10, keycode 192 (keysym 0x1008ff45, XF86Launch5), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x8a00001,
    root 0x1ad, subw 0x8a00002, time 1478036213, (31,45), root:(1213,101),
    state 0x10, keycode 192 (keysym 0x1008ff45, XF86Launch5), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

**Key 2**
KeyPress event, serial 36, synthetic NO, window 0x8a00001,
    root 0x1ad, subw 0x8a00002, time 1478031142, (31,45), root:(1213,101),
    state 0x10, keycode 193 (keysym 0x1008ff65, XF86MenuKB), same_screen YES,
    XKeysymToKeycode returns keycode: 147
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x8a00001,
    root 0x1ad, subw 0x8a00002, time 1478031302, (31,45), root:(1213,101),
    state 0x10, keycode 193 (keysym 0x1008ff65, XF86MenuKB), same_screen YES,
    XKeysymToKeycode returns keycode: 147
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

**Key 3**
KeyPress event, serial 36, synthetic NO, window 0x8a00001,
    root 0x1ad, subw 0x8a00002, time 1478631962, (46,53), root:(1228,109),
    state 0x10, keycode 194 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x8a00001,
    root 0x1ad, subw 0x8a00002, time 1478632129, (46,53), root:(1228,109),
    state 0x10, keycode 194 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

**Key 4**
KeyPress event, serial 36, synthetic NO, window 0x8a00001,
    root 0x1ad, subw 0x8a00002, time 1478632601, (46,53), root:(1228,109),
    state 0x10, keycode 195 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x8a00001,
    root 0x1ad, subw 0x8a00002, time 1478632761, (46,53), root:(1228,109),
    state 0x10, keycode 195 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

**Key 5**
KeyPress event, serial 36, synthetic NO, window 0x8a00001,
    root 0x1ad, subw 0x8a00002, time 1478633241, (46,53), root:(1228,109),
    state 0x10, keycode 196 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x8a00001,
    root 0x1ad, subw 0x8a00002, time 1478633385, (46,53), root:(1228,109),
    state 0x10, keycode 196 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

So, the first two buttons already have an X-Server label associated with them and can therefore be slotted into a standard UI function...but the other 3 have no label yet.  Not sure if there is a .conf file somewhere that has keycodes associated with a label...likely there is.  Hope this helps someone.

---

### Post by denisk on 2011-06-13
Greetings to the brave knights of Microsoft ergo 4000! I would like to share my experience as well. I'm using Kubuntu Natty (11.04), and here's what I've got.
In my case all the keys except (you guess it!) zoom key are working. Of course, some of them (like calculator or favorites) are not assigned to anything from the beginning, but this is simply fixable by System Setting -> Shortcuts and gestures.
With zoom the situation is much more tough though. It seems that the *system* itself is not aware of it. I ran 
```
xev
```
and tested the keys - and I got responses for all of them, ***except*** zoom. I hope this will be fixed in subsequent kernels - this zoom key must be freaking cool for scrolling. Anyway, Ergo 4000 is the best keyboard in the world, and is the only thing I like from Microsoft :D

UPDATE - this [bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/313514") seem to cause the problem. According to it, keys with codes that are greater then 255 are ignored. From using
```
 sudo showkey -k

```
as someone suggested, it is visible that key codes for UP and DOWN for zoom are 418 and 419 - so no chance for them to work out of the box...

---

### Post by abid_naqvi83 on 2011-10-13
The usual labyrinthine search through the internet and a little trial and error has led to solve the Zoom Slider problem and I am now able to scroll using it. The solution is as follows:

Summary:

(i) Discover the keycodes generated by moving the Zoom Slider.
(ii) Map the keycodes (greater than 255) to vacant values below 255.
(iii) Bind the mapped keycodes to mouse scroll events.

Details:

Install evtest ```
sudo apt-get install evtest
```

Discover the device node for the Ergonomic Keyboard ```
ls -l /dev/input/by-id
```

The output will contain a symlink to the event number corresponding to the Ergonomic keyboard. For example when I run it:

```
total 0
lrwxrwxrwx 1 root root  9 2011-09-29 15:01 usb-Logitech_USB_Receiver-event-kbd -> ../event5
lrwxrwxrwx 1 root root  9 2011-09-29 15:01 usb-Logitech_USB_Receiver-event-mouse -> ../event6
lrwxrwxrwx 1 root root  9 2011-09-29 15:01 usb-Logitech_USB_Receiver-mouse -> ../mouse1
lrwxrwxrwx 1 root root 10 2011-09-29 15:01 usb-Microsoft_Natural®_Ergonomic_Keyboard_4000-event-kbd -> ../event10

```

So on my computer the Ergonomic keyboard resides at /dev/input/event10. The number X in /dev/input/eventX will be different for each setup.

Now use evtest to find the keycodes for the Zoom Slider ```
sudo evtest /dev/input/event10
```

This will generate a list of all the keycodes for the device and some of the common mappings. You can look at the output to find vacant keycodes. A small sample of the output:

```

    Event code 192 (F22)
    Event code 193 (F23)
    Event code 194 (F24)
    Event code 206 (Close)
    Event code 207 (Play)
    Event code 208 (Fast Forward)

```

I chose to use keycodes 193 and 194 for remapping since I don't have F23 and F24 (function keys) on my system.

While evtest is running pressing any key on the keyboard will display information about said key. Pushing the Zoom Slider up displays ```
Event: time 1318494418.113457, type 4 (Misc), code 4 (ScanCode), value c022d
Event: time 1318494418.113487, type 1 (Key), code 193 (F23), value 1

```

Pushing the Zoom Slider down displays ```
Event: time 1318494466.969461, type 4 (Misc), code 4 (ScanCode), value c022e
Event: time 1318494466.969478, type 1 (Key), code 194 (F24), value 1

```

Press Ctrl+C to exit evtest. We are interested in the values that start with c, so Zoom Up has value c022d and Zoom Down has value c022e. Note that the keycodes are 418 and 419, that is greater than 255, which is why they cannot be accessed directly (practically this means the Zoom Slider is not detected by 'xev').


The next step is to map these keycodes to the vacant ones (193 and 194) below 255. This involves the implementation of a udev rule. The first step is create a keymap file.

I created an empty file named 'microsoft-ergonomic-keyboard' in the folder /lib/udev/keymaps and entered the following lines in to it ```
0xC022D 0xC1 # Zoom Up which we wish to be Scroll up
0xC022E 0xC2 # Zoom Down which we wish to be Scroll down

```

0xC1 and 0xC2 are the vacant codes 193 and 194 in hexadecimal. We need to implement a udev rule that implements the remapping laid out in the file we have just created. The udev rule needs to be applied to the Ergonomic Keyboard only so we must do a little research.

```
ls -l /sys/class/input/event10
``` gives us ```
lrwxrwxrwx 1 root root 0 2011-10-13 03:42 /sys/class/input/event10 -> ../../devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/input/input10/event10
```

We have used the /sys/class folder to find the location of the Ergonomic Keyboard (which we know to reside at /dev/input/event10) in the sysfs tree. This location will be used to get udev attributes we will need to construct the necessary udev rule.

```
udevadm info -a -p /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/input/input10/event10
```

The output displays the udev attributes of the device and all its parents. Part of the output follows:

```

...
  looking at device '/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1/input/input10/event10':
    KERNEL=="event10"
    SUBSYSTEM=="input"
    DRIVER==""
...
 looking at parent device '/devices/pci0000:00/0000:00:1d.3/usb5/5-1':
    KERNELS=="5-1"
    ...
    ATTRS{manufacturer}=="Microsoft"
...
```

Our task is to use a combination of the attributes of the device itself and no more than one of its parents to uniquely identify the device (the Ergonomic keyboard) regardless of where (which USB port) and when it is connected. I chose to use SUBSYSTEM=="input" and ATTRS{manufacturer}=="Microsoft".

Open /lib/udev/rules.d/95-keymap.rules for editing and add the udev rule ```
SUBSYSTEM=="input", ATTRS{manufacturer}=="Microsoft", RUN+="keymap $name microsoft-ergonomic-keyboard"
``` in the external USB Keyboards section. The pertinent section of 95-keymap.rules after the addition has been made is ```
#
# The following are external USB keyboards
#

LABEL="keyboard_usbcheck"

ENV{ID_VENDOR}=="Logitech*", ATTRS{name}=="Logitech USB Multimedia Keyboard", RUN+="keymap $name logitech-wave"
ENV{ID_VENDOR}=="Logitech*", ATTRS{name}=="Logitech USB Receiver", RUN+="keymap $name logitech-wave-cordless"
# Logitech Cordless Wave Pro looks slightly weird; some hotkeys are coming through the mouse interface
ENV{ID_VENDOR_ID}=="046d", ENV{ID_MODEL_ID}=="c529", ATTRS{name}=="Logitech USB Receiver", RUN+="keymap $name logitech-wave-pro-cordless"

ENV{ID_VENDOR}=="Lite-On_Technology_Corp*", ATTRS{name}=="Lite-On Technology Corp. ThinkPad USB Keyboard with TrackPoint", RUN+="keymap $name lenovo-thinkpad-usb-keyboard-trackpoint"
ENV{ID_VENDOR_ID}=="04b3", ENV{ID_MODEL_ID}=="301[89]", RUN+="keymap $name ibm-thinkpad-usb-keyboard-trackpoint"

SUBSYSTEM=="input", ATTRS{manufacturer}=="Microsoft", RUN+="keymap $name microsoft-ergonomic-keyboard"

GOTO="keyboard_end"

```

The idea is to identify the correct device using the attributes and then implement the keymaps we placed in /lib/udev/keymaps/microsoft-ergonomic-keyboard. The new udev rule is usually implemented when the computer is restarted but we can force its immediate implementation using ```
sudo /lib/udev/keymap input/event10 /lib/udev/keymaps/microsoft-ergonomic-keyboard
```

Running evtest now and pushing the Zoom Slider will now display the new keycodes: 193 and 194. This indicates that the remapping was successful.

A discrepancy arises at this juncture. evtest and xev disagree as to the keycodes associated with the Zoom Slider. We will need the keycodes as detected by xev. So run 'xev' and find the keycodes for the Zoom Slider. They come out to be 201 for Zoom Up and 202 for Zoom Down.

Now install xbindkeys and xdotool ```
sudo apt-get install xbindkeys xdotool
``` xbindkeys allows one to associate bash commands with keysyms and keycodes. xdotool allows one to inject keyboard and mouse events in to the X Server. 

Create an empty ~/.xbindkeysrc file (or append to an already existing one) and add the following lines to it

```
"xdotool click 4"   # Scroll Up
c:201

"xdotool click 5"   # Scroll Down
c:202

```

The command 'xdotool click 4' implements a Scroll Up mouse event. The c:201 line tells xbindkeys to execute "xdotool click 4" when the key with keycode 201 is pressed. By virtue of the remapping we did with the udev rule pushing the Zoom Slider up generates this keycode.

Simply execute ```
xbindkeys
``` to implement these bindings. '/usr/bin/xbindkeys' will need to be placed in System >> Preferences >> Startup Applications to ensure that it is called on boot up.

At this point the Zoom Slider should be working as a Scroll control. Enjoy.

---

### Post by abid_naqvi83 on 2011-10-13
References:

The various websites (incomplete list) I used to gather information for the solution presented above (with my profound thanks and appreciation) are:


[http://askubuntu.com/questions/33038/how-to-get-microsoft-natural-ergonomic-keyboard-4000s-zoom-slider-and-other-but](http://askubuntu.com/questions/33038/how-to-get-microsoft-natural-ergonomic-keyboard-4000s-zoom-slider-and-other-but)  *(udev rule for remapping)*

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/313514](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/313514)   *(udev rule for remapping)*

[https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes](https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes)    *(udev rules)*

[http://www.reactivated.net/writing_udev_rules.html#sysfsmatch](http://www.reactivated.net/writing_udev_rules.html#sysfsmatch)    *(udev rules)*

[http://www.signal11.us/oss/udev/](http://www.signal11.us/oss/udev/)   *(sysfs tutorial)*

[http://joomla.unlikelysource.com/index.php/misc-tutorials-category/34-howto-udevinfo](http://joomla.unlikelysource.com/index.php/misc-tutorials-category/34-howto-udevinfo)    *(udevadm tutorial)*

[http://www.semicomplete.com/projects/xdotool/xdotool.xhtml#mouse_commands](http://www.semicomplete.com/projects/xdotool/xdotool.xhtml#mouse_commands)   *(xdotool commands)*

---

### Post by zerwas on 2011-11-16
abid_naqvi83, great research and guide on how to enable the slider. Unfortunately don't own this keyboard anymore so i can't test it, but i will update the first post and point to your posting.

---

### Post by denisk on 2011-11-16
abid_naqvi83, thanks a lot for this tutorial! It worked flawlessly for me, finally after almost half a year of using Ergo 4000 i can use Zoom key! You rock! :guitar:

---

### Post by trulan on 2011-11-22
Hi all,

I'm currently running Ubuntu Natty.  I recently picked up one of these keyboards at our local discount office supply store, and  I was delighted to find that almost everything, including the back and forward keys, just worked.  Additionally, the Web/Home, Search, Mail, My Favorites, and Calculator keys were easily re-mapped using 'Keyboard Shortcuts."  That left the five shortcut keys and the zoom joystick.  Being a tinkerer at heart, I had to get _everything_ working, including actually making the zoom joystick zoom in and out.  Here's how I did it:  (many thanks to abid_naqvi83 for the tips and tools to figure it out!)

1. Install a few packages:
```
sud apt-get install xbindkeys xautomation
```(I use xte, from the xautomation package, rather than xdotool.  I couldn't get zooming to work with xdotool.)

2. Tell udev to load a corrected keymap:
```
sudo gedit /lib/udev/rules.d/95-keymap.rules
```I added this, right below LABEL="keyboard_usbcheck"
```
# Microsoft 4000 Natural Keyboard
ENV{ID_VENDOR}=="Microsof*", ATTRS{name}=="*", RUN+="keymap $name microsoft-ergonomic-keyboard"
```Save it and close gedit.

Then, create the keymap file:
```
sudo gedit /lib/udev/keymaps/microsoft-ergonomic-keyboard
```Paste this into gedit:
```
0xC022D 0xC1 # Zoom In
0xC022E 0xC2 # Zoom Out

```Save it and close gedit.

3. Set up your custom keybindings:
```
gedit ~/.xbindkeysrc
```Paste this into gedit:
```

## This keybindings file is intended for a Microsoft Natural Ergonomic Keyboard 4000.
## Using it requires installing xbindkeys and xautomation. Enabling the zoom joystick
## also requires some udev keymap magic.

# Zoom in and out
"xte 'keydown Control_L' 'mouseclick 4' 'keyup Control_L'"
c:201 + Release
"xte 'keydown Control_L' 'mouseclick 5' 'keyup Control_L'"
c:202 + Release

## Shortcut keys 1-5 (edit these to perform your desired action)

# Shortcut no. 1
"nautilus"
c:192

# Shortcut no. 2
"firefox"
c:193

# Shortcut no. 3
"libreoffice"
c:194

# Shortcut no. 4
"gedit"
c:195

#Shortcut no. 5
"totem"
c:196
```Save it and close gedit.

4. Add xbindkeys to your autostart programs list, then reboot.
(Or, load the keymap as described by abid_naqvi83 in his guide.  Then run xbindkeys.)

For more info and troubleshooting tips, please see the full guide here:
[http://ubuntuforums.org/showpost.php?p=11336640&postcount=178](http://ubuntuforums.org/showpost.php?p=11336640&postcount=178)

---

### Post by jj3jj3 on 2011-12-05
Hi - I realize this is entirely the wrong board to raise this question on. However I am desperate, and this is a relevant and active thread.

I'm trying to switch the function of the zoom rocker to scroll on a Mac. I know there are easily implemented solutions for PC and it seems like you've got it down for Linux, but no one has come up with a fix for Mac users. (I also realize that may have a lot to do with the inherent drawbacks of our platform.)

So far I've gotten no further than locating the keyboardlayout bundle in my Library and popping open the "US Intl - Microsoft" layout as a likely target for modification. But I have a feeling I'm a ways off and might not even be on the right track at all.

Would so much appreciate if anyone's able to point me in the right direction! Thanks.

---

### Post by michalsmid on 2011-12-11
Thanks to abid_naqvi83 as well! After few years having this keyboard I finally managed to make the zoom slider work.

But anyway, going through the /lib/udev/rules.d/95-keymap.rules file, I realized there was already line
ENV{ID_VENDOR}=="Microsoft", ENV{ID_MODEL_ID}=="00db", RUN+="keymap $name 0xc022d zoomin 0xc022e zoomout"
which I don't really understand, but I guess that 'someone' has already made another attempt to work this keys by default. Unfortunately I don't know how:)

m.

---

### Post by trulan on 2011-12-20
Indeed, it seems that in Oneiric there was some attempt made at supporting this keyboard.  When I upgraded my system a few weeks ago, that of course made the zoom slider quit working.  I changed that line to read
```
ENV{ID_VENDOR}=="Microsoft", ENV{ID_MODEL_ID}=="00db", RUN+="keymap $name microsoft-ergonomic-keyboard"
```
and now it works again.

---

### Post by exXplode on 2012-05-12
Thanks everyone for your help! I found this thread and it helped me to get the keyboard (esp. the zoom slider) to work on **Ubuntu 12.04** in almost no time.

I put **condensed instructions** on how to do it on my blog: [[COLOR="DarkRed"]Microsoft Natural Ergonomic Keyboard 4000 with Mac OS X and Linux[/COLOR]]("http://goo.gl/zWOd2").

---

### Post by Ratzian on 2012-05-18
Hey guys! Thanks a lot for helping get the keys working :) Big up to abid_naqvi83

---

### Post by rahoolpaliwal1989 on 2013-01-31
Hey, thanks a lot!
Works like a charm! :)

---

### Post by bigmak on 2013-02-14
This worked great for me on my first MS Ergo 4000 keyboard.  But unfortunately, I got a second MS Ergo 4000 keyboard which I ended up keeping that made the scroll UP stop working.  Both keyboards looks identical, but the model number is slightly different.  I think my problem is with the last step on instructions:

"xdotool click 4"   # Scroll Up
c:201
"xdotool click 5"   # Scroll Down
c:202

When I ran xev, I saw that scroll down was keycode 202.  However, when I tried the scroll up key, it couldn't tell me the keycode:

FocusOut event, serial 41, synthetic NO, window 0x5600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 41, synthetic NO, window 0x5600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 41, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

I then went to Keyboard Shortcuts (on 12.10) and tried to associate the scroll up or down key to some random action.  When I did scroll down, it correctly detected that I pressed 0xca (202 in hex).  But when I tried to scroll up, the value was "TouchpadOff".  Does anyone have any clever ideas??  Thanks!

---

### Post by abid_naqvi83 on 2013-02-14
The Scroll Up key when pushed generates a keycode. It seems that the keycode is being "caught" by some other application and being converted in to a "TouchpadOff" signal before it can reach xev or xbindkeys.

I would suggest tracking down the application that is catching the scroll up keycode and fixing it there.

---

### Post by bigmak on 2013-02-14
> **abid_naqvi83 said:**
> The Scroll Up key when pushed generates a keycode. It seems that the keycode is being "caught" by some other application and being converted in to a "TouchpadOff" signal before it can reach xev or xbindkeys.

I would suggest tracking down the application that is catching the scroll up keycode and fixing it there.

Thanks for the response!  I think you're right, but I can't seem to figure out what is intercepting that key.  When I have .xbindkeysrc setup, I notice that the working scroll down key also gave the same unhelpful output for the xenv command as the scroll up key.  However, when I rename .xbindkeysrc to something else (so to severe the binding), I can see scroll down giving me a nice KeyPress event detail:

KeyPress event, serial 41, synthetic NO, window 0x4600001,
    root 0x25b, subw 0x0, time 3513819, (393,387), root:(443,441),
    state 0x10, keycode 202 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

I just can't seem to see this at all for scroll up.  Is there any way for me to find out what keycode 201 is bind to and which app is creating that binding?

---

### Post by bigmak on 2013-02-14
I can definitely see my scroll up key is bound to TouchpadOff.  I just have no idea how that happened and how to make it stop!

---

### Post by bigmak on 2013-02-14
I do not understand this, but now, everything suddenly works again!!  I did multiple things, so I am not sure which one did it.  I uninstalled synclient, which might actually be the key.  In any event, both scroll up and down now works perfectly!  Thanks, everyone!

---

### Post by Boccarossa on 2013-06-12
Hi.

Im using Ubuntu 12.04 and after following exXplode's guide at [http://blog.philippklaus.de/2012/05/microsoft-natural-ergonomic-keyboard-4000-with-mac-os-x-and-linux/](http://blog.philippklaus.de/2012/05/microsoft-natural-ergonomic-keyboard-4000-with-mac-os-x-and-linux/) I finally managed to get some success, thou not completly.

Im still having problems with the "zoom-up"-button... In System Settings>Keyboard>Shortcuts the "zoom-up"-button is reffered to as "TouchpadOff" (althou this may not be a problem?) and the "zoom-down"-button is reffered to as 0xca (as it should, I asume?).

After every systemstartup I have to manually go into Settings>Keyboard>Shortcuts, bind the "zoom-up"-button to any random shortcut and then remove the bind. After this has been done everything works as it should. If I do not do this, the system seem to interpret the "zoom-up"-button as some kind of invalid mouse-code of sorts. Ubuntu shows me a picture of what I asume is a mouse with an X-mark over it. One of the commenters on exXplode's guide seem to have had the same problem.

I guess one (easy?) solution to my problem could be to run some kind of bash-script on system startup that automatically goes into System Settings>Keyboard>Shortcuts, binds the "zoom-up"-button to something and then unbinds it.

Could this be done, and if so, could someone please write a script for me?

It will take a while for me until I learn bashscripting because I got other things I need to learn right now.

Also, why doesnt Ubuntu fix this bug/problem? Is it really that hard? I hear lots of people praising this keyboard (mostly geeks/programmers). Could it possibly have anything to do with the company behind the keyboard (M$) being the leading competitor to Ubuntu :)? Conspiracy theories are great.

---

