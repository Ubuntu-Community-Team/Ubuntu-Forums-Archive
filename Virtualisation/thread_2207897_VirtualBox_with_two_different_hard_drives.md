---
title: "VirtualBox with two different hard drives"
date: 2014-02-25
forum: Virtualisation
---

### Post by nosto53 on 2014-02-25
Patient: 2008 Dell Studio 17", Intel T9600 2.8GHz CPU, 4GB DDR2 Ram,
SSD: PlextorM5Pro 128GB MLC, SuperSpeed 64GB SLC, OS:Ubuntu 12.04LTS

I have seen a few guides for installing VirtualBox.  One said: Start with a Windows OS (host), install VBox, and then install Ubuntu as 'guest'. OK.....
I am thinking(ha!) of using a 'old' version of Windows 7(not ask...) as the 'host' on my 128GB SSD and the Ubuntu as 'guest' on the 64GB SSD. 
(These SSD are SMALL, but I not need music/pictures/videos/gameing; only playing with the laptop with some 'old' C/C++ apps devs.)

I have done a few dual-boot with Windows/Ubuntu (desktop) and needed to 'reboot' each time to see the other OS.  The VBox will (I hope) yet me 
use either OS at the same time. 

Question: Will using the 2 different SSD work?  Any suggestions?

Thanks!
RickO

---

### Post by varunendra on 2014-02-25
Why do you want to use a physical hard disk in the first place? Just create a virtual hard disk file on any of the drives and you should be fine.

I don't think you'll have any performance gains by using the physical hard disk. On the other hand, it would only add complexity and may risk the data on the disk if not used properly.

Answering your original question, I don't have personal experience with SSDs, but I believe it should definitely work. But like I mentioned above, it is not necessary to use any of the physical drives and will only add complexity.

---

### Post by QIII on 2014-02-25
Hello!

The advantage to putting your virtual drives for your guests on a different drive from the one your host OS is running on is that you avoid read/write conflicts between the host and guest - if both are trying to write at the same time on the same drive, for instance, you'll get a delay on one while it waits for the other to get finished.  

SSDs are so fast that you might not notice any delay by having your virtual disk on the same drive, but it wouldn't hurt to have them on separate drives.

But don't commit an entire drive to a guest.  I make my guest drives about 50Gb and set up a shared folder for saving stuff to.

---

### Post by varunendra on 2014-02-25
> **QIII said:**
> The advantage to putting your virtual drives for your guests on a different drive from the one your host OS is running on is that you avoid read/write conflicts between the host and guest - if both are trying to write at the same time on the same drive

Oh, yeah, that's a definite advantage and a very significant one. I was too focused on physical vs virtual factor.

+1 to keeping the virtual disk on the separate partition (the 64 GB one as per your plan), but don't commit the physical disk to the VM, unless you are doing this for learning purpose and have your data on that drive (if any) backed up.

Creating a virtual disk is much simpler and 100% safe.

---

