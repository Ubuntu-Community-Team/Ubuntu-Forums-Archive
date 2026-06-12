---
title: "Virtualbox, Vmware player, etc? Should I try it? Which is good? ?????"
date: 2008-07-12
forum: The Cafe
---

### Post by Redrazor39 on 2008-07-12
Is it a good idea to have a virtual machine running in my Ubuntu install to try out other OSs (which I will want to do) if I only have 27GB free in ubuntu? Which VM program is better? Is it in the repos? Is it easy to use?

Help? I need some sort of explanation of this stuff. Thanks.

---

### Post by FuturePilot on 2008-07-12
I'll give a +1 to Virtualbox. I love Virtualbox. :)
But in your situation you might find yourself running short on disk space because the virtual disks generally are several GB in size.

---

### Post by Redrazor39 on 2008-07-12
I was thinking of having one virtual machine and just switch the OS there when I want.

I was thinking of putting BSD there and checking that out. I really need to read up on BSD much more, though.

---

### Post by Canis familiaris on 2008-07-12
+1 for Virtualbox

---

### Post by Lord Xeb on 2008-07-12
go with virtualbox. It is your best bet and you get more bang than any of the other free vms out there. Also, if you do get it, download it from the site directly so you can have USB

---

### Post by Redrazor39 on 2008-07-12
wait, so I can put it on a USB and install an OS on that?

I've been wanting to have an entire computer OS with all my files, settings, programs, etc. on a USB stick that I could plug into any computer and run.

---

### Post by Canis familiaris on 2008-07-12
> **Redrazor39 said:**
> wait, so I can put it on a USB and install an OS on that?

I've been wanting to have an entire computer OS with all my files, settings, programs, etc. on a USB stick that I could plug into any computer and run.

Yes you can but only in closed source versions of Virtualbox NOT on Virtualbox OSE available in the repos.

---

### Post by VitaLiNux on 2008-07-12
> **FuturePilot said:**
> I'll give a +1 to Virtualbox. I love Virtualbox. :)
But in your situation you might find yourself running short on disk space because the virtual disks generally are several GB in size.

+1
xVM Virtualbox just worx!:biggrin:

---

### Post by Redrazor39 on 2008-07-12
So download it from the site then? Is there a guide as to how to put it on USB stick (i don't have a USB stick available that's big enough right now, but still. If I get one.

---

### Post by kk0sse54 on 2008-07-12
Virtualbox is great but I also really like Vmware because it's so easy to set up all you do is download the vm image from vmware.com and start it in vmware player and bam you got a fully functional virtual machine right off the bat. Very simple and very nice. The downside to it is that you only have so many vm images to pick from hence where virtualbox gets the edge.

---

### Post by VitaLiNux on 2008-07-12
[Download xVM VirtualBox now!]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") 
Try it out! It's awesome!

---

### Post by dizee on 2008-07-12
virtualbox is very easy to use, just make sure you install the kernel module for it as well.

i don't know about running it from a usb stick though (if that's what you mean), there is a version of damn small linux that runs from a usb stick in windows using a program called qemu though so it's technically possible.

---

### Post by Masoris on 2008-07-12
Maybe Virtualbox is the best in free software. But Virtualbox is still unstable and has some critical bugs.

You can see bug list in here:
[http://www.virtualbox.org/report/1](http://www.virtualbox.org/report/1)

If you use 64bit Ubuntu, I cannot recommend Virtualbox because of this bug:
[http://www.virtualbox.org/ticket/1046](http://www.virtualbox.org/ticket/1046)

---

### Post by Lord Xeb on 2008-07-12
No, the vm will allow you to access USB things like external harddrives and stuff from inside the VM.

But yes, you could save your VM on a USB flash and then go and put it another machine that has Virtualbox after you set it up to use it :D

And you can also install Linux a USB and carry it everywhere >_> Like I did for school to piss my PC apps teacher off <_< Worked like a charm when it booted faster from the USB than when it was booting into windows :D

---

### Post by Redrazor39 on 2008-07-12
What's the kernel module?

I just downloaded the package from sun (.deb) for Ubuntu hardy i386

Do I just use GDebi to install?

---

### Post by dizee on 2008-07-12
well for the open source version that's in the repos you need to install the kernel module (virtualbox-ose-modules-2.6.24.19-generic for an up-to-date hardy install) and reboot to use vbox, not sure if the closed source one is the same.

---

### Post by cardinals_fan on 2008-07-12
I hate Virtualbox.  It's caused me endless problems.  VMware is awesome :)

---

### Post by Tichondrius on 2008-10-28
> **cardinals_fan said:**
> I hate Virtualbox.  It's caused me endless problems.  VMware is awesome :)

Virtualbox works great for me. It's MUCH better than VMPlayer, which is the only free software you can get from VMWare, because VirtualBox lets you create and install new VMs, but VMPlayer can only run existing VMs, so you have to download these VM images, and try to customize them. Compare that to creating your own VM using your favorite distro/OS which you can do using VirtualBox as well as VMWare workstation/server but that is not free.

I have my PC on 24/7 for months, and VirtualBox is always running my Linux VM as a server (file,mail,web,etc). It NEVER crashed or had any other problem. Running months with no issues, serving pages, files, mail. Not sure if VMWare can do that.

---

### Post by pp. on 2008-10-28
> **Tichondrius said:**
> ... VMPlayer, which is the only free software you can get from VMWare

I seem to remember that VMWare Server was free as well.

---

### Post by mips on 2008-10-28
> **pp. said:**
> I seem to remember that VMWare Server was free as well.

You are 100% correct.

---

### Post by kernelhaxor on 2008-10-28
> **Anurag_panda said:**
> Yes you can but only in closed source versions of Virtualbox NOT on Virtualbox OSE available in the repos.

Nope you dont need the closed source version .. you can create the virtual disk on a USB drive and use that for the virtual machines ..

Closed sourced version is needed only if you need USB support inside the guest OS

---

### Post by forrestcupp on 2008-10-28
I've personally had more luck with vmware than I have had with virtualbox.  Virtualbox is easier to set up, but vmware has better support for their virtual hardware.  But then again, that was for installing Windows in my vm, and you don't seem to be interested in using it for Windows.

---

