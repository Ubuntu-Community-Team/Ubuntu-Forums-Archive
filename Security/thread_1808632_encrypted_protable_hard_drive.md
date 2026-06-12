---
title: "encrypted protable hard drive"
date: 2011-07-20
forum: Security
---

### Post by SeaKing on 2011-07-20
Now since 1TB 2,5" hard drives have been released and are payable I've thought about buying one. The most improtant issue for me when using a protable drive is security and data security. I found the "Western Digital My Passport Essential" with hardware encryption but the description says that only Windows and MAC operating systems are supported not Linux in anyway. 
My question is are there any significant diffetences between the WD hardware decryption or a truecrypt container/drive? And is there another program out there better for this job? I want to use the drive on Windows and Linux systems.

---

### Post by bodhi.zazen on 2011-07-20
> **SeaKing said:**
> Now since 1TB 2,5" hard drives have been released and are payable I've thought about buying one. The most improtant issue for me when using a protable drive is security and data security. I found the "Western Digital My Passport Essential" with hardware encryption but the description says that only Windows and MAC operating systems are supported not Linux in anyway. 
My question is are there any significant diffetences between the WD hardware decryption or a truecrypt container/drive?

Depends on who you ask, WD will claim their encryption is superior in some way.

If you ask me, you are unlikely to notice any significant performance impact with encryption, let alone a performance impact of one vs another algorithm.

> And is there another program out there better for this job? I want to use the drive on Windows and Linux systems.

Personally I would use LUKS, with multiple encrypted partitions, rather then a singly monolithic encrypted partition.

LUKS is cross platform, secure, and open source.

---

### Post by SeaKing on 2011-07-21
So in the end, the so called hardware encryption is also just a software, only made by WD?

> **bodhi.zazen said:**
> 
Personally I would use LUKS, with multiple encrypted partitions, rather then a singly monolithic encrypted partition.


I took a look at LUKS/FreeOTFE and found a portable Version for Win OS and I instandly tried them. The result unter Windows7 64 Bit Version (nearly all Windows7 users use) is that I cannot start it because the delivered drives does not have a digital signature and so windows do not load them, even with administrator privileges.

Is truecrypt much worse than LUKS?

---

### Post by bodhi.zazen on 2011-07-21
> **SeaKing said:**
> So in the end, the so called hardware encryption is also just a software, only made by WD?

As far as I know, there has to be software to drive the hardware.

> I took a look at LUKS/FreeOTFE and found a portable Version for Win OS and I instandly tried them. The result unter Windows7 64 Bit Version (nearly all Windows7 users use) is that I cannot start it because the delivered drives does not have a digital signature and so windows do not load them, even with administrator privileges.

Is truecrypt much worse than LUKS?

There is nothing wrong with truecrypt, it is popular, and if it worksforyou, go for it.

---

