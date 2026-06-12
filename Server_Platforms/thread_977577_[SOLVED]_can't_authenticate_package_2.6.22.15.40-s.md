---
title: "[SOLVED] can't authenticate package 2.6.22.15.40-server"
date: 2008-11-10
forum: Server Platforms
---

### Post by Alt69 on 2008-11-10
hi, I am getting an warning that this package "can't be authenticated" when trying to install 2.6.22.15-server update for ver 7.10. This package is an update from 2.6.22-15.39 to 2.6.22-15-40.

I have never recieved this type of message before an update. 

Also this is what is says about the update:


Changes:

Version 2.6.22-15.40: 

  
[Stefan Bader]

  * ndiswrapper: Prevent buffer overflow if nickname is IW_ESSID_MAX_SIZE characters long.
    - LP: #275860
    - CVE-2008-4395
  * ndiswrapper: Print exactly the number of characters in essid
    - LP: #275860
    - CVE-2008-4395


Description:

This package contains modules supplied by Ubuntu for Linux kernel 2.6.22 on x86/x86_64.

You likely do not want to install this package directly. Instead, install the linux-server meta-package, 
which will ensure that upgrades work correctly, and that supporting packages are also installed. 


Question:
- Do I want to install this update, and if yes, how do I install the linux-server meta-package?

thanks

---

### Post by cariboo on 2008-11-10
Unless you need ndiswrapper to get a wireless card working on your server I wouldn't bother.

Jim

---

### Post by Alt69 on 2008-11-17
thanks, that makes it easy. :)

---

