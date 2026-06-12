---
title: "Virtualbox crashes ubuntu 12.04"
date: 2012-04-07
forum: Virtualisation
---

### Post by kallek on 2012-04-07
Hi,
I got a new laptop (HP Pavilion g4, with Intel HD Graphics 3000), and installed 12.04 (beta version). I copied the VirtualBox VDI file from my old computer and attached to VirtualBox in the new computer.
XP starts nicely in VirtualBox, but after a 1/2 minute or so ubuntu crashes completely. I'm not completely sure, but it looks like it's the graphics card restarting (and not a compltete restart of the laptop).
I followed the advice on [http://www.ehow.com/info_12201744_virtualbox-ubuntu-crashes.html]("http://www.ehow.com/info_12201744_virtualbox-ubuntu-crashes.html"), but it doesn't help. I have some additional graphics issues (besides the directly VirtualBox related), for example, when I hoover the mouse pointer over the icons in "system settings" the pointer flickers.

Virtualbox version: 4.1.12_Ubuntu r77245

Does anyone have experience with this type of issues?

Thanks,
Kallek

---

### Post by 2F4U on 2012-04-07
If it is a problem with the graphics card or the desktop environment, it may be worth looking into the file .xsession-errors in your home folder. To decide whether it is a crash of the desktop environment it would be good to know if your are just logged out or if the laptop reboots. A typical crash of the desktop just logs you out and you are back at the login screen.

---

### Post by kallek on 2012-04-07
Thanks for the quick reply.
Looking at xsession-errors I see that unity-2D is being used, but in my VirtualBox settings is have checked Enable 3D Acceleration.

---

### Post by kallek on 2012-04-07
I tried unchecking "Enable 3D Acceleration" and instead checked "Enable 2D Acceleration", but it still crashed. 
And I unchecked "Enable 2D Acceleration" also (both unchecked), and it still crashed.

Further, it is definitively **not** just the graphics restarting, the entire computer restarts. The laptop rebooots.

---

### Post by yhjhoo on 2012-05-10
I have the same issue with a fresh installed ubuntu12.04. It works fine in previous version11.10

---

### Post by kallek on 2012-05-11
I created a new virtual machine and tried to make a fresh installation of xp, but again, the computer crashed/restarted after a minute or so. I.e. it appears that the problem is not caused by some odd quirk in the original virtual machine.

---

### Post by kallek on 2012-05-12
I created a new virtual machine with xp on my old laptop, and it worked fine. It also runs 64-bit Ubuntu 12.04, but an upgraded version and not a fresh install. Also, on the new laptop (HP pavilion g4) neither suspend nor xorg works properly (pointer flickers, external monitor doesn't work). But, on the old computer all these things work perfectly (as well as VirtualBox). I don't know but, these problems may be related to the VirtualBox problem.

---

### Post by Dedoimedo on 2012-05-13
Crash - what do you mean by that exactly?
Does the X session go down? The machine reboots? Something else?
Did you try enabling kdump and collecting a memory core?
Dedoimedo

---

### Post by kallek on 2012-05-13
The computer reboots.
I will enable kdump and return with the resluts.
Thanks

---

### Post by kallek on 2012-05-13
Excuse my ignorance, but how do I enable kdump and collect a memory core. I've been looking around on the Ubuntu documentation/wiki pages but has been unable to find guiding information. Do you know where I can find instructions?

---

### Post by Dedoimedo on 2012-05-13
Here's a nice short read for you:
[http://www.dedoimedo.com/computers/crash-book.html](http://www.dedoimedo.com/computers/crash-book.html)

Dedoimedo

---

### Post by atarixle on 2012-05-14
> **yhjhoo said:**
> I have the same issue with a fresh installed ubuntu12.04. It works fine in previous version11.10

VirtualBox in 12.04 makes my computer restart, whenever I want to run a 64 Bit guest.

32-Bit Machines run well in VirtualBox unter 12.04

---

### Post by Antionio on 2012-05-15
> **atarixle said:**
> VirtualBox in 12.04 makes my computer restart, whenever I want to run a 64 Bit guest.

32-Bit Machines run well in VirtualBox unter 12.04

I have this exact same problem. Running ubuntu 12.04 32bit and trying to run a 64bit Windows 7 on virtualbox crashes. This worked fine on 11.10.

Intel EliteBook 8560p, Ubuntu 12.04 32bit

---

### Post by asadmalik on 2012-05-15
i have the same problem with virtualbox.
I installed Ubuntu 12.04 as guest (Host is also 12.04) and now whenever i try to install the update, the guest OS gets aborted abruptly

---

### Post by PrintStar on 2012-05-23
Just wanted to jump in as well.  Same problem here.  Upgraded to 12.04 and installed latest VirtualBox on x86 Ubuntu, and i get a full host system reboot while Windows 7 64 bit VM is starting.

Any solutions?

---

### Post by gtuxljb on 2012-05-24
Has anyone tried an alternative DE, and see if the behavior is similar?  

At this point it sounds like a kernel issue.  But I am also wondering if it is a Unity problem.

---

### Post by PrintStar on 2012-05-24
Well I'm running Unity2D, but I haven't tried any other DE's with regards to this issue.  If a Unity2D problem can cause a complete system crash-and-reboot, this problem is much, much bigger than what's being reported here.

Also, it looks like this problem exists in Debian sid right now:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=655202](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=655202)

---

### Post by gtuxljb on 2012-05-24
> **PrintStar said:**
> Well I'm running Unity2D, but I haven't tried any other DE's with regards to this issue.  If a Unity2D problem can cause a complete system crash-and-reboot, this problem is much, much bigger than what's being reported here.

Also, it looks like this problem exists in Debian sid right now:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=655202](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=655202)

I haven't had a chance to test this yet, but if it's Debian as well then I have to believe it's a conflict with the Virtualbox kernel extension and the latest stable kernel.  I would report this bug to the VirtualBox developers.

---

### Post by skriv on 2012-06-30
Same problem with Ubuntu 12.04 32-bit and Windows 7 64-bit, with Gnome Shell DE.

UPDATE: Just found the solution here. Worked for me at least. [https://www.virtualbox.org/ticket/10528#comment:6](https://www.virtualbox.org/ticket/10528#comment:6)

---

### Post by kallek on 2012-07-24
I followed the instructions skriv and edited grub.
It appears to have solved my virtualbox issues.
The relevant line in grub now looks like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nmi_watchdog=0 i915.modeset=0"
I forgot to add "nowatchdog", but it works anyway.
"i915.modeset=0" is not relevant for virtualbox. It was because of another issue I had with a black screen.
On the virtualbox site, it appears that this should be a fix only for a 32-bit linux host running a 64-bit windows guest, but in my case, the fix still works, and I have a 64-bit ubuntu host, and a 32-bit windows xp guest.

---

### Post by Crackouch on 2012-08-03
I have a similar problem...
 
I installed VirtualBox on Ubuntu 12.04 with no problems. But when I install virtual OSs (my goal is to create a virtual Windows network with 2 XPs and 2003[DC and Exchange]), my screen "snaps" and removes all icons and menus from my display. Not even the virtualbox home screen shows up which would enable me to switch between guest OSs.

I can't access my guest server 2003 because I can't get to the v-box Cntrl-Alt-Del function, essential to start configuring my virtual machines. The keyboard and mouse work on a host level, but without access to host functions, my vbox project is on hold.
 
It seems my Ubuntu host freezes and I am with no choice but to init 0 and start over.

Any thoughts? Thanks, Crackouch.

---

