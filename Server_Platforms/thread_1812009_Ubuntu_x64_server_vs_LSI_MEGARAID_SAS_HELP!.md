---
title: "Ubuntu x64 server vs LSI MEGARAID SAS HELP!"
date: 2011-07-25
forum: Server Platforms
---

### Post by Kira_Belka on 2011-07-25
I have DEPO STORM 1000 with LSI MEGARAID SAS 8208 .. so 6 HDD in RAID (0,1)..
So I tryed to install ubuntu 10.04 server both x86/x64 ..same with ubuntu 11.04 and 10.10 .. there are not drivers for GNU Debian/Ubuntu on official site of LSI.. I tryed to compile from REDHAT/SUSE sources..there was just very long errors during compilation process.
:confused:

---

### Post by disabledaccount on 2011-07-26
I think You should look at this:
[http://forums.gentoo.org/viewtopic-t-731366.html](http://forums.gentoo.org/viewtopic-t-731366.html)
and this:
[http://kb.lsi.com/KnowledgebaseArticle15753.aspx#linux](http://kb.lsi.com/KnowledgebaseArticle15753.aspx#linux)

;)

---

### Post by Kira_Belka on 2011-07-27
I found way.. it's just one.. to downgrade kernel to 2.6.18 and to install Chernomoor's Megasr driver

---

### Post by bakegoodz on 2011-07-28
Seriously? I have a LSI Megaraid card, and had another that I sold to a friend. Both cards installed Ubuntu just without any extra steps. It is supported by the Official Linux kernel. I'm wondering what went wrong with your install.

---

### Post by Kira_Belka on 2011-07-29
> **bakegoodz said:**
> Seriously? I have a LSI Megaraid card, and had another that I sold to a friend. Both cards installed Ubuntu just without any extra steps. It is supported by the Official Linux kernel. I'm wondering what went wrong with your install.
I think it was not M1068 ( 8208 series ) :)
Because MSI Megaraid SAS 8208  is not in list of supported raid controllers.

---

