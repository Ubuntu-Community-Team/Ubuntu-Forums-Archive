---
title: "Virtual Machine - Resize/Move option is not enable on root partition"
date: 2014-05-17
forum: Virtualisation
---

### Post by indi on 2014-05-17
Hi,

I am very much new to Ubuntu. Ubuntu is running on VMware palyer. I want to increase the size of root partition and I used gparted for it. 

But unfortunately Resize/Move option is not enable on root partition.

This was enable once at the very beginning. But I had swap and extended partition in between unallocated space. So I could resize (drag) a littile. So I cancel that operation. Afterward resize/move option did not enabled on root partition.

Then I swap off swap partition and removed those partition. Still resize/move option not enabled on root partition.

I have attach here a screen shot.

Please help how to increase root partition here.
Thank you!
Indi

---

### Post by sammiev on 2014-05-17
> **indi said:**
> Hi,

I am very much new to Ubuntu. Ubuntu is running on VMware palyer. I want to increase the size of root partition and I used gparted for it. 

But unfortunately Resize/Move option is not enable on root partition.

This was enable once at the very beginning. But I had swap and extended partition in between unallocated space. So I could resize (drag) a littile. So I cancel that operation. Afterward resize/move option did not enabled on root partition.

Then I swap off swap partition and removed those partition. Still resize/move option not enabled on root partition.

I have attach here a screen shot.

Please help how to increase root partition here.
Thank you!
Indi

You would need to make a bootable USB/DVD with GParted and boot from it. Before making any changes you should make a backup.

---

### Post by coldcritter64 on 2014-05-17
The root partition is showing a key on it in your gparted screenshot (it is in use). As sammiev notes, make a backup of your data before altering partitions. A live cd/dvd image of Ubuntu also comes with gparted installed or use a live cd version from gparted itself to do the changes. 

You can't alter any partition that is in use by a system while it is being used (hence the key symbol in your picture, meaning your partition has been locked).

---

### Post by monkeybrain20122 on 2014-05-17
To put it in plain language, you cannot alter a partition when it is mounted, you cannot unmount a partition when it is in use. You are now using the partition as you are running gparted from it so it cannot be modified. 

So to modify it you have to run gparted from another device/partition to alter this one, say you have a liveusb with gparted in it or have another Linux installed in a different partition (i.e dualboot)

---

### Post by indi on 2014-05-18
Hi,

Thank you very much for quick responses. I followed below steps to overcome the issue but ended up with no success.

I run Ubuntu 12.04 on VMWare Player.

I tired to boot from USB, but finally I understood USB boot is not supported by VMWare Player. (I have to install additional tools and run ubuntu VM on it)

Next I tried to boot from gParted live cd, but failed to do it also.
 In VMWare Virtual machine settings I map gParted .iso file to CD/DVD IDE and enable connect at power on
 I changed boot order to "CD.."

But still my Ubuntu virtual machine boot from Hard disk, it never goes to gParted Live cd. 
I restarted so many times but result is same. When booting CD icon on VM player is blinking and it is connected.

Please help to solve this.

Thank you!
Indi

---

### Post by monkeybrain20122 on 2014-05-18
I don't know about vmware player, as I don't use it. But in Virtualbox you can boot from a gparted iso or any live iso with gparted by simply attaching the media in the VM and adjust the boot order to boot from CD. Then you can resize the partition just like for real machine.

What is the advantage of Vmware player over virtualbox?

---

### Post by indi on 2014-05-18
I just install in VMWare Player without thinking twice about the advantages. I think it is better to use VirtualBox as it let disk space grow dynamically too.. :)

Any way I have installed tools on ubuntu running on VMWarePaly, so I give my last try to port it to virtualbox.. otherwise I have to do from the scratch :(

---

### Post by monkeybrain20122 on 2014-05-18
Actually the disk space doesn't grow dynamically, that sorts of depends on what you call "disk space". It allows the vd to grow dynamically until it hits the pre-allocated disk size, at which point it doesn't grow anymore. Otherwise I wouldn't have to use gparted on the VM and wouldn't have found out that it works just like a real machine. :)

---

### Post by indi on 2014-05-18
Ohh thank you! I thought virtual disk space grow as far as it can consume actual free space of real hard disk. Thank you for clarification. I am totally new to these subject.

---

### Post by Elfy on 2014-05-18
> **monkeybrain20122 said:**
> Actually the disk space doesn't grow dynamically, that sorts of depends on what you call "disk space". It allows the vd to grow dynamically until it hits the pre-allocated disk size, at which point it doesn't grow anymore. Otherwise I wouldn't have to use gparted on the VM and wouldn't have found out that it works just like a real machine. :)

What I've done in the past is 

VBoxManage modifyhd /path/to/vdi --resize 20000

would resize to 20GB (ish)

Boot the vbox machine you are intending to resize with a gparted iso mounted in the vbox cd drive.

Then you can resize the partition to the new size.

( @monkeybrain20122  - I assume that's what you were alluding to - just putting more information in the thread for someone to find later)

Editing thread title

---

### Post by Elfy on 2014-05-18
*Thread moved to **Virtualisation**.*

---

