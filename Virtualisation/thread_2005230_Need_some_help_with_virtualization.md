---
title: "Need some help with virtualization"
date: 2012-06-17
forum: Virtualisation
---

### Post by szafran on 2012-06-17
Hi,

I'd like to get some information on the topic of virtualization. I've read some time ago (don't remember where tho) that VMWare has something that you can install like a foundation on whitch later on you install other OS'es. Right now I have a server/nas pc that has Ubuntu Server installed on it, and VMWare Player with Windows 7 (since unfortunatelly some software is still only available under Windows - like DTS compressor that I use quite often, and my laptop is to slow for that). But the emulated pc under VMWare is quite slow. It would be very nice if I could run those OS'es simultanously side by side with as low hardware emulation as possible.

My server/NAS config:

MoBo: Gigabyte GA-890GPA-UD3H
CPU: AMD Phenom II X6 1090T
Mem: 2 x Kingston HyperX 2x4GB DDR3-1600 Dual Chanel Kit Non-ECC CL9 Grey XMP
SAS Controler: LSI IBM BR10i (2 x SAS / 8 x SATA2)
OS Drives: 6 x Seagate ST3500413AS 500GB SATA III 16MB (RAID0)
Data storage: 10 x WD Caviar Green WD20EARS 2TB SATA II 64MB (RAID5)
Backup drive: USB 3.0 Verbatim Desktop Drive 2TB 3,5"
OS: Ubuntu Server 11.04

I would be very greatfull for any tips on how to accomplish my goal (if it's unclear then please ask what more information is needed). I'd prefer a cost free solution (since that's my home server for private use).

---

### Post by Cheesemill on 2012-06-17
I believe you're thinking of VMware vSphere Hypervisor (also known as ESXi).
[http://www.vmware.com/products/vsphere-hypervisor/overview.html](http://www.vmware.com/products/vsphere-hypervisor/overview.html)

It's a good choice as long as the following issues aren't a problem for you:

You can't use a keyboard and monitor attached to the server to view/control the VM's. This can only be done using the vSphere client running on another machine.

The vSphere client is only available for Windows.

---

### Post by szafran on 2012-06-17
Yes I think that that was what I was reading about.
But the vision of being restrained to just Windows as the client OS is a bit limited.

Now I'm using the Ubuntu Server with Gnome UI installed (since it's a lot faster to do some things under a GUI), and also Windows platform is GUI only. I'm used to connecting to those OSes from different platforms (and places - like home, work, frinds place, and my android phones), by just using any available ssh/vnc/rdc clients for any given OS/device (and there are a lot of those to choose from).
So using just one (and I guess that the VMWare client is heavy and needs to be installed on each machine, as for most of the other clients it's download and run procedure). So the restrictions are great in my case.

They are going to be bigger since I'm slowly thinking about kicking Windows also from my laptop and using something like ChromeOS (currently also in the process of moving all my documents to GDrive/GDocs).

I've also read some thing about KVM/Xen - not to much tho. Is there anyone with the knowledge of those, it would be nice to get some info/feedback as to if those going to work for me ? And maybe some tips on how to bite the topic ;)

---

### Post by Cheesemill on 2012-06-17
The vSphere client doesn't need to be installed on all of your machines, once a VM is set up and running you can access it however you want (SSH, RDP, VNC etc).

You only need the vSphere client to set up a new VM. I know it's not best practice in case the host goes down but I actually use a Windows VM running on the host to run the vSphere client, and RDP to that machine from my Ubuntu workstation.

---

### Post by szafran on 2012-06-17
Yes. But that's just a walkaround and not a solution.

I would like to be independent of Windows platform in the case of the setup and management of the VM's. Especially since I've tested Windows 8, and think it's total cr*p (even worse than ME and Vista mishaps).

What do you do if your LAN connection gets down, or something similiar ? (normally my server is headless, but when I need to I switch my TV to the RGB input, where a VGA cable from the server is connected, and get my wireless keyboard and mouse to get the machine up and running again - It's not happening very often, but it sometimes does).

---

### Post by Cheesemill on 2012-06-17
This is the only reason I didn't completely delete Windows from my laptop, I left it as a dual boot.

If you're looking for a Linux solution based on KVM take a look at Proxmox, I have it installed at a couple of my clients sites.

[http://www.proxmox.com/products/proxmox-ve](http://www.proxmox.com/products/proxmox-ve)

---

### Post by szafran on 2012-06-17
Thank you for your replies.

And how does the Proxmox perform ? My main interest here are the stability and performance (mostly CPU since that machine does a lot of video and audio conversions - video under Ubuntu with Handbrake, and audio under Windows 7 with eac3to+Surcode DTS Encoder)

Now I have something to play with after I manage to get some time to upgrade to the latest Ubuntu Server version (I have to do a clean install each time since after automatic upgrade I'm always unable to bring up the Gnome GUI for some driver related reson).

Since this isn't going to be in the next few days (I'm currently starting a new job), so if someone has any other suggestions (preferably with some pros/cons) I'd be gratful.

---

