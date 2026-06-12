---
title: "Whoopsie daisy and launchpad bugs."
date: 2013-04-18
forum: Ubuntu Development Version
---

### Post by philinux on 2013-04-18
Just had another of these error dialogs. I though these were supposed to check bugs at launchpad via apport and allow a user to raise a new bug.

It seems this system bypasses launchpad and sends error reports to canonical instead. 

Have I missed something here, when you click continue thats it no launchpad.

---

### Post by dino99 on 2013-04-18
seems that the apport's query have some issues: [https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1163235](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1163235)

---

### Post by jbicha on 2013-04-18
Is what you're seeing just because Ubuntu 13.04 will be released soon?

[https://launchpad.net/ubuntu/+source/apport/2.9.2-0ubuntu6](https://launchpad.net/ubuntu/+source/apport/2.9.2-0ubuntu6)

---

### Post by philinux on 2013-04-18
> **jbicha said:**
> Is what you're seeing just because Ubuntu 13.04 will be released soon?

[https://launchpad.net/ubuntu/+source/apport/2.9.2-0ubuntu6](https://launchpad.net/ubuntu/+source/apport/2.9.2-0ubuntu6)

Not sure as this behaviour has been noticed before.

---

### Post by mc4man on 2013-04-18
apport crashers to LP was turned off  a short while ago. (typical just prior to release.) I guess you could turn back on if inclined, not sure if appreciated or matters.

> apport (2.9.2-0ubuntu6) raring; urgency=low

  * etc/apport/crashdb.conf: Disable Launchpad crash/kernel reports for the
    raring release. Only report to [http://errors.ubuntu.com](http://errors.ubuntu.com) from now on.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Thu, 11 Apr 2013

Edit: - missed the above post that linked to change...

---

### Post by Mr. Picklesworth on 2013-04-19
Error reports are collected by the Ubuntu Error Tracker, which you can see over here:
[http://errors.ubuntu.com/](http://errors.ubuntu.com/)

As I understand it, it will help you to create a new bug report in certain cases, particularly when it has encountered a new error.

---

