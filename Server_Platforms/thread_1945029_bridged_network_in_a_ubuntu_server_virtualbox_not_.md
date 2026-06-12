---
title: "bridged network in a ubuntu server virtualbox not working"
date: 2012-03-22
forum: Server Platforms
---

### Post by binarypill on 2012-03-22
Hi, I'm trying to setup a headless virtualbox ubuntu server. I've installed the machine and I am now trying to get the network working.

I want the guest to have access to the network that the host does. Basically, I want it to look like another machine within the hosts ip range.

I've set the virtualbox machine's network to use bridge adapter but the guest can't seem to get an IP from the router. I should note that the host is connected to the network via wifi and the guest has been set to brige to the wifi card.

---

### Post by collisionystm on 2012-03-22
> **binarypill said:**
> Hi, I'm trying to setup a headless virtualbox ubuntu server. I've installed the machine and I am now trying to get the network working.

I want the guest to have access to the network that the host does. Basically, I want it to look like another machine within the hosts ip range.

I've set the virtualbox machine's network to use bridge adapter but the guest can't seem to get an IP from the router. I should note that the host is connected to the network via wifi and the guest has been set to brige to the wifi card.


run

sudo /etc/init.d/networking restart

do you see it attempting DHCP?

post the output of

cat /etc/network/interfaces

---

### Post by binarypill on 2012-03-22
> **collisionystm said:**
> run

sudo /etc/init.d/networking restart

do you see it attempting DHCP?

post the output of

cat /etc/network/interfaces

that's weird. it says 'Cannot find device eth0'. I tried changing it to eth1 and it still didn't work.

contents of /etc/network/interfaces is:

auto eth0
iface eth0 inet dhcp

auto lo
iface lo inet loopback

---

### Post by binarypill on 2012-03-22
Okay, I got it fixed. I had to edit my 

/etc/dev/rules.d/70-persistent-net.rules (might not be exactly right. I cant' cut and paste from vbox.

I deleted all the ethx definitions to get the system to reconfigure once I rebooted. From the thread I read from another site, Linux creates new eth interfaces whenever it detects a mac change. I wish I'd saved the link but I've lost it.

---

### Post by mgtsol on 2012-10-22
I just happened to bookmark the page I think you're referring to. It's here:

[https://forums.virtualbox.org/viewtopic.php?f=7&t=43090](https://forums.virtualbox.org/viewtopic.php?f=7&t=43090)

---

### Post by krthk33@gmail.com on 2012-12-30
Thanks for your support in bringing eth0 to work, after cloning ubuntuserver vdi disk image.

I had cloned virtual box ubuntu server vdi file with new UUID:

VBoxManage clonehd  <paste UUID of vdi file> Clonename.vdi

After attaching new cloned vdi file and after starting vm, the ethernet interface show error message:

Cannot find device "eth0"
Failed to bring up eth0

The above error was solved by using the command:

sudo rm -rf /etc/udev/rules.d/70-persistent-net.rules

sudo reboot

The above command will remove network persistence rules.

---

