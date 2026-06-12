---
title: "Removing kernel modules"
date: 2006-06-02
forum: The Cafe
---

### Post by lkagan on 2006-06-02
Where is the conf file that instructs the kernel which modules to load?  My kernel is loading the pcmcia module (i82365.0) which is causing Hal to fail.  I don't need that module on my desktop machine.  I can remove it via modprobe or rmmod but how can I configure the kernel to NOT continue loading it at boot.

*edit*
The kernel module was NOT what caused Hal to fail.  The kernel module was an unrelated issue along with another issue involving ifrename not being found.  Anyway, the problem was caused by auto mounting smb shares.  It's a known bug in Dapper.  I must say, I'm a bit disappointed in the upgrade to Dapper.  The upgrade killed my productivity at work today. 
* end edit *
Thanks.

Larry

---

