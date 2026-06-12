---
title: "User/Directory &quot;convention&quot; for home file server??"
date: 2006-10-31
forum: Server Platforms
---

### Post by SSTwinrova on 2006-10-31
I'll soon be getting a 500 GB drive to put in an old computer for the use of both a backup and file/media server. I have a separate 25 GB drive which I'll be installing the OS (probably Dapper) on, and I figure I'll mount /home to the 500 GB drive. However, I was curious what most people would recommend for setting up the users and directories. Here are the possible options I've thought of so far:

[LIST]
[*]Single user, separate directories in home for each purpose
[*]Multiple users (one for each person's backup, one for media, one for storage/archival, etc.), separate directory structure in each for files
[*]Multiple users setup as above, but each user on own partition
[/LIST]

Obviously ease of setup/use is a concern, but as I'd maybe like to add an internet gateway for remote access eventually, security is also something I want to keep in mind.

---

### Post by MJN on 2006-11-01
Just as an aside, how old is your 'old' PC? Older BIOS's can have trouble with disks of that size (i.e. >137GB).

Mathew

---

### Post by SSTwinrova on 2006-11-01
I must have gotten it in 1999 (I upgrade every three years, and my second upgrade since then was summer of 2005) -- it's a Dell XPS T550. I don't want to boot from it or use it for anything besides storage though; is that still going to present a problem??

---

### Post by cmileto on 2006-11-02
Make sure its running the latest bios update from the manufacturers website. You should be ok.

---

### Post by dannyboy79 on 2006-11-02
> **SSTwinrova said:**
> I must have gotten it in 1999 (I upgrade every three years, and my second upgrade since then was summer of 2005) -- it's a Dell XPS T550. I don't want to boot from it or use it for anything besides storage though; is that still going to present a problem??

If I were you I would go with 3 partitions, if that's how many users you have. this way if someone downloads a nasty virus that can erase the entire partition everyone else's data will be ok. the next issue is going to be what filesystem do you want to use. FAT32 can be read/written to from both linux and winbloz but there's that damn 4gb max file size problem, if you format the partitions as ext3, then you have to install some sort of program on winbloz so that it can write to the ext3 partition. ntfs write support in linux has come a long way and many people swear that it works great but since i have heard that in the past linux writing to ntfs ended up ruining the entire drive I still am going to wait longer before I start to "write" files from linux onto a ntfs filesystem. Next, you'll need to figure out if you're going to use samba to share stuff, or maybe ftp. what did you mean when you stated the following, "I don't want to boot from it or use it for anything besides storage though" if you;re going to be installing the os, presumably Ubuntu, on this computer than of course you're going to have to boot from it!!! maybe you meant that the 500gb hard drive isn't going to be booted from, at least I hope that's what you meant. Anyway, i hope I have given you some insight. I setup ubuntu as a media/ftp server as well as a normal desktop. It has 1TB of hard drives in the box, i run a 2.66ghz celeron p4 w/64 bit something or other but since I installed the processor in a non-64bit motherboard it isn't being utilized as a 64bit chip. i have 512mb ram, a GeForce 6200 graphics card and that's about it. I have been using linux since 6/1/06 and I love it so far, Ubuntu was my first choice and I hav stuck with it thru thick and thin./ hell, I even brought back to life an ancient laptop (266mhz pentium mmx with 128mb ram) with Xubuntu and it flys now! I do use Opera though because firefox is to slow.

---

### Post by MJN on 2006-11-02
> **SSTwinrova said:**
> I must have gotten it in 1999 (I upgrade every three years, and my second upgrade since then was summer of 2005) -- it's a Dell XPS T550. I don't want to boot from it or use it for anything besides storage though; is that still going to present a problem??

With that era it'd be touch and go - try reflashing the BIOS anyway (I think the Dimensions of that age are on version A11) and see if it mentions supporting 48-bit LBA. My Dimension 4100 (PIII 1GHz) from a similar time doesn't, and hence cannot use >137GB discs - or rather it can but you can't see anything above 137GB. I strongly suspect you'll be in the same position.

There are some workarounds e.g. a PCI IDE card or even drive overlay software (provided by the HDD manufacturer) but I would not recommend the latter if any of your data is important to you as they can fail with spectacularly disasterous consequences.

Mathew

EDIT: Here's one report of an XPS T500 **not** supporting 48-bit LBA: [http://forums.us.dell.com/supportforums/board/message?board.id=dim_harddrive&message.id=78459&query.id=767295#M78459](http://forums.us.dell.com/supportforums/board/message?board.id=dim_harddrive&message.id=78459&query.id=767295#M78459)

---

### Post by SSTwinrova on 2006-11-02
> **dannyboy79 said:**
> If I were you I would go with 3 partitions, if that's how many users you have. this way if someone downloads a nasty virus that can erase the entire partition everyone else's data will be ok. 
The only person except me who is really going to be writing anything to this comp is an automated backup from my dad's work laptop (he got burned with a hard drive failure and lst everything not archived on his work's servers, hence why I have my parents finanfial backing for this project  :)). Good point about being able to wipe partitions if something does happen to one of them, though.

> **dannyboy79 said:**
> the next issue is going to be what filesystem do you want to use. FAT32 can be read/written to from both linux and winbloz but there's that damn 4gb max file size problem, if you format the partitions as ext3, then you have to install some sort of program on winbloz so that it can write to the ext3 partition. ntfs write support in linux has come a long way and many people swear that it works great but since i have heard that in the past linux writing to ntfs ended up ruining the entire drive I still am going to wait longer before I start to "write" files from linux onto a ntfs filesystem.
This comp is going to be Ubuntu-only, so I was just going ext3 as I don't need to worry about Windows support (right?).

> **dannyboy79 said:**
> Next, you'll need to figure out if you're going to use samba to share stuff, or maybe ftp.
My plan was Samba so that Windows could see them as shared folders.

> **dannyboy79 said:**
> what did you mean when you stated the following, "I don't want to boot from it or use it for anything besides storage though" if you;re going to be installing the os, presumably Ubuntu, on this computer than of course you're going to have to boot from it!!! maybe you meant that the 500gb hard drive isn't going to be booted from, at least I hope that's what you meant.
That's correct; as I mentioned in the first post, I'll be installing Ubuntu on a separate 25 GB drive.

> **MJN said:**
> With that era it'd be touch and go - try reflashing the BIOS anyway (I think the Dimensions of that age are on version A11) and see if it mentions supporting 48-bit LBA. My Dimension 4100 (PIII 1GHz) from a similar time doesn't, and hence cannot use >137GB discs - or rather it can but you can't see anything above 137GB. I strongly suspect you'll be in the same position.

There are some workarounds e.g. a PCI IDE card or even drive overlay software (provided by the HDD manufacturer) but I would not recommend the latter if any of your data is important to you as they can fail with spectacularly disasterous consequences.

Mathew

EDIT: Here's one report of an XPS T500 **not** supporting 48-bit LBA: [http://forums.us.dell.com/supportforums/board/message?board.id=dim_harddrive&message.id=78459&query.id=767295#M78459](http://forums.us.dell.com/supportforums/board/message?board.id=dim_harddrive&message.id=78459&query.id=767295#M78459)
Well, grrr......lol. Any controller card recommendations that won't be a PITA to set up (and preferably cheap, too)??  :rolleyes:

---

### Post by MJN on 2006-11-03
> **SSTwinrova said:**
> Well, grrr......lol. Any controller card recommendations that won't be a PITA to set up (and preferably cheap, too)??  :rolleyes:

I'm afraid I don't have any recommendations as I personally just went with a 120GB drive as it sufficed for my minds. However, from the limited 'research' I didn't find that people were having any problems with any cards so I think it's probabably quite a straightforward function for them to provide. Indeed, looking at the prices (<20 £/$) there's clearly not that much to it.

I'd just see what your usual vendor (perhaps wherever you're getting your HDD from) has available, unless someone can make a personal recommendation for one.

Mathew

---

### Post by dannyboy79 on 2006-11-03
> **SSTwinrova said:**
> This comp is going to be Ubuntu-only, so I was just going ext3 as I don't need to worry about Windows support (right?).


My plan was Samba so that Windows could see them as shared folders.

Ok, well your first statement doesn't really make sense when I read the second statement. If you want this 500gb hdd to be a file server and you have other computers on your lan that aren't linux than obviously you will need to be sure whatever os your other boxes on your lan can "write and read" what you are going to format the 500 gb as. So when you said, "This comp is going to be Ubuntu-only, so I was just going ext3 as I don't need to worry about Windows support (right?)." which is fine if every computer on your lan is ubuntu or a form of linux that supports the ext3 (which I believe they all do) then why would you then state, "My plan was Samba so that Windows could see them as shared folders."? So, if i were you I would look into the support for windows writing capabilities to ext3, I believe it can be done using a driver or whatever but I don't know if this is as reliable as having both the winbloz and ubuntu writing to fat32? (NOte: that's a HUGE I DON'T KNOW, so please no one jump down my throat for saying this!) The only bad thing is the 4gb file limit size for fat32. I personally have a file server that has 200gb as fat32, 100gb as ntfs, and 700gb as ext3. YES, you read corrrectly, I have a TB of disk space in my ubuntu server/desktop (it's to bad that when a drive says it's 400gb, after you format it, you end losing about 10% of the drive, at least that's been my experience if i remember correctly) 1x400gb sata drive, 1x300gb pata drive, 1x300gb pata drive and my os sits on a 20gb pata drive. The following is my fdisk -l info:

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       29420   236316118+   b  W95 FAT32
/dev/hdb2           29421       36483    56733547+   f  W95 Ext'd (LBA)
/dev/hdb5           29421       36483    56733516    7  HPFS/NTFS

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           6       48163+  83  Linux
/dev/hdc2               7        1281    10241437+  83  Linux
/dev/hdc3            1282        1472     1534207+  82  Linux swap / Solaris
/dev/hdc4            1473        2434     7727265   83  Linux

Disk /dev/hdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       36483   293049666   83  Linux

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   83  Linux

and then here is my fstab for your reference:


proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /boot           ext3    defaults        0       2
/dev/hdc4       /home           ext3    defaults        0       2
/dev/hdd1       /home/daniel/300gb-ext3 ext3    defaults        0       2
/dev/sda1       /home/daniel/400gb-ext3 ext3    defaults        0       2
/dev/hdc3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,sync  0       0
/dev/hdb5       /home/daniel/ntfs       ntfs    ro,uid=1000,gid=1000,nls=utf8,umask=0222        0       0
/dev/hdb1       /home/daniel/fat32      vfat    rw,uid=1000,gid=1000,iocharset=utf8,umask=0000  0       0
/home/daniel/300gb-ext3/torrents        /home/ftp/download/mirror-torrents      vfat    bind    0       0

The last line basically binds a partition I have with media stuff on it into my ftp server folder so I can share with friends etc. If you want any other suggestions or whatever just post back and i'd be happy to help.

---

### Post by MJN on 2006-11-03
> **dannyboy79 said:**
> Ok, well your first statement doesn't really make sense when I read the second statement. If you want this 500gb hdd to be a file server and you have other computers on your lan that aren't linux than obviously you will need to be sure whatever os your other boxes on your lan can "write and read" what you are going to format the 500 gb as. So when you said, "This comp is going to be Ubuntu-only, so I was just going ext3 as I don't need to worry about Windows support (right?)." which is fine if every computer on your lan is ubuntu or a form of linux that supports the ext3 (which I believe they all do) then why would you then state, "My plan was Samba so that Windows could see them as shared folders."? So, if i were you I would look into the support for windows writing capabilities to ext3, I believe it can be done using a driver or whatever but I don't know if this is as reliable as having both the winbloz and ubuntu writing to fat32? 

I think you might be getting confused.

The OP is planning on setting up a machine as a dedicated file server. It'll be running Ubuntu and sharing access to the disk across the LAN using Samba. Hence it doesn't matter what file format the *disk* is using - Samba will be using the SMB protocol to share the disk with whatever SMB-compatible clients (Linux or Windows) are on the LAN.

Mathew

---

### Post by dannyboy79 on 2006-11-03
> **MJN said:**
> I think you might be getting confused.

The OP is planning on setting up a machine as a dedicated file server. It'll be running Ubuntu and sharing access to the disk across the LAN using Samba. Hence it doesn't matter what file format the *disk* is using - Samba will be using the SMB protocol to share the disk with whatever SMB-compatible clients (Linux or Windows) are on the LAN.

Mathew

Duh, I was thinking about dual booting. My bad, here is a cool little article about setting up a home backup server which could also be used to serve files as well. It's for Red H__ (naughty word, just kidding) but most of it should be applicable, [http://www.linuxjournal.com/comment/reply/8590](http://www.linuxjournal.com/comment/reply/8590)

---

### Post by SSTwinrova on 2006-11-03
I purchased this one online this afternoon: [http://www.newegg.com/Product/Product.asp?Item=N82E16816132004](http://www.newegg.com/Product/Product.asp?Item=N82E16816132004)

A couple of the comments said it worked with Linux, and people also reported having it work with 200 GB drives, so hopefully it'll fit my needs. If not, only $16 and I can save it for future use.

---

