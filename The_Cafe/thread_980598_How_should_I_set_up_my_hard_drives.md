---
title: "How should I set up my hard drives?"
date: 2008-11-13
forum: The Cafe
---

### Post by Oplix on 2008-11-13
I'm wondering what the best way of setting up my computer's hard drives would be.

I want to dual-boot Windows XP and Ubuntu 8.10 (is anyone as happy with 8.10 as I am?).

I also want to be able to share my files between both the OS's.

I will have a 1TB hard drive to store the files I will be sharing. What I'm wondering is, what it be better to boot Linux and Windows off separate hard drives? Or should I boot them both off the same drive?

From what I understand, having multiple drives booting your OS's and a storage drive is a bit more secure for your system.

I'm wondering if it's worth going with 2 drives and a separate drive for storage, or just 1 drive partitioned and then a storage drive?

If I were to go with 2 drives, how would I do this? From what I understand, there's master and slave drives. Master drives can boot and read/write, while slaves are only read/write. It's also my understanding that there can only be 1 master drive on a computer.

Please either clarify where I'm wrong on this, or explain to me how this is managed. Thanks!

---

### Post by eternalnewbee on 2008-11-13
My advice: First install xp. Windoze refused to install as 2nd OS with me. But Ubuntu no problem.
Separate hard drives sounds like the safest option
Edit: It's best to create a separate root partition and home partition. If your system crashes or you want to upgrade, then your home partition, with all your personal data will still be there.

---

### Post by mssever on 2008-11-13
I don't think it really matters whether you use separate hard drives or not. Separate partitions is the key.

Remember, too, that unless you're using encryption, there's no such thing as true security when you're dual booting with Windows. Here's why: When you're in Linux, you can mount your NTFS partitions and use them. But since Windows and Linux permissions are incompatible, the NTFS driver will set global permissions and ignore the permissions specified in the filesystem. If you're in windows and access your ext3 partitions using the fs-driver, the same thing will happen--your Linux permissions will get ignored and the driver will use some sort of wide open permissions. This situation isn't anybody's fault; it's merely the way things have to be due to the incompatible permissions models.

Furthermore, the only security benefit to using separate drives is if you physically remove one of them. Otherwise you can access partitions on separate drives just as easily as you can access partitions on the same drive.

---

### Post by pansz on 2008-11-13
1. There is no master or slaves for the modern hard drives. Your computer can boot from any partition in any of your hard drives and there is generally no need to use separate drives for different OS. My suggestion is to install both XP and Linux on the same hard drive.

2. Windows can use NTFS journal and Linux cannot, Linux can use ext3 journal and Windows cannot. ---- If you always shutdown gracefully, then there is no difference using NTFS or ext3. but if you have a power-cut when Linux writing to NTFS or when Windows writing to ext3, file system may be corrupt. My suggestion is to avoid *write-in-both-OS*, if you just write in one OS and read in the other there should be no problem.

---

### Post by Skripka on 2008-11-13
My advice: sandbox as MUCH as possible.


If a harddrive dies-make sure it does not kill 2 OSes and your media.

I have 3 drives:

Linux-Primary drive in boot order in BIOS: divided into Root, Media, and Swap partitions (GRUB is installed on this drive)...formatted ext3

XP-all it's own, formatted ntfs

3rd media drive, that can be accessed via USB from any old computer, that plugs into my tower by SATA bay adapter...acts as a backup drive for my day-to-day in Linux, and if I'm ever on XP it allows my to access my media documents-formatted FAT32


With my drives set this way, I can lose my linux system partition and not hurt Windows (as MBR is still as original on install), equally I can lose windows and not really effect linux at all....and I can lose BOTH and still have a working partition of my /media documents, as WELL as a backup-inside my tower.  It would take 3 seperate harddrive dying for me to lose EVERYTHING inside my box (and I have a backup outside as well).

---

### Post by Oplix on 2008-11-13
Wow, my mental RAM is outdated -_-

Well here's how the HD's currently set up

[(~50%WINDOWS)(x% swap)(~50%Ubuntu)]

If you haven't guessed, yeah, I just installed XP and used the Linux installation to do the partitioning and installation.

I only have 1 hard drive at the moment.

So, you're suggesting I set up a separate home partition.

I looked into doing this when installing Ubuntu but I was a little confused about it. Which partition do I want larger for storing my files? If I'm installing software, do I install it to the home, or root partition?

Can I still do this while keeping all my files and settings even though I've already installed Ubuntu? (I can probably google that actually)

Also, Pansz, you advise against writing from one file-system to the other?

This is somewhat unavoidable for me...

Linux is my little pet project that I'm learning and experimenting with. I use it mostly for downloading media, watching media, and playing some games.

Windows is my work OS, and it runs a couple games I can't get running very well on Linux.

When I'm just watching media and playing games I don't mind having to google virtually every feature or setting I want to adjust, or hardware I want to use. When I'm busy with work, I don't need that. If I need to adjust something in my computer's settings, I want it done fast and well enough that I can get back to what I was doing. So the dual-booting is essential for me.

I also happen to be studying in a field of media, so, often I end up using media files while I work and need to access some of the entertainment I've got on the Linux/recreation partition. So, it would be really impractical to transfer all these files with a USB stick. Also, eventually I will have another computer set up in the living room as a "tv". Since my mom doesn't know how to use Linux and doesn't care to learn, it looks like that computer might have to run Windows, or maybe dual-boot. The computer in the living room will be on a network with the one I'm on now. I'd like to be able to access my files from a drive shared on the network. (so each computer with their own personal/private hard drives and a single large hard drive sharing files on the network.

So one way or another, it looks like the cross transfering may just be unavoidable.

---

### Post by eternalnewbee on 2008-11-13
> I looked into doing this when installing Ubuntu but I was a little confused about it. Which partition do I want larger for storing my files? If I'm installing software, do I install it to the home, or root partition?
I'd say about 10 gigs should do it for your root partition (go for 15 or 20. What the heck) You should store your files in your home partition. Any software you install, will go to the root partition.

---

### Post by Polygon on 2008-11-13
the ext2 driver for windows is terrible

its for ext2 drives, so you dont get journaling for ext3 drives
if windows crashes, next time you boot linux it checks ALL OF YOUR DRIVES, even if you had not mounted them during your windows session

ive had fsck tell me terrible things (errors and such) as a result of using that driver

just stay away from it. make a fat32 partition or something. its not worth the effort to use the ext2 driver

---

### Post by mssever on 2008-11-13
> **Oplix said:**
> So, you're suggesting I set up a separate home partition.

I looked into doing this when installing Ubuntu but I was a little confused about it. Which partition do I want larger for storing my files? If I'm installing software, do I install it to the home, or root partition?Your /home should probably be larger. My root partition is 15 GB, and that's larger than I need. Give the rest to /home. When you install software from debs, it'll go on your root partition.

> Can I still do this while keeping all my files and settings even though I've already installed Ubuntu? (I can probably google that actually)Since you don't have a separate /home directory, you'll have to do a bit of juggling. First, make sure you have a backup. Then, I suggest that you resize your root partition to make room for /home, then create a new partition for /home (formatted as ext3 unless you have a good reason for doing otherwise), mount that partition somewhere temporarily (I'll use /mnt as an example) ```
sudo cp -a /home /mnt
```Once you've verified that everything copied correctly (including hidden dotfiles and permissions/ownership), delete the contents of your current /home, remount /mnt on /home, and edit /etc/fstab to automatically mount your new partition on /home.

I realize that you might not know how to carry out all these steps. But Google can help you with the details. This is just the overview.

> Also, Pansz, you advise against writing from one file-system to the other?
I think that's bad advice. There's nothing wrong with writing from one fs to another. But I don't think that's what Pansz was saying. He/she was saying that you should only treat your shared filesystem as writable from one OS. That advise has some merit, but I don't necessarily follow it. Furthermore, I've heard that the most recent versions of NTFS-3G do support NTFS journalling.
> **Polygon said:**
> its for ext2 drives, so you dont get journaling for ext3 drives
if windows crashes, next time you boot linux it checks ALL OF YOUR DRIVES, even if you had not mounted them during your windows sessionI've never had that kind of trouble, though I should point out that I don't use Windows very much.

> just stay away from it. make a fat32 partition or something. its not worth the effort to use the ext2 driverUsing ext2/3 is much better than FAT32. Ext3 will give you journalling when you're in Linux. FAT32 doesn't support journalling ever. If you're in Windows, then your ext3 partition will be treated as ext2 and won't have journalling. But then again, neither will FAT32.

Also, ext2/3 supports Linux-style permissions when mounted from Linux (but not from Windows). FAT32 doesn't support permissions of any kind ever.

Finally, FAT32 is much more susceptible to fragmentation than ext2/3. If you **must** use a windows format, these days it's better to use NTFS.

---

### Post by billgoldberg on 2008-11-13
Windows need around 10gb (vista) or 5gb (xp) to run. 

Double or triple that number for the Windows partition.

Ubuntu needs around 2-3gb, also triple that number.

Create a small swap partition (2gb).

Use the rest to put your files in, formats as ntfs or fat32.

--

So,

30gb ntfs partition (Windows)
10gb ext3 partition (Ubuntu, mousepoint: /)
2gb swap partition (choose manual install in Ubuntu setup)
9xxgb ntfs partition to store your data on


That's what I would do.

You can partition your hdd with the gparted live cd before installing any OS.

Make sure you install XP first.

--

Since you would be storing all your files on the 9xxgb drive, so you can use them in Ubuntu and Windows, I wouldn't bother setting up a separate /home partition.

---

### Post by Grant A. on 2008-11-13
> **billgoldberg said:**
> Double or triple that number for the Windows partition.

Ubuntu needs around 2-3gb, also triple that number.

Create a small swap partition (2gb).

Use the rest to put your files in, formats as ntfs or fat32.


Choose FAT32 for your media partition, it's much more compatible with other operating systems. (DOS, BSD, GNU/Linux, Windows, Mac)

Btw, that is quite small if he plans on installing any programs considering he has a 1TB HDD, I would recommend 100GB for Windows, 100GB for Ubuntu, 2GB for his swap file, 48GB for his home partition, and 750GB for his media.

Example:

/dev/sda1 NTFS (Windows) 100GB  Boot
+------------+ Extended Partition +-------------+
/dev/sda5 Ext3 (Ubuntu /) 100GB
/dev/sda6 Ext3 (Ubuntu /home) 48GB
/dev/sda7 Swap (Swap File) 2GB
+-----------------------------------------------+
/dev/sda3 FAT32/VFAT (Media) 750GB

---

### Post by billgoldberg on 2008-11-13
> **Grant A. said:**
> Choose FAT32 for your media partition, it's much more compatible with other operating systems. (DOS, BSD, GNU/Linux, Windows, Mac)

Btw, that is quite small if he plans on installing any programs considering he has a 1TB HDD, I would recommend 100GB for Windows, 100GB for Ubuntu, 2GB for his swap file, and 798GB for his media.

I have a 30gb partition for windows and have 10 games installed and loads and loads of software. I still have 8gb to spare or something.

I have a 460gb Ubuntu partition that I use every day, without the home folder I don't think it would take up more than 3gb.

But sure, he could give Windows and Ubuntu a bit more, just in case.

---

### Post by billgoldberg on 2008-11-13
> **Grant A. said:**
> Choose FAT32 for your media partition, it's much more compatible with other operating systems. (DOS, BSD, GNU/Linux, Windows, Mac)

Btw, that is quite small if he plans on installing any programs considering he has a 1TB HDD, I would recommend 100GB for Windows, 100GB for Ubuntu, 2GB for his swap file, and 798GB for his media.

I would use NTFS.

He will only be using Ubuntu and Windows, and those OSs support ntfs, no problem.

---

### Post by Grant A. on 2008-11-13
> **billgoldberg said:**
> I would use NTFS.

He will only be using Ubuntu and Windows, and those OSs support ntfs, no problem.

But isn't NTFS a bit slower than VFAT in Linux?

---

### Post by mssever on 2008-11-13
> **billgoldberg said:**
> Since you would be storing all your files on the 9xxgb drive, so you can use them in Ubuntu and Windows, I wouldn't bother setting up a separate /home partition.

Some of the dotfiles in $HOME have specific permissions requirements (~/.ssh springs immediately to mind). Also, all your settings are stored in dotfiles in $HOME. So if you omit a separate /home partition, you'll have to separately backup and restore /home--losing the benefits of a separate /home partition. And you can't put /home on a FAT32 or NTFS partition because of the permissions issues mentioned above.

I maintain a separate /home (ext3) and keep all my files there. If I need to access them from Windows, I use the Windows ext2 driver.

---

### Post by mssever on 2008-11-13
> **Grant A. said:**
> Choose FAT32 for your media partition, it's much more compatible with other operating systems. (DOS, BSD, GNU/Linux, Windows, Mac)

FAT32 doesn't support journalling, so it's less safe than the other options.

---

