---
title: "help with using ubuntu to clean windows"
date: 2009-11-17
forum: Security
---

### Post by b4t3m4n on 2009-11-17
I do a lot of work on computers for friends and family and the problem is almost always virii.  And I don't get the computer when it gets infected, no no, I get it after multiple virii have duplicated themselves a few dozen times and the computer is borderline unusable.

Normally I would just throw in the towel and reformat, reinstall windows.  This is not a great option because it takes forever and they always forget to tell me about something that needed to be backed up.

Recently I have been trying to use ubuntu on a usb flash drive to boot their computer and use ClamAV to flush their systems.  The problem is, it never seems to find all the virii.  

I would think this would be a common problem for IT people and wonder if there is not a better solution.  Any help would be appreciated.

---

### Post by Lars Noodén on 2009-11-17
> **b4t3m4n said:**
> I do a lot of work on computers for friends and family and the problem is almost always virii.  And I don't get the computer when it gets infected, no no, I get it after multiple virii have duplicated themselves a few dozen times and the computer is borderline unusable.

Normally I would just throw in the towel and reformat, reinstall windows.  This is not a great option because it takes forever and they always forget to tell me about something that needed to be backed up.


That's an advantage for Microsoft.  Eventually you will either forget to install third party applications or run out of time and leave them off anyway.  Same for the configurations.  Windows doesn't have any of the ease of installation that the linux distros have had for a Very Long Time(tm)

> **b4t3m4n said:**
> 
Recently I have been trying to use ubuntu on a usb flash drive to boot their computer and use ClamAV to flush their systems.  The problem is, it never seems to find all the virii.  

I would think this would be a common problem for IT people and wonder if there is not a better solution.  Any help would be appreciated.

Corrective action is and always will be like that.  You're mopping the floor to remove water instead of fixing the hole in the roof. 

So, the obvious solution would be to wipe Windows and do a fresh install of Ubuntu.  Obviously, you'll want to test this and expand in phases.  WINE will be of great help if you have any legacy applications.  

Another option would be to wipe Windows and do a fresh install of Ubuntu and then use a virtual machine like VirtualBox or Qemu to run Windows from a known-good 'snapshot'  VMs have the ability to start from an image and keep changes (including states) separate, known as a snapshot.  

If there is a political or ideological or other reason keeping windows on the harddisk, a third option would be to use the Wubi Installer for Windows and run Ubuntu except when the need for legacy apps dictates otherwise.

---

### Post by b4t3m4n on 2009-11-17
> **Lars Noodén said:**
> That's an advantage for Microsoft.  Eventually you will either forget to install third party applications or run out of time and leave them off anyway.  Same for the configurations.  Windows doesn't have any of the ease of installation that the linux distros have had for a Very Long Time(tm)



Corrective action is and always will be like that.  You're mopping the floor to remove water instead of fixing the hole in the roof. 

So, the obvious solution would be to wipe Windows and do a fresh install of Ubuntu.  Obviously, you'll want to test this and expand in phases.  WINE will be of great help if you have any legacy applications.  

Another option would be to wipe Windows and do a fresh install of Ubuntu and then use a virtual machine like VirtualBox or Qemu to run Windows from a known-good 'snapshot'  VMs have the ability to start from an image and keep changes (including states) separate, known as a snapshot.  

If there is a political or ideological or other reason keeping windows on the harddisk, a third option would be to use the Wubi Installer for Windows and run Ubuntu except when the need for legacy apps dictates otherwise.

I appreciate your answers, but since these are other people's machines, I would prefer to keep their original Windows installation on board.

---

### Post by JBAlaska on 2009-11-17
The problem with using a Linux AV to clean windoze (and someone correct me if I'm wrong) is that the virus definitions are geared towards Linux viruses.

You might have better luck using a dedicated boot disk like BartPE and run a windoze based AV from that.

---

### Post by b4t3m4n on 2009-11-17
> **JBAlaska said:**
> The problem with using a Linux AV to clean windoze (and someone correct me if I'm wrong) is that the virus definitions are geared towards Linux viruses.

You might have better luck using a dedicated boot disk like BartPE and run a windoze based AV from that.

No clam has windows defs

I found many of the virii, just not all of them.

---

### Post by EJeanmaire on 2009-11-17
> **b4t3m4n said:**
> I appreciate your answers, but since these are other people's machines, I would prefer to keep their original Windows installation on board.

After you use Clam AV is the Windows box stable enough (in Windows) to run the Microsoft AV scan from the OneCare site?

---

### Post by wilee-nilee on 2009-11-17
You must be familiar with Hirens you can get a bootable disc with built in AV scanners to clean it up enough to get the MS to boot and use a thumb or cd filled with your favorite AV programs.

A fresh install may be the best route anyway. If the client or friends don't know how to protect themselves in the 1st place it can be a learning experience for future reference.

Edit: So I was able to down load Hirens 10 and scan it, it appears to be the real thing so after extracting then loading to a thumb I booted with it, but it can also be burned to a disc this is a powerful toolbox. If you want any links or info PM or email me.

---

### Post by b4t3m4n on 2009-11-17
> **EJeanmaire said:**
> After you use Clam AV is the Windows box stable enough (in Windows) to run the Microsoft AV scan from the OneCare site?

Yes it is, and is currently running.  Only 11% in on the virus scan and already have "30 items detected, 6 issues found".  Clam was reporting 0 virus. :?

---

### Post by xpod on 2009-11-18
@Op
9 times out of 10 when we get machines in such a state the *only* sensible option is a complete format/re-installation.....the quick way.Re-installing Windows can take a while, if your using an original CD and then manually adding all the updates,service packs & software etc.If you create your own bootable CD though, or better still, a [USB](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)  key with a slipstreamed Windows installation then you can get that install time down dramatically.
Due to the time saved installing what you could then do is create a [nlited/vlited](http://www.nliteos.com/) installation disk with all the users drivers & commonly used programs.....for future reference.

---

### Post by EJeanmaire on 2009-11-18
> **b4t3m4n said:**
> Yes it is, and is currently running.  Only 11% in on the virus scan and already have "30 items detected, 6 issues found".  Clam was reporting 0 virus. :?

If I remember correctly, the Windows one was never fast to begin with.

---

### Post by Lars Noodén on 2009-11-18
> **b4t3m4n said:**
> I appreciate your answers, but since these are other people's machines, I would prefer to keep their original Windows installation on board.

Ok.  Then the Wubi Installer might be an option.  That will leave Windows on the drive.  Have they voiced any particular reasons for not upgrading?

As far as re-installs go, there are some live cds with backup utilities and several means of making disk images.  So in the worst case, you could boot with the live cd and copy the restoration image over.  I don't expect Windows can make separate system and data partitions, but if it could, that would speed the restoration greatly.

Ubuntu has live cds, but there are also specialist distros like Finnix, which is packed with utilities.  There are instructions at the Finnix site about how to roll your own, so you could make one with the programs, keys and certificates you want.  Making a bootable USB stick is fairly close.

---

### Post by xpod on 2009-11-18
> **Lars Noodén said:**
> Ok.  Then the Wubi Installer might be an option.  That will leave Windows on the drive.  Have they voiced any particular reasons for not upgrading?

As far as re-installs go, there are some live cds with backup utilities and several means of making disk images.  So in the worst case, you could boot with the live cd and copy the restoration image over.  **I don't expect Windows can make separate system and data partitions, but if it could, that would speed the restoration greatly.**

Ubuntu has live cds, but there are also specialist distros like Finnix, which is packed with utilities.  There are instructions at the Finnix site about how to roll your own, so you could make one with the programs, keys and certificates you want.  Making a bootable USB stick is fairly close.

You can locate the users Documents & Settings on a [separate partition](http://lifehacker.com/5271338/separate-your-data-from-windows-on-a-standalone-partition) in Windows.

---

### Post by b4t3m4n on 2009-11-18
Thanks for all the help everyone.  I managed to recover the computer completely by using ClamAV to stabilize the machine then run MS's CareOne.

Strangely the additional Virii that CareOne found were just copies of the worms that ClamAV had already found.  I am unsure why Clam did not find the copies.

---

### Post by EJeanmaire on 2009-11-19
> **b4t3m4n said:**
> Thanks for all the help everyone.  I managed to recover the computer completely by using ClamAV to stabilize the machine then run MS's CareOne.

Strangely the additional Virii that CareOne found were just copies of the worms that ClamAV had already found.  I am unsure why Clam did not find the copies.

The Microsoft OneCare is a pretty thorough virus scanner for Windows boxes... surprisingly enough.

---

