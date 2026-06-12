---
title: "PC vs. Mac"
date: 2008-07-16
forum: Server Platforms
---

### Post by Sbwarren21 on 2008-07-16
Is there any difference between running a server on a MAC vs. a PC?  The is besides the version differences.

---

### Post by windependence on 2008-07-16
Shouldn't be, especially on newer Mac hardware.

-Tim

---

### Post by perfecttao on 2008-07-16
Depends on how you define the term Server....

What do you want it to do?  Web, Mail, SSH, Proxy, Authentication....

PC's and Macs are run on similar architecture now though, so the difference is narrowing.  It mostly comes down to software and i'm guessing that your referring to running Ubuntu server (seeing as this is a post on the Ubuntu forums ;)) Hardware is a consideration though....are you talkign about high availability (ie running RAID etc?)

---

### Post by Sbwarren21 on 2008-07-16
> **perfecttao said:**
> Depends on how you define the term Server....

What do you want it to do?  Web, Mail, SSH, Proxy, Authentication....

PC's and Macs are run on similar architecture now though, so the difference is narrowing.  It mostly comes down to software and i'm guessing that your referring to running Ubuntu server (seeing as this is a post on the Ubuntu forums ;)) Hardware is a consideration though....are you talkign about high availability (ie running RAID etc?)


If I go the MAC route, it is a G4.  However, the only people that will be on it will be controlled to around 50 users, or at least that is the plan.  I am basically wanting to run a ftp server as well as a forum area.  Similar to this.  I want to be able to assign user names and passwords.  This is a project for a college Professional Engineering Fraternity.

---

### Post by promodus on 2008-07-16
> **Sbwarren21 said:**
> If I go the MAC route, it is a G4.  However, the only people that will be on it will be controlled to around 50 users, or at least that is the plan.  I am basically wanting to run a ftp server as well as a forum area.  Similar to this.  I want to be able to assign user names and passwords.  This is a project for a college Professional Engineering Fraternity.

You can get the power pc version of ubuntu here:
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

The architecture is different, but the configurations should be the same as the intel version. The only thing you got to keep in mind as a server is that you have no BIOS on the PPC. (I'm sure you know that already) It would be a good idea to know alternate ways to boot the server, just in case you need to do a rescue.

For security, having a different architecture is good to have, you may not be exposed to the same level of hardware bugs. However, seeing that intel is more mainstream having support would be easier to relate with something that is more common. 

If the server role isn't that critical, give the PPC version a shot you'll get to learn the differences.

---

