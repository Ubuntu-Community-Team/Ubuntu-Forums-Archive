---
title: "KVM GUI interface"
date: 2009-03-17
forum: Virtualisation
---

### Post by freakalad on 2009-03-17
Been using KVM for about a month now, with some mixed results.

Could anyone please recommend a decent GUI front-end for KVM? 
I'd prefer having some sort of web-based interface (maybe similar to VMWare 2.x?). Possibly something universal, should I employ other servers in a "farm"
I've been using the CLI (too much typing if you pop systems frequently) & remote X with virt-manager.

Please advise

Thanks

-J

---

### Post by HermanAB on 2009-03-17
There doesn't seem to be one.  You should consider being a champion and writing a Webmin plug-in for KVM.

Cheers,

Herman

---

### Post by bodhi.zazen on 2009-03-17
Actually, take a look at Proxmox :

here is a review on the Montana LUG : [http://www.montanalinux.org/proxmox-ve-review.html](http://www.montanalinux.org/proxmox-ve-review.html)

Home page : [http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

Personally I write a wrapper script for KVM which adds (then removes) a tap interface and has most of the common arguments I use.

See also : [https://help.ubuntu.com/community/KVM/Managing](https://help.ubuntu.com/community/KVM/Managing) (this page in fact shows a GUI interface).

and [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by HermanAB on 2009-03-17
Wow.  Wish I knew about that sooner.

Thanks,

Herman

---

### Post by cb951303 on 2009-03-17
if you need an actual GUI frontend, look at qemu frontends. they should work for KVM too.

---

### Post by freakalad on 2009-03-17
Fantastic info, guys!

Thanks for that.

Herman : you're absolutely right. A WebMin interface would be fantastic; especially if it can be implementation-independent

---

### Post by freakalad on 2009-03-18
Gave Proxmox the quick once-over, and that may very well be a solution I'll seriously consider when starting from scratch, since it's essentially a separate distro in it's own right, but it may not be feasible as a simple management interface. 

Any other recommendations?

---

### Post by vorgusa on 2009-03-19
What were you hoping to do that proxmox does not allow?  Its built off of Debian and pretty soon they are going to upgrade to Debian Lenny.  You can SSH into the machine and its just a regular linux box that has apt-get too.

---

### Post by freakalad on 2009-03-19
I was planning on cheating.

Wanted to take a shortcut & simply add the repositories to my sources.list & do a simple apt-get install.

Didn't work out as planned. (no surprises there)

When I initially bought my new (personal) system, I was thinking this EXACT setup (well, couldn't decide on XenSource or KVM at the time), but at the time I didn't know of ProxMax, so I wend with a vanilla Ubuntu installation (from mini ISO).

I'll have to reassess my setup & start from scratch (i.e. scratch dom0 OS), but luckily I separated my system into LVM partition, so I should be OK...theoretically.

Just not up to completely re-doing my system at this time.

I understand the custom distro tailored to VM's, but I was hoping for a pretty interface to take the legwork out of the CLI.
May have to plan this as a project of my own (learning a bit of python, so may be a good excersice) & release it when in a working condition...

---

### Post by Schorschi on 2009-04-05
Can you not use remote console within the VM in KVM?  For example, VNC for Ubuntu VMs, and RDP for Windows VMs?  This worked for me for most things.  Of course I can not do a forced reboot, but most of the time that is not needed.  The one thing I do not like about the current situation is the fact that all the solutions to use virt-manager require a GUI on the server.  I which virt-manager had a GUI client like VMware VI client.

---

### Post by freakalad on 2009-04-05
Remote desktop viewing (VNC/remote-X/Terminal services) is very do-able, but that only solves half of the problems (like no 3D Hardware Acceleration/OpenGL). But it's a start..

I too dearly miss a polished frond-end, preferably like VMWare (as you've pointed out). oVirt is a pretty good option, but it's RedHat only at this stage.

Will have to wait & see what gets shaken loose with the next release (Jaunty)

---

### Post by freakalad on 2009-04-22
I think I may have located a solution that fits the bill
Enomalism or [Enomaly]("http://www.enomaly.com/")

& a how-to:
[http://www.howtoforge.com/kvm-virtualization-with-enomalism-2-on-an-ubuntu-8.10-server](http://www.howtoforge.com/kvm-virtualization-with-enomalism-2-on-an-ubuntu-8.10-server)

A web-based interface making use of Python to hook into libvirt

Gonna try it & will report back on any problems

Thanks again for all your guys' help

---

### Post by HDave on 2009-05-18
I too am really looking hard for a thin client management interface like VMWARE ESX for KVM.  How did it go with Enomaly?

---

### Post by freakalad on 2009-05-18
Enomaly seems to fit the bill (ticks all the right boxes, pretty good reviews), but it's a fairly significant installation & requires a bit of configuration.

For instance, I keep a fairly comprehensive set of ISO's, ready for distribution to my mates & any that may become interested in FLOSS, but the Enomaly, by default, gives you a list to pick from, which it then downloads.

Not really an issue, but is a bit annoying.

---

### Post by gbear14275 on 2009-11-01
Looking pretty sharp!  I'll be giving this a shot in karmic.  Anyone been there yet with words of wisdom?

Edit: Reading through the HowTo I saw something about a lack of lvm support... this true?

---

### Post by NaOH on 2009-12-17
Not sure if this would be applicable for you, but my vm needs were small: Non-Windows environment needing 7-10 users with Windows access.  My solution was this (don't laugh!): Barebone install of server 9.10, installed fluxbox on top of this, and then virtualbox ose.  Users rdp into their Windows environment and thats that.  This is built on a 2x dual xeon system, 8GB of memory, and RAID 10 (softraid), which has yet to flinch at 7 concurrent connections.

I was considering KVM but was under the gun to provide a solution, so chose this route being already familiar with virtualbox ose.  So far I'm happy with the performance, and the management isn't bad either.  Virtualbox offers an okay set of command line tools, enough to make some startup and shutdown scripts.  And of course it offers a polished GUI.

If this continues to work out as nicely as it is now I hope to write up a quick tutorial on it.

---

### Post by freakalad on 2010-09-20
I've recently settled on [Convirt]("http://www.convirture.com"), & it seems to be treating me well.

I still have a few issues to iron out, such as importing/migrating my existing libvirt guests across, but for the most part this seems OK.

Cheers

- J

---

### Post by manzdagratiano on 2010-09-20
I would second writing a script with most of the common arguments in place and making it accept merely the name of the VM and/or the cdrom image. The command line has kept me quite happy. I tried using Qemulator in the past, as well as virt-manager, and I hated them. With the command line I feel I enjoy all the power regarding tweaking and such things - and I used to be big on Virtualbox at one point of time!

---

