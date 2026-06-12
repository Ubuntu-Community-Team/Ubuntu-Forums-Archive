---
title: "Number of times user can enter encryption passphrase"
date: 2017-12-28
forum: Ubuntu, Linux and OS Chat
---

### Post by avinash1992 on 2017-12-28
Hello, 

I would like to know how many times a user can enter the encryption passphrase (sda5 crypt) before it get blocked?
If it is blocked what is the solution?

thank you

---

### Post by deadflowr on 2017-12-28
I think it's 3.
(or at least 3 is normal for most password tries)
Reboot machine to try again.

---

### Post by avinash1992 on 2017-12-28
Thank very much.

So it does not block the laptop. you just have to restart it?

---

### Post by untrustytahr on 2017-12-28
I believe it drops you to an initramfs shell after 93 attempts.  If you want to understand how that number is reached:

[http://hmarco.org/bugs/CVE-2016-4484/CVE-2016-4484_cryptsetup_initrd_shell.html](http://hmarco.org/bugs/CVE-2016-4484/CVE-2016-4484_cryptsetup_initrd_shell.html)
[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1660701](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1660701)

---

