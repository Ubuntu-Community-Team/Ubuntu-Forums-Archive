---
title: "Extra encrypted hardisk fails after resume"
date: 2014-09-16
forum: Security
---

### Post by Esben_Nielsen on 2014-09-16
I have an extra harddisk in my labtop. I originally installed by system with full disk encryption.  The extra harddisk I installed with cryptsetup and lvm back when I ran Ubuntu 12.04, and got extra space mounted as /extra. Then when I boot the machine I have to type a password for the root filesystem and another for the extra hd, and then everything works as expected.

But the labtop have suspended to RAM and then resumes, I sometimes get a popup asking for the password to the extra HD. I type the password, but then when I access /extra I get:

ll /extra/
ls: reading directory /extra/: Input/output error

It looks like the cryptsetup and Luks newer get the volume resumed properly.

I have now updated to 14.04, but it still does not work.

---

