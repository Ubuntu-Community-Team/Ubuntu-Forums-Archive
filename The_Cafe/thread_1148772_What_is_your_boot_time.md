---
title: "What is your boot time?"
date: 2009-05-04
forum: The Cafe
---

### Post by the8thstar on 2009-05-04
Hello all,

I am interested to know what your boot times are.

I use two PCs right now.

PC 1 is a desktop P4 2.4GHz with 768Mb or RAM and an ATI Radeon 9500 graphic card with 128Mb onboard. 

PC 2 is the laptop in the sig.

On PC 1, Windows XP boots in 1m30s and Ubuntu Jaunty boots in 55 seconds.

On PC 2, Jaunty boots in 55 seconds and Windows 7 boots in 55s too.


What about you?

---

### Post by Kareeser on 2009-05-04
the8thstar, are you using ext4, or ext3?

My production computer, Intel 630 3 GHz, 2 GB RAM, 8800GT = 21 seconds from GRUB menu*

[size=1]* I assume that's how we're counting, since that's how it's counted in that amazing "11 second boot" youtube video...[/size]

---

### Post by Hyper Tails on 2009-05-04
I use ext4 on my primary pc

---

### Post by skymera on 2009-05-04
Bootchart says 11 seconds.

Intel Core2Quad Q6600
4GB XMS2 800MHz
ATi 4870 OC 512MB
WD Raptor 10,000 RPM 16MB

---

### Post by Eviltechie on 2009-05-04
60 seconds from power button to desktop. That includes a bunch of bios screens and the 10 seconds for grub to auto chose linux.

---

### Post by sports fan Matt on 2009-05-04
22, 23 seconds from grub using auto login and ext3...

---

### Post by dragos240 on 2009-05-04
45 seconds on my netbook. On intrepid.

---

### Post by Muffinabus on 2009-05-04
About 20 seconds after GRUB, EXT4.

---

### Post by mamamia88 on 2009-05-04
31 seconds

---

### Post by Eisenwinter on 2009-05-04
About 15 - 20 seconds, because of udev and network detection.

---

### Post by OutOfReach on 2009-05-04
17 seconds on the machine in my sig, according to bootchart.
The SATA drivers take a little long to load, that's why the time isn't lower.

---

### Post by garythegoth on 2009-05-04
About 20 seconds from a cold boot to login screen. But that is with using Startup Manager to turn the GRUB countdown off...

---

### Post by meho_r on 2009-05-04
20 seconds from GRUB to login screen. Another 20 from login screen to usable desktop (with Gnome-Do, Parcellite, Guake, Dropbox in start-up apps, plus Tomboy, Tracker and Desklet which load last). Configuration: AMD Athlon 3800+ 2,4 GHz, 3GB of RAM.

---

### Post by Stupendoussteve on 2009-05-04
In beta my laptop was 18 seconds, now it's about 20.

---

### Post by richg on 2009-05-04
Around twenty to thirty minutes. Usually closer to twenty minutes. Depends on when I get out of bed and wander into the kitchen for coffee.

Rich

---

### Post by rudenko_ruslan on 2009-05-04
21 seconds.

---

### Post by the8thstar on 2009-05-05
> **the8thstar said:**
> Hello all,

I am interested to know what your boot times are.

I use two PCs right now.

PC 1 is a desktop P4 2.4GHz with 768Mb or RAM and an ATI Radeon 9500 graphic card with 128Mb onboard. 

PC 2 is the laptop in the sig.

On PC 1, Windows XP boots in 1m30s and Ubuntu Jaunty boots in 55 seconds.

On PC 2, Jaunty boots in 55 seconds and Windows 7 boots in 55s too.


What about you?

Both PCs are on EXT4.

---

### Post by b@sh_n3rd on 2009-05-05
According to bootchart, my PC boots in 31.11s
/boot;/home and / are XFS
DELL OptiPlex GXa (11yrs :D)
Intel Pentium II 266MHz (Klamath)
386MiB RAM
15.0GB HDD
I think it would have been faster if 3D Acceleration was enabled. This allowed the PC to boot fast on XP too but i'm not sure whether Jaunty or XP was faster...maybe Jaunty as winblows gets stuffed once too often...:D

---

### Post by LightB on 2009-05-05
Oh about 15 nanoseconds and you can't prove it doesn't.

---

### Post by kerry_s on 2009-05-05
about 5 secs, i use suspend, turning the computer on just wakes it up. :lolflag:

---

### Post by b@sh_n3rd on 2009-05-05
> **kerry_s said:**
> about 5 secs, i use suspend, turning the computer on just wakes it up. :lolflag:

Good 1! :lolflag:

---

### Post by Orlsend on 2009-05-05
I am on a EeePc bloated with services, its 40 seconds to boot all the way!

---

### Post by lisati on 2009-05-05
I have Ubuntu on three machines: from grub to login screen bootchart reckons 21 on the fastest, 22 on the next, and 26 on the slowest.

---

### Post by mihai.ile on 2009-05-05
My boot time is either 16 seconds or 50 seconds.
It depends on a random unknown issue in Jaunty which I can't find a solution for, as I explain here:
[http://ubuntuforums.org/showthread.php?t=1148898](http://ubuntuforums.org/showthread.php?t=1148898)

---

### Post by calrogman on 2009-05-05
17 seconds according to bootchart, ext4 /, ext3 /home.

---

### Post by oomingmak on 2009-05-05
7 seconds. 

That's a complete cold boot, up to the full Gnome desktop.

[http://ubuntuforums.org/showthread.php?p=7136475#post7136475](http://ubuntuforums.org/showthread.php?p=7136475#post7136475)

---

### Post by the8thstar on 2009-05-05
A word to remind users out there: boot chart does not include the time from cold boot, only the time when boot chart starts til the desktop is loaded.

In other words, boot chart doesn't start when you power on your computer. I'm interested in the REAL time.

---

### Post by oomingmak on 2009-05-05
Well obviously bootchart does not include HW POST time, but it was still a full boot rather than a resume from suspend (as someone joked earlier).

POST takes an additional 11 seconds on my main PC. Therefore 18 seconds total.

---

### Post by sydbat on 2009-05-05
> **LightB said:**
> Oh about 15 nanoseconds and you can't prove it doesn't.Gotcha beat....0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000002 sub-nanoseconds...and that can't be proven either

---

