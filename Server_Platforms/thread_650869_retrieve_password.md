---
title: "retrieve password"
date: 2007-12-26
forum: Server Platforms
---

### Post by dpj23 on 2007-12-26
If you forgot you password for your Ubuntu system you can recover using the following steps:

 

1.       Turn on your computer.

2.       Press ESC at the grub prompt

3.       Press “e” for edit

4.       Highlight the line that begins kernel……., press “e”

5.       Go to the very end of the line, add “rw” init=/bin/bash

6.       Press enter, then press “b” to boot your system

7.       Your system will boot up to a password-less root shell

8.       Type in passwd username

9.       Set your password

10.   Type reboot

 Of course, now that we know this how do you protect against it…

---

### Post by p_quarles on 2007-12-26
1. You don't need to edit the GRUB menu: just select the option for "Recovery Mode."

2. You can't protect against this. Physical access to a computer allows you to change anything on it. If the computer is accessible to unknown persons, any important data on it should be encrypted.

---

### Post by dpj23 on 2007-12-26
I would agree...

Then encryption should be the next topic...

Would you have any recommend software for encryption???

---

### Post by p_quarles on 2007-12-26
I use dmsetup + cryptsetup, along with the dm-crypt kernel module. The book* Ubuntu Hacks* has a good step-by-step tutorial, but I haven't been able to find a similar one anywhere on the internet. 

Truecrypt, however, is another good application, and it's much better documented on the net, including at howtoforge.com.

---

### Post by dpj23 on 2007-12-26
Thanks again for the information...

---

### Post by jtc on 2007-12-27
> **p_quarles said:**
> I use dmsetup + cryptsetup, along with the dm-crypt kernel module. The book* Ubuntu Hacks* has a good step-by-step tutorial, but I haven't been able to find a similar one anywhere on the internet.

There are some descent tutorials in the community docs.

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
--> EncryptedFilesystem*

---

