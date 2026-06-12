---
title: "Auto-lock Grub 2 Entries"
date: 2010-02-09
forum: Security
---

### Post by user2037 on 2010-02-09
How does one auto-lock entries in Grub 2 so only certain/authenticated users can access them. The Grub 2 wiki seems to indicate it can be done. But it is not clear what/where the changes should be made so they aren't erased by the next update.

---

### Post by kiranmurari on 2010-02-10
Hi,

Please look at the "Security" section of the GRUB Manual.
[http://www.gnu.org/software/grub/manual/html_node/Security.html#Security](http://www.gnu.org/software/grub/manual/html_node/Security.html#Security)

---

### Post by user2037 on 2010-02-10
> **kiranmurari said:**
> Hi,

Please look at the "Security" section of the GRUB Manual.
[http://www.gnu.org/software/grub/manual/html_node/Security.html#Security](http://www.gnu.org/software/grub/manual/html_node/Security.html#Security)

That is the Grub 1 manual. Ubuntu 9.10 uses Grub 2.

---

### Post by kiranmurari on 2010-02-11
Hi,       

Security/Authentication is partially implemented in Grub 2. This has been
discussed in detail at the following launchpad bug report.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392158](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392158)
   
To make use of the current implementation of security/authentication, please see
the following Grub 2 wiki link.
[http://grub.enbug.org/Authentication](http://grub.enbug.org/Authentication)

Hope this helps.

---

