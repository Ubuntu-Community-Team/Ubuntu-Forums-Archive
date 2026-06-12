---
title: "Ubuntu 7.04 File Server for Windows Clients"
date: 2007-10-11
forum: Server Platforms
---

### Post by johnathanamber on 2007-10-11
Hello,

I have checked other threads but I need more information.

I want to setup a File Server with Ubuntu 7.04 and have it work with Windows Clients. I also have a BIOS RAID array running with two IDE hard drives with data on them already. The server is currently working as  Windows 2003 File Server. I will format and reinstall with Ubuntu on a seperate partition with all of the data on the rest of the drive.

Is it possible to get a step-by-step to get all this working?

Your help is very much appreciated.

BTW, this will be going on an AMD Sempron 64-bit processor based system.

God bless,
Johnathan

---

### Post by gautada on 2007-10-11
Lets take this one step at a time first get [Ubuntu installed]("https://help.ubuntu.com/community/WindowsDualBoot").  Then just setup [samba]("https://help.ubuntu.com/community/SettingUpSamba").

I am not sure from your post if you are trying to dual boot or not if not then you probably just need to mount an [ntfs partition]("https://help.ubuntu.com/community/MountNtfsOnBoot").


[SIZE="6"]**[COLOR="Red"]BACKUP ALL OF YOUR DATA FIRST!!!![/COLOR]**[/SIZE]

---

### Post by johnathanamber on 2007-10-11
OK sorry for not clarifying...

I am replacing Windows 2003 Server with Ubuntu 7.04.

I have BIOS controlled RAID.

I currently have two partition with RAID 1, both partitions are setup as NTFS.

I want to keep the parition sizes the same if I have to reformat the drives with ext3.

And also, which partition format is best for file servers?

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2007-10-12
Hello everyone,

OK I realize that this is a big order... I have gather several documents that I can take bits and peices from to get this working. I just have another question...

Which partition format is best to do this? Can I keep the data partition as NTFS or do I have to convert to ext3 or another partition type? Then which one is best?

Thank you and God bless,
Johnathan

---

### Post by elvis on 2007-10-12
For native Linux systems, ext3 is recommended.

What type of RAID controller have you got in the system?  Many low-end motherboards use software drivers to do RAID calculations, and a great deal of these software manufacturers choose not to support Linux or release specifications to the free software community.  As such, there may be a chance your onboard RAID will not work.

However don't let this stop you.  Linux has it's own software RAID systems which is infinitely superior in both terms of performance and tools and maintenance compared with cheap on-board RAID controllers.

Regarding your desire to set up a file server for Windows clients, I strongly recommend reading "Samba 3 By Example" byJohn H. Terpstra.  

Online version here:
[http://www.samba.org/samba/docs/man/Samba-Guide/](http://www.samba.org/samba/docs/man/Samba-Guide/)

Paperback here:
[http://www.amazon.com/Samba-3-Example-Practical-Successful-Deployment/dp/013188221X/ref=pd_bbs_sr_1/104-9989214-0738322?ie=UTF8&s=books&qid=1192233005&sr=8-1](http://www.amazon.com/Samba-3-Example-Practical-Successful-Deployment/dp/013188221X/ref=pd_bbs_sr_1/104-9989214-0738322?ie=UTF8&s=books&qid=1192233005&sr=8-1)

I set these things up for a living, and I've yet to come across any Samba documentation that does a better job than that book.  It's an excellent resource for Samba administrators.

---

