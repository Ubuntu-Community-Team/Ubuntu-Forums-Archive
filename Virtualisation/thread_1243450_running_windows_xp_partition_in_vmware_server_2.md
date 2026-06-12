---
title: "running windows xp partition in vmware server 2"
date: 2009-08-18
forum: Virtualisation
---

### Post by mesman00 on 2009-08-18
My hard drive currently dual boots ubuntu 9.04 and Windows XP.  Is there a way to run my Windows XP partition as a guest operating system on Ubuntu using vmware server 2?

I have seen ways to do this with older versions of vmware server, but none for version 2.  Thanks.

*edit* i would actually prefer to be able to do this using virtual box 3.

---

### Post by SoftwareExplorer on 2009-08-19
Would it be good enough to make a backup of the XP and then restore it in the Virtualbox? If so, I could help you do that. Iirc, there are some issues when VMware boots a native partition and then the partition is booted natively because things keep changing. Mainly, XP would probably want to be activated every time you booted it on a different hardware. I don't think virtualbox can boot a partition on a native hardisk. If you changed XP from on the native hard drive, then you would have to get activation out of the way just once.

---

