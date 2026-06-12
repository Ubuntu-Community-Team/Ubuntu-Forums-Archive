---
title: "Where can i find the information i need?"
date: 2009-03-19
forum: The Cafe
---

### Post by MasterNetra on 2009-03-19
I was wondering where i can find out how to create a custom Ubuntu CD? All i want to do is add the proprietary wireless driver i need for my wireless so that i can use the internet upon install or even during Live-CD.

**Also I'm currently stuck on winxp atm so if its a way it can be done on windows that be great.**

---

### Post by pytheas22 on 2009-03-19
remastersys lets you create custom live CDs very easily from within Ubuntu.  There's a guide [here]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html").

I don't know how you could do it from Windows.  I suppose there might be some way to crack open the Ubuntu ISO image and change what you need, but it would be difficult to do and you'd need to know a lot about Ubuntu in order to make the changes.  remastersys is a much easier way to go.

---

### Post by MasterNetra on 2009-03-19
Even for just adding the STA Drivers for my Broadcom BCM4310?

---

### Post by pytheas22 on 2009-03-20
The STA driver is already built into Ubuntu 8.10 (this is not the case on older versions).  You just need to enable it, which you should be able to do using the System>Administration>Hardware Drivers utility.  You can also insert the module manually by typing:
```

sudo modprobe wl
```

If that's all you want to do, maybe you don't need to go to the trouble of creating a custom live CD.

---

### Post by MasterNetra on 2009-03-20
ohhh I was thinking i had to be connected to the net to get the drivers.. I didn't realize it was ready to go x.x *feels like a noob* Anyrate... is there someway i can fake a restart to impliment the driver for live-cd sense restarting would be pointless?

---

### Post by cariboo on 2009-03-20
You don't need to restart after inserting a module.  Just restart networking after you have inserted the module and you should be good to go. Open a terminal and type:

```
sudo /etc/init.d/networking restart
```

Jim

---

### Post by MasterNetra on 2009-03-20
Thanks everyone. :)

The restart code doesn't seem to work as needed on live-cd in terminal it says it reconfigures but it isn't reflected in the hardware drivers nor with the network manager...

---

### Post by pytheas22 on 2009-03-20
Please run these commands on the live CD and post the output.  They should make your wireless come up:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo modprobe wl
sudo ifconfig eth1 up
lshw -C Network
sudo iwlist scan
```

---

### Post by Sealbhach on 2009-03-20
You can use remastersys to make an iso of your system as mentioned above. Then use Unetbootin to make it bootable from a USB. At least that's what I did anyway.


.

---

### Post by MasterNetra on 2009-03-20
> **pytheas22 said:**
> Please run these commands on the live CD and post the output.  They should make your wireless come up:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo modprobe wl
sudo ifconfig eth1 up
lshw -C Network
sudo iwlist scan
```

```

ubuntu@ubuntu:~$ sudo rmmod b43
ubuntu@ubuntu:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
ubuntu@ubuntu:~$ sudo rmmod ssb
ubuntu@ubuntu:~$ modprobe wl
ubuntu@ubuntu:~$ sudo ifconfig ethl up
ethl: ERROR while getting interface flags: No such device
ubuntu@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user
* - network UNCLAIMED
       description: Network Controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap list
       configuration: latency=0
* - network
       description: Ethernet Interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: *<censored>*
       width: 64 bits
       clock: 33MHz
       capabilities: bus master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94
       firmware = 5755m - v3.32 latency=0 module=tg3 
       multicast=yes
* - network DISABLED
       description: Ethernet Interface
       physical id: 1
       logical name: pan0
       serial: *<censored>*
       capabilities: ethernet physical
       configuration: broadcast=yes driver=Dridge 
       driverversion=2.3 firmware=N/A multicast=yes
ubuntu@ubuntu:~$ sudo iwlist scan
       lo - Interface doesn't support scanning
     eth0 - Interface doesn't support scanning
     pan0 - Interface doesn't support scanning

```

Be happy i had to hand write all this then type it sense i have no internet access for live-CD. For security purposes i censored the serials. Can't see why you would need them for diagnostic purposes anyway -.-

---

### Post by pytheas22 on 2009-03-20
Thanks for typing that out.  For future reference, keep in mind that you could always paste the output into a text file (Applications>Accessories>Text Editor), then save it to a USB drive and transfer to another computer for posting here.  Much easier than copying by hand :)

Anyway, it looks like the STA driver is not claiming your card at all.  Are you certain you were using the STA driver before?  You may have been using the b43 driver instead, which does require an Internet connection to download firmware.  The open-source b43 driver supports all Broadcom-based cards; closed-source STA only supports certain ones.  I'm not sure about the status of yours, but if you post the output of the command:

```
lspci -nn | grep -i broadcom
```

I'll look it up.

---

### Post by MasterNetra on 2009-03-20
Thats the output of the LiveCD I currently have WinXP installed not Ubuntu. Yes I use STA driver. However the b43 driver claims LiveCD system. Also i don't currently have a USB drive to plug in :/

---

### Post by pytheas22 on 2009-03-20
In the output you posted above, the STA driver (i.e., the 'wl' module) was not claiming the card.  But if you say that's the driver you use, I'll take your word for it.

Anyway, whether you're using b43 or STA, I guess that what you need to do to achieve your end result is the same: use remastersys to create a custom ISO image.  It's possible that remastersys would work from the live CD if you have enough RAM--it needs a lot of disk space (up to 2 gigabytes, temporarily) to generate the ISO image, and when you're running from the live CD, your available disk space is limited to available memory.

If you don't have enough memory to support remastersys on the live CD, your only option is going to be to install Ubuntu to hard disk.  You could always use [wubi]("http://wubi-installer.org") to install inside Windows if you want to be able to uninstall Linux easily once you're done.

---

### Post by MasterNetra on 2009-03-20
> **pytheas22 said:**
> In the output you posted above, the STA driver (i.e., the 'wl' module) was not claiming the card.  But if you say that's the driver you use, I'll take your word for it.

Anyway, whether you're using b43 or STA, I guess that what you need to do to achieve your end result is the same: use remastersys to create a custom ISO image.  It's possible that remastersys would work from the live CD if you have enough RAM--it needs a lot of disk space (up to 2 gigabytes, temporarily) to generate the ISO image, and when you're running from the live CD, your available disk space is limited to available memory.

If you don't have enough memory to support remastersys on the live CD, your only option is going to be to install Ubuntu to hard disk.  You could always use [wubi]("http://wubi-installer.org") to install inside Windows if you want to be able to uninstall Linux easily once you're done.

Apparently I don't need to create one anymore. Apparently the Ubuntu CD comes with STA, I was under the impression that it had to download the driver when it simply isn't so and the Display "Downloading & Installing* when activating the driver kinda enforced that to some degree.

Now if i can only learn how to "refresh" the system while in LiveCD so that it will implement the STA drivers sense restarting the system is kinda pointless in LiveCD...

---

### Post by pytheas22 on 2009-03-20
> Apparently I don't need to create one anymore. Apparently the Ubuntu CD comes with STA, I was under the impression that it had to download the driver when it simply isn't so and the Display "Downloading & Installing* when activating the driver kinda enforced that to some degree.

If it says 'Downloading and Installing', then I really suspect that you're using the b43 driver--especially since manual insertion of the wl module doesn't seem to do anything.  But the only way to know for sure would be to see what actually happens behind the scenes when you click to activate the driver.  If you could plug the machine into the Internet, enable the driver in Hardware Drivers and then post the output of these commands after the card is up and running, it would tell me exactly which driver you're using:
```

lshw -C Network
ls /lib/firmware
```

---

### Post by MasterNetra on 2009-03-21
Sadly I can't plug my machine into the net I have to use a wireless connection. Although I have installed Ubuntu into WinXP and activating the STA driver is not a issue sense doing a restart isn't a issue for a installed OS (obviously). My only issue atm is getting it to work in a LiveCD session...well not my only problem i mean I also would like to know how to view the printers on my school network (they are on a windows server) via samba or other means...but thats a differant subject i guess.

---

### Post by pytheas22 on 2009-03-21
If all you're looking to do is make a live CD where your wireless would always work, one option to consider would be installing Ubuntu to a USB drive; these [instructions]("http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/") explain how.  Unlike the regular live CD, changes made to your USB drive would be persistent through reboots, so once you set up the wireless driver the first time, it should remain in place.

As for the printers, you probably need to install samba, but I don't know much about that; you'd be better off starting a new thread to deal with that issue if it's important to you.

---

### Post by MasterNetra on 2009-03-21
I suppose I could get a 4GB flash drive for Ubuntu itself & a 2GB one for file storage...whenever the funds become available. I was just hoping I could rig something up to implement the STA driver in the Live-CD session. But if it cannot be done then it cannot be done i suppose...

---

