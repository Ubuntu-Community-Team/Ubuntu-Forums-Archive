---
title: "Partitioning"
date: 2008-08-13
forum: Windows
---

### Post by Ezlo4 on 2008-08-13
Okay, I've asked this question before in another thread but no one answered. Okay, so I have a 320 GB hard drive and I made a 40 GB partition in order to install Vista. However, when I try to install Vista it says that no drives were found to install Vista into. 

What can I do to install Vista?

---

### Post by tamoneya on 2008-08-13
most likely an issue in the BIOS.  Try going and setting sata for compatibility mode.  This isnt supposed to be necessary for vista but it couldnt hurt.  Out of curiosity what is the motherboard model on the computer.

---

### Post by kernelhaxor on 2008-08-13
did u format that partition with ext3 or ntfs?
I wud try ntfs

---

### Post by castor_troy on 2008-08-13
Which tool did you use to create the partition ? 

What type of partition did you create ? ntfs or ext3 ?

---

### Post by jimv on 2008-08-13
People, it's not a partition problem.  Even if Vista couldn't see the partition, it would still show the harddrive and he would would be able to have Vista create a parition.

---

### Post by Ezlo4 on 2008-08-13
> **jimv said:**
> People, it's not a partition problem.  Even if Vista couldn't see the partition, it would still show the harddrive and he would would be able to have Vista create a parition.

Well, if it's not a problem with the partition then what's the issue? And what can I do to solve this problem?

---

### Post by tamoneya on 2008-08-13
> **Ezlo4 said:**
> Well, if it's not a problem with the partition then what's the issue? And what can I do to solve this problem?

seems to be something relating to the BIOS and windows seeing the disk.  Even if there was a partition issue windows would see the disk and you could tell it to install into the whole disk. You obviously dont want to do that but because that option didnt show up that means that windows doesnt see the disk at all.  Try setting the drive for IDE/compatibility mode.  Also do you know what your motherboard model is?  Do you have any RAIDs or anything?

---

### Post by Ezlo4 on 2008-08-13
> **tamoneya said:**
> seems to be something relating to the BIOS and windows seeing the disk.  Even if there was a partition issue windows would see the disk and you could tell it to install into the whole disk. You obviously dont want to do that but because that option didnt show up that means that windows doesnt see the disk at all.  Try setting the drive for IDE/compatibility mode.  Also do you know what your motherboard model is?  Do you have any RAIDs or anything?

I'm sorry but I have no idea how to do any of those things. :(

---

### Post by logos34 on 2008-08-13
I agree with Tamoneya--it's more than likely something in the Bios--hard disk detect settings or sata mode (AHCI or IDE emulation mode, vista can run under both)

Look up the manual for your motherboard--the Bios section will tell you exactly where it is.

---

### Post by TreeFinger on 2008-08-13
"General Help

Description: General Help
All your general support questions for Ubuntu, Kubuntu, Edubuntu and Xubuntu."

[www.vistaforums.org](www.vistaforums.org) ?

---

### Post by bodhi.zazen on 2008-08-13
> **Ezlo4 said:**
> Okay, I've asked this question before in another thread but no one answered. Okay, so I have a 320 GB hard drive and I made a 40 GB partition in order to install Vista. However, when I try to install Vista it says that no drives were found to install Vista into. 

What can I do to install Vista?

Moved to "Windows discussions" for obvious reasons.

---

### Post by tamoneya on 2008-08-13
you could also try swapping around the sata ports and IDE channels.  I dont really know why it would make any difference since we know the ports work (it worked in linux) but I also think it couldnt hurt to give it a try.

---

### Post by MaxIBoy on 2008-08-14
Is the hard drive IDE, or SATA, or what?

---

### Post by Ezlo4 on 2008-08-15
This is a problem I'm having for a some time now. I would really like to solve it in the next week or so.

---

