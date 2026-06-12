---
title: "virtualbox error"
date: 2008-03-03
forum: Virtualisation
---

### Post by jrockpunk1 on 2008-03-03
k so i want a VM of winXP on my ubuntu OS. ive installed virtualbox from the repositories. ive set up the machine, but when i try to run it it comes up with this error:

```


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

now i fixed this before by doing this:

```

sudo chmod 666 /dev/vboxdrv

```

and it worked, but said it couldnt find a bootable device. now, when i turned the comp on again, it comes up with the first error, and sudo chmod 666 /dev/vboxdrv doesnt work.
also, ive added myself to the vbox users list and reinstalled everything. ive also looked for a file called '/dev/vboxdrv', and it isnt there. ive reinstalled everything many times. is there somewhere where i can get that file? or is there another way to fix this?

any help much appreciated,

jrockpunk1

---

### Post by FuturePilot on 2008-03-03
After you added yourself to the vboxuser group did you log out and back in? That's necessary to update the groups that you belong to.

---

### Post by jrockpunk1 on 2008-03-03
yup. i think the problem lies with the file /dev/vboxdrv, as it isnt there, and it says thats the file that should be.

---

### Post by FuturePilot on 2008-03-03
Try completely removing Virtualbox, then reinstall it.

---

### Post by jrockpunk1 on 2008-03-04
i have. like i said i think the problems with that file, and reinstalling it isnt fixing it.

---

### Post by natirips on 2008-06-19
I've got the same problem (Ubuntu 8.04, kernel 2.6.24-19-generic), and when I try to install WinXP it said the following:```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```. I did install ALL virtualbox-ose-modules* packages except the -server ones. I tried ```
sudo /etc/init.d/vboxdrv setup
```, but it said:```
natirips@natirips-laptop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for natirips: 
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
natirips@natirips-laptop:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
natirips@natirips-laptop:~$
```Any ideas appriciated.

P.S.: Knoppix run fine before, gives the same error as with the OS-less WinXP now.
P.P.S.: Kernel (or Ubuntu version) was NOT upgraded/changed since then, I only installed almost all availible kernel versions after I got the error.
Edit: I am using 64-bit Ubuntu.

---

### Post by NetworkGuy on 2008-06-19
The problem is that you are running the latest kernel but the Virtual Box kernel module has not been updated for that kernel yet.   

You can either wait for the kernel module to be updated via your update manager or boot the kernel that matches your Virtual box kernel module.   

The OSE version does not give you the option of recompiling the kernel module on the fly with the "setup" parameter.  You must wait for the matching kernel module to be released.

---

### Post by natirips on 2008-06-19
I see... Anyway, thanks for the information.

---

### Post by Victormd on 2008-06-19
I would remove the OSE version and install the PUEL version that can be found [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI").
One of the main reasons, being that you'll get USB support. Second reason, you'll be able to quickly recomplie the kernel module following on-screen instructions directly from virtualbox during startup (if there is a need to).

---

### Post by natirips on 2008-06-19
> **Victormd said:**
> I would remove the OSE version and install the PUEL version that can be found [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI").
One of the main reasons, being that you'll get USB support. Second reason, you'll be able to quickly recomplie the kernel module following on-screen instructions directly from virtualbox during startup (if there is a need to).

That's you (no hard feelings), it's just not that important to me. I just wanted to do a fresh installation of WinXP (without any additional software or drivers) and connect it to Internet and see how much time will it take for the first malware to auto-install if it were a virtual version under Ubuntu.

Just for the record, it took about 15 mins on a non-virtual one two meters away from the computer I'm writing this text from, it was something OneStep Search something, lol.

---

### Post by Victormd on 2008-06-19
Given your reasons, I totally agree with you! :)

---

### Post by antez on 2008-06-21
I have the same problem and I think it hapened after an update 2 days ago  

I use ubuntu 7.10


it says: 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

 I have to fix this in one day because I am a graff designer and in monday I have to to give the work I have made, so for
a problem in f*cking virtualbox I may lose my job in 2 days!!!



please I need help more than ever......

---

### Post by natirips on 2008-06-21
Boot using an older kernel (select it from grub), or update (I'm using Ubuntu 8.04, yesterday it got fixed). Or do as Victormd said and install the PUEL version [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI") ). After you have installed that version, simly reuse the same virtual hard drive file you used for the old one.

---

### Post by antez on 2008-06-21
I will do this thnx if it be fixed i will owe you this manths paycheck!!!!!!!!!

---

### Post by antez on 2008-06-21
I tried to install but the install failed.....

---

### Post by antez on 2008-06-21
xexe I hadn't  unistalled the old virtualbox but now I fixed it

man I LOVE YOU

you just saved my life

thnx thnx thnx thnx thnx thnx thnx thnx thnx thnx thnx thnx thnx thnx thnx

---

### Post by natirips on 2008-06-21
no problem

---

