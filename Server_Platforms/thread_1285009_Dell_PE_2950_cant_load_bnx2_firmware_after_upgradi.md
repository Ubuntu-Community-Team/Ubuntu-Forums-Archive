---
title: "Dell PE 2950 cant load bnx2 firmware after upgrading the kernel"
date: 2009-10-07
forum: Server Platforms
---

### Post by b4tn on 2009-10-07
[FONT=UniversLTStd-LightCn][SIZE=1][FONT=UniversLTStd-LightCn][SIZE=1][COLOR=black][FONT=UniversLTStd-LightCn][SIZE=2]I am running Ubuntu 9.04 server and in order to fix a security vulnerability I need to upgrade the Kernel to 2.6.30.5. I have been through the process so many times and everything seems to be successful except that it cant load the bnx2 firmware for the [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=UniversLTStd-LightCn][SIZE=2]NetXtreme II 5708 NIC's and Apparmor fails to load. Since it looses all connectivity I cant apt-get drivers but I did copy the firmware-bnx2_0.18_all.deb package locally and ran dpkg -i. It appears to install but on reboot I get the same failure. I am very new to Linux and I am at my wits end here! Any ideas?[/SIZE][/FONT][/COLOR]
[/SIZE][/FONT][/SIZE][/FONT][FONT=UniversLTStd-LightCn][SIZE=1]
[/SIZE][/FONT]

---

### Post by LowSky on 2009-10-07
what process did you use to upgrade the Kernel?

---

### Post by b4tn on 2009-10-07
I have used two different methods.  The first was using pre compiled kernel images.  The second was customizing the kernel using the method here [http://ubuntuforums.org/showthread.php?t=311158&highlight=xconfig](http://ubuntuforums.org/showthread.php?t=311158&highlight=xconfig)

---

### Post by LowSky on 2009-10-07
Boot up and use grub to boot to working kernel, usually the one prior to the current non working one.

try running this command to update your system

```
sudo apt-get update && sudo apt-get upgrade
```


File a bug with Launchpad.net, if you still have errors using the newer kernel
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by b4tn on 2009-10-07
I was thinking about trying that but wasnt sure if it only upgrades the kernal you are booted in or any kernal that is in the grub menu. I assume it upgrades all?

---

### Post by b4tn on 2009-10-07
[COLOR=black][FONT=Verdana]Well I found this article

[[COLOR=#444444]http://www.ducea.com/2009/03/02/debi...x2-annoyances/[/COLOR]]("http://www.ducea.com/2009/03/02/debian-lenny-pxe-installation-on-dell-poweredge-19502950-servers-bnx2-annoyances/")

it basically says that the bnx2 firmware and is not included in the kernel because of licensing issues.

The page gives instructions for modifying the initrd.gz file by adding the downloaded firmware. I "think" that the initrd.gz file for Ubuntu 9.04 is actually initrd.-img-2.6.30.5-mk. I did the above process using that file instead and the server wouldn&#8217;t start anymore :) Any tips would be appreciated. I'm a gluten for punishment so I am going to try again.[/FONT][/COLOR]

---

### Post by b4tn on 2009-10-07
Well, I attempted to add **lib/firmware/bnx2-06-4.0.5.fw** , **bnx2-09-4.0.5.fw** and **bnx2/usr/share/initramfs-tools/hooks/firmware_bnx2** to [COLOR=black][FONT=Verdana]initrd.-img-2.6.30.5-mk using the above link and ended up getting a kernel panic.  I reverted to a backed up copy of [/FONT][/COLOR][COLOR=black][FONT=Verdana]initrd.-img-2.6.30.5-mk and it boots again but still cant find the bnx2 firmware. 

If anyone can tell me how to successfully modify [/FONT][/COLOR][COLOR=black][FONT=Verdana]/boot/initrd.-img-2.6.30.5-mk with the bnx2 firmware files without hosing the initrd file it would be great.  

This is for a snort box and I have spent 3 days on it already if I cant get this resolved I am going to have to go with a winblows application instead.  As much as I hate giving up I have several other projects that need working.  
[/FONT][/COLOR][COLOR=black][FONT=Verdana] [/FONT][/COLOR]

---

### Post by b4tn on 2009-10-09
Just incase someone else wants to do this on a Dell PE2950 I want to post the fix. I was getting the following firmware error
 
Cant load firmware file "bnx2/bnx2.mips-06-4.6.16.fw" 
 
It would then boot but with no network cards. I booted into the old kernel and and downloaded the broadcom 5708 drivers from broadcom. I then booted back into the new kernel and and did a make and make install after unzipping the drivers. Once they where installed I switched to /lib/modules/your kernel version/drivers/net and did sudo rmmod bnx2 then sudo insmod bnx2.ko.
 
This started the network drivers so I could do sudo apt-get install firmware-bnx2. after reboot everything loaded just fine.

---

