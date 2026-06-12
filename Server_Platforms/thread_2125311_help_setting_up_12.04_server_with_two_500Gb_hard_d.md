---
title: "help setting up 12.04 server with two 500Gb hard drives"
date: 2013-03-13
forum: Server Platforms
---

### Post by pappo on 2013-03-13
I have an old Dell Optiplex GX280 laying around and two spare 500Gb hard drives.
I would like to set up a home fileserver for my pictures / ham radio articles / DDO stuff ... LOL
I downloaded ubuntu-12.04.2-server-i386.iso and created a boot CD.

I was planning to setup the first disk /dev/sda with a 5Gb / ;  5Gb /boot ; 20Gb /home, using the fdisk type 83 (linux) and put all the rest ( 470Gb) into an LVM partition type 8e.  Then add the second 500Gb drive /dev/sdb as another LVM
If anyone has a better suggestion on partition allocations, please reply.

I really do not know much about LVM other than a basic understanding that it will allow me to add disks and create physical volumes/ volume groups / logical volumes.

My goal is to end up with my network seeing one big 480Gb + 500Gb = 980Gb area to save files/pictures.

I have downloaded a couple of LVM tutorials which will help me understand the terminology better, but I would appreciate anyone who can point me to a link or examples on how to do this.

Thank you

---

### Post by papibe on 2013-03-13
Hi pappo.

I would go with a bigget root partition. 1Gb is to little. I would go with at least 5Gb.

Regards.

---

### Post by pappo on 2013-03-13
papibe - thanks, I will change the original post for that.

---

### Post by darkod on 2013-03-13
Since you will be using lvm, make / and /home to be LVs inside the LVM. No need to have them as separate partitions. Leave only /boot outside the LVM but 5GB is too much, waste of space. Make it 500MB which is sufficient for /boot. The rest will be inside the LVM.

---

### Post by pappo on 2013-03-13
> **darkod said:**
> Since you will be using lvm, make / and /home to be LVs inside the LVM. No need to have them as separate partitions. Leave only /boot outside the LVM but 5GB is too much, waste of space. Make it 500MB which is sufficient for /boot. The rest will be inside the LVM.

darkod - Thanks for replying.

You will have to humor me if my questions seem like I am a novice, because I am a novice.... lol

So are you saying I should take the first disk /dev/sda and just make two partitions.  One 500Mb linux (83) and a second partition 499.5Gb LVM (8e) ?  Then make the second drive /dev/sdb one big 500Gb LVM partition.
Then make a / and /home LVs and a big /fileserver LV and then extend the /fileserver LV with /dev/sdb LV ?

I am starting with a fresh install of 12.04.2 server LTS.  Do I have to do a custom partitioning when I do the installation ?

Do you have any links you would recommend I read to get an idea on how to do this ?

---

### Post by darkod on 2013-03-14
Yes and no. :) Correct about the partitions, but no need to extend /fileserver to sdb LV, sdb will not be an LV. The physical partitions on the disks would be like:
/dev/sda
partition #1, primary, 500MB, Use As: ext4, Mount point: /boot
partition #2, primary, the rest, Use As: physical device for LVM

/dev/sdb
partition #1, primary, all of it, Use As: physical device for LVM

You install with the manual method (manual partitioning), and create the above partitions on the disks. After that go into Configure LVM in the options at the top of the partitioner. Once there, it will ask you which partitions you want to use for LVM. Select sda2 and sdb1. Note that in the text menus you select with Space bar and it will show * next to the selected item. So, you select both LVM partitions so that it can join them.
After that it will ask you to create a Volume Group. Create only one and you can let it have all the space.
After that you need to create the Logical Volumes. You need at least two for root and swap, but you can create as many as you want. Every separate mount point you want must have a LV created. When creating the LVs DO NOT give them too much space. Start small and you will expand them later when needed.
For example, for the root LV give it only 10GB. For swap as much as you want for swap. If you create fileserver LV give it for example 200GB or how much you want to start with.

The point of not giving the whole space to one or two LVs is that if you need to expand another LV later there will be no space to use because it will all belong to other LVs. To expand you need space inside the VG that does not belong to any LV. That's why you start small and expand the LVs you need. Otherwise you need to shrink one LV so that you can expand another.

Once the LVs are created, select Finish for that step and it will bring you back to the partitions list. The new LVs will be there. Select them one by one and set their filesystem (Use As) and mount point. Note that in the partitions list for each LV there will be one title line, and below it the size of the LV. You need to select the size, not the title so that you can work with it. For example:
root LV ......
10GB

That's it.

---

### Post by pappo on 2013-03-14
Darko - Thanks again for the help.  I will give that a try today.

Pappo.

---

### Post by Cheesemill on 2013-03-14
You don't need to have a separate /boot volume with LVM anymore (GRUB2 supports booting from an LVM partition), I would create...

sda1 - primary, entire drive, LVM.
sdb1 - primary, entire drive, LVM.

For a good background on LVM check out this thread...
[http://crunchbang.org/forums/viewtopic.php?id=19411](http://crunchbang.org/forums/viewtopic.php?id=19411)

---

### Post by pappo on 2013-03-14
Hello Cheesemill

Thanks for the comments.  I know when 12.04 Server installs LVM it creates a root ( / ) and swap vg and leaves the rest alone.
Should I just let the server install do it for me, or do a custom partitioning ?

---

### Post by pappo on 2013-03-18
Thanks to all for the help.

I created on partition for root, one for swap, and the rest LVM on /dev/sda, and then on big 500Gb LVM partition for /dev/sdb

I made a lvm directory and mounted it on /mnt/storage on /dev/sda and still had 200Gb left but now I have that /dev/sdb as additional storage that I can expand when needed.

Thanks to the forum users.

---

