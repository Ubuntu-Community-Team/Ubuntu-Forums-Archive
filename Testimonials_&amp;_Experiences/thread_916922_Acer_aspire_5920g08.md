---
title: "Acer aspire 5920g/08"
date: 2008-09-11
forum: Testimonials &amp; Experiences
---

### Post by rvm4000 on 2008-09-11
I installed kubuntu 8.04 (amd64) in this laptop. It seems there are many 5920G models, this one includes an ATI card (HD 3470) instead of a Nvidia card.

[img]http://img91.imageshack.us/img91/8334/5920gxf8.jpg[/img]

This is my experience with this computer, things that work out of the box, things that don't work and how to make them work.

Features:

Intel Core 2 Duo T5750 @ 2.0 GHz
RAM: 4 Gb DDR2
TFT 15,4" WXGA CristalBright
Graphic card ATI HD 3470
Hard disk: 250 GB 
WebCam Acer Cristaleye
Wi-Fi, Firewire, 4 x USB, HDMI
DVD Double Layer recorder
S.O Windows Vista Home Premium

Partitions:
The hard disk already had 4 partitions. On Windows Vista only 2 were visible: drive C: (where Windows is installed) and drive D: (empty). Both partitions are about 100 GB size each. 

Note: drive C: is actually the 2nd partition on the disc, and drive D: the 3rd. The other two are hidden.

So the obvious thing was to delete D: and install linux using that space. Maybe it could be done by the kubuntu installer but I preferred to use gparted. So I downloaded the live CD iso and burn it to a CD. Then I rebooted the computer, entered in the BIOS (F2) and set it to boot from the CD drive in first place.

In gparted I've just simply deleted the D: partition (labeled "DATA") and created in its place an extented partition. I didn't create any partition in it.

After the reboot I let Windows to boot, just to be sure I didn't make anything wrong. Everything went fine, now Windows only shows one drive (C:).

Installation:
Now I booted with the kubuntu live CD. I took a quick look, I saw that Wi-Fi and sound worked. There was a little problem with the screen, it seems it was using 1024x768 (4:3) as resolution. As the monitor's ratio is 16:9 the image appeared a little bit stretched.

Finally I clicked on the Install icon. Just one thing: by default the installer wanted to split the Window partition, that wasn't what I wanted, so I selected the option to use the maximum available free space. 

The installation went fine, so there's nothing more to comment about it.

After the first boot it offered me to install the proprietary driver for the graphic card. After the installation (and another reboot) at last the screen was at 1280x800.

Sound: it was necessary to enable and move up the "surround" control in kmix. Initially the PCM didn't work, but after installing all the updates (which included a new kernel), it worked too.

Wi-Fi: works out of the box.

Graphic card: I found two problems: there was no Xvideo support, and most important, the computer crashes if you log out of the KDE. I updated the ATI driver using envy, and that fixed those two problems. Anyway the graphic card is still giving problems, I have crashes from time to time...

S-Video output: works. It can be enabled in the ATI Catalyst Control Center. Anyway it was enabled by default (in clone mode).

HDMI output: not tested.

Webcam: works out of the box (tested with "cheese", I tried first with "camorama" but it didn't worked, it complained that it couldn't connect to /dev/video0)

Microphone: not tested yet

Firewire: not tested

Touchpad: works, but it's not properly configured. Tapping is very sensitive and the wheel button doesn't work. It can be fixed following [this guide](http://www.ossramblings.com/disable_touchpad_in_ubuntu_with_acer_5920).

Suspend: works (tested only once)
Hibernate: works (tested only once)

Booting:
There was a problem with grub. It created a menu with several options to launch kubuntu (ok), but there were also 3 options to boot Windows. The first two were named the same "Windows Vista/Longhorn". I chose the first one, but that didn't boot Windows, but what it seemed a recovery application from Acer. I rebooted and tried the 2nd one, that actually booted Windows Vista. And the 3rd option was named "Microsoft Windows XP Embedded" (I didn't test it).

So I realized that grub had added options for the 2 hidden partitions. As I thought those weren't intented to be used by the user, I made some changes in /boot/grub/menu.lst.

At the end of the file there were these lines:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title           Microsoft Windows XP Embedded
root            (hd0,3)
savedefault
makeactive
chainloader     +1

```

I renamed the 2nd entry (which is the one that boots Vista) to "Windows Vista" and the first one to "Windows Vista/Recovery" and move the 2nd one up so "Windows Vista" appeared first. Later, (after checking that these changes worked) I decided to comment out the other entries so they cannot be selected by mistake. So finally my changes looked this way:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title          Windows Vista/Recovery
#root           (hd0,0)
#savedefault
#makeactive
#chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
#title          Microsoft Windows XP Embedded
#root           (hd0,3)
#savedefault
#makeactive
#chainloader    +1

```

---

### Post by giovi81 on 2008-11-16
rvm4000,

first of all thank you for reporting your experience.
I have an ACER aspire 5920g-302G16Mi laptop running the OS Kubuntu 8.04 Hardy Heron.

After enabling sorround in the "Output" menu of KMix sound works but only the right speaker is working!
Could you please suggest me on how to get both speakers working ?
And what do you mean by "initially the PCM didn't work, but after installing all thHi e updates (which included a new kernel).." in your post ? what is the PCM and which updates did you perform ?

I would appreciate if you can help me.

Regards, Giovanni

---

### Post by giovi81 on 2008-11-17
I resolved the problem! both the speakers works fine now.
I just went on -> K Menu -> System Settings -> Sound System.
Then I selected in the Hardware Tab, line
"Select the audio device": Advanced Linux Sound Architecture.
I recall that I previously enabled the "Sorround control" in KMix (green light over the control) and moved it upwards.

Laptop : ACER aspire 5920G-302G16Mi
O.S. : Kubuntu 8.04 Hardy Heron

Regards, Giovanni

---

### Post by rvm4000 on 2008-11-17
> **giovi81 said:**
> And what do you mean by "initially the PCM didn't work, but after installing all thHi e updates (which included a new kernel).." in your post ? what is the PCM

Just after the installation, the PCM control in kmix didn't work (moving it up and down didn't change the volume).

> **giovi81 said:**
> 
and which updates did you perform ?

You know, there's an icon in the KDE taskbar which notifies about packages updates. I just accepted to install all updates, that downloaded and installed a lot of packages, including a new kernel. After the upgrade the PCM control worked.

---

### Post by rvm4000 on 2008-11-17
BTW, now I have another problem: does anyone know how to make the microphone to work?

This laptop includes a microphone near the webcam. I enabled all mic controls in kmix, and I tried to record audio with krec, but there's no way, no sound it's recorded :(

---

### Post by ikamrafossav on 2008-12-03
just install a mixer

```
sudo apt-get install gnome-alsamixer
```

and unmute the capture volumes

---

### Post by rvm4000 on 2009-01-18
Finally I could make the built-in microphones to work, with these setting in kmix:

[img]http://a.imagehost.org/0570/kmix1_r.png[/img]
[img]http://a.imagehost.org/0059/kmix2_r.png[/img]

Now I can record sound with the gnome sound recorder (using the "capture" input). Sound recording doesn't work with krecorder (maybe because it seems it uses arts and I have it disabled).

Now, the remaining problem is that the recorded audio has a lot of noise, is that normal?

---

### Post by solwic on 2009-01-18
> **rvm4000 said:**
> Sound recording doesn't work with krecorder (maybe because it seems it uses arts and I have it disabled).

Now, the remaining problem is that the recorded audio has a lot of noise, is that normal?

I had a lot of problems with KDE4 as far as Kubuntu is concerned.  I don't know a lot about the problems you're having, but if it were my PC, I'd dual-boot good old Ubuntu with Gnome and see if it's the hardware, or just KDE issues.  

Either way, good luck!

---

### Post by wolfen69 on 2009-01-18
> **jrock612 said:**
> but if it were my PC, I'd dual-boot good old Ubuntu with Gnome and see if it's the hardware, or just KDE issues.  



exactly. i still don't trust kde4. especially kubuntu's version. i'm sure it will be good down the road, but right now i'll pass. gnome works too darn good to give up.

---

### Post by solwic on 2009-01-18
> **wolfen69 said:**
> exactly. i still don't trust kde4. especially kubuntu's version. i'm sure it will be good down the road, but right now i'll pass. gnome works too darn good to give up.

+1.  It wasn't long ago that I loved KDE and Kubuntu.  Still do, in a way.  But I kept running into problem after problem in Kubuntu that I just didn't have in Ubuntu, and eventually switched back.  

I'll stick to Gnome until KDE gets their **** together.  :)

EDIT:  As for the OP...I'd bet that even 

```
sudo apt-get install ubuntu-desktop
``` 

would work well enough to see if it's KDE issues.

---

### Post by rvm4000 on 2009-01-19
I'm using KDE 3.5.10 (kubuntu 8.04), not KDE 4.

I don't have gnome installed, but I'm using the gnome sound recorder, and I have even the gnome mixer installed.

The only problem I have now is some noise in the audio recordings. Do you have a clear sound or could this noise be normal for the built-in microphones?

---

