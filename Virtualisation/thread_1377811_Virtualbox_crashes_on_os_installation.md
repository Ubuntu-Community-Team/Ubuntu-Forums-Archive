---
title: "Virtualbox crashes on os installation"
date: 2010-01-10
forum: Virtualisation
---

### Post by xude on 2010-01-10
I have Virtualbox working fine on my Dell laptop, but when I try to install it on my son's desktop, running Ubuntu 9.10, I am successful in getting Vurtualbox working but as soon as I try to install Windows XP it crashes the entire system. I have reinstalled the entire system from scratch but get the same result each time.

What do I need to do to identify the root of the problem and then to fix it?

---

### Post by jocampo on 2010-01-10
Xude, which version of VBox are you installing? did you get the same problems if you try to install a different guest, like Linux?

---

### Post by xude on 2010-01-11
I have tried both 3.1.2 and the ose version listed in the system update manager, but get the same problem each time.

---

### Post by SecretCode on 2010-01-11
How much disk space is free on the problem machine? (Unlike to be the issue, but worth a check.)

The log might show something ... can you open virtualbox, select the failed XP installation, click Machine > Log... and save VBox.log to a file and attach it here?

---

### Post by snowpine on 2010-01-11
Did you try installing Ubuntu in the virtual machine, to see whether the error is specific to Windows? Are you using an official, legal Windows install CD? ;)

---

### Post by xude on 2010-01-11
The HDD is 320Gb and I have nothing other than Ubuntu on the system, having done a fresh install. The version of Windows XP is 2002 which includes service pack 2. It is an original copy - bought stand-alone after I got annoyed grappling with the OEM version that came with an (old) machine. I am currently running Ubuntu on a Shuttle. I also tried installing Ubuntu 9.10 on the same VirtualBox and had the same issue. As soon as it looks for the CD on install the entire system hangs.

On going into VirtualBox after the new Windows os install has failed I get the following message in details:

 p, li { white-space: pre-wrap; }  Start tag expected, '<' not found.
 Location: '/home/christopher/.VirtualBox/Machines/CiTunes/CiTunes.xml', line 1 (0), column 1.
 /home/vbox/vbox-3.1.2/src/VBox/Main/MachineImpl.cpp[5821] (nsresult Machine::loadSettings(bool)).
    Result Code: 
  [FONT= ]NS_ERROR_FAILURE (0x80004005)[/FONT]
   Component: 
  VirtualBox
   Interface: 
  IVirtualBox {2158464a-f706-414b-a8c4-fb589dfc6b62}
 
...but I do not get access to a log file.

I have found a VBox.log file under /*computer*/.VirtualBox/Machines/*guest*/Logs however, which is attached.

Help is appreciated.

---

### Post by fouadatmeh on 2010-01-11
Hello,
a couple more things to check.. make sure you have enough RAM + swap space to run both the host machine (ubuntu) and the guest machine (xp) together
Also, try to take an image from your cd and use the image inside vbox instead of the real cd..

Hope that helps

---

### Post by SecretCode on 2010-01-11
It's not reading from the CD correctly. That log shows
> 00:00:05.495 Guest Log: BIOS: CDROM boot failure code : 0003
00:00:05.496 Guest Log: BIOS: Boot from CD-ROM failed
00:00:05.496 Guest Log: BIOS: Boot from Hard Disk 0 failed
00:00:05.496 Guest Log: BIOS: Boot from Floppy 0 failed
00:00:05.498 Guest Log: Could not read from the boot medium! System halted.

I like fouadatmeh's idea of booting from an image of the CD not the physical CD. But first, do you have "Passthrough" enabled for the CD drive in the vm?

---

### Post by xude on 2010-01-11
Passthrough is not enabled. Each time I set up a guest I have gone into settings/storage and then selected the CD crive, but not selected passthrough, in the hope it will pick up the CD when first opening the guest os.

---

### Post by SecretCode on 2010-01-11
It might make a difference this time.

Has this CD been successfully used for an install before? Either physical or in a different virtual installation?

---

### Post by xude on 2010-01-11
Yes - the CD has been used to install Ubuntu on which VirtualBax is now running (a number of times). My son was also successful installing the same Windows CD on VirtualBox on Ubuntu on the same machine a few weeks ago, but after a couple of days the Windows os would hang. So we removed it and re-installed.

When that did not work we started from scratch with a full install - and that is when the current problem arose.

I will give it a try with passthrough selected tomorrow and if that does not work I will pull the os from an iso file. I will revert on any progress.

Thanks for the help so far.

---

### Post by xude on 2010-01-15
Tried both installing the o/s with passthrough enabled and separately from an iso file. In both cases the system hung - the same as in past attempts.

Any new ideas?

---

### Post by SecretCode on 2010-01-15
I can't see whether you've answered the question a couple of people asked:

What happens if you install a linux guest, e.g. ubuntu, under virtualbox?

---

### Post by xude on 2010-01-15
Post #6 - I tried installing Ubuntu 9.10 but it had the same effect as XP - system hung.

---

### Post by Samatva on 2010-01-15
Since other OS's hang too, my suggestion may not help... 

I had a problem getting XP to install in VertBox, made and ISO of the CD and mounted that - it all installed just fine. As I recall,  the copy of XP I was using (a bulk-licence corporate edition) had some case-sensitivity or other filename issue in the install routines when reading from CD, but not from the ISO. 

If VirtBox is not accessing your CD drive properly, the ISO route may help (it's *much* faster too!)

---

### Post by xude on 2010-01-15
As mentioned earlier... the iso route hung in the same way. The issue I am experiencing must be more fundamental than locating the XP install.

---

### Post by SecretCode on 2010-01-15
You may have found a bug in virtualbox. I suggest you ask at [http://forums.virtualbox.org](http://forums.virtualbox.org) - and if no one can resolve it there, take it to [http://www.virtualbox.org/wiki/Bugtracker](http://www.virtualbox.org/wiki/Bugtracker)

---

