---
title: "Ubuntu Lucid 32bit actually i686??"
date: 2010-08-21
forum: The Cafe
---

### Post by MasterNetra on 2010-08-21
Having ubuntu 10.04.1 installed and fully updated (including linux kernal 2.6.32-24 from ubuntu's regular update), I was tweaking some things with Ubuntu tweak and on computer it claims its platform is i686, Is Ubuntu 10.04.1 naturally i686? Did the kernal update turn into i686, or is it a error reading on ubuntu tweak's part? I know i686 is essentially 32bit but with support for more then 3-4GB's of ram. I am just curious how my system became i686 when I installed the normal Ubuntu 32bit.

---

### Post by FuturePilot on 2010-08-21
You're confusing i686 with x86_64.

---

### Post by MasterNetra on 2010-08-21
> **FuturePilot said:**
> You're confusing i686 with x86_64.

No, but I think I am assuming i686 utilizes PAE by default... At anyrate been associating i386/x86 for 32bit...

---

### Post by LightningCrash on 2010-08-21
> **MasterNetra said:**
> Having ubuntu 10.04.1 installed and fully updated (including linux kernal 2.6.32-24 from ubuntu's regular update), I was tweaking some things with Ubuntu tweak and on computer it claims its platform is i686, Is Ubuntu 10.04.1 naturally i686? Did the kernal update turn into i686, or is it a error reading on ubuntu tweak's part? I know i686 is essentially 32bit but with support for more then 3-4GB's of ram. I am just curious how my system became i686 when I installed the normal Ubuntu 32bit.

normal Ubuntu 32-bit is i686.


32bit with more than 4GB of RAM is called 32-bit w/PAE


i386, i586, and i686 are all x86 instruction standards.

---

### Post by MasterNetra on 2010-08-21
> **LightningCrash said:**
> normal Ubuntu 32-bit is i686.


32bit with more than 4GB of RAM is called 32-bit w/PAE


i386, i586, and i686 are all x86 instruction standards.

ah. So yea I guess I was assuming PAE was automatically part of i686, my bad.

hmm I wonder why PAE isn't included by default in Ubuntu 32bit... is it unstable or something?

---

### Post by LightningCrash on 2010-08-21
> **MasterNetra said:**
> ah. So yea I guess I was assuming PAE was automatically part of i686, my bad.

hmm I wonder why PAE isn't included by default in Ubuntu 32bit... is it unstable or something?

not unstable at all... IIRC my last 32-bit install with 8GB of ram picked up the PAE automatically.

Could have been a different distro, though, it's been a while ;)

---

### Post by MasterNetra on 2010-08-21
> **LightningCrash said:**
> not unstable at all... IIRC my last 32-bit install with 8GB of ram picked up the PAE automatically.

Could have been a different distro, though, it's been a while ;)

hmm I wonder why then Canonical has neglected to included PAE in its 32bit version.

---

### Post by Starks on 2010-08-21
It is included. The -pae packages are in the repo and are used automatically if 4GB or more of RAM is detected during install.

---

### Post by fatality_uk on 2010-08-22
> **Starks said:**
> It is included. The -pae packages are in the repo and are used automatically if 4GB or more of RAM is detected during install.

Yup I am using 6GB ram in my server and PAE works fine.

---

