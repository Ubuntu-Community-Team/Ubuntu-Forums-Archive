---
title: "Deleting/ Permanently Erasing old files"
date: 2010-06-18
forum: Security
---

### Post by mailc on 2010-06-18
I am going to give away a dual boot laptop (XP and Ubuntu).  How do I delete all the old stuff? The new owner is young and inquisitive and I would prefer that he not show off his skills with my passwords.                                        .                         I was told  that a hard drive does not really delete things (documents, pics, videos etc )but it keeps adding them  till it fills up and then starts overwriting the oldest files.  That is supposedly in Windows, and in Ubuntu ‘Trash’ apparently does not really delete things.                   .                                                                       .How do I get to all that stuff and delete it - permanently? .              Thanks in advance

---

### Post by yeleek on 2010-06-18
Personally?  I'd can the entire disk and reinstall fresh (or have him do it).  As securely erasing files alone doesn't guarantee security, for example data can be recovered from the windows pagefile.

[http://www.dban.org/](http://www.dban.org/)

For complete disk wiping

---

### Post by mkvnmtr on 2010-06-18
I have no idea about Windows but in Ubuntu the secure-delete package includes programs to completely erase any file, wipe all unused space, wipe swap space and wipe memory.

---

### Post by wojox on 2010-06-18
> **yeleek said:**
> Personally?  I'd can the entire disk and reinstall fresh (or have him do it).  As securely erasing files alone doesn't guarantee security, for example data can be recovered from the windows pagefile.

[http://www.dban.org/](http://www.dban.org/)

For complete disk wiping

+1 for dban

---

### Post by Darthwolfs on 2010-06-18
ok im taking a computer forensics class right now at school and i have learned that the true only way to erase data from a hard drive it a magnet. just deleting it or reformatting the entire drive, files can be retrieved.

all programs do, like this dban, is use an mathematical algorithm that hides them, and allows the hard drive sector be written over with other files. any and all files, no matter how many times the disk has been over written can be retrieved.

so yeah your best bet is to just put a new drive in

---

### Post by rookcifer on 2010-06-18
> **Darthwolfs said:**
> ok im taking a computer forensics class right now at school and i have learned that the true only way to erase data from a hard drive it a magnet. just deleting it or reformatting the entire drive, files can be retrieved.

You learned wrong.  If the data is not overwritten then, yes, it can be retrieved.  A mere format doesn't do anything to overwrite the data.  If this is what your instructor meant, then he/she is correct. However, if he meant that overwritten data can be retrieved, he is dead wrong.  The truth, as shown by experiments, is that data overwritten one time is not recoverable (people who tell you otherwise are perpetuating an urban legend.  Ask your instructor to give you examples of it being done, he/she won't be able to).

Overwriting a disk can be done with several tools, of which D-ban is the most familiar.  An easier way is just to pop in an Ubuntu liveCD, open the terminal and run:

```
sudo shred -vfz -n 1 /dev/sdx
```

Or, "dd" will do the same thing:

```
sudo dd if=/dev/zero of=/dev/sdx bs=1M
```

Or, you can use the "secure erase" utility built into most modern drives by using "hdparm."  Google that if interested.

> all programs do, like this dban, is use an mathematical algorithm that hides them, and allows the hard drive sector be written over with other files. any and all files, no matter how many times the disk has been over written can be retrieved.


That is incorrect.  If your instructor is teaching this, you really need a new instructor.  He doesn't know what he is talking about.

Why don't you tell your instructor that you will overwrite a hard disk with the methods I gave above and then ask him to recover the data in front of the class.  If he says there isn't enough time, tell him to take it to a data recovery firm and see what they tell him (they will tell him what I am telling you -- it can't be done).

---

### Post by FuturePilot on 2010-06-18
> **rookcifer said:**
> You learned wrong.  If the data is not overwritten then, yes, it can be retrieved.  A mere format doesn't do anything to overwrite the data.  If this is what your instructor meant, then he/she is correct. However, if he meant that overwritten data can be retrieved, he is dead wrong.  The truth, as shown by experiments, is that data overwritten one time is not recoverable (people who tell you otherwise are perpetuating an urban legend.  Ask your instructor to give you examples of it being done, he/she won't be able to).

Overwriting a disk can be done with several tools, of which D-ban is the most familiar.  An easier way is just to pop in an Ubuntu liveCD, open the terminal and run:

```
sudo shred -vfz -n 1 /dev/sdx
```

Or, "dd" will do the same thing:

```
sudo dd if=/dev/zero of=/dev/sdx bs=1M
```

Or, you can use the "secure erase" utility built into most modern drives by using "hdparm."  Google that if interested.



That is incorrect.  If your instructor is teaching this, you really need a new instructor.  He doesn't know what he is talking about.

Why don't you tell your instructor that you will overwrite a hard disk with the methods I gave above and then ask him to recover the data in front of the class.  If he says there isn't enough time, tell him to take it to a data recovery firm and see what they tell him (they will tell him what I am telling you -- it can't be done).

This

---

### Post by bodhi.zazen on 2010-06-18
> **Darthwolfs said:**
> ok im taking a computer forensics class right now at school and i have learned that the true only way to erase data from a hard drive it a magnet. just deleting it or reformatting the entire drive, files can be retrieved.

all programs do, like this dban, is use an mathematical algorithm that hides them, and allows the hard drive sector be written over with other files. any and all files, no matter how many times the disk has been over written can be retrieved.

so yeah your best bet is to just put a new drive in

As has been pointed out, that theory has been debunked:

[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html")

I agree dban is "nice", you do not need it, overwrite your HD once with dd from a live CD.

---

### Post by mailc on 2010-06-18
I was going to install ' secure-delete ' from the Ubuntu Software Center but it says on its face:    "Even if you overwrite a file 10+ times, it can still be recovered. This package contains tools to securely wipe data from files, free disk space, swap and memory. "    Now would secure-delete not overwrite files but wipe them clean by some other method?

---

### Post by wilee-nilee on 2010-06-18
I have used dban from a hirens cd and there are several others that will write the drive to all 0's, but the dd is the easiest.

---

### Post by yetiman64 on 2010-06-18
I'd tend to agree with rookcifer, bodhi.zazen and willee-nillee that the easiest and simplest means is to use either dd or shred off a live cd terminal.

Shred off a live cd is how I usually clean a drive and the command given by rookcifer is perfect for your stated needs (I use the longhand command equivalent to rookcifer's ie. "sudo shred --force --verbose --iterations=1 --zero /dev/sdX" -don't include the quotation marks and change X to your device eg. a,b or c etc - note after shred or dd complete you will need to add a partition table back to the drive with gparted from the live cd before it can be reused, goto Device menu > Create Partition Table and click apply for an "msdos" partition table). 

Obviously repartitioning and a complete reinstall of your OSes will be necessary, but is advisable to be completely satisfied young curiosity fails at finding anything :).

Having used shred, then run the spinrite utility from grc.com (which can show the raw data on each sector as it is processed by spinrite), I noted that the complete drive was all blank sectors.

Although dban works well for some, I myself have had it fail at loading a few times and promptly gave up on it. 

Cheers yetiman64.

---

### Post by The Cog on 2010-06-19
Another vote for dd. Probably shred will do too, but I haven't looked at it myself so can't vouch for it.

As for secure delete, that may be fine for files that you delete with secure delete, but what about files that have already been deleted some other way? You can't point secure delete or shred at a file that's already been deleted, so its contents might stay on disk and un-overwritten for a long time. If you're really that paranoid, you have to overwrite the entire disk and then start afresh.

---

### Post by yeleek on 2010-06-19
Have to say I favour DBAN, just used to it, but whatever suits your fancy (so to speak).  A point worth mentioning, depending on the controller you may have problems with DBAN actually seeing the disks.

---

### Post by FuturePilot on 2010-06-19
> **The Cog said:**
> Another vote for dd. Probably shred will do too, but I haven't looked at it myself so can't vouch for it.

As for secure delete, that may be fine for files that you delete with secure delete, but what about files that have already been deleted some other way? You can't point secure delete or shred at a file that's already been deleted, so its contents might stay on disk and un-overwritten for a long time. If you're really that paranoid, you have to overwrite the entire disk and then start afresh.

sfill

---

### Post by Penguin Guy on 2010-06-19
> **Darthwolfs said:**
> ok im taking a computer forensics class right now at school and i have learned that the true only way to erase data from a hard drive it a magnet. just deleting it or reformatting the entire drive, files can be retrieved.

all programs do, like this dban, is use an mathematical algorithm that hides them, and allows the hard drive sector be written over with other files. any and all files, no matter how many times the disk has been over written can be retrieved.

so yeah your best bet is to just put a new drive in
That's completely wrong. Files are made up of bits:
```

1111111111111111 1111111111111111 1111111111111111
0111010110101101 1010111010110101 1010101010101011
1010101010101011 0101010101011010 1010101101011011
1010101010101101 0101011010101011 1010101010101010
1111111111111111 1111111111111111 1111111111111111

```
Most programs just remove the file header in a way that means the data *could* be recovered:
```

0000000000000000 0000000000000000 0000000000000000
0111010110101101 1010111010110101 1010101010101011
1010101010101011 0101010101011010 1010101101011011
1010101010101101 0101011010101011 1010101010101010
0000000000000000 0000000000000000 0000000000000000

```
But DBAN **completely overwrites** the **entire file** with random data **lots of times**:
```

0101010101010010 0101111010101000 0101010101010101
0111011101010101 1011111010101101 1101010110101101
1010101010101011 0011011111111000 0101010101010101
0101010101111100 1111110101010111 1110010110101010
1111101010101101 0000011010101001 1010101010101010

```
I assure you, after using DBAN, retrieving the data that was on the disk is **completely impossible**.

---

### Post by rookcifer on 2010-06-19
> **The Cog said:**
> As for secure delete, that may be fine for files that you delete with secure delete, but what about files that have already been deleted some other way? You can't point secure delete or shred at a file that's already been deleted, so its contents might stay on disk and un-overwritten for a long time. If you're really that paranoid, you have to overwrite the entire disk and then start afresh.

You can use secure-delete's free space wiper for this purpose.  This way you don't have to overwrite the entire disk.

---

### Post by bodhi.zazen on 2010-06-19
> **rookcifer said:**
> You can use secure-delete's free space wiper for this purpose.  This way you don't have to overwrite the entire disk.

Or just use dd to write zeros to the free space ;)

---

### Post by mailc on 2010-06-20
Thank you all for your input.
 I finally got to look at this a bit closer and hope to do it during the week. Here are the partitions:
 - /dev/sda1  : Dell Utility 41MB FAT ; 
 - /dev/sda2  : 55GB  NTFS ( XP);
 - /dev/sda3 : 20GB Extended (10GB ext4, 1.5GB ext4, 2.0GB Swap,6.5GB ext4);
 - /dev/sda4 : 5.0GB Dell REstore.

  I plan on burning an  Ubuntu live CD  and enter in the terminal: 
  'sudo dd if=/dev/zero of=/dev/sda2 bs=1M '  and also :
   'sudo dd if=/dev/zero of=/dev/sda3 bs=1M'  
  and leave sda1 and sda4 untouched just in case the new owner wants to reinstall Windows in the future.
 In the empty space of 75GB  I will use the live CD to reinstall Linux 10.04 on a 35GB extended partition  and leave the remaining 40GB empty.

 Any additional suggestions/comments  greatly appreciated.   I am not that computer savvy but would like to do it right and also learn something
  I am still surprised by what  ' secure-delete ' from the Ubuntu Software Center says on its face: 'Even if you overwrite a file 10+ times, it can still be recovered. ...... '  Are they referring to old and discredited info (Peter Gutmann's paper of 1996 ?)

---

### Post by StewartM on 2010-06-20
> **bodhi.zazen said:**
> As has been pointed out, that theory has been debunked:

[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html")



If it's an urban legend--and I read the link you provided--then I should say that it's gotten wide currency. An uncited article in the magazine *New Scientist* claimed that the NSA was able to read (detect?) a specific instance of a Unix installation underneath a Linux installation underneath a Windows one. I have also heard, personally, of attempts by the military to render the data on hard drives completely unrecoverable and how difficult this actually is. Also, the author only marginally and insufficiently (I believe) addressed the fact that the DoD did create standards for overwriting data, and that these standards are probably based upon well, *something*.

That being said, I do agree that 35 Gutmann passes are completely unwarranted, that commercial services and police forces don't have the capability to recover data overwritten even once (or even on non-overwritten data from damaged sectors) and that any such capability, if it exists, is in the domain of intelligence and military organizations. And even there it probably is not complete--there is a difference between the aims of a criminal/civil procedure, where a high standard of evidence is required, versus that of an intelligence organization, where *any* evidence you can dig out is maybe worth something and deems your effort a "success". 

StewartM

---

### Post by StewartM on 2010-06-20
> **Darthwolfs said:**
> ok im taking a computer forensics class right now at school and i have learned that the true only way to erase data from a hard drive it a magnet.

Actually--using the magnet, even a powerful one, is a poor way to render the stuff on a drive unrecoverable to a powerful adversary. (So are other physical means of destruction, except maybe those that turn the drive completely to ashes or powder). :p  Overwrite programs, if they do their job properly (and that's the big sticker, how do you know that they are?), are a better choice.

For your purposes, if the overwrite program performs as advertised, one overwrite is all you need.

StewartM

---

### Post by rookcifer on 2010-06-20
> **mailc said:**
>  I am still surprised by what  ' secure-delete ' from the Ubuntu Software Center says on its face: 'Even if you overwrite a file 10+ times, it can still be recovered. ...... '  Are they referring to old and discredited info (Peter Gutmann's paper of 1996 ?)

Yep, that's exactly what they're referring to.  Gutmann's paper was written in '96 and refers to old hard drives with different technology (and much smaller capacity) than modern EPRML's.  Moreover, even Gutmann himself says he has been misquoted; he claims that he never intended to say that 35 passes was necessary for all drives.  He has since said that "a few passes of random data" is the best we can do.  Experiments show that even a few passes is too much.  One overwrite renders data unrecoverable, even by MFM's.

---

### Post by mailc on 2010-06-22
> **mailc said:**
> ..   Here are the partitions:
 - /dev/sda1  : Dell Utility 41MB FAT ; 
 - /dev/sda2  : 55GB  NTFS ( XP);
 - /dev/sda3 : 20GB Extended (10GB ext4, 1.5GB ext4, 2.0GB Swap,6.5GB ext4);
 - /dev/sda4 : 5.0GB Dell REstore.

  I plan on burning an  Ubuntu live CD  and enter in the terminal: 
  'sudo dd if=/dev/zero of=/dev/sda2 bs=1M '  and also :
   'sudo dd if=/dev/zero of=/dev/sda3 bs=1M'  
  and leave sda1 and sda4 untouched just in case the new owner wants to reinstall Windows in the future.
 In the empty space of 75GB  I will use the live CD to reinstall Linux 10.04 on a 35GB extended partition  and leave the remaining 40GB empty.

 Any additional suggestions/comments  greatly appreciated.   I am not that computer savvy but would like to do it right and also learn something
 

 RE: Post # 18
 One more question: 
 somebody told me that it is a waste to leave 40GB of space for the possibility that the new owner may want to use the Dell re-installation for Windows. 
 Because if one reinstalls XP, that process will automatically take up the entire disk and Ubuntu will be erased .  A new repartitioning will have to be done and Ubuntu will have to be reinstalled. 

  Hope that somebody can confirm or elaborate on this . 
  Thanks

---

### Post by yetiman64 on 2010-06-22
> RE: Post # 18
 One more question: 
 somebody told me that it is a waste to leave 40GB of space for the  possibility that the new owner may want to use the Dell re-installation  for Windows. 
 Because if one reinstalls XP, that process will automatically take up  the entire disk and Ubuntu will be erased .  A new repartitioning will  have to be done and Ubuntu will have to be reinstalled. 
Don't know for sure about the Dell recovery utility, but the Acer recovery utility that was for XP on this laptop did exactly as suggested above. That is it would wipe all partitions and form one whole C:\ partition using the rest of the drive not used by the recovery utility. It would even wipe a Windows data partition (D:\) that I'd created, much to my annoyance at the time.

It may be a good idea from within XP to create a "recovery" cd or dvd (this preserves the ability to reinstall XP from disc - even this disc may wipe Ubuntu out, but at least it will preserve the original XP setup) and do away with the recovery partition.

---

### Post by bodhi.zazen on 2010-06-22
> **yetiman64 said:**
> Don't know for sure about the Dell recovery utility, but the Acer recovery utility that was for XP on this laptop did exactly as suggested above. That is it would wipe all partitions and form one whole C:\ partition using the rest of the drive not used by the recovery utility. It would even wipe a Windows data partition (D:\) that I'd created, much to my annoyance at the time.

It may be a good idea from within XP to create a "recovery" cd or dvd (this preserves the ability to reinstall XP from disc - even this disc may wipe Ubuntu out, but at least it will preserve the original XP setup) and do away with the recovery partition.

Normally, at least with Windows XP, one can install to C: and preserver all other partitions, you need to carefully read the information the recovery disks and / or windows installer gives you. If you blindly click (enter) the defaults you will use the entire drive.

I can not speak for more recent versions of windows (Vista or Windows 7) nor can I speak for all recovery CD / partitions.

When working with partitions or installing an OS you need to take great care and it is best to keep a back up of your data off the hard drive.

---

