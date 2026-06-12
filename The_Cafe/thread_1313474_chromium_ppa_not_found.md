---
title: "chromium ppa not found"
date: 2009-11-03
forum: The Cafe
---

### Post by sdowney717 on 2009-11-03
scott@scott-desktop:~$ sudo add-apt-repository ppa:chromuim-daily
[sudo] password for scott:
HTTP Error 404: Not Found
scott@scott-desktop:~$ sudo add-apt-repository ppa:chromuim-daily
HTTP Error 404: Not Found
scott@scott-desktop:~$

---

### Post by schauerlich on 2009-11-03
cool story, bro.

---

### Post by Frak on 2009-11-03
> **sdowney717 said:**
> scott@scott-desktop:~$ sudo add-apt-repository ppa:chrom**iu**m-daily
[sudo] password for scott:
HTTP Error 404: Not Found
scott@scott-desktop:~$ sudo add-apt-repository ppa:chrom**iu**m-daily
HTTP Error 404: Not Found
scott@scott-desktop:~$

EHEM, fixed.

---

### Post by dirtylobster on 2009-11-03
> **sdowney717 said:**
> scott@scott-desktop:~$ sudo add-apt-repository ppa:chromuim-daily

try sudo add-apt-repository ppa:chromium-daily/ppa

and oh, wrong forum.

---

### Post by dirtylobster on 2009-11-03
> **Frak said:**
> EHEM, fixed.

lol, didn't even notice that

---

### Post by sdowney717 on 2009-11-03
thanks working now

> scott@scott-desktop:~$ sudo add-apt-repository ppa:chromium-daily/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv FBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
gpg: key 4E5E17B5: public key "Launchpad PPA for chromium-daily" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
scott@scott-desktop:~$ 


you still have to refresh the package lists in synaptic

---

### Post by Mr. Picklesworth on 2009-11-03
I know why you did that, I know why you did that!

(Someone's signature. Quickly, let's find him!)

---

