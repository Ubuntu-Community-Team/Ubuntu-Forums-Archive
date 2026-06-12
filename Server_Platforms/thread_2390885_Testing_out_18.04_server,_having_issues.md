---
title: "Testing out 18.04 server, having issues"
date: 2018-05-02
forum: Server Platforms
---

### Post by Drenriza on 2018-05-02
I have just installed 18.04 LTS to check it out, and i noticed that in /etc/hostname i have the hostname i expect, "test01_1804", but in the console it says that the hostname is localhost?
Whats up with that?

Also is it no longer possible to say no to installing "standard system utilities"?

Thanks in advance
Best regards

---

### Post by SeijiSensei on 2018-05-02
[https://ubuntuforums.org/showthread.php?t=2389098](https://ubuntuforums.org/showthread.php?t=2389098)

---

### Post by Drenriza on 2018-05-02
> **SeijiSensei said:**
> [https://ubuntuforums.org/showthread.php?t=2389098](https://ubuntuforums.org/showthread.php?t=2389098)

Thats insane, the solution according to the thread was
> 
Hi,

I had the same problem. You can try to remove ubuntu cloud packages:
apt remove cloud-init    cloud-initramfs-copymods      cloud-initramfs-dyn-netconf

Then you can try to change hostname with hostnamectl.


Is it not a major bug that cloud packages would create this behavior? I did not even install the system with cloud functionality in mind.

---

### Post by SeijiSensei on 2018-05-03
Seemed pretty wonky to me as well.  Then again, I use CentOS for servers.

---

### Post by slickymaster on 2018-05-03
*Thread moved to **Server Platforms**.*

---

