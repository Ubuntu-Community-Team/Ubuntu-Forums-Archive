---
title: "hard drive partition issue - no space available"
date: 2009-04-25
forum: Server Platforms
---

### Post by mwylie on 2009-04-25
Hello,

This is my first post here and I tried to find others who have had similar problems, but didn't know how to word my question because of my "newness" to linux.  

**Setup:**
OS: Ubuntu Server Edition 8.11
Purpose: File Server
HD: 650GB SATA
CPU: Intel Core 2 Duo
RAM: 6GB (only shows as 2GB)
Applications: Samba File Server


**Environment:**
4 XP Pro laptops
1 Ubuntu File Server



**Problem:**
We have about 1.9GB of documents and spread sheets on a shared folder on the server.  I just tried to put my printer drivers on the server as well (400MB) and I got an error saying there was not enough free space on the server.  I find this hard to believe being that I have a 650GB hard drive.  This leads me to believe that I made a mistake when I used the guided partition during the Ubuntu install.  


**Additional Information:**
I used the command "df-H" and "fdisk -l", but I am not sure what to do after that.  I can see that my /dev/sda6 is where the data is being stored and it is only 2.2GB.  
****Please see attachments for results****



**Ideal Solution:**
I would like to use at least 300GB of my hard drive to store data such as presentations, spreadsheets, PDFs, and word documents. 


Thank you for your time and I look forward to your expert suggestions.
-Mike

---

### Post by bluefrog on 2009-04-26
you have 2 swaps. one too much to begin with.

all space (or almost) was allocated to / (sda1)

Redesign the partitions and use LVM so that in the future it will be very easy to extend a partition (see ubuntu server guide - LVM)

---

### Post by BkkBonanza on 2009-04-26
You have /dev/sda6 being mounted on /. And /dev/sda1 is where all your space is.
You should mount /dev/sda1 somewhere and copy all the files from / over to that mount. Then change the mount to put /dev/sda1 on /.

Alternatively and perhaps better you could mount /dev/sda1 somewhere and copy all your /home/* to that place and then alter your boot / fstab file to mount /dev/sda1 on /home instead. 

The simplest config is one big drive on /. But the places where space are often needed are /home, /var, /tmp. So sometimes people partition the drive to place big spaces on those mount points. While one big root is easy the advantage to limiting some mounts like /tmp or /var is that big allocations there won't interfere and cause out-of-disk errors on other mounts. 

You can mount the partition this way,

[B]sudo mkdir /mnt/test
sudo mount /dev/sda1 /mnt/test[/B]
(where test is just an arbitrary name)

If you do that then you can copy the files like this,

**sudo cp -aR /home/* /mnt/test**

and add a line to fstab to mount it on bootup as /home. See **man fstab**.

With that size drive it makes sense to use gparted to split the big partition into a second one to use for /var. Even 2.2GB for root is pretty small. That's why I thought you may be better to start over as this will involve a bunch of fixing.

Apparently there is no advantage to using a swap partition now so it's likely more flexible to just use a large swap file within one of the large partitions instead. There's tutorials around for that.

I would suggest more reading before tackling this as typing in commands given here is not foolproof - I can't see your system and don't know exactly what you need.

---

### Post by mwylie on 2009-04-26
Thank you both for your time.  I wanted to make sure it was possible to correct the problem without reformatting.  I will do some reading, thank you.

---

