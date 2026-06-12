---
title: "Back to windows  :("
date: 2008-05-12
forum: Testimonials &amp; Experiences
---

### Post by Guzman on 2008-05-12
Hi,

I tried and tried.... this time Ubuntu freezes a few seconds after the username/password menu.
Previously I installed 7.10 with virtualbox, but as I been told, Ubuntu could not "see" my hardware and I decided to install 8.04 with wubi.

The install process went fine, but after the dualboot menu two things happen... some times he canot reach the passord screen turning all black and freezes there.... other times he passes the username/password screen but frezzes a few moments after finishing the boot process. i only have time to move the mouse and open firefox or whatever I try to do.

Dunno. Ubuntu is getting user friendly I supose, but in order to resolve many problems users must allways go to the so called grub menu or to console and type strange commndas and that is not very easy for newbies like me... back to windows I guess :(

My specs:

Board: 775Dual-880Pro 1.00
Bus Clock: 200 megahertz
BIOS: American Megatrends Inc. P1.30 12/21/2005
2048 Megabytes Installed Memory

NVIDIA GeForce 6600 LE [Display adapter]
Video Graphics Accelerator [Display adapter]
LGE L1915S [Monitor] (19,1"vis, Março 2005)
nVidia WDM A/V Crossbar
nVidia WDM Video Capture (universal)
Realtek AC'97 Audio for VIA (R) Audio Controller

ST3200822AS [Hard drive] (200,05 GB)
HL-DT-ST DVD-ROM GDR8164B [CD-ROM drive]

3,00 gigahertz Intel Pentium D
16 kilobyte primary memory cache
1024 kilobyte secondary memory cache

---

### Post by Separ on 2008-05-12
Is there any way to get the contents of your /etc/X11/xorg.conf file? (such as going into the recovery mode and using it to copy the file to a USB drive?)
```
fdisk -l
```
To list the partition tables of your devices, it should show the USB drive in there.
```
sudo mount -t vfat /dev/sd** /media/USB
```
Replace ** with the USB drive letter + number
```
sudo cp /etc/X11/xorg.conf /media/USB
```
To copy the file.
```
sudo umount /dev/sd**
```
Which unmounts the USB drive so you can remove it.

I suspect it could be using the "nv" driver instead of the "nvidia" one. This seems to be a common problem.

---

### Post by KOTAPAKA on 2008-05-12
Why give up linux? Ubuntu is not the only distro available you know? there are a lot of distros that are better at recognising hardware - simply find the one that is for you.

---

### Post by Joeb454 on 2008-05-12
I hear Linux Mint (though Ubuntu based) is pretty good at finding hardware, and is a lot easier "out of the box"

---

### Post by SlappyPappy on 2008-05-12
I'll second that idea about Mint. Have heard some of the same things about recognition. 

                   Perhaps you should get Minty fresh.    :)

---

### Post by Dougie187 on 2008-05-12
Also, I have heard a couple other people complaining about installtion with wubi, you might try a clean install on a dedicated partition.

---

### Post by scorp123 on 2008-05-12
> **Guzman said:**
>  Ubuntu is getting user friendly I supose, but in order to resolve many problems users must allways go to the so called grub menu or to console and type strange commndas and that is not very easy for newbies like me... back to windows I guess :(

Linux is NOT Windows
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

If you expected to find a "Windows-like" OS when you switched to Linux then you switched for the wrong reasons ;)

---

### Post by tech9 on 2008-05-12
try PCLinuxOS - it's really good at detecting Hardware.

quite a nice OS all together.

---

### Post by NightwishFan on 2008-05-12
Linux Mint is a cool name for a distro I think. :)

As for going back to Windows I agree. What makes windows such a stable platform to spring from. It is buggy and slow on hardware made for it. Ubuntu on hardware made for it would perform much better, but Ubuntu tends to work on almost everything.

---

### Post by barney385 on 2008-05-12
Yes, you should definately stay with XP/Vista. The pre-installed software that reports to Homeland security against your wishes is one of my personal favorites.
 
I don't understand why anyone would go to the trouble of investing a few moments of time to learn a more secure Operating System.
 
Carry On...

---

### Post by tech9 on 2008-05-12
> **barney385 said:**
> Yes, you should definately stay with XP/Vista. The pre-installed software that reports to Homeland security against your wishes is one of my personal favorites.
 
I don't understand why anyone would go to the trouble of investing a few moments of time to learn a more secure Operating System.
 
Carry On...

how's the weather up there in AK?

---

### Post by Cavalryman on 2008-05-13
> **tech9 said:**
> how's the weather up there in AK?

In Anchorage, it's beautiful. 55 degrees with bright, clear skies and light breeze.

---

### Post by Guzman on 2008-05-13
Well, the thing is that I need to have it running in order to learn.

All I have recieved is a valid suggestion to try other distros and a lot of ******** after that.

I think that having it running after install it is not asking to much right? I will not buy other PC to run linux that's for sure and that kind of help it is not helping at all.

Anyway Linux mint shown me the same results. After booting to desktop it freezes. No mouse and no keybord. Im running it from a ISO burned into a DVD.

Any proactive sugestion? Or you simple dont know?

---

### Post by NightwishFan on 2008-05-13
I lose patience. Linux works fine I sense human error. Perhaps you can try the "alternate install cd".

---

### Post by gameryoshi600 on 2008-05-13
well whatever floats your boat.

---

### Post by Guzman on 2008-05-14
Well... Im sure Linux is worth to try, and I will keep trying couse I`ve been well suceed with other open source applications with non usual interfaces like my prefered 3d app Blender.

Sorry to say that your help sucks in an arrogant kind of way.


Cheers

---

### Post by Sef on 2008-05-14
> All I have recieved is a valid suggestion to try other distros

Sometimes only one type of distro will work on certain hardware.  I had a computer where only a slackware derivative worked.

---

### Post by karellen on 2008-05-14
> **Sef said:**
> Sometimes only one type of distro will work on certain hardware.  I had a computer where only a slackware derivative worked.

and, off topic, don't you consider this to be a problem? a desing inconsistency...

---

### Post by ukripper on 2008-05-14
> **Joeb454 said:**
> I hear Linux Mint (though Ubuntu based) is pretty good at finding hardware, and is a lot easier "out of the box"

yeh +1 on that, as one of my mate who is new to linux is finding Mint easy.

---

### Post by webcoded612 on 2008-05-14
> **NightwishFan said:**
> I lose patience. Linux works fine I sense human error. Perhaps you can try the "alternate install cd".

Actually Linux is quite broken, especially when it comes to the installer.  I've had the same video card for over a year (ATI Radeon X1300) and even three updates in Ubuntu still can't seem to make my card work without manual configuration.

In this case I imagine the original poster is having hardware trouble (unlike myself; my hardware works wonderfully on XP/Vista, which makes it a Linux problem).  But I'm with the original poster with not buying new hardware.  If you're going to buy new hardware just to get an OS to work, go buy Vista.  It's much more user friendly (and much more familiar to former Windows users).  

I have nothing helpful to contribute I guess, other than that I'm tired of people getting frustrated and blaming the end user.  Linux should work better out of the box.  Period.  You can't get upset or "impatient" helping people who know nothing about Linux and are trying to make something work out of the box that doesn't.  

My two cents anyway.  I'm downloading Linux Mint right now to see if it picks up my hardware properly.  

Good luck, and I hope you stick with Linux!

EDIT:  I should actually say that Ubuntu is quite broken as far as the installer goes, not Linux.  If every distro had this many problems we'd all still be using Windows :P

---

### Post by maiadestinee on 2008-05-15
Yes,.....

I could not understand why anyone would go to the trouble of investing a few moments of time to learn a more secure Operating System.

It is very bad...

---

### Post by Geekkit on 2008-05-15
> **Guzman said:**
> Well... Im sure Linux is worth to try, and I will keep trying couse I`ve been well suceed with other open source applications with non usual interfaces like my prefered 3d app Blender.

Sorry to say that your help sucks in an arrogant kind of way.


Cheers

I'd have to agree with you. Most of the comments here are arrogant and unhelpful. This is one of the things that's going to kill this distro. Sorry to hear that it didn't work out for you. Maybe try again on a different system or try the next version of Ubuntu dude. :(

---

### Post by karellen on 2008-05-15
> **Geekkit said:**
> I'd have to agree with you. Most of the comments here are arrogant and unhelpful. This is one of the things that's going to kill this distro. Sorry to hear that it didn't work out for you. Maybe try again on a different system or try the next version of Ubuntu dude. :(

agree with you. silly "elitism", "I have no problem so you must be a moron" are the kind of things that drive people away (unless they are fanatics)

---

### Post by hyper_ch on 2008-05-15
> **webcoded612 said:**
> I have nothing helpful to contribute I guess, other than that I'm tired of people getting frustrated and blaming the end user.  Linux should work better out of the box.  Period.
You are free to contribute ;)

---

