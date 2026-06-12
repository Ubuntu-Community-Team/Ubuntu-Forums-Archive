---
title: "Lightdm update - no desktop"
date: 2014-09-04
forum: Ubuntu Development Version
---

### Post by Elfy on 2014-09-04
Update to 1.11.8-0ubuntu1 leaves me with no desktop.

Just a warning :)

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1365336](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1365336)

---

### Post by ibjsb4 on 2014-09-04
It must be a coincidence.

Did an update yesterday and the same thing happen to me.

It boots to tty

Startx takes me to a black screen, no cursor.

This is 12.04.5, 3.2 kernel.

---

### Post by Cavsfan on 2014-09-04
> **ibjsb4 said:**
> It must be a coincidence.

Did an update yesterday and the same thing happen to me.

It boots to tty

Startx takes me to a black screen, no cursor.

This is 12.04.5, 3.2 kernel.

This section of the forum is for developmental version Utopic Unicorn 14.10 only. The current kernel is 3.16.0-12-generic

It got me too I just tried to boot into Utopic with systemd and could only boots to tty.
I got a bunch of updates and then rebooted and the results were the same no GUI login.

Waah! :cry: Back in the same boat as we were the other day.

This is where patience comes in handy. ;) Oh what fun! :p

---

### Post by fooman on 2014-09-04
got me last night as well.  nvidia card if that means anything.  booted only to TTY,  if i typed "startx" at that point...it would go to the desktop which still had my wallpaper,  but with no unity, panels or anything,  not even a cursor!

i wanted to try the lalest daily anyway (which i had just put onto a usb drive),  so i did a fresh install and *did not* install any nvidia drivers.  after updating everything just now,  all seems to be working just fine WITHOUT the nvidia drivers.  i think i will hold off on those for now  :D

edit: just wanted to add that when i was stuck at the TTY,  i did try purging the nvidia drivers.  which did get me to a working desktop....but at a really crappy screen resolution which i could not change.

---

### Post by jvcastle on 2014-09-04
Exact same problem - updated from 12.04 to 14.04.  Black screem at boot, but booting to command line (boot param "text") works ok.  From command line forced "sudo service lightdm start" - gave me a perfect login screen, but after logging in the flash screen just stayed, never got to desktop.  "dmesg" at that point included:
init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
init: gdm main process (936) killed by TERM signal
init: plymouth-stop pre-start process (1182) terminated with status 1

I am guessing something didn't get installed or put in the correct place ("No such file or directory") but after scouring the forums and posting elsewhere, there were hundreds of reads, but nobody seemed to want to touch it...

Note the past tense.  Since I had the command line, attached an external drive, copied everything I didn't want to lose  (like my Crossover and Thunderbird config files and junk on my Desktop (the rest like photos, music etc linked to the Win8 partition) - and did an install from scratch.  PIA, but spent less time doing that than the 2 days I tried to fix the upgrade.  System is Dell XPS, Intel 4000 graphics connected to laptop and external display - NVIDIA 540 (hdmi out) not connected to anything.  Dual boot system with Win8

---

### Post by cariboo on 2014-09-04
I ran into the same problem running Ubuntu, the only way I can get a semi working desktop is to start in recovery mode, then log in on the command line and then run startx. This brings me to a desktop where the only thing that works is the right-click context menu. I created a new folder, open it and navigate to /usr/bin, where I start an xterm. Once the terminal is running I issue the following commands:

```
dconf reset -f /org/compiz
```

and 

```
setsid unity
```

to get a low resolution desktop. :)

---

### Post by P-I H on 2014-09-05
I followed the instruction in [https://bugs.launchpad.net/ubuntu/+s...m/+bug/1365336]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1365336") and created the file [COLOR=#333333][FONT=monospace]/etc/udev/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]rules.d/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]71-nvidia.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]rules
[/FONT][/COLOR]with the content
[COLOR=#333333][FONT=monospace]SUBSYSTEM=="drm", KERNEL=[/FONT][/COLOR][COLOR=#333333][FONT=monospace]="card[[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0-9]*", TAG+="master-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]of-seat"
[/FONT][/COLOR]and rebooted.
That worked.

---

### Post by zika on 2014-09-05
Is that bug confined to Nvidia or not?

---

### Post by Elfy on 2014-09-05
well ... from one of the comments in the bug report, it would appear not

> 3. systemd-logind ships a default set of udev rules that tags any
framebuffer devices (/dev/fb*) as "master-of-seat", which is OK for all
KMS-compliant video drivers like Intel, Nouveau (open-source driver for
NVIDIA graphics devices) and Radeon (open-source driver for AMD graphics
devices).

4. However, NVIDIA or AMD proprietary drivers don't expose kernel
framebuffer devices, so they need their own udev rule to tag another
kernel device they expose as "master-of-seat" (in @elfy example, we tag
kernel device /dev/dri/card0):

---

### Post by zika on 2014-09-05
Just on the spot. As I thought (proprietary drivers). Thank You. That helped me prepare several weekend activities related to U+1 (on someone_else's machine(s))... ;) I was not reading bug report carefully enough. After reading it thoroughly I've learned much even beyond this bug. Nice read. Thank You again.

---

### Post by Cavsfan on 2014-09-05
Thanks Elfy for all the work you did with that bug! 
I only had a little time to work with Ubuntu yesterday. Today it booted to tty I got the updates and rebooted and all is well once again. I noticed nvidia-331 and other nvidia modules were in the updates.

I just glanced at the bug but could tell you did a lot of work.
Glad it's working again now. :guitar:

I seen there was a kernel held back I would suspect 3.16.0-13-generic. I'm going to get that in dist-upgrade and then go square up my Utopic Mate install.

---

### Post by Elfy on 2014-09-05
yea - I'm not convinced that all is over with that issue, booting (at least) xubuntu and ubuntu images and you'll get CanGraphical=no currently from loginctl show-seat seat0

I've just this minute triggered a rebuild for my images - will see if it's any better afterwards

---

### Post by ventrical on 2014-09-05
After updating an existing Utopic system (i386) in finally knocked out the nVidia proprietary drivers for:

```

04:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 GS] (rev a1)
ventrical@ventrical-Asus-Overclock:~$ 

```

which was fixed by purging nvidia  and installing nouveau-firmware.

---

### Post by Elfy on 2014-09-05
possibly the lightdm issue, especially if lightdm is 1.11.8-0 and nvidia isn't upgraded yet [http://ubuntuforums.org/showthread.php?t=2242791](http://ubuntuforums.org/showthread.php?t=2242791)

---

### Post by ventrical on 2014-09-05
You don't have the thread marked, ya know , ubuntu.xubuntu ..etc.. but I assume you refer <all variants> but looks like same problem. Please merge then.

Thanks..

---

### Post by Elfy on 2014-09-05
yesterday I wasn't sure - and I don't think anyone would expect me to be the OP of an issue that's not Xubuntu at least :D

I'll not merge until you're sure it IS the same issue though.

---

### Post by ventrical on 2014-09-05
Purged nVida proprietary drivers on <lubuntu install> and installed nouveau-firmware and got desktop working again.

```

ventrical@ventrical-Asus-Overclock:~$ uname -a
Linux ventrical-Asus-Overclock 3.16.0-13-generic #19-Ubuntu SMP Thu Sep 4 23:02:21 UTC 2014 i686 i686 i686 GNU/Linux
ventrical@ventrical-Asus-Overclock:~$ 


```

---

### Post by ventrical on 2014-09-05
+1

Same issue :)

thnxs

---

### Post by Cavsfan on 2014-09-05
Ironically Utopic Mate did not boot to tty. Went straight to GUI.
I have these nvidia drivers installed and they work well - no problems whatsoever.
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                331.89-0ubuntu3                          amd64        NVIDIA binary driver - version 331.89
ii  nvidia-331-uvm                            331.89-0ubuntu3                          amd64        NVIDIA Unified Memory kernel module
ii  nvidia-libopencl1-331                     331.89-0ubuntu3                          amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                     331.89-0ubuntu3                          amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                              0.6.6                                    amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                           331.20-0ubuntu8                          amd64        Tool for configuring the NVIDIA graphics driver
```

nvidia-331 gets the DKMS checksum error but nvidia-331-uvm does not.

---

### Post by Elfy on 2014-09-05
> **ventrical said:**
> +1

Same issue :)

thnxs

merged then

---

### Post by fooman on 2014-09-05
working here as well with todays nvidia driver updates.  thanks to all for getting this fixed so quickly! \\:D/

---

### Post by grahammechanical on 2014-09-05
I knew that I had made the right decision by taking a vow of abstinence from using Nvidia proprietary drivers.

---

### Post by Elfy on 2014-09-06
> **grahammechanical said:**
> I knew that I had made the right decision by taking a vow of abstinence from using Nvidia proprietary drivers.
I made the same decision 3 cycles ago - since then nouveau had gotten worse for me - had to move back.

However, livesession uses whatever it uses to boot, that'll not be nvidia - CanGraphical=no 

Would be good to see other people trying the livesession - [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1366206](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1366206)

I've tried Xubuntu, Ubuntu and Lubuntu.

---

### Post by jerrylamos on 2014-09-06
I've only got intel and ATI hardware - workaround to get at least something working is to add
nomodeset
to the boot command line that starts with
linux
This gets me up with crippled resolution, 1024x768, so I can do at least something.

I don't know how to try this when booting the .iso

---

### Post by Elfy on 2014-09-06
> **Elfy said:**
> ...
Would be good to see other people trying the livesession - [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1366206](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1366206)

I've tried Xubuntu, Ubuntu and Lubuntu.

Appears to be a vbox issue (for me) clean install to hardware doesn't show the same thing.

---

