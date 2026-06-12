---
title: "Re: need to image a fresh install of Win 10 to external HDD via Ubuntu 16.04 bootdisk"
date: 2017-06-04
forum: Windows
---

### Post by isa.k on 2017-06-04
Yeah... the title says it all.

I have recently factory reset my Dell Inspiron model 5348, and installed all software on it that I will need for the foreseeable future, except for my games.

I want to be able to create an image of the Windows 10 system on to an external HDD, so when I inevitably do another factory reset down the track (in six months?), I can use the backup to just plonk the image onto the Dell HDD (which is something else I will have to learn how to do, and is the topic for another day... unless it is relatively simple/straightforward, and someone could explain that too).

What I currently have to work with:

My Dell HDD is 1 TB
External HDD is 1.5 TB
Ubuntu 16.04 bootdisk, which is currently what I am running the PC off. So I can't download any new files to be able to install any new software it'd seem (unless there is a fix for that as well?)

Problems:
I can see the 1000 GB Volume HDD icon in the dock on the left of the screen, but can't open it
I have my external Seagate HDD attached via a SATA dock, and can't seem to get it to register, as I can't see it at all it'd seem.

Here is the result of sudo fdisk-l

```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 22F0C908-8122-4F57-80A9-B1420D370954

Device       Start        End    Sectors  Size Type
/dev/sdb1     2048     923647     921600  450M Windows recovery environment
/dev/sdb2   923648    1126399     202752   99M EFI System
/dev/sdb3  1126400    1159167      32768   16M Microsoft reserved
/dev/sdb4  1159168 1953523711 1952364544  931G Microsoft basic data

```

**How do I get to do what I aimed to do in the current situation?**

Thank you to all that try to help from now.

Screenshot:

---

### Post by howefield on 2017-06-04
Thread moved to the "*Windows*" forum.

You may be better off with [Clonezilla]("http://clonezilla.org/") or the free version of [Macrium Reflect]("https://www.macrium.com/reflectfree"), both of which will clone partitions/disks.

---

### Post by isa.k on 2017-06-05
> **howefield said:**
> . . .

You may be better off with [Clonezilla]("http://clonezilla.org/") or the free version of [Macrium Reflect]("https://www.macrium.com/reflectfree"), both of which will clone partitions/disks.

I would do so, but I am not interested in installing "bloatware", hence my intention to use Ubuntu's Live CD.

Is what I am after, not possible with Ubuntu?

---

### Post by isa.k on 2017-06-05
I have continued having issues with reading USBs attached to the PC, so I shut down, and booted up with the Ubuntu Live CD again.

Now I can see the 32 GB USB I have attached. However the internal HDD is still not accessible, giving this message:


I have started the PC with the Live CD three times so far. I remember that during the initial instance, I had no USBs plugged in, and I received no messages during bootup.

The second time I booted up I had the external 1.5 TB plugged in, and had received some sort of text during bootup. This is before I saw any graphical Ubuntu splash screen. I don't know why (read, I forgot) I tried switching off whilst Ubuntu was loading the second time (I think I felt that it was taking too long. Yet despite this, I was surprised to see it boot up at all. It worked pretty much flawlessly otherwise, it seemed), and I believe external drive access issues may have been due to that. As I couldn't access any external drives, I decided to reboot, and leave it to do its stuff  this time.

So, I booted up for the third time with the USBs plugged in again. I received the error messages again, yet decided to let it run its full course and see what would happen this time. I took a pic:

Some more text scrolled up before I could snap it with the camera. But at least I can now access my 32 GB USB. However, as mentioned before, I can't access the main HDD. Add to this, the external doesn't even show up, it'd seem.

---

### Post by howefield on 2017-06-05
> **isa.k said:**
> I would do so, but I am not interested in installing "bloatware",

Bloatware ?

Both are bootable live media just like your Ubuntu Live media is.

Yes, it is possible to dd the drive with the Ubuntu Live media, wouldn't be my recommended route though, ymmv.

PS. I have removed the over sized images, please feel free to use the forums attachment facility to upload your images.

---

### Post by isa.k on 2017-06-05
> **howefield said:**
> Bloatware ?

Both are bootable live media just like your Ubuntu Live media is...Nice :KS ! Please forgive my ignorance. I thought I would have had to install the software. Never knew it was live :) I will definitely give it a go. Thank you so much :D> **howefield said:**
> ...PS. I have removed the over sized images, please feel free to use the forums attachment facility to upload your images.Not an issue. Thank you for your continued support **howefield**. Have a great one!

---

### Post by isa.k on 2017-06-06
> **howefield said:**
> Bloatware ?

Both are bootable live media just like your Ubuntu Live media is.

...For future reference for others.

To be able to utilise Macrium Reflect, it needs to be installed. I tried creating a live disc, but had to install the software to allow it to create the live disc.

It is a pity extra software, software that I will never use again, had to be installed, to achieve a HDD clone. At least I guess that if I want to ever create another clone, I now have a live disc, courtesy of the current install. Even then, I'm not sure if the created rescue disc can create clones.

Time will tell.

For now though, I'll begrudgingly consider this case solved.

---

### Post by howefield on 2017-06-10
That's unfortunate, for info it is very easy to create a Clonezilla live USB media, the down side is the user interface appears more intimidating <shrug> than many other applications of that sort. I use an old 512MB stick that's not much use for anything else. 

1. Download Clonezilla zip file.
2. Extract all files to the USB drive.
3. cd to /utils/linux/ on the USB and run sudo bash makeboot.sh /dev/sdb1 (amend path to suit if USB is not /dev/sd1)

---

### Post by isa.k on 2017-06-10
> **howefield said:**
> That's unfortunate, for info it is very easy to create a Clonezilla live USB media, the down side is the user interface appears more intimidating <shrug> than many other applications of that sort. I use an old 512MB stick that's not much use for anything else. 

1. Download Clonezilla zip file.
2. Extract all files to the USB drive.
3. cd to /utils/linux/ on the USB and run sudo bash makeboot.sh /dev/sdb1 (amend path to suit if USB is not /dev/sd1)

Perhaps in the future, for another machine? **howefiled**, thank you for your advice nonetheless.

---

