---
title: "Moving raid server OS to it's own (3rd) drive"
date: 2015-10-12
forum: Server Platforms
---

### Post by dries2 on 2015-10-12
Hi All
I have tried googling this but no luck so far.
Existing (1404) Raid 1 server with two drives. I need to move the OS to it's own (3rd) drive. Can somebody tell me how to do this or post a weblink.

Many thanks

---

### Post by darkod on 2015-10-12
Do you need exact commands in detail or just guidance of the process?

In short, the process should be simple:
1. Create root (and maybe swap) partitions on the new HDD. Fromat them accordingly (ext4 and swap for example).
2. Boot with a desktop CD in live mode. Create temporary mount points for old root and new root.
3. Asemble the existing raid1 old root. Mount it and the new root at the temp mount points.
4. Use cp or rsync to copy all data from old root to new root.
5. Modify fstab to mount the new root at boot. Reinstall (modify) grub to detect the new root.
6. Try to boot into the new root and see if it worked. If it did, continue using the new root and after a while you can delete the old root files on the raid1 to free that space.

If you need the detailed commands we need to go step by step, not all at once.

---

### Post by dries2 on 2015-10-12
Thanks darkod. I've got a fair idea of what you're talking about. 
Create root and swap on new HDD with Gparted?
Does it matter what live cd I use. Got some older ones here.
I don't understand what you mean by **assemble** the existing raid 1 old root.
The rest I think I can figure out
So I never actually load ubuntu server on new HDD. I just bring /root across?

Thanks a mil for the prompt response

---

### Post by darkod on 2015-10-12
You should be OK using older live cd, just not too old. By assemble I mean that booting in live mode the system will not know of the raid. The mdadm package is not included in live mode so you need to add it in the live session and assemble the array(s).
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That will scan all HDDs and assemble all valid arrays it can find.

You can create partitions using Gparted or parted in the command line of the current installation. I personally prefer parted because it gives more flexibility. But you can do it however you prefer better.

Yes, you do not install a new installation of ubuntu server on the new HDD (unless you wish to). You copy/rsync the current installation because it sounded like that's what you want. Just make sure when copying to keep all ownership and permissions.

---

### Post by TheFu on 2015-10-12
"assemble" is a RAID term,  mainly used for Linux Software RAID. If your RAID is NOT SW-RAID, we need to know ASAP. If  a  HW RAID card is used, that is important. Same if "FakeRAID" is used.

You probably do not need to perform an install - the copy will put stuff over.

/root will come when you copy / <---- also called "root".  Yes, it is confusing. 
/root is "root's home directory" and
/ is "the root directory"

You want / in your copy.

I'd use rsync.
Also, don't forget the few grub commands. That will fix the boot so the system knows where to boot the OS from - which partition has the OS and which partition has the /boot.

---

### Post by dries2 on 2015-10-12
Thanks darkod and the Fu. The live cd is prob 1004 or 1204. Whoa! If I copy / does my whole old OS come across? Not what I want, I want a clean inst. as the prev one is giving me problems with sucking down a lot of bandwidth

---

### Post by TheFu on 2015-10-12
> I need to move the OS to it's own (3rd) drive. Can somebody tell me how to do this or post a weblink.

Was the original post, so we thought you wanted to "move the OS".
If you want to start fresh, delete everything and do a fresh install.

---

### Post by dries2 on 2015-10-12
Yes, apologies, can be read both ways. I really don't want to lose the data on the raid drives. Is it possible to insert a new OS drive in there and disabling the OS on the data drives?

---

### Post by mastablasta on 2015-10-13
> **dries2 said:**
>  Is it possible to insert a new OS drive in there and disabling the OS on the data drives?

easiest and most amateur way. install OS on new drive. Boot from it and mount the RAID array (actually you can mount during install). remove grub from the RAID drive(s) or delete the OS files.

---

### Post by dries2 on 2015-10-13
Thanks mastablasta. Seeing as I am an amateur it's right up my street. I have found this: [http://askubuntu.com/questions/11293/rebuild-mdadm-raid5-after-os-hard-drive-died](http://askubuntu.com/questions/11293/rebuild-mdadm-raid5-after-os-hard-drive-died)
Will see how I go

---

