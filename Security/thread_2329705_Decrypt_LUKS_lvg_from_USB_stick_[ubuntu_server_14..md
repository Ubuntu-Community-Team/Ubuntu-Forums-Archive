---
title: "Decrypt LUKS lvg from USB stick [ubuntu server 14.04]"
date: 2016-07-04
forum: Security
---

### Post by hprado on 2016-07-04
Hi everyone, this is my first thread in the comunity.
I've recently **encrypted my ubuntu server** 14.04 (installed on a **RAID 1 in a lvg**) so I **encrypted only the / partition** with a specific passphrase, swap has a random passphrase.
Now **what I want** to do is to be able to **decrypt or auto fill the passphrase from an usb stick**, I mean, having in a file a passphrase which is like this (not the same):     */aFgS@nTb&$ (0HR!F_&z6uKe@!{~j2+]*         but its long and complex to write as this one (**I want to use the same I've defined**)

All the tutorials suggested creating a new one in a file, but I have this error when adding that new one to the LUKS keys.
Im attaching a screenshot of the last things I did. 
This are the tutorials I've tried 
[https://www.centos.org/forums/viewtopic.php?t=53452](https://www.centos.org/forums/viewtopic.php?t=53452)
[https://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](https://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)
[https://s31.postimg.org/srru2k06z/Sin_nombre.png](https://s31.postimg.org/srru2k06z/Sin_nombre.png)

---

