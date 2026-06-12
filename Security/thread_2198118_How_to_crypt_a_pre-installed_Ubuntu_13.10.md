---
title: "How to crypt a pre-installed Ubuntu 13.10"
date: 2014-01-07
forum: Security
---

### Post by stealth_anon on 2014-01-07
Hi all, as per subject, i have a new laptop with pre-installed Ubuntu 13.10.

My issue is that i would like now to crypt the disk at boot, as i usually do when installin other distro.

I have been reading around and found few different ways, but before doing any mess up wanted to ask here.

Thanks for any suggestion, comment or lesson learned.

---

### Post by Dave_L on 2014-01-07
Do you want to encrypt the entire disk, or only the home directory? The ecryptfs-migrate-home command will do the latter; the former probably requires a re-install.

---

### Post by stealth_anon on 2014-01-07
yep i am looking for the entire disk, something like truecrypetr does in windows.

---

### Post by Dave_L on 2014-01-07
This is probably the best method:
[https://help.ubuntu.com/community/FullDiskEncryptionHowto](https://help.ubuntu.com/community/FullDiskEncryptionHowto)

But it does require re-installation.

---

### Post by stealth_anon on 2014-01-08
Tx, Dave_L, i think i will reinstall from scratch if this is the case.

---

