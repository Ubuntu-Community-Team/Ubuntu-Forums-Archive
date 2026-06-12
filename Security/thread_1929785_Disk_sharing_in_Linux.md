---
title: "Disk sharing in Linux"
date: 2012-02-22
forum: Security
---

### Post by aajax on 2012-02-22
I use multi-boot (dual-boot) to install more than one copy of Ubuntu onto a drive.  This serves different purposes with respect to managing changes to the base operating system.  Since both instances of the operating system are used to process the same data I have created additional partitions just for that purpose.  This has been working pretty good if I use exactly the same version of Ubuntu (in this case Ubuntu Server 10.04).  However, I'd now like to migrate to Ubuntu Desktop.  For now Version 10.04 would be fine.  Both Ubuntu Desktop and Ubuntu Server have the exact same underlying software for the packages (for example MySQL) that are common between them.  However, the data sharing breaks because different user-ids end up being created for certain user names such as mysql.  This leads me to conclude that there is a need for the system admin to be able to control what user-ids are assigned for select user names such as mysql.  The idea that the installation software makes arbitrary decisions about what values to assign ends up creating problems such as described above.  Without some way to control this aspect of software installation we're stuck with a poorly designed system.

I'm hoping that this problem is merely a matter of some lack of knowledge on my part and that someone might be able to refer me to sources of information that I could use to overcome this deficiency.

Please help!

---

