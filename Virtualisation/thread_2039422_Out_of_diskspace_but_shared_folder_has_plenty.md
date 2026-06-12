---
title: "Out of diskspace but shared folder has plenty"
date: 2012-08-08
forum: Virtualisation
---

### Post by TRiCiDE on 2012-08-08
Win 7 Host
Ubuntu Guest

So, I have been getting low disk warnings. I set the box up for 8gb and I download torrents. I set it up small so I could download to another drive that has alot of space. I mount a shared folder on the big drive and it goes to the shared folder. Im new to all this and Linux. the shared folder name is share because the commands someone showed me was to "mkdir mnt/share" and combine the sf_downloads to it. For some reason I am thinking im accually putting the new files on my box's 8gb because of this. Is there a way to put share sf_downloads cause I can't access it even when this is mounted, but I can see contents through the /mnt/share directory. Any help would be awesome. i'd really like to keep the 8gb for the OS and put ALL files on the shared folder on the other drive that win7 uses.

---

### Post by Bucky Ball on 2012-08-08
Ok. You have the /share directory in /mnt? Open /mnt and make sure.

Now, if your other drive is, say, sdb3, then:

```
sudo mount /dev/sdb3 /mnt/share
```Now if you look in mount, the /share directory should have your other drive mounted on it. Think of it like this: There is nothing in /share until you mount something to it. I acts as a holder only; a mount point for something else to be mounted to. ;)
 
Of course, once you reboot sdb3 will no longer be mounted and you need to do it manually again unless you change the /etc/fstab file, which we can show you how to do if the manual mount works.

PS: To find all your info, either use Gparted (partition editor) to have a look or you can use the terminal and:

```
sudo blkid
```

---

### Post by TRiCiDE on 2012-08-08
> **Bucky Ball said:**
> Ok. You have the /share directory in /mnt? Open /mnt and make sure.

Now, if your other drive is, say, sdb3, then:

```
sudo mount /dev/sdb3 /mnt/share
```Now if you look in mount, the /share directory should have your other drive mounted on it. Think of it like this: There is nothing in /share until you mount something to it. I acts as a holder only; a mount point for something else to be mounted to. ;)
 
Of course, once you reboot sdb3 will no longer be mounted and you need to do it manually again unless you change the /etc/fstab file, which we can show you how to do if the manual mount works.

PS: To find all your info, either use Gparted (partition editor) to have a look or you can use the terminal and:

```
sudo blkid
```

/dev/sda1: UUID="b354a321-2b92-4372-9dde-bb1223dee278" TYPE="ext4" 
/dev/sda5: UUID="1b99d159-b93c-4645-bc1b-4bec4ae57933" TYPE="swap"
Grabbed Gparted. I see more options. sda2 says is an extended file system 1 TB I am trying this but when I hit the command to mount it. The cursor stops and when I try to close the terminal it says there is a process still loading..

---

### Post by Bucky Ball on 2012-08-08
Got ya. I think. If it is just an extended partition then there is nothing there. That is like a holder for, theoretically, as many logical partitions/drives as your hardware can handle. Reason for extendeds? Physical hard drive can only have four primary partitions (in the common scenario).

So, I think you need to create some logical partitions in the extended partition. You have a Tb there so have a think before leaping. 

Open Gparted and you should see that extended partition. Right click on it and create a logical partition/drive in there or whatever your plan dictates. Make sure you assign a mount point for the partition (name). This can be anything you like. (/music /torrents /vids)

Once you've done all this, reboot and the new logical partitions should be mounted and available.

---

### Post by TRiCiDE on 2012-08-09
> **Bucky Ball said:**
> Got ya. I think. If it is just an extended partition then there is nothing there. That is like a holder for, theoretically, as many logical partitions/drives as your hardware can handle. Reason for extendeds? Physical hard drive can only have four primary partitions (in the common scenario).

So, I think you need to create some logical partitions in the extended partition. You have a Tb there so have a think before leaping. 

Open Gparted and you should see that extended partition. Right click on it and create a logical partition/drive in there or whatever your plan dictates. Make sure you assign a mount point for the partition (name). This can be anything you like. (/music /torrents /vids)

Once you've done all this, reboot and the new logical partitions should be mounted and available.

I decided to create a new virtualbox with plenty of room.  Thanks for the help!

---

