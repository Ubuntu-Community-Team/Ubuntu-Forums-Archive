---
title: "Setup VB 2.2 on Interpid Server with bridged connection."
date: 2009-04-19
forum: Virtualisation
---

### Post by nlinecomputers on 2009-04-19
Hello.

I am trying to setup a headless WinXP guest on a Intrepid Server using VirtualBox 2.2.   

I am able to setup the system using a NAT connection but I have no idea how to setup this unit using a bridged connection.

If I set the nic up with bridged using VBoxManage modifyvm the guestOS fails to load.  It works with NAT but not bridged.  I assume there is a virtual nic driver that I need to setup in ubuntu but I can't find info on how to do this.  All the information out there assumes a X-server with a GUI and I don't have(and really don't want) that on this server.

How to I setup this?

---

### Post by nlinecomputers on 2009-04-19
nvm.

I found Virtualization Mega thread [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

It solved my problem.

---

### Post by marmellata on 2009-05-31
Ihave the same problem.. and I read the mega thread but couldnt find a solution :( where did you find it?

---

### Post by domthehat on 2009-06-13
A copy of my recent post to the relevant VB forum:  

[http://forums.virtualbox.org/viewtopic.php?f=7&t=18669&p=80611#p80611](http://forums.virtualbox.org/viewtopic.php?f=7&t=18669&p=80611#p80611)

[please excuse the formatting, I can't seem to fix it]

========================================================== 

At about the same time I finally received enlightenment (from a Linux mailing list) as to *how* this bridged thing works, I'd already schedule a reboot of the server to make a BIOS change, so it is possible that a physical reboot fixed the problem - because I'm pretty sure that I'd already tried the configuration that now works. 

Somebody else reports "restarting" as a fix: [http://forums.virtualbox.org/viewtopic.php?f=7&t=18632](http://forums.virtualbox.org/viewtopic.php?f=7&t=18632) 

The important things to remember are 

1. Bridged mode isn't complicated - it simply sticks your virtual machine on the same network(s) as your physical machine. 

2. You do *not* make any changes to the host OS; no aliased interfaces, no extra IP addresses, nothing. 

3. The guest OS sets or gets its IP in the usual way - so if you don't want to or cannot use DHCP, you assign a static IP address in the normal way for that OS. 

4. That's it. 

5. Ignore all that stuff about TAPs and TUNs written for previous versions of VirtualBox.  

This is *all* you have to do on the Host 

VBoxManage controlvm "vmname" poweroff 

VBoxManage modifyvm "vmname" --nic1 bridged --bridgeadapter1 eth

VBoxHeadless --startvm "vmname"

(assuming that you've got it working as a NAT'd VM). 

The newly assigned or obtained IP address / interface will appear in the "ifconfig"output of the guest OS, but not the host OS. 

If in doubt - reboot. I know it's anathema to Unix people but if you've been messing around with the networking on the host OS it may be that starting from a clean sheet is what's needed. As I say, I was pretty sure that I'd already tried it with eth0:1 disabled and a static IP specified in the guest OS. 

If you're having problems, check the output of dmesg (or BSD equivalent) on the guest for kernel messages about the virtual network card.  Check that your guest OS supports the virtual card you're using. 

More Keywords: remote headless VirtualBox 2.2 2.2.4 bridge mode networking

---

