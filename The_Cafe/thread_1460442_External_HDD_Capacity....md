---
title: "External HDD Capacity..."
date: 2010-04-22
forum: The Cafe
---

### Post by speedwell68 on 2010-04-22
OK I have done a quick search for the answer to this question, but alas I don't seem to be able to find the answer.  I have a 250GB Freecom external HDD and it is currently formatted as a FAT32 drive, giving me 232GB of available space.  Would I gain more free space on the drive if I reformatted it to EXT4?

---

### Post by JC Cheloven on 2010-04-22
Usually the OS reserves some 5% of the volume fot its own use (so that it can write to disk even if the user populates it). This is not really needed for a data volume (with no os). If you format in ext, you'll be able to free that percentage thru  the tune2fs command. [B][U]Please see the manpages for details.
[/U][/B]

As a hint/example:
```
sudo tune2fs -m 0 /dev/sda3
``` will free for you the aforementioned space in sda3.

Regards
JC
EDIT: BTW, a question for a support forum, not the cafe :-)

---

### Post by speedwell68 on 2010-04-22
> **JC Cheloven said:**
> Usually the OS reserves some 5% of the volume fot its own use (so that it can write to disk even if the user populates it). This is not really needed for a data volume (with no os). If you format in ext, you'll be able to free that percentage thru  the tune2fs command. [B][U]Please see the manpages for details.
[/U][/B]

As a hint/example:
```
sudo tune2fs -m 0 /dev/sda3
``` will free for you the aforementioned space in sda3.

Regards
JC
EDIT: BTW, a question for a support forum, not the cafe :-)

Thanks for that.

---

### Post by scouser73 on 2010-04-22
> **speedwell68 said:**
> OK I have done a quick search for the answer to this question, but alas I don't seem to be able to find the answer.  I have a 250GB Freecom external HDD and it is currently formatted as a FAT32 drive, giving me 232GB of available space.  Would I gain more free space on the drive if I reformatted it to EXT4?

You'd get more space if you reformatted it to NTFS, I know that sounds silly as NTFS is a native filesystem of Windows but it's true.

---

### Post by CharlesA on 2010-04-22
> **scouser73 said:**
> You'd get more space if you reformatted it to NTFS, I know that sounds silly as NTFS is a native filesystem of Windows but it's true.

What's the reason for that?

---

### Post by scouser73 on 2010-04-23
The reason I format to NTFS rather than EXT4 or any other notable Linux filesystem is that less space is taken up.

If you see the screen shots, I've got two external 500GB HD's.

One is formatted to EXT4 & the other is formatted to NTFS

EXT4 says that the total capacity is 458.4GB, whereas NTFS is showing 465.8GB.

**Drive formatted to EXT4**

[[IMG]http://img97.imageshack.us/img97/7760/ext4.th.png[/IMG]](http://img97.imageshack.us/my.php?image=ext4.png)

**Drive formatted to NTFS**

[[IMG]http://img63.imageshack.us/img63/2416/ntfs.th.png[/IMG]](http://img63.imageshack.us/my.php?image=ntfs.png)

---

### Post by CharlesA on 2010-04-23
Thanks. I'm guessing the other 7 gigs is taken up by the Journal.

---

### Post by speedwell68 on 2010-04-23
I have just formatted to EXT4 and starting restoring the data on it now.:D

I will try it under NTFS again another time.  I just want to maximise the free space available really and be able to write files that are in excess of 4GB in size.

---

### Post by CharlesA on 2010-04-23
I must be a huge space hog, since my monthly backup from my server takes up just under 2TB. That drive is formatted as EXT3.

Media server, so take it with a grain of salt. I think documents and whatnot take up around 200GB.

---

### Post by speedwell68 on 2010-04-23
> **CharlesA said:**
> I must be a huge space hog, since my monthly backup from my server takes up just under 2TB. That drive is formatted as EXT3.

Media server, so take it with a grain of salt. I think documents and whatnot take up around 200GB.

Hell, my total backup is only 86GB.

---

### Post by CharlesA on 2010-04-23
> **speedwell68 said:**
> Hell, my total backup is only 86GB.

That is not bad at all. I've got images of machines that take up 89GB of space. *twitch*

185GB total, give or take.

---

