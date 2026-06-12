---
title: "No wifi after the Linux image 3.8.0-25-lowlatency update"
date: 2013-06-14
forum: Ubuntu Studio
---

### Post by Acepony on 2013-06-14
I thought I would try doing what I did when I had no wifi after installing the 13.04 but that did not work this time.

Terminal output of attempt

> octavian@octavian-Inspiron-1545:~$ sudo apt-get install linux-headers-generic
[sudo] password for octavian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  hyphen-en-us linux-headers-3.8.0-19-lowlatency
  linux-image-3.8.0-19-lowlatency linux-lowlatency-headers-3.8.0-19
  mythes-en-au openoffice.org-hyphenation sword-comm-mhcc sword-comm-pers
  sword-dict-naves sword-language-pack-en
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
octavian@octavian-Inspiron-1545:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
The following packages were automatically installed and are no longer required:
  hyphen-en-us linux-headers-3.8.0-19-lowlatency
  linux-image-3.8.0-19-lowlatency linux-lowlatency-headers-3.8.0-19
  mythes-en-au openoffice.org-hyphenation sword-comm-mhcc sword-comm-pers
  sword-dict-naves sword-language-pack-en
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
octavian@octavian-Inspiron-1545:~$ sudo modprobe wl
FATAL: Module wl not found.
octavian@octavian-Inspiron-1545:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
The following packages were automatically installed and are no longer required:
  hyphen-en-us linux-headers-3.8.0-19-lowlatency
  linux-image-3.8.0-19-lowlatency linux-lowlatency-headers-3.8.0-19
  mythes-en-au openoffice.org-hyphenation sword-comm-mhcc sword-comm-pers
  sword-dict-naves sword-language-pack-en
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
octavian@octavian-Inspiron-1545:~$ sudo modprobe wl
FATAL: Module wl not found.
octavian@octavian-Inspiron-1545:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

octavian@octavian-Inspiron-1545:~$ rfkill list all
octavian@octavian-Inspiron-1545:~$ 


Terminal output for lspci

> octavian@octavian-Inspiron-1545:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
octavian@octavian-Inspiron-1545:~$ 


---

### Post by Mr. Kaschei on 2013-06-14
Same problem here.

---

### Post by Acepony on 2013-06-15
Ok there is two of us with this problem. May I ask if we can get some help. We have been waiting. I know it is the week end but I would really apreciate it if we could get an answer. I am very grateful of what you guys have helped me with so far. It is wthe week end and tommarow is fathers day so I understand. Yea I am very grateful that you help us begginers.

---

### Post by mkeuter on 2013-06-20
Looks like I have the same issue. It's related to [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1156138](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1156138), and the issue is the wl module not building for pre-emptive kernels, like the ubuntustudio lowlatency kernel. I've got no idea why a preemptive setting on your kernel build would affect a module like wl and not on a non-preemtive kernel build, I guess we'll just have to be patient 'till some figures it out.

---

### Post by mkeuter on 2013-06-22
Workaround: Booting in generic kernel and doing a "sudo dpkg-reconfigure bcmwl-kernel-source" does work and I have wireless again, but only when I boot in the generic kernel. 

*OT: I'm now considering switching to a non-preemptive distribution, but probably not standard Ubuntu. I switched to Ubuntustudio because the audio setup is much cleaner than the generic ubuntu and it does not default to Unity. *

---

### Post by slippycurb on 2013-06-22
you will probably have to compile your own driver......try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
it was pointed to me by someone else..........when you have it compiled and installed it wont run automatically, you will have to "sudo modprobe b43" eg.....(this is for an onboard bcm wifi card, yours looks similar to mine if not the same one)

---

### Post by mkeuter on 2013-06-22
Ok, but I guess that will break every time an update to the kernel comes along?

---

### Post by slippycurb on 2013-06-22
i dont think it does, it didnt for me last time, but dont quote me on that.

---

### Post by dundundund dun da dun on 2013-06-23
I have the same problem and have been using the quantal package 5.100.82.38... with success on the newest kernels (on 3.8.0-25 atm):

[http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)

At this stage the lazy amongst us should probably just choose to either stick with an older kernel paired with the newer wl driver or go to a newer kernel with the older driver. Probably best not to update the kernel too much in the latter case though... Personally I went for new kernel and old driver because the new kernel made my laptop much more stable and reliable so it's worth it for me... I also need the low latency kernel as my computer is unable to keep up otherwise.

I really dislike this wireless card (bcm4313) and its terrible linux drivers.

---

### Post by Acepony on 2013-06-24
Perhaps this is a step in the right direction. Is there any way to use a wifi adapter? You may not be able to install a new card but a wifi usb adapter is worth trying.

So far I hit a brick wall with it. I looked on the ubuntu forums to find an anwser and it looks like other people are having the same problem. The networks will show up but it will keep asking for a password. I found this USB wifi burried in my computer stuff; 802.11 b/g/n
Terminal output calls it;  Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter

It will show networks but will ask you for the password until you give up. rfkill has no block.

Can some one point me in the right direction?

---

### Post by slippycurb on 2013-06-24
[http://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card](http://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card)
[http://alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/](http://alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/)

a few links i found on google,,,,the second one looks promising,,,read the comments at the bottom too, it might help with the password generation....

---

### Post by slippycurb on 2013-06-24
[http://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card](http://askubuntu.com/questions/168032/how-to-disable-built-in-wifi-and-use-only-usb-wifi-card)
[http://alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/](http://alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/)
a few links i found on google...the second one looks promising,,,,read the comments too as some of refers too password generation

sorry double posting....

---

