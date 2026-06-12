---
title: "Ubuntu Server 7.10 issues"
date: 2008-07-08
forum: Server Platforms
---

### Post by dunvar on 2008-07-08
I have just loaded Ubuntu Server 7.10 and I am having an issue with it on booting after the install.  During install I noticed that it identified the hard drive as sda.  This is an IDE drive and not a SCSI, thus I think this maybe my issues.  As I had Debian on it identified as hda and it would boot.

During boot it stops at "Running local boot scripts (/etc/rc.local) {OK}" 

Can someone please help me on this?

Thanks,

Ken

---

### Post by cdenley on 2008-07-08
> **dunvar said:**
> I have just loaded Ubuntu Server 7.10 and I am having an issue with it on booting after the install.  During install I noticed that it identified the hard drive as sda.  This is an IDE drive and not a SCSI, thus I think this maybe my issues.  As I had Debian on it identified as hda and it would boot.

During boot it stops at "Running local boot scripts (/etc/rc.local) {OK}" 

Can someone please help me on this?

Thanks,

Ken

Sounds fine to me. Try pressing enter, or ctrl+alt+f2. The login is available before /etc/rc.local is run, so that message you refer to is printed AFTER the login prompt. Why aren't you using hardy?

---

