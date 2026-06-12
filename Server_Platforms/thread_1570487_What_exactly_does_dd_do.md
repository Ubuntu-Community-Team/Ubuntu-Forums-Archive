---
title: "What exactly does dd do?"
date: 2010-09-08
forum: Server Platforms
---

### Post by BetterSense on 2010-09-08
If you use dd to dump one hard drive to another, is the new hard drive a perfect clone of the old one? In what ways? What are the "gotchas" of cloning a hard drive with dd? Is a "dd-clone" truly a clone?

I have a Windows box that acts as a serial monitor/relay for some industrial equipment. The box was set up by an outside vendor and I don't have confidence in their ability to always be available for support. I was thinking it would be a good idea to clone the hard drive so that if anything happens I can always slap in the cloned hard drive and restore the box to a known working state. I was going to do this by using two SATA-USB adapters and my Linux laptop, and just dd the current 1TB drive to a new 1TB drive. If I do this, will Windows boot the clone drive? Will it even know anything happened? What if the new hard drive is a different model, or brand, or has a different amount of cache? I need to be confident the new hard drive will work, or there's no point to the exercise. I would like to actually clone the hard drive and then put the CLONED drive back in the computer when I'm done; then I know that the cloning is working as planned. But I don't want to mess anything up, and I know next to zero about Windows.

---

### Post by CharlesA on 2010-09-08
Depends on how it's used. It is able to make an exact copy, but I'd suggust something such as clonezilla if you are trying to clone drives.

---

### Post by BetterSense on 2010-09-08
Ok, so what is different about using Clonezilla compared to using dd? What are the differences in the resulting clones?

---

### Post by CharlesA on 2010-09-08
There shouldn't be many difference outside of dd requiring a drive of the same size, where clonezilla can put the image on a drive that is larger.

It all depends on what you want to do.

---

### Post by BetterSense on 2010-09-08
Does dd really require the destination drive to be exactly the same size? In my case, the source and destination drive are both 1TB. They may be different brands though.

---

### Post by CharlesA on 2010-09-08
As far as I know they have to be the same size. You'd be ok to use dd then.

---

### Post by BetterSense on 2010-09-08
Ok, just to be sure, if /dev/sda is source hard drive and /dev/sdb is target hard drive, running 

```
dd if=/dev/sda of=/dev/sdb 
```

will copy the whole drive, that means MBR, partition table, and all partitions, correct? And it doesn't matter if source hard drive has windows filesystems on it, because dd doesn't care, right?

---

### Post by BkkBonanza on 2010-09-08
dd is dumb, it is just raw byte copy, it will just copy bytes with no regard for any meaning, structure or formats - until it runs out of bytes to copy. And and space left on the target after that will just be left as it was.

---

### Post by LightningCrash on 2010-09-08
Another note: you can dd to a file and then use that file in virtualization. You'll have to screw around with a bit to get it up and running though. ;)

---

### Post by BkkBonanza on 2010-09-08
Ya, and you can even create a gzip compressed file,

Backup,
dd if=/dev/sda conv=sync,noerror bs=64K | gzip -c  > /mnt/sda1/sda.img.gz

Restore,
gunzip -c /mnt/sda1/sda.img.gz | dd of=/dev/sda conv=sync,noerror bs=64K

Info found here,
[http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd](http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd)

He has a good idea about zeroing the free space first to let it compress down more.

---

### Post by BetterSense on 2010-09-08
Ok. Basically what I want to do first, since the computer is in production and I can't work on it at my leisure, is to make a perfect clone HDD of the computer. Then, I can work with that cloned HDD to make a zipped backup on the company servers or whatever.

Any guesses as to how long it will take to copy a 1TB image through two USB-to-SATA convertors? What block size should I tell dd to use?

---

### Post by BkkBonanza on 2010-09-08
If the drive is in active use during copying then you will likely end up with corruption of some sort. Parts will get written and changed while being copied.

Best I've seen for my USB or Sata drives is about 30MB/s. That means about 9 hours. And if the USB devices are on the same controller it will be slower.

In active use you are much better off making a file by file copy. And if there is database data on there even that won't be valid. With a file copy you can use rsync and multiple passes. Each pass rsync will skip what it did already. At the end you rsync again and it copies anything changed since the initial passes. The idea is the last pass transfers very little data to bring the images into sync.

---

### Post by BetterSense on 2010-09-08
I can take the computer down for the purposes of cloning the drive, but 9 hours is too long. If 30MB/s gives 9 hours, then 3Gb/s should be like, 45 minutes. I don't have a desktop to use, but I guess I could use the production box itself and a LiveCD.

---

### Post by BkkBonanza on 2010-09-08
You won't get anywhere near 3Gb/s on a usb - sata adapter.
Like I said, you can expect 30MB/s in the real world.

This is why I suggested rsync instead. You can do it in multiple shorter sessions fit in when convenient to be offline. 

Another option is to give dd start offset and length values so it can do the drive in sections.

---

### Post by BetterSense on 2010-09-08
The 3Gb/s is what it says on the drive. I mentioned it because I could hook the drive up with SATA and then it would go much faster than using the USB adapters. I don't think real-world HDD speeds are 3Gb/s, though. I'm not sure if it's the operating system or the HDD or the SATA that is the bottleneck there.

---

### Post by C.S.Cameron on 2010-09-08
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Drives do not need to be same size.

---

### Post by BkkBonanza on 2010-09-08
You can do a brief test on the actual or similar drive.

dd if=/dev/sda of=/dev/null

Let it run a bit and hit Ctrl-C. It will output statistics saying how fast.

I just did a test on my Hitachi 500GB drive connected to a 3Gb/s SATA interface and got 95MB/s. But I also know from past tries that it's slower when copying to a drive than to /dev/null.

Like wise you could test write speed on a spare drive.

dd if=/dev/zero of=/dev/sda 
(!!! wipes out data)

---

### Post by arrrghhh on 2010-09-08
> **BetterSense said:**
> I can take the computer down for the purposes of cloning the drive, but 9 hours is too long. If 30MB/s gives 9 hours, then 3Gb/s should be like, 45 minutes. I don't have a desktop to use, but I guess I could use the production box itself and a LiveCD.

Keep in mind, 3Gb/s = 384MB/s NOT 3GB/s!  See the difference?  Bits and bytes.

Plus, there's a ton of bottlenecks in the system - the hard drive is probably the least of your worries.  To truly get 3Gb/s, you'd need a RAID array and a very, very beefy computer.

---

### Post by BkkBonanza on 2010-09-08
His math isn't off if he can get specified speed. But that's unlikely.

30 MB/s = 9 hours
384 MB/s  = 9 * 30 /384 = 42 minutes.

I wouldn't bet on more than 100 - 125 MB/s so that's about 3 hours.

---

### Post by LightningCrash on 2010-09-19
> **CharlesA said:**
> Depends on how it's used. It is able to make an exact copy, but I'd suggust something such as clonezilla if you are trying to clone drives.

I used Clonezilla to do a P2V migration recently and I was VERY impressed. It was just flawless.

I used to do the whole LiveCD+DD/SSH thing but I think I will be keeping Clonezilla around for a long time ;)

---

### Post by windependence on 2010-09-19
dd is an extrememly versatile and useful tool in the right hands.
 
To clone a drive even if the destination is larger:
 
```
 
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror

```
 
Where sda is your source drive and sdb is your destination. Your device names may vary depending on your drives.
 
Don't do this to copy a live database - unpredictable things will happen.
 
As was stated, you may want to use rsync after the initial copy as you would only be transferring what has changed.
 
-Tim

---

