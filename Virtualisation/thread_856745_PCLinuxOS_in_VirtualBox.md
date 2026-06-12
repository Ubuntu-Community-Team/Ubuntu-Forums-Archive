---
title: "PCLinuxOS in VirtualBox"
date: 2008-07-11
forum: Virtualisation
---

### Post by solwic on 2008-07-11
I'm not sure where this goes, so forum staff, please feel free to move it to it's proper home (as if you needed my permission :P)

Anyway, I'm trying to dual-boot Ubuntu and PCLinuxOS (I want a little Gnome and a little KDE, and no, Kubuntu isn't an option :() but I want to try out PCLinuxOS first.  I'm using VirtualBox (Not the OSE edition) in Ubuntu HH.  

It runs the Live CD fine, installs to the virtual disk fine, but when I try to boot it up from the virtual hard drive it opens the window for the guest OS, goes through a few steps, and then closes itself.  In the original VirtualBox window it says "PCLinuxOS" and underneath it says "Aborted".

Every other OS I've tried to install in VB (Kubuntu, Windows XP, even Fedora, though the video is broken with Fedora) works.  PCLinuxOS is the only one that does this.  I know it's not an Ubuntu problem, but these forums are probably the best around, so I thought I'd throw the question out there.  

I tried Google, came up with nothing.

Thanks.

---

### Post by bromix on 2008-07-11
If KDE is all you want, you can just install kubuntu-desktop to your existing Ubuntu installation.  Then you'll have the option to choose KDE or Gnome at login, without a whole new installation.  (not sure why Kubuntu "isn't an option".)

---

### Post by solwic on 2008-07-11
> **bromix said:**
> If KDE is all you want, you can just install kubuntu-desktop to your existing Ubuntu installation.  Then you'll have the option to choose KDE or Gnome at login, without a whole new installation.  (not sure why Kubuntu "isn't an option".)

Well I tried installing kubuntu-desktop in Ubuntu before...ended up reformatting the whole drive and reinstalling Ubuntu just to get rid of all the garbage that came with it.  

As for Kubuntu not being an option...that's because I've heard (and from my limited experience with KDE, quite agree) that Kubuntu is about the worst example of the KDE desktop you can get.  I've installed Kubuntu and...well...didn't care for it.

So...any tips with gettin PCLinuxOS to work?  I'm willing to wipe out my Windows Partition for this if I know it works...but my only experience with it is a crash.  Is this an Ubuntu thing?  Or a VB thing?  Or is it the PCLinuxOS that's messed up?

Thanks!

---

### Post by bromix on 2008-07-11
Hmmm,  sorry, I can't help ya there.  I haven't used KDE since SuSE 10, and thats when I switched to Ubuntu.  I've been stuck on Gnome ever since.  Hopefully someone else has some helpful input for ya.

---

### Post by bodhi.zazen on 2008-07-11
Hard to tell from the information you provided.

Any idea what error message you are getting ?

---

### Post by solwic on 2008-07-11
> **bodhi.zazen said:**
> Hard to tell from the information you provided.

Any idea what error message you are getting ?

It doesn't give one.  The window goes away, and when I go back to VB where it lists installed OS's it says "Aborted" beneath PCLinuxOS.  

No errors, no logs...nothing.  

I'm downloading OpenSUSE11 now in case I can't get this working.  

Sorry I can't provide more info.  :(

---

### Post by balaknair on 2008-07-11
I've installed PCLOS in VirtualBox on Gutsy, it seemed to work just fine. I think your VB settings for the virtual machine might be at fault(RAM allocated too low, CD iso still mounted, Virtual hard disk on an external drive(USB issues), virtual disk vdi file corrupted and so on).
The installation might also have been faulty or corrupted, maybe a faulty CD or iso.

PClinuxOS isn't on the list of supported guest OSes on VirtualBox, but it's based on Mandriva, so maybe you could try again with a new Virtual machine, and this time choose 'Mandriva' as OS type. Allocate more RAM as well.

---

### Post by solwic on 2008-07-11
> **balaknair said:**
> I've installed PCLOS in VirtualBox on Gutsy, it seemed to work just fine. I think your VB settings for the virtual machine might be at fault(RAM allocated too low, CD iso still mounted, Virtual hard disk on an external drive(USB issues), virtual disk vdi file corrupted and so on).
The installation might also have been faulty or corrupted, maybe a faulty CD or iso.

PClinuxOS isn't on the list of supported guest OSes on VirtualBox, but it's based on Mandriva, so maybe you could try again with a new Virtual machine, and this time choose 'Mandriva' as OS type. Allocate more RAM as well.

I gave the VM 768MB RAM and 128MB video, removed the .ISO before I rebooted, and the virtual disk vdi is brand new and on my main drive.  I guess it could be corrupted, but it created fine, and the LiveCD works perfectly, as does the initial install.  It's only when I reboot after installing that it craps out on me.

I had been using Linux 2.6.x or whatever for the OS type, except for the last time I used Ubuntu.  I didn't know PCLinuxOS was based on Mandriva, nor did I know Mandriva was in the supported OS list in VB.  That could very well be the problem.  

Thanks for the help...I'll let you know if that was the problem.  :)

---

### Post by solwic on 2008-07-11
I changed the OS type to Mandriva and started it up.  It still crashed and said Aborted, but this time it gave me this error in the log:

00:11:45.772 ********************* End of statistics **********************
00:11:46.502 Changing the VM state from 'DESTROYING' to 'TERMINATED'.
00:11:47.147 ERROR [COM]: aRC=E_ACCESSDENIED (0x80070005) aIID={fd443ec1-0006-4f5b-9282-d72760a66916} aComponent={Mouse} aText={The console is not powered up} aWarning=false, preserve=false

It crashes right after I select the first option in GRUB.

Any ideas?  Also, it's a dynamically expanding vdi, if that makes a difference....

---

### Post by solwic on 2008-07-12
*bump*  Any ideas as to what could be causing this?  

Thanks.

---

### Post by balaknair on 2008-07-17
Hi
Sorry for the delay in answering.
I'm assuming you're installing PCLOS 2007. I had it working on Virtualbox on both WinXP and Ubuntu 7.10 hosts, but I think I got some errors on WinXP first(no bootable media found- failed to boot) in the beginning. When I reinstalled it I used manual partitioning for the drive during install, individually assigning a mount point, /home(both as ext3 partitions) and swap. When I rebooted after that, it booted up fine. On Ubuntu(I use the closed source binaries from Virtual box instead of the OSE though that shouldn't make a difference here) I used steps similar to what I used in Winxp, and it was running quite well. So I'm not sure what the error messgae you got is due to. But maybe the Automatic drive partitioning part during install is responsible(some sort of bug there? not sure). 
After reading your post I just installed PCLOS2008(minime) on Virtualbox under Gutsy as i was typing this. It's working fine. The parameters on Vbox are given below. Hope this info is helpful. Attaching screenshots below.


```
General
Name
PCLOS2k8
OS Type
Linux 2.6
Base Memory
512 MB
Video Memory
8 MB
Boot Order
Floppy, CD/DVD-ROM, Hard Disk
ACPI
Enabled
IO APIC
Disabled
VT-x/AMD-V
Disabled
PAE/NX
Disabled
 

Hard Disks
IDE Primary Master
PCLOS2k8.vdi [Normal, 6.31 GB]
 

CD/DVD-ROM
Not mounted

 

Floppy
Not mounted

 

Audio
Host Driver
PulseAudio
Controller
ICH AC97
 

Network
Adapter 0
PCnet-FAST III (NAT)
 

Serial Ports
Disabled

 

USB
Disabled

 

Shared Folders
None

 

Remote Display
Disabled

```

Hope this is helpful.
All the best.

PS: as an alternative, try Mint Daryna KDE edition, it turned out to be a pretty good KDE distro. It's based on Ubuntu 7.10, but also includes the proprietary drivers and codecs(like PCLOS).

---

