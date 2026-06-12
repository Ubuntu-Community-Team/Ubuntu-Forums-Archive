---
title: "Lost ETH0"
date: 2011-02-08
forum: System76 Support
---

### Post by rokstar on 2011-02-08
Somehow I lost eth0.  It no longer comes up automatically when I boot up.  Here's the output of my lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
06:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
06:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)

Can anyone please help me out?

Thanks for your time!

---

### Post by slooksterpsv on 2011-02-08
So in terminal what does the output of the following show:

```

ifconfig
sudo ifconfig eth0 up

```

And if you go up to the network icon in your notification area, right click on it and is Enable Network marked? Then if you go to Edit Connections... for Wired is anything listed?

---

### Post by rokstar on 2011-02-08
ifconfig only shows lo and wlan0. when I get back to my laptop I'll try the up command but I have a feeling it will not work since there is no eth0 in the ifconfig. network manager shows nothing under wired connections. I tried to add one but can't find a wau to get the MAC address to fill in all the necessary information

---

### Post by isantop on 2011-02-08
Try going with the default (Blank) settings, and make sure that "Connect automatically" is checked. Then, see if it works.

---

### Post by rokstar on 2011-02-09
Setting up an empty wired connection in network manager didn't work.  Any other ideas? Thanks again for taking the time to help me.

---

### Post by isantop on 2011-02-09
Have you tried connecting from a LiveCD? That would tell us if the issue was hardware or software.

---

### Post by rokstar on 2011-02-11
I'm typing this using a Maverick live CD and I'm connected via my ethernet.  So I guess it must be some software thing since the hardware is working properly.

---

### Post by rokstar on 2011-02-11
I just tried to do a full removal of network-manager.  After reinstalling all my settings were still there.  I'm not sure how to fully reset network-manager.  The following didn't work

sudo apt-get remove --purge network-manager

---

### Post by jdb on 2011-02-11
> **rokstar said:**
> I just tried to do a full removal of network-manager.  After reinstalling all my settings were still there.  I'm not sure how to fully reset network-manager.  The following didn't work

sudo apt-get remove --purge network-manager

Try WICD, for me it's always worked a lot better than network manager.

After you install it & reboot you should be able to purge net manager.

I think gnome likes to have one or the other installed & doesn't care which.

jdb

---

### Post by rokstar on 2011-02-12
I had the same issue with WICD.  It did not see the ETH0 interface.  So it was unable to connect.  Its almost like my user account has no access to the eth0 interface.

---

### Post by rokstar on 2011-02-12
I came across this somewhere.  Someone was asked to run this..

sudo lshw -c network

PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:af:7e:f6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-25-generic firmware=8.24.2.12 ip=192.168.1.108 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:f8500000-f8501fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:06:00.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list
       configuration: latency=0
       resources: memory:f8600000-f8603fff ioport:3400(size=128) ioport:3000(size=256)

It shows my Ethernet controller as UNCLAIMED.  I'm not sure what that means.  Can anyone lend a helping hand?

---

### Post by rokstar on 2011-02-12
After some time to really think about what was going on I finally got eth0 to come up.

On the upgrade to maverick I had problems with the jme module.  I had to unload and restore it and reinstall it...you can see the full details here if you like:

[http://ubuntuforums.org/showthread.php?t=1601165](http://ubuntuforums.org/showthread.php?t=1601165)

I checked my /etc/modules file and found out that the jme was never reloaded after I got the upgrade completed.

So after adding jme to /etc/modules eth0 now loads properly on startup.

I also had to modify /etc/NetworkManager/nm-system-settings.conf to get network-manager to manage the device correctly

I changed:

[ifupdown]
managed=false

to:

[ifupdown]
managed=true

So now everything is working again.  The upgrade from 10.04 to 10.10 could have gone much more smoothly.  I'm hoping the transition from 10.10 to 11.04 will be much better in a couple of months.

Thanks everyone for your help!!!

---

