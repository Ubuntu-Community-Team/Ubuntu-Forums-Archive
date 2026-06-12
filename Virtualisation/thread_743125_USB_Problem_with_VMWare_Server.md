---
title: "USB Problem with VMWare Server"
date: 2008-04-02
forum: Virtualisation
---

### Post by pburns5042 on 2008-04-02
I have VMWare server hosted on my Vista machine and guesting the latest Ubuntu 8 beta release. VMWare does not allow me to connect to my USB thumbdrive and therefore I cannot mount/see any USB devices inside Ubuntu.

---

### Post by pburns5042 on 2008-04-03
Ok so I get to answer my own question.

Well Vista bites me again! Case of love the hardware, but the OS supplied lets me down.

Please see [http://communities.vmware.com/thread/101227](http://communities.vmware.com/thread/101227)

VMWare Server 1 doesn't support Vista and neither will Server 2 it seems.

---

### Post by pburns5042 on 2008-04-04
Also, dont bother with Windows Virtual PC, it doesn't support USB either and takes forever to get Ubuntu installed.

The best bet appears to be VMWare Workstation which costs. I think it both supports USB and shared folders between the guest and the host, which would be nice. For now Ill just keep messing up the planet and burning CDs to transfer the data between the two!!

---

### Post by wey97 on 2008-06-04
> **pburns5042 said:**
> Also, dont bother with Windows Virtual PC, it doesn't support USB either and takes forever to get Ubuntu installed.

The best bet appears to be VMWare Workstation which costs. I think it both supports USB and shared folders between the guest and the host, which would be nice. For now Ill just keep messing up the planet and burning CDs to transfer the data between the two!!


You don't have to burn CDs!  Copy the files you want to an iso using a free tool such as [http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by fjgaude on 2008-06-04
Samba permits complete file transfers, seeing host from guest, guest from host, using file browsers, and other apps.

---

