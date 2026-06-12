---
title: "Uable to boot the VM"
date: 2017-04-19
forum: Virtualisation
---

### Post by satimis on 2017-04-19
Hi all,

Host    Ubuntu 16.04.1 LTS
Guest-VM	Ubuntu 14.04.1 LTS
VirtualBox

Ran;```

sudo do-release-upgrade

```

It went through without problem at start, but freezing in mid of the process.  I was compelled to click;
-> Close Virtual Mahine -> Power off the machine

However on re-starting Guest-VM it popup a black screen.

Then boot again -> F12
It popup```

VirtualBox temporary boot device selection
Detected Hard disks:

ANCI controller"
1) Hard disk

Other boot devices:
f) Floppy
c) CD-ROM
l) LAN
b) Continue booting

```

Please advise how to boot the Guest-VM.  Thanks in advance

Regards
satimis

---

### Post by ajgreeny on 2017-04-19
You should have tried to run the Shutdown command rather than the Power-off when your VM froze, and you may have tried to do so, but nothing happened.

However as you did a hard shutdown it is possible that there is some filesystem corruption, so you may need to attach a live Ubuntu iso image to your VM using the main VBox window, then press F12 when you boot that VM and choose to run the live system, not the hard disk.

From that live system you should be able to run ```
sudo e2fsck /dev/sda1
``` assuming sda1 is the root partition of your VM, to see if it reports any filesystem problems which you can correct.

---

### Post by satimis on 2017-04-19
> **ajgreeny said:**
> You should have tried to run the Shutdown command rather than the Power-off when your VM froze, and you may have tried to do so, but nothing happened.

Hi,

Thanks for your advice.

This box has been running at least 4 years

CPU - AMD 8 Cores
RAM - 32G
HD - SSD 1TB

with at least >30 VMs running.  In recently 2 days I have upgraded about 12 VMs to Ubuntu 16.04 from 14.04.  It is because there are some software running on them otherwise I prefer fresh installation.

All upgrade went through without problem except 2 of them with the problem reported on the original posting.  The upgrade was freezing.  I have no way starting another terminal to run the shutdown command and was compelled to run Power-off 

> 
However as you did a hard shutdown it is possible that there is some filesystem corruption, so you may need to attach a live Ubuntu iso image to your VM using the main VBox window, then press F12 when you boot that VM and choose to run the live system, not the hard disk.

From that live system you should be able to run ```
sudo e2fsck /dev/sda1
``` assuming sda1 is the root partition of your VM, to see if it reports any filesystem problems which you can correct.
I have no idea whether the drive is /dev/sda1 how to find it?

Thanks

Regards
satimis

---

### Post by ajgreeny on 2017-04-19
Once you have inserted the live Ubuntu iso into the virtual disk and booted to it run ```
sudo parted -l
``` in terminal and it will show you all the partitions in that virtual disk.

You should be able to figure out from that which is the root partition of your virtual OS, which if you did not manually partition when installing the virtual OS, will probably be sda1.

---

### Post by satimis on 2017-04-19
> **ajgreeny said:**
> Once you have inserted the live Ubuntu iso into the virtual disk and booted to it run ```
sudo parted -l
``` in terminal and it will show you all the partitions in that virtual disk.

You should be able to figure out from that which is the root partition of your virtual OS, which if you did not manually partition when installing the virtual OS, will probably be sda1.
Performed following steps

1) Attach ubuntu-16.04.2-desktop-amd64.iso to the VM as Live-CD
2) Boot to Run Ubuntu 16.04
3) Run following command on terminal
sudo parted -l```

.......
Disk  /dev/sda"  21.5GB
.......
Number ... Type     File system  Flags
1          primary  ext4         boot
.....

```

4) Then run
sudo e2fsck /dev/sda1```

e2fsck 1.42.13 (17-May-2015)
/dev/sda1 clean, 235068/1179648 files, 1897433 blocks

```

5) Remove Live-CD and reboot
Still popup to a black screen

satimis

---

