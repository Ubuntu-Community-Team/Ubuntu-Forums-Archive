---
title: "Are external/USB drives too unreliable for a server?"
date: 2010-03-10
forum: Server Platforms
---

### Post by Donny Bahama on 2010-03-10
I'm in the early stages of setting up a server. I'm currently in the process of moving data around via a series of rsync jobs, and my rsyncs keep failing because the drives are unmounting themselves. Is this typical?

I'm mounting them using the UUIDs in fstab. I'm not sure what's causing the unmounting but the two drives I'm working with so far are ntfs drives. Maybe that's the problem?

I have some special considerations regarding the server's location, and this dictates using external USB drives. Each drive has its own dedicated power supply, likewise the USB hub.

6 of the 7 drives are earmarked for a RAID5 array, but I'm loathe to set that up if the drives are going to constantly unmount themselves. If this is going to be an ongoing problem, I'm going to have to rethink *everything* - right down to the motherboard.

I'd appreciate hearing the experiences of others with regard to using external USB drives with a server.

---

### Post by spynappels on 2010-03-10
I'd be worried about too many failure points attaching a string of HDDs using USB connections. Also, read and write speed/data throughput would be lower on USB than on SATA or SAS drives.

---

### Post by bodhi.zazen on 2010-03-10
I do not know what the problem is from your post, but why are you using NTFS on and Linux server ?

NTFS does not support permissions and will likely cause problems.

---

### Post by Donny Bahama on 2010-03-10
Thanks for the response!
> **bodhi.zazen said:**
> I do not know what the problem is from your postCan I infer from that statement that external drives should work reliably?> but why are you using NTFS on and Linux server ?It's just temporary. The drives were originally part of a Windows server. (Before I started using Linux.) I just need to get the data backed up before converting them to a Linux filesystem and incorporating them into a RAID array.

---

### Post by bodhi.zazen on 2010-03-10
In general I do not have problems with external drives and I suspect your problem may be with ntfs as rsync can not preserve permissions, although I am not sure as I do not use ntfs enough. I would not expect the types of problems your are having, however, even with ntfs.

May I suggest you try backing up your data, making an ext2 or ext3 partition, copy your data, then re-try rsync.

---

### Post by Donny Bahama on 2010-03-10
> **bodhi.zazen said:**
> May I suggest you try backing up your data, making an ext2 or ext3 partition, copy your data, then re-try rsync.That's precisely what I'm trying to do. And in the process of step 1 (backing up my data), I'm getting this spontaneous unmounting. :(

---

### Post by bodhi.zazen on 2010-03-10
Anything in the logs ?

Error message on the command line ?

```
dmesg | tail
```

---

### Post by Donny Bahama on 2010-03-10
Last night, I booted my notebook into Windows, attached the destination drive and ran a chkdsk. Problems were found and fixed and I reattached it to the server. It seems to be working more reliably since then (but I can't be certain since the other one continues to act up!) I guess I'll try the same thing with the source drive. 

Maybe while I'm at it I'll wipe the destination drive and give it an ext3 (ext4?) filesystem before trying to rsync again.

At the same time, I'm trying to get creative about where to put the server when it's all set up. I have a great server case and could install all these drives via the ATA interface rather than using USB. As spynappels pointed out, I'd have fewer failure points and much faster throughput. I just don't know where I'd put the darn thing!

---

### Post by Donny Bahama on 2010-03-10
> **bodhi.zazen said:**
> Anything in the logs ?

Error message on the command line ?

```
dmesg | tail
```I'm new enough to linux that I don't really know what(/where/how) to look for in the logs. (Also I shutdown several hours ago.) There were error messages on the command line. I don't remember what they were.

I think I'll try doing a chkdsk on the source drive in Windows and format the destination drive as ext3 then try again. If the problem occurs again, I'll post the CL output and check the logs per your instructions.

This is so frustrating. I'm trying to rsync about 700GB to 3 x 300GB drives. It would be SO much easier if I could [LIST=1]
[*]resize the ntfs partition to 700GB
[*]create an 800GB ext3 partition in the free space
[*]transfer the files from the ntfs partition to the ext3 partition
[*]delete the ntfs partition
[*]expand the ext3 partition to use the freed space
[/LIST]I started to do that, then got [totally stuck]("http://ubuntuforums.org/showthread.php?t=1420846"). Any thoughts or suggestions on that?

---

### Post by bodhi.zazen on 2010-03-10
Boot a live CD and use Gparted ? Gparted has a graphical interface.

Edit: if you get error messages, post them here we can (hopefully) help more if we see the error messages.

---

### Post by Donny Bahama on 2010-03-10
> **bodhi.zazen said:**
> Boot a live CD and use Gparted ? Gparted has a graphical interface.Unfortunately, the server has no optical drive. Is there no way to do the same things Gparted is doing - but from the command line?
> Edit: if you get error messages, post them here we can (hopefully) help more if we see the error messages.Will do. Thanks ***very much*** for the help!

---

### Post by bodhi.zazen on 2010-03-10
How do you boot it then ? From a usb ?

In that case, use unetbootin (or other method) to put the ubuntu iso on a USB.

---

### Post by Donny Bahama on 2010-03-10
> **bodhi.zazen said:**
> How do you boot it then ?It has an (internal) system drive.
> In that case, use unetbootin (or other method) to put the ubuntu iso on a USB.OK. I'll check into that.

---

### Post by Donny Bahama on 2010-03-14
I decided to really shake things up. Found a place for my server case to live and installed all the drives internally. With all my drives mounted as IDE or SATA drives, there've been no more mysterious unmounts.

I did use unetbootin to create a Karmic Live image. Gparted took care of my resize issues. I'm now in the process of an rsync to copy everything from the ntfs partition to the ext4. Then I'll delete the ntfs partition and expand the ext4 to fill the drive.

Thanks for all the help!

---

### Post by bodhi.zazen on 2010-03-15
Sweet !

Glad it seems to be working out for you.

---

### Post by hessiess on 2010-03-15
I realise that you have now fixed this problem, but I would be suspicious of the enclosure and/or cable used to connect the drive. I have a similar problem with a USB pen drive which unmounts itself, the problem here is a bad USB connection, slightly tapping the drive causes it to unmount.

---

