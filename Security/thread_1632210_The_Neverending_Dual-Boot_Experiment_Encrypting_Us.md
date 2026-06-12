---
title: "The Neverending Dual-Boot Experiment: Encrypting User Data"
date: 2010-11-27
forum: Security
---

### Post by thezwallrus on 2010-11-27
Hi all,

I'm Johno. I've been messing around with a dual-boot of Lucid Lynx and Windows 7, using a separate partition for User Data (my documents, etc). I have it all mounted and working awesome between W7 and LL, and now it's time I want to keep my files from all my guest users. I was wondering if there is a way, similar to windows EFS, where the User Data partition could be hashed against the password (which is the same between 7 and buntu), and easily accessed from both Johno's Windows and Ubuntu user account, while not from the guest accounts. I figured before I dedicate tonight to finding a solution, I would post a thread here. Let me know your ideas!

Thanks,
John

---

### Post by Enigmapond on 2010-11-27
I use TruCrypt for that. Essentially you encrypt a container and move all the data into it. TC is usable by both Win and Ubuntu as it's cross platform but you will need to install the Linux version on Ubuntu and the Win version on the other....

---

### Post by thezwallrus on 2010-11-30
awesome, i will try that!

---

