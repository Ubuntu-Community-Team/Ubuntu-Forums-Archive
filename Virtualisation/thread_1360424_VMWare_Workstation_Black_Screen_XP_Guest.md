---
title: "VMWare Workstation Black Screen XP Guest"
date: 2009-12-20
forum: Virtualisation
---

### Post by bkg-22 on 2009-12-20
I am not sure whether to post this under VMware or some other X11 discussion, but I will start here.

I am running Ubuntu 9.10 (the VMWare host) with VMware Workstation 6.5.3.  I have a couple of WinXP guests running with no apparent problems _*as long as I am sitting at the monitor/keyboard physically attached to the server*_.  However, when i access this server via VNC, VMWare displays the XP guests as a solid black screen after starting them.  Based on io activity & cpu, I think they are actually starting just fine, I just have no way to view them through my remote X11/VNC session - the XP guest screens are just black.  The rest of the gnome desktop looks fine.

I am using vnc4server via an X session.  I can log into the Ubuntu server from my personal XP laptop using a generic VNC client - it works pretty well.  After starting the vm (guestOS - WinXP) I do get several errors from VMware about X keyboard mappings and one error about not being able to match the screen resolution if I go full screen - but the guest machine seems to start just fine.  However, I can't really verify that visually because the XP guest screen is black.

I have played with resolution of the XP guest virtual machine (guest), resolution of the gnome desktop, resolution of my remote system I am accessing from.  I have also played with the color depth setting for the Xvnc config, and the color depth on the guest vm.  Nothing seems to help.

Suggestions?

---

### Post by HermanAB on 2009-12-21
Howdy,

Enable remote Desktop in each guest OS and connect to it using rdesktop from Linux:
$ rdesktop -g 90% 192.168.1.2

You can change the Xp registry to run RDP on different ports:
$ rdesktop 192.168.1.2:1234

This is the best way to access XP remotely whether virtual or physical.

---

### Post by bkg-22 on 2009-12-21
Thanks for the suggestion Herman.  That is certainly an option I will consider.

I am slowly trying to wean myself off of MS Windows and for some things, it has been a really easy experience - and for others, it has been like pulling teeth.  This whole remote access/remote desktop across the internet to my linux server has been a pretty bumpy road with no "tried/true/proven" solution.  Once I finally got it working (setting up a headless server and need remote login capability without having to login manullay at the console first), now I have this color depth issue VMWare guests.

As much as I really want this to work on LINUX, I know the server would be done and mounted in the wiring closet if I was doing this on Windows :(.

I am beginning to think maybe I need to re-evaluate my approach on this project.

Thanks again....

---

### Post by dcstar on 2009-12-23
> **bkg-22 said:**
> I am not sure whether to post this under VMware or some other X11 discussion, but I will start here.

I am running Ubuntu 9.10 (the VMWare host) with VMware Workstation 6.5.3.  I have a couple of WinXP guests running with no apparent problems _*as long as I am sitting at the monitor/keyboard physically attached to the server*_.  However, when i access this server via VNC, VMWare displays the XP guests as a solid black screen after starting them.
.........
Suggestions?

Access the VMs directly via the various VMware console tools. I can access any VM running on a VMware Server host using another VMware Server host or the separate (multi-platform) console access tools software from VMware.

I assume the same functionality is available for Workstation.

---

