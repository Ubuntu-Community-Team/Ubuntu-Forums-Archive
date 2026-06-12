---
title: "Server 12.04.1 install fails after &quot;Loading additional components&quot; message"
date: 2012-12-02
forum: Server Platforms
---

### Post by #1udancqSHv% on 2012-12-02
Hi all, 

I'm fairly new to Linux, but comfortable with partitioning and installing onto a multi-boot system. I'm having a bit of trouble installing Ubuntu Server 12.04.1 LTS onto my desktop box, for testing purposes.

The installation seems to hang after showing the "Loading additional components" message, or in expert mode after a message that reads something like "Detecting network hardware (or similar). I see a blank purple screen, with a light grey line at the bottom, I'm able to type into this area, but nothing I type seems to have any effect.

My initial attempts were using the standard installer, but I've tried expert mode, and selecting each of the other F6 options (including 'nomodeset'), all with the same result. One of the many search results I found on my quest to fix this: [http://askubuntu.com/questions/53257/why-do-i-get-a-purple-screen-whilst-installing-ubuntu-server-11-04](http://askubuntu.com/questions/53257/why-do-i-get-a-purple-screen-whilst-installing-ubuntu-server-11-04) - didn't work in my case...

I used the installer to check that the CD was ok - no problems there. The same disk also installs Ubuntu Server onto my laptop just fine. I've been able to install various flavours of Ubuntu and other distros onto the desktop without any problems, but usually from live CD/DVDs - Ubuntu Studio, Linux Mint, Manjaro, Mageia, CentOS and Fedora all install ok.

However, I did have exactly the same result using the Xubuntu 12.04 minimal installer, and the Debian 6.0.5 Live CD installer came up with an error at the Network Adapters stage of the installation, "missing firmware: tigon/tg3_tso5.bin". However, the Debian Live CD installer did still complete, and the installation is bootable.

The network hardware in question is a dual gigabit LAN on a Foxconn X48 BlackOps motherboard, apparently a Broadcom 'NetLink BCM5786' and a 'NetXtreme BCM5788'. I found this bug on Launchpad which I thought might be relevent: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1021747](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1021747)

Could anyone please suggest a fix or workaround? Is it possible to add specific network adapter drivers to the Ubuntu Server installation process? Failing that, is there another way to get Ubuntu Server onto my desktop?

I've tried to be as clear and comprehensive as I could with my limited experience, but if any other information is needed, please ask. Thanks in advance!

---

### Post by Cheesemill on 2012-12-02
Try disabling the network adapter in your computers BIOS, this should at least let the installation complete successfully.

If this works we can then try and sort out the driver issue.

---

### Post by #1udancqSHv% on 2012-12-02
D'oh, didn't think of that - thanks Cheesemill! :)

---

### Post by #1udancqSHv% on 2012-12-05
Just to update, I disabled the network adapters in BIOS, and but the installer still seemed to hang. However, I've now installed 12.10 (not LTS, but it's only for testing purposes), which found the network adapters without any issues.

Thanks for the help in any case, Cheesemill - it was still appreciated! :)

---

