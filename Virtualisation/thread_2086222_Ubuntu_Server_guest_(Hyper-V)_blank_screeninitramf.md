---
title: "Ubuntu Server guest (Hyper-V) blank screen/initramfs problems"
date: 2012-11-20
forum: Virtualisation
---

### Post by kritt on 2012-11-20
Hi all. I've asked help about this in the Hyper-V forums but I thought I'd ask here too for insights, as we couldn't come up with a solution.

I'm trying to set up an Ubuntu server guest on an MS Server 2012 Hyper-V host. I've tried both 12.10 and 12.04 but I've faced various issues with both releases. The host machine is a completely fresh installation. The guest machine is also a completely fresh installation of ubuntu server (no gui) with openssh server and LAMP. Nothing else, the only configuration is of a static IP address.

The first issue is the guest getting stuck during installation with either a blinking cursor or a completely blank screen. There seems to be some cpu usage, fluctuating between 0-30%, but no change even after an hour. This is rare but it happened with both 12.10 and 12.04. Rebooting the guest and restarting installation solved the problem.

The second issue is a blank screen on boot. Grub flashes for half a second and then the guest's screen goes blank. This happens on almost every restart of the guest. When I restart the guest after this happens, it boots successfully.

The third and most serious issue is at some point the guest machine only boots to initramfs with the message "Gave up looking for root device". After that I can't get it boot normally unless I reinstall.

I've tried reinstalling Server 2012 on another hdd. I have tried installing both versions of Ubuntu numerous times with the same issues. I am using the HP N40L microserver, with an added 2gb of ram (matching second stick as the stock), and only the stock 250gb hdd. The latest Hyper-V "Integration services" download don't support Ubuntu yet, but Microsoft says that "they are built in". I've tried many settings to make things simpler, such as a single processor/no scsi vhdd. I've a friend who's running more than 5 Ubuntu VMs inside Hyper-V 2012 without issues.

Any ideas, please?:)

---

### Post by ubugib on 2013-03-25
I've got the same environment, a Hyper-V 2012 host. Trying to install the latest Ubuntu as a guest VM. I've run into the same exact problems. Also tried installing the desktop version of Ubuntu, and it's hardly working correctly.
Very annoying. I want to set up a reverse proxy on a linux VM but this puts a damper in those plans..
Ubuntu worked perfectly in WinServer 2008.. 
I think Microsoft's new windows server doesn't want to play nice with ubuntu anymore..

---

### Post by WhaleVPS on 2013-03-26
I see what your problem is, you are using Microsoft. Kidding.

Do you have any other virtual machines already running in this environment? Can you try an older version of Ubuntu, such as 10.04?

---

