---
title: "Why the hell do they sell external HDDs as FAT32?"
date: 2009-11-17
forum: The Cafe
---

### Post by cptrohn on 2009-11-17
formatted into FAT32?


Just bought a new one today and the first thing I had to do was format it into NTFS (would go with Ext4 but the mountpoints are just a pain to deal with)


I should have just bought a darn HDD and an enclosure...

---

### Post by Roasted on 2009-11-17
I wonder the same thing. Flash drives are understandable, but external hard drives that are getting bigger and bigger... doesn't make sense.

What's up with the mount points? I run 3 via fstab with EXT4 just fine without issues.

---

### Post by -grubby on 2009-11-17
1) OS X can't write to NTFS.
2) Old versions of Windows don't even know what NTFS is.

That's why.

---

### Post by cptrohn on 2009-11-17
> **-grubby said:**
> 1) OS X can't write to NTFS.
2) Old versions of Windows don't even know what NTFS is.

That's why.

Ok, that makes sense then.

---

### Post by cptrohn on 2009-11-17
> **Roasted said:**
> I wonder the same thing. Flash drives are understandable, but external hard drives that are getting bigger and bigger... doesn't make sense.

What's up with the mount points? I run 3 via fstab with EXT4 just fine without issues.

Yeah but I don't even have to run fstab with NTFS.... just plug and play.

---

### Post by FuturePilot on 2009-11-17
> **cptrohn said:**
> Yeah but I don't even have to run fstab with NTFS.... just plug and play.

I don't have my external drive in fstab and it's Ext3. Plug it in and it mounts, done.

---

### Post by RiceMonster on 2009-11-17
> **FuturePilot said:**
> I don't have my external drive in fstab and it's Ext3. Plug it in and it mounts, done.

Shouldn't this be the case for any file system supported by the kernel if you're running HAL/DeviceKit?

---

### Post by FuturePilot on 2009-11-17
> **RiceMonster said:**
> Shouldn't this be the case for any file system supported by the kernel if you're running HAL/DeviceKit?

Yes. But the OP made it sound like it was an issue with Ext4

---

### Post by HappyFeet on 2009-11-17
> **cptrohn said:**
> Yeah but I don't even have to run fstab with NTFS.... just plug and play.

Exactly. That's what I do.

---

### Post by Roasted on 2009-11-17
> **cptrohn said:**
> Yeah but I don't even have to run fstab with NTFS.... just plug and play.

So does ext3 and ext4. They auto mount to a generic folder, just as ntfs does. I have a 160gb external drive with ext3 and when I plug it in to my Ubuntu Jaunty PC on my desk here, it auto mounts just fine.

You only need to mess with fstab if you need the drives to mount automatically upon boot. My 3 drives I spoke about are backup drives... which I want to mount automatically with my system boot, hence why I use fstab in that case.

---

### Post by phrizek on 2009-11-17
I always buy an enclosure + hard drive if I need an external. Much cheaper that way and no strange formatting issues.

---

### Post by Mike'sHardLinux on 2009-11-17
I am still curious what issues the OP was having with EXT4 on the external drive. As others have already stated, with an external drive, you shouldn't have to mess with mount points.

---

### Post by blueshiftoverwatch on 2009-11-17
> **-grubby said:**
> 1) OS X can't write to NTFS.
2) Old versions of Windows don't even know what NTFS is.

That's why.
That's why my 750GB external HD is formatted FAT32.

---

### Post by benj1 on 2009-11-17
isnt it because microsoft would want money if they used NTFS but if they use FAT32 they don't (or is that just FAT16?(it could still be a lower license fee i suppose))

---

### Post by markp1989 on 2009-11-17
> **-grubby said:**
> 1) OS X can't write to NTFS.
2) Old versions of Windows don't even know what NTFS is.

That's why.

alot of older versions of windows need drivers before they will even reconize an external hard drive, but that points still makes sence :D

---

### Post by Roasted on 2009-11-18
> **-grubby said:**
> 1) OS X can't write to NTFS.
2) Old versions of Windows don't even know what NTFS is.

That's why.

LOL. OSX. Who runs OSX anymore anyways. :P :P

---

### Post by Hallvor on 2009-11-18
> **blueshiftoverwatch said:**
> That's why my 750GB external HD is formatted FAT32.

Why didn`t you use ext3? It will fragment less and you can have files larger than 4 GB. If you need to access it from Windows, just install the fs-driver and it will read/write to ext3 flawlessly.

---

### Post by blueshiftoverwatch on 2009-11-18
> **Hallvor said:**
> Why didn`t you use ext3? It will fragment less and you can have files larger than 4 GB. If you need to access it from Windows, just install the fs-driver and it will read/write to ext3 flawlessly.
I don't care about fragmenting because 90% of the files that get put on the hard drive are never moved/changed. But the 4GB file size limit would present a problem if I want to backup my virtual hard drives onto it. I'll have to change it over.

Do the drivers that allow compatibility with ext3 work on Windows 7? Once I do that I'll just put the Windows-Ext3 drivers on my flash drive so I'll have access to them everywhere.

---

### Post by aysiu on 2009-11-18
> **-grubby said:**
> 1) OS X can't write to NTFS.
2) Old versions of Windows don't even know what NTFS is.

That's why.
Added to that, there isn't a great urgency for most people to switch over to anything else.

The only real limitation to FAT32 is not being able to store files larger than 4 GB. Unless you use a lot of virtual machines or back up long, high definition movies, you probably don't have a lot of files that large.

---

### Post by RiceMonster on 2009-11-18
> **Roasted said:**
> LOL. OSX. Who runs OSX anymore anyways. :P :P

Are you serious?

---

### Post by t0p on 2009-11-18
Heh.  I saw the title of this thread in the listing and thought "You what!?"  Yeah, why the hell do they sell external HDDs?  What possible use is an external HDD?  LOL.

Surely I'm not the only one?

---

### Post by Marlonsm on 2009-11-18
They use FAT32 because pretty much all computers can read/write to it. 
And if you know about it's limitations it's likely that you also know how to reformat it to other FS. Most people won't get even close to storing files bigger than 4Gbs.

> **t0p said:**
> Heh.  I saw the title of this thread in the listing and thought "You what!?"  Yeah, why the hell do they sell external HDDs?  What possible use is an external HDD?  LOL.

Surely I'm not the only one?

No, you're not the only one...

---

### Post by FuturePilot on 2009-11-18
> **Hallvor said:**
> Why didn`t you use ext3? It will fragment less and you can have files larger than 4 GB. If you need to access it from Windows, just install the fs-driver and it will read/write to ext3 flawlessly.
Not if you used any recent distro to format it. Just about all distros these days default to formating Ext3 with an inode size of 256. The Windows Ext3 driver only works with an inode size of 128.

> **t0p said:**
> Heh.  I saw the title of this thread in the listing and thought "You what!?"  Yeah, why the hell do they sell external HDDs?  What possible use is an external HDD?  LOL.

Surely I'm not the only one?

I thought the same thing too. I thought I must be weird or something for using one of these external hard drive thingies.

---

### Post by aysiu on 2009-11-18
I've retitled the thread to make more sense.

---

### Post by alphaniner on 2009-11-18
You spoiled the fun!

---

### Post by Hallvor on 2009-11-18
> **blueshiftoverwatch said:**
> I don't care about fragmenting because 90% of the files that get put on the hard drive are never moved/changed. But the 4GB file size limit would present a problem if I want to backup my virtual hard drives onto it. I'll have to change it over.

Do the drivers that allow compatibility with ext3 work on Windows 7? Once I do that I'll just put the Windows-Ext3 drivers on my flash drive so I'll have access to them everywhere.

It does support Vista, so it probably works with Windows 7 too.

[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by cptrohn on 2009-11-18
> **Mike'sHardLinux said:**
> I am still curious what issues the OP was having with EXT4 on the external drive. As others have already stated, with an external drive, you shouldn't have to mess with mount points.

I've never been able to do this in ext3 or ext4....

---

