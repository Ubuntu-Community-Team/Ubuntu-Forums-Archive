---
title: "Ubuntu compatible on HP Proliant server?"
date: 2007-06-01
forum: Server Platforms
---

### Post by boumbo on 2007-06-01
Hi,

I am about to purchase a new HP Proliant server that will be used as a web server and was looking for advice or comments on installing Ubuntu server edition on it.

HP Proliant 
[http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/15351-15351-3328412-241644-241475-1121516.html]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/15351-15351-3328412-241644-241475-1121516.html")
**Server specs**:
HP DL380 G5 PROC 5140 / 2.33 GHz;

430028-005 SMARTBUY DL380 G5 X5140 HP-SAS;

375861-B21 72GB 10K SAS 2.5 HOT-PLUG HDD; ( 4 disks, 2 mirrors, one for the OS, the other for the data)

399771-B21 RPS 350/370/380 G5 KIT;

My 2 main concerns are the following:
1) **How compatible is Ubuntu server edition with SAS drives? Will I have to update the kernel differently then a regular SCSI drive? If so, is there documentation on the matter?**

2) As you can see I will be using 4 SAS HDs with 2 mirrors, one for the OS, the other for the data. **Will this configuration be possible with a RAID 1 setup on each HD? If so, is there documentation on how to setup mirror disks with Ubuntu? Documentation on how to setup RAID 1 configuration?**

Also, how stable is Ubuntu? Compared to another distro, like Gentoo Linux. We tried installing Gentoo, it took many failed installation attempts and alot of configuring just to install the OS, we're afraid of complex configuration of server security on it. **Is Ubuntu stable enough to run a LAMP web server with a CMS like Xoops (xoops.org)?**

**Btw, why is there 2 versions of Ubuntu available (LTS version and the other) ?** I know there's a difference in the support time, but why isn't the LTS version the only version available?

Sorry for so many questions, I want to make sure I am using a stable Linux Distro and compatible with this specific server.

Thanks.

Patrick S.

---

### Post by obimeister on 2007-06-02
I just installed ubuntu on ML350 G5, it has SAS and smart array controller E200i. No problems with hardware so far but NIC didn't got detected during installation (but worked after minor configuration after 1st boot). so

1. No need for extra configuration. Just configure raids in your controllers BIOS. 

2. Just make the raids with smart array bios. Then they will be shown you as a single device. 

I think ubuntu is as stable as anything, specially LTS version. 7.04 is for those who want to be on edge ;) LTS is something you usually see only on in commercial side like Red Hat or Novell.

---

### Post by zax123 on 2007-10-03
obimeister,

Could you please tell me what minor configuration change you had to make to get Ubuntu to recognize the NIC?

Glad to hear you got it working, I just ordered one.

Thanks!

Robert

---

### Post by cronos6 on 2007-11-12
Hello guys,

  Ubuntu Dapper/Edgy/Feisty/Gusty support fully HP servers hardware such as DL360, DL380 (G4), DL580 (G5)
  Install it with your eyes closed ;)

---

