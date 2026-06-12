---
title: "Aptitude Update Breaking Hyper-V Virtual NIC Driver"
date: 2010-08-17
forum: Virtualisation
---

### Post by aarmenaa on 2010-08-17
I have a fresh install of Ubuntu Server 10.04 in a Hyper-V VM.  I have made the following changes to enable the kernel drivers for the virtual devices:

Added in /etc/initramfs-tools/modules```
hv_vmbus
hv_storvsc
hv_blkvsc
hv_netvsc
```

Updating initramfs image:```
sudo update-initramfs –u
```

Added in /etc/network/interfaces```
Auto seth0
iface seth0 inet dhcp
```

This works, until I go to update my install:```
sudo aptitude update
sudo aptitude upgrade
```

The virtual network controller is gone when I reboot after grabbing updates.  I have attempted updating initramfs again after performing updates, but that doesn't seem to help.  I note that the kernel has been altered (2.6.32-21-server REMOVED, 2.6.32-24-server NEW); is there a changelog I can look at to see what what changed?  Has anyone else had success with this?

---

### Post by GrumpyBum on 2010-08-17
Hello, I have had this same issue the first time I installed Ubuntu 9.10 as a Hyper-V guest.
I found that after every update for the OS I had to reinstall the Microsoft tool pack for Ubuntu.

The only solution I have at this time is to re-configure the VM to use a **Hyper-V Legacy Network Adapter**. This has worked for me and updates are not affecting this.
I have even reinstalled and updated again to confirm this had resolved the issue.

If anyone has resolved this without using the Hyper-V Legacy Network Adapter, then I will be interested in the solution as well.

---

### Post by aarmenaa on 2010-08-17
> **GrumpyBum said:**
> Hello, I have had this same issue the first time I installed Ubuntu 9.10 as a Hyper-V guest.
I found that after every update for the OS I had to reinstall the Microsoft tool pack for Ubuntu.

The only solution I have at this time is to re-configure the VM to use a **Hyper-V Legacy Network Adapter**. This has worked for me and updates are not affecting this.
I have even reinstalled and updated again to confirm this had resolved the issue.

If anyone has resolved this without using the Hyper-V Legacy Network Adapter, then I will be interested in the solution as well.

Kernels 2.6.28 and later have drivers for the high performance synthetic NIC and SCSI driver, so you don't need to install the tools from Microsoft's ISO, though you do need to perform the steps I outlined above to make them work.  I actually have the high performance synthetic NIC working, as long as I don't update!

---

### Post by GrumpyBum on 2010-08-17
> **aarmenaa said:**
> I actually have the high performance synthetic NIC working, as long as I don't update!

Hi aarmenaa, as noted in my post, I was in the same situation, just letting you know how I got this to work long term without constant admin work.

---

### Post by sh1ny on 2010-08-18
So, this doesn't work if you just add those modules to /etc/modules ?

---

### Post by ascendo on 2010-08-22
Same problem here - update to 2.6.32-24 broke seth0 for me as well. Booting into 2.6.32-21 has temporarily fixed the problem.
 
How does one go about reporting this to get it fixed?

---

### Post by ascendo on 2010-08-23
Solution found! I have tested this on both 2.6.32-24 (10.04) and 2.6.35 (10.10 Alpha).
 
After updating (and therefore breaking) your install:
 
1) open /etc/udev/rules.d/70-persistent-net.rules in VI and comment out ALL the lines.
 
2) reboot
 
3) open /etc/udev/rules.d/70-persistent-net.rules in VI and find the newly (auto) created entry. Change 'NAME="eth0"' to 'NAME="seth0"'. 
 
4) reboot
 
Networking should now be working again.

---

### Post by microbolt on 2010-09-22
> **ascendo said:**
> Solution found! I have tested this on both 2.6.32-24 (10.04) and 2.6.35 (10.10 Alpha).
 
After updating (and therefore breaking) your install:
 
1) open /etc/udev/rules.d/70-persistent-net.rules in VI and comment out ALL the lines.
 
2) reboot
 
3) open /etc/udev/rules.d/70-persistent-net.rules in VI and find the newly (auto) created entry. Change 'NAME="eth0"' to 'NAME="seth0"'. 
 
4) reboot
 
Networking should now be working again.

I know this post is a little old but just wanted to let anyone with this same issue know that it does in-fact fix the issue!  I'm running the 10.10 beta and this got the native Hyper-V nic working perfect!  Thanks for your help!!!

---

### Post by BakaNeko59 on 2010-10-14
I had similar problems and had to use a combination of the solution above and a couple others - see the thread at [http://ubuntuforums.org/showthread.php?t=1589339](http://ubuntuforums.org/showthread.php?t=1589339).

---

