---
title: "Hplip 0.9.7"
date: 2005-12-03
forum: Requests
---

### Post by eeclark on 2005-12-03
Currently the packages for HPLIP are 0.9.5 which is "root" dependant.
0.9.6 came out for debian/ubuntu users....and even 0.9.7 is out now.
Can we have a current package (that was actually tweaked for us)?

Thanks.

From the hpinkjet.sourceforge.net site:

HP Linux Imaging and Printing System (HPLIP) 0.9.6 Release
This release has the following changes.

5. Removed hardcoded "/var/run" paths, added "/var/run" path to hplip.conf. Removed root groupid check from hpiod. 
   This allows HPLIP to be run from different userid and groupid other than root (debian/ubuntu request).

---

### Post by eeclark on 2005-12-05
I am still new to Debian-based systems and if someone wants to point me in the direction to build my own deb package from the .tar.gz file of HPLIP, I would be happy to give it a try.

Thanks.
Ed

---

### Post by ERam123 on 2005-12-06
[QUOTE=eeclark]I am still new to Debian-based systems and if someone wants to point me in the direction to build my own deb package from the .tar.gz file of HPLIP, I would be happy to give it a try.

Thanks.
Ed[/QUOTE]

[http://hpinkjet.sf.net/](http://hpinkjet.sf.net/) should have the source files.

I wonder if this new version will fix my margin problems.

---

### Post by eeclark on 2005-12-06
I am such a novice.  I can't seem to be able to build this thing.
We will have to leave it to the experts.

---

### Post by strikeforce on 2005-12-06
hplip 0.9.6 is in dapper that would be the one backported.

From the dependancies I would assume it would not be able to be backported due to libs required.  I tried to have a look at what needs to be backported for the libs and you have to backport snmp so I'm pretty sure its going to be a hard slog.

E: Build-Depends dependency for hplip cannot be satisfied because the package libsnmp9-dev cannot be found
I couldn't resolve build dependencies by myself. I'll drop you to a shell

This is in dapper but not in breezy

---

### Post by eeclark on 2005-12-09
guess I'll have to wait til April and get Dapper

---

