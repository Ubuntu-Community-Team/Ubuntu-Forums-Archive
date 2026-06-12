---
title: "Ubuntu behind corp proxy (MS ISA Proxy)"
date: 2007-10-01
forum: Server Platforms
---

### Post by toupeiro on 2007-10-01
Anyone successfully get apt-get commands to work behind a Microsoft ISA proxy?  How do businesses running ubuntu work behind proxies like this?  I do not have direct access to administer our proxy server, and the admins for it are not local.  I have no choice but to work "through" it rather than around it.

---

### Post by gfowler on 2007-10-01
You don't say whether you are behind ISA 2K, 2004 or ..
From a workstation using using SBS 2K (running ISA 2K) I've not had a problem using apt-get.  That is to say there are not a mess of problems (ports) using other applications with ISA 2K.

I understand the above is not much help solving your issues, as they may be.  Your sysadmin may have locked the system down tight.  Have you configured your workstation to use the proxy?  He (sysadmin) may or may not be allowing a connection to the internet without it.  

Jerry

---

### Post by Maxtorm on 2007-10-01
Seems the process is a bit convoluted, but it is possible. See: [http://ubuntuforums.org/showthread.php?p=3434680#td_post_3340675](http://ubuntuforums.org/showthread.php?p=3434680#td_post_3340675) and/or [http://www.tuxmachines.org/node/12889](http://www.tuxmachines.org/node/12889).

---

### Post by calfella on 2007-10-01
I had the same problem, and edited the /etc/apt/sources.list to use ftp:// instead of http:// .  So far it has worked and I haven't had any issues with it.

I have also tried the NTLMaps approach and that worked also.

---

