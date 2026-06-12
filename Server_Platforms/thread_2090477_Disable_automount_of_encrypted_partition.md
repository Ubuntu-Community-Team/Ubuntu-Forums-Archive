---
title: "Disable automount of encrypted partition"
date: 2012-12-02
forum: Server Platforms
---

### Post by selepo on 2012-12-02
Hi, I'm running a headless server and have an encrypted partition (fileserver). It is encrypted with LUKS.

I would like to mount it manually, but it keeps asking for a password at startup which is kind of annoying on a headless server. 
I have tried all combinations of setting it to noauto/deleting the entry entirely in fstab and crypttab. 

I get a feeling it ignores these files and prompts for password based on something else during startup.

Please help!

/Selepo

---

### Post by Ms. Daisy on 2012-12-02
automount options are set in fstab. 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by selepo on 2012-12-02
> **Ms. Daisy said:**
> automount options are set in fstab. 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
Thanks for the quick reply. I realize that, as i stated above I have tried both setting options to "rw,noauto" and totally editing out the entry for this drive in fstab. I can confirm that does work for non-encrypted drives (that is they are no longer mounted on startup).
/selepo

---

### Post by selepo on 2012-12-04
Anyone ?
/Selepo

---

### Post by tubbygweilo on 2012-12-04
selepo,
At time of posting 112 people have given your problem some thought, some may be considering your problem, some may not have the knowledge to answer you question, some may have other things to do.

Give it a bit of time and those who can contribute may well do so.

ATB

---

### Post by howefield on 2012-12-04
Thread moved to the "*Server Platforms*" forum.

---

