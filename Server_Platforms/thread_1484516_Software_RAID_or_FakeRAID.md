---
title: "Software RAID or FakeRAID?"
date: 2010-05-15
forum: Server Platforms
---

### Post by ilynx on 2010-05-15
Hello,

I've got my first ubuntu server up and running 10.04 sever edition.  I have already set it up with a static ip and started messing around with text editors and ssh.  Next I want to try to set up a RAID1 array on two disks without going back to re-install ubuntu.  The OS is on its own disk, the RAID array will be using two new blank drives.  

I want to use this array to:
-back up other PCs and a Mac
-store the files so the server can be a file server
-potentially be a web server in the future (after figuring out this Linux stuff, I want to make my own web page)

My questions so far are:

1.  Should I use software RAID or FakeRAID?  After reading a few posts, I am pretty certain I should use software RAID, but I thought I read somewhere that it is not supported by ubuntu server.  That doesn't seem right, but wanted to make sure.

2.  Where is a good "How-to" or tutorial that I can follow?  I have seen a few on these forums, but they all seem to address different concerns than mine.  The one on [this page]("http://ubuntuforums.org/showthread.php?t=1165328") looks good.  I think it also backs up the /home directory from the OS drive to the array as well, and I assume that's a pretty good plan, no?  I can't tell if it will completely move the /home directory off of the OS drive though.  Is that safe to do?  I also found [this one]("http://www.howtoforge.com/software-raid1-grub-boot-debian-etch") at how-to-forge, but it is a few years old, and not specifically for ubuntu, so I am concerned about its content.

3.  Is there a dictionary resource for server terms (ubuntu-specific or not)?  I can pick up a lot from context, but many times I would really love to have access to some definitions since I am picking this up as I go and it would be a lot faster than searching for the term in the forums and piecing together definitions from different posts.


TIA,

ilynx

---

### Post by BoneKracker on 2010-05-15
Based on what I know, the only reason to use "Fake Raid" (i.e. BIOS RAID) is if you are going to dual-boot with a Windows system that is installed on or access a RAID array and your linux system is going to be installed on or access the same RAID array.

To the best of my knowledge, it offers no performance advantage over Linux software RAID.  So, based on the use case you describe, I would suggest using software RAID.

I don't use Ubuntu, but I can't imagine that Ubuntu Server lacks support for it.  Hopefully someone else will chime in and confirm or deny that for you.

---

### Post by iversonm on 2010-05-16
Go with software raid. As mentioned above, fakeraid is a kludge for windows, and you should avoid it if you can. Please keep in mind that many of the RAID setup guides indicate that you must make a separate /boot partition. This is obsolete advice, and also probably irrelevant, as you don't want to reinstall. 

Also, there is no problem moving the home directory to an entirely new drive. This is a very common configuration, and is the reason unix file systems are organized the way that they are. This allows different segments of the file system to be placed on a different partition, drive or network share, as needs dictate. For example, a typical setup from the days of yore might be:
[LIST]
[*]/bin and /etc are on the root file system, and contain enough stuff to boot the machine. This is mounted read only.
[*]/var is on a separate partition, mounted rw, for log messages, etc.
[*]/usr is a NFS share, so multiple computers can share the same software, mouted read only for security.
[*]/usr/local is for stuff unique to the computer, and is a local partition.
[*]/home is a NFS share mounted rw, so you always have your stuff, regardless of the machine you log on to.
[/LIST]

For the raid setup, I don't have a guide for you, but you'll want to do the following, in rough terms. All these commands will need a "sudo" in front of them. Please validate this against other guides, in case I state anything misleading here.

1. Partition the disks using fdisk. One big partition will be fine, and set the type to "RAID" ("fd" is the code I think.) If your first drive is /dev/sda, the second and third will probably be /dev/sdb and /dev/sdc. Be careful to choose the correct one. Save the changes to disk.

2. Build the raid partition: mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

3. Format the partition: mkfs.ext4 /dev/md0

4. Mount the partition: mount -t ext4 /dev/md0 /mnt

5. Copy files from /home to /mnt, preserving permissions: cp -a /home/* /mnt

6. VERIFY YOUR FILES HAVE COPIED AS YOU INTENDED.

7. Delete files from the /home directory: rm -rf /home/*

8. umount /mnt: umount /home

9. remount on /home: mount -t ext4 /dev/md0 /home

10. edit /etc/fstab to mount this directory automagically when you reboot.

For the file server part, you'll want to install and configure samba. If this is just for personal use by a couple of people, ignore the domain controller stuff and just manage the passwords on your ubuntu box.


As for your file server, I suggest a vanilla samba installation

---

### Post by ilynx on 2010-05-16
Thank you both for your answers.

iversonm, the outline you provided looks like what I am wanting to do, and unless someone else voices some opinions against it, I will probably give it a go later this afternoon.

I am curious about one thing though.  I have read on these forums that ext4 might still have some stability issues in ubuntu, but it seems like most of those statements are in reference to the versions pre-10.04.  I don't mind using ext3 if that would mean better stability, and as I understand it, I could later change over to ext4 when the verdict is clear.  So, is it as easy as substituting ext3 in all the places where you have ext4 if that's currently a safer option?

Thanks again for the help,

ilynx

---

### Post by Cracauer on 2010-05-16
I strongly recommend Linux' md RAID.

Reasons include:
[list]
[*]I don't trust mainboard RAID. Internet forums are full of posts where people lost raid1s when BIOS and OS driver disagreed on the state of things and e.g. an involuntary reboot during re-sync (switching from OS drivers to BIOS) wrote the bad disk's data over the good one. Intel's implementation might be decent but no way I'd trust NVidia.
[*]Mainboard raid is limited to the ports on there. md RAID can be spawned across everything. In an emergency you can plug in any raw device anyway, including your ipod or whatever.
[*]Trust me, you will want to transport the RAID later, and you don't want to be limited to have to have the same mainboard chipset.
[/list]

Linux' md on the other hand has always been rock-solid for me and made it through numerous recoveries, resizing (both # of disks and size of partitions under the raid).

Performance-wise md is probably better, too. Last time I benchmarked the mainboard RAID was too dumb to even give a read-after-seek advantage for raid1.

---

### Post by ilynx on 2010-05-16
Thanks Cracauer, it seems like most people agree that Linux's Raid implementation is solid.  I am poking around on a few more forum threads and will soon be having a go at it this afternoon.

ilynx

---

### Post by aphatak on 2010-05-16
@ilynx: Is there a specific reason you are planning on RAID-1?  If you can spare the cash for one more disk, I would recommend RAID-5.  I have *two* file servers set up for home use.  Each has 6 1TB disks arranged as RAID-5 arrays, so I get *two* 5TB dataspaces.  If I used RAID-1, I would get two 3TB dataspaces.  Plus you also have the advantage of a striped volume (I assume you have one controller per disk, as in SATA or SCSI).

I find RAID-5 highly resilient.  In fact, when I had one 5TB dataspace, one of the disks (which was old) died suddenly.  I got a warning from mdadm, but the array continued uninterrupted.  I do not have hot-swap disks, so I had to bring the file server down, replace the disk and re-start it.  I then told mdadm to add the new disk to the array, and it did it in the background, without suspending service.  The only time lost was between initiating shutdown and completing restart.

If your server serves a large number of users, you might want to act paranoid, and go for RAID-6.  But we are talking of serious money here - at least 4 drives.

---

### Post by laluz on 2010-05-16
> **iversonm said:**
> 

7. Delete files from the /home directory: rm -rf /home/*


Why? I'd say, leave them where they are. Deleting is not material to raid setup.

Also make sure you have a UPS and consider adding a bitmap with --grow --bitmap internal. This should make your power failure (or any surprise reboot) recovery painless.

---

### Post by ilynx on 2010-05-16
aphatak,

Well, this is my first foray into Linux, servers, RAID, etc. and after speaking with my brother, who has been dealing with this kind of stuff for 20+ years, he suggested that I don't need to worry about RAID5 just yet because it requires more attention.  Also, this is for home server usage, which right now consists of my wife and me.  I imagine it will mostly be a file server for media files and a place for backups.  I hope to eventually learn some web/apache stuff and other server type applications, but that may be a bit down the road.

ilynx

---

### Post by ilynx on 2010-05-16
laluz,

I already have the server on a UPS, but have never heard the terms bitmap and grow when speaking about RAID arrays.  Off to do a search now, but would love some explanation about it!

UPDATE:  Found enough info on the forums to understand what growing an array means (simple enough concept) but haven't had as much luck with the "bitmap" concept.

ilynx

---

### Post by BoneKracker on 2010-05-16
If you are extremely risk-averse, go with ext3.  Otherwise go ext4 now.  I personally wouldn't upgrade a filesystem from ext3 to ext4.

I've been using ext4 on everything but my router (where I still have reiser3) for quite a while.

You should definitely have your server on a UPS though.  Almost every data corruption issue I've ever had has come as a result of an abrupt power loss on a machine unprotected by UPS.

---

### Post by RyanRahl on 2011-12-19
I have a question about this. What if the disk that the operating system is on fails and you lose /dev/md0? How would one recover or rebuild the info on the RAID array after replacing the OS disk and re-installing the server?

[edit]sorry to resurrect this thread, I didn't check the date first. answers would still be greatly appreciated though[/edit]

---

