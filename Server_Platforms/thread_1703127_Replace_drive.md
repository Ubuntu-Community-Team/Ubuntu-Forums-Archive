---
title: "Replace drive?"
date: 2011-03-08
forum: Server Platforms
---

### Post by Cfhs_1 on 2011-03-08
Hello everyone, I have a data server running ubuntu 10.04 LTS, and it has two HDD's in it. One is a 20GB Drive used for the OS files, etc. The other drive is a 200GB drive for data. The data drive is almost full, only about 5GB free, and I want to swap it for a larger 1TB drive. My question is would it be possible to format the new drive to ext3 (same as old drive) and simply copy everything from the old drive to the new one via a live CD then simply plug the new drive into the old drive's IDE cable. Would the OS simply see it as the same drive, or would I have to go through the trouble of completely setting up the new drive with the server, user profiles ETC. What would be the easiest way to do this? I'm lost, any help would be appreciated. Sorry if I confused you with any of this.

---

### Post by BkkBonanza on 2011-03-08
If you can physically mount the new drive on the system at the same time as the old drive, then do that. Format it and copy all the data files from the old drive (not including your OS which I presume is on the 20GB drive).

eg. if the old drive is mounted at /home and the new one at /mnt then this should work,

rsync -arp /home/* /mnt/

Once done, **umount** the old drive and edit the /etc/fstab file to mount the new drive in the same place as the old one was previously mounted. If this is done using UUIDs then you may need to determine the correct UUID for the correct mount location.

You can see current active UUIDs using **dir /dev/disk/by-uuid/**. Make sure the /etc/fstab file mounts the new UUID in the place you want. Then reboot to test it comes up correctly. 

Once it is working you can power down and remove the old drive. Or just edit /etc/fstab to mount it at another location and continue using it as a backup or for other data.

For a data drive there is no special system needs. If you want to replace the OS drive then you need to take a few extra steps to ensure it will boot correctly.

If you need exact steps for your system then post details of where drives mount (eg. /home) and device names (/dev/sdb1) and I can post commands.

---

### Post by tgalati4 on 2011-03-08
Assuming the new drive is sdc:

sudo cp /dev/sdb /dev/sdc

sudo gparted

Recapture the unused space on the rest of the drive.

man blkid

You need to get the UUID of the drive so you can modify your grub configuration file--which is probably not needed since it's not a boot drive, but you will need to modify your /etc/fstab.

---

### Post by Cfhs_1 on 2011-03-08
Thanks for your prompt replies guys, I appreciate all of the help. I came across a program called Clonezilla in my research of this issue. Could I just simply clone the data drive to the new drive, then plug and play, or would I still have to edit /etc/fstab? I don't believe I used drive uuid's when I set the server up, It's been about a year ago since I did it, because I only have two drives using uuid to specify drives seemed like overkill to me.

---

### Post by BkkBonanza on 2011-03-08
You'll probably have to edit /etc/fstab - but it's been a few years since I used clonezilla and I don't recall exactly how much it takes care of for you. The default install uses UUIDs. 

You can tell easily with **cat /etc/fstab**. If it has long drive ids with (seemingly) random values then uuids are being used. If it just has lines like /dev/sdb1 /home... then it's just device names. UUIDs are better since they make sure a specific drive mounts consistently in cases where a device name may change when a new drive is added.

Either way is a simple edit. Just copy the line, comment out the old one, and modify the new one to have correct UUID or device name.

Here's a typical line from mine, (the # line is just a comment added during install saying what the device name was during install)

```
# /dev/sda2
UUID=f651eaca-f066-4767-ac88-057c2aa2f381 /media	ext3	defaults	0 0
```

---

### Post by Cfhs_1 on 2011-03-08
> **BkkBonanza said:**
> You'll probably have to edit /etc/fstab - but it's been a few years since I used clonezilla and I don't recall exactly how much it takes care of for you. The default install uses UUIDs. 

You can tell easily with **cat /etc/fstab**. If it has long drive ids with (seemingly) random values then uuids are being used. If it just has lines like /dev/sdb1 /home... then it's just device names. UUIDs are better since they make sure a specific drive mounts consistently in cases where a device name may change when a new drive is added.

Either way is a simple edit. Just copy the line, comment out the old one, and modify the new one to have correct UUID or device name.

Here's a typical line from mine, (the # line is just a comment added during install saying what the device name was during install)

```
# /dev/sda2
UUID=f651eaca-f066-4767-ac88-057c2aa2f381 /media	ext3	defaults	0 0
```

alright, turns out I am using UUID, but if all I have to do is comment out the old line, and add in a new line containing the new drive's UUID in it's place it should be a piece of cake. Thanks for all of your help! I'll let you know If I have any problems. :popcorn:

---

### Post by BkkBonanza on 2011-03-08
Incidentally, something that's really handy if you change drives around quite a bit (like me) is one of [these cheap USB-IDE-SATA adapters]("http://cgi.ebay.com/USB-2-0-IDE-SATA-S-ATA-2-5-3-5-HD-HDD-Adapter-Cable-/180550148600?pt=LH_DefaultDomain_0&hash=item2a09a0a1f8"). They make it painless to connect up a drive, format and copy and then move it into a system, or just put on a shelf for raw backup. Great for making easy use of the many drives I have kicking around too.

I've used mine for years now and whenever I go to a friend's to help with their system.

---

### Post by Cfhs_1 on 2011-03-10
So I used the clonezilla method, and it worked flawlessly. Clonezilla is an awesome disk cloning tool! The only thing it didn't do for me was expand the partition to fill the entirety of the new drive, but I did that in Gparted in no time at all. I didn't have to edit fstab either, I guess I actually wasn't using UUID's because it detected the disk as sdb1 and gave no errors. I can access the drive from the network with no problems either! It's great! Thanks for everyone's help. I'm a happy camper!:popcorn:

---

