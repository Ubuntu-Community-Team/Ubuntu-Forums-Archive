---
title: "Recovering deleted ext3 files ?"
date: 2006-03-15
forum: Server Platforms
---

### Post by dbee on 2006-03-15
Has anyone ever done this sucessfully ?

If so how ?

I'm really in a bind here :confused: 

thanks,

---

### Post by John.Michael.Kane on 2006-03-21
[http://e2undel.sourceforge.net/usage.html](http://e2undel.sourceforge.net/usage.html)
[http://linuxmafia.com/faq/Filesystems/ext3-no-undeletion.html](http://linuxmafia.com/faq/Filesystems/ext3-no-undeletion.html)
[http://en.wikipedia.org/wiki/EXT3](http://en.wikipedia.org/wiki/EXT3)
dont think you can recover files from ext3...

---

### Post by dbee on 2006-03-22
Hi guys

just to finalize this post ... collecting files from deleted ext3 filesystems is impossible.

However you can collect data if you know some keywords to look for 

The bash script I used went something like this

> 
cat /mnt/sda1 | strings | grep -B100 -A100 'keyword'


where sda was the image of the filesystem

---

### Post by Zyphrexi on 2006-04-25
that's so depressing, I accidentally formatted my dapper drive + all my data and lost everything. Well I guess that's what I get for using a gui. next time i'm just using fdisk. On another note, since ext3 is unrecoverable, what would be better?
I've heard a lot about reiserfs, but that's usually from my gentooist bretheren.

---

### Post by LordHunter317 on 2006-04-25
No modern journaling filesystem I'm aware of is really that recoverable, on Linux anyway.

None of them have worthwhile tools, to say the least.

---

### Post by az on 2006-04-25
You can use foremost from a live cd (or another hard disk) to recover lost files from an ex ext3 filesystem.


It works on other filesystems, too, like vfat and ntfs.[http://packages.ubuntu.com/breezy/admin/foremost](http://packages.ubuntu.com/breezy/admin/foremost)

If you have another disk, you can recover the files to it.  You can't really revive that filesystem and the data on it, though.

---

### Post by az on 2006-04-25
[QUOTE=Zyphrexi]that's so depressing, I accidentally formatted my dapper drive + all my data and lost everything. Well I guess that's what I get for using a gui. next time i'm just using fdisk. [/QUOTE]


You say you formatted with fdisk?  That's not what fdisk does.  It just rewrites your partition table.  You can use parted to recover lost partitions like that.  Unless you recreated another filesystem over it, the data is still there.

Use the rescue function

Basically, If you borked a 20Gig drive (call it hda) you would run:
sudo parted /dev/hda
rescue
0
20000

and then you would get prompted for every partition parted thinks it found.  It will ask you if you want to add t to the partition table - say yes.

---

### Post by Zyphrexi on 2006-04-26
no I didn't use fdisk, I used System>Admin>Disks
and it/breezy had my disks mis-labelled so I in essence formatted the wrong drive.

all I merely did was change the filesystem type to vfat instead of ext3.
> 
You can use foremost from a live cd (or another hard disk) to recover lost files from an ex ext3 filesystem.


so does that mean I can recover the files? That's all I really care about, I'm pretty sure dapper is dead, but i'd like to save my data/files.

---

### Post by Zyphrexi on 2006-04-26
I checked out foremost, I have absolutely no idea what I'm supposed to do. I really don't want to screw things up again.

---

### Post by az on 2006-04-26
Sorry!  I had always compiled foremost myself, I just noticed that the older version in ubuntu lacks some functionality.  You have to config it up the wazoo...  Use the latest version - compile it.


Okay, let's say you borked a ten gig hard drive and have another hard drive lying around with enough room to hold all the files you want to recover.  You would install the second drive, boot the live cd and format that hard drive so that you can save data to it.  Mount it and then install (compile) foremost

sudo apt-get install build-essential
Get the source: [http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

(Get the 1.2 version)

tar xvzf foremost*
cd foremost*
make
sudo make install

sudo foremost -t all -o /mnt/MyHardDrive -i /dev/hda1
Where you mounted your data hard drive as /mnt/MyHardDrive and your deleted filesystem is on hda1

---

### Post by Zyphrexi on 2006-04-26
my dapper partition was larger than my (current)breezy partition, I don't have the kind of setup you are suggesting, I'm running the command (tweaked for my settings) in my current breezy partition. I hope I didn't need to do it the other way :???:

i installed using checkinstall btw, i love that proggy.

UPDATE: yeah everything worked out fine, I was able to access most of my data though there are a few where the data is either split between files or missing altogether, but I won't say I didn't expect that. One thing I noticed that is both good and bad is that the filetypes were nicely categorized in folders according to extension, the problem there though is that there were some files (mostly text) without an extension or a odd extension, and those files are not there

---

