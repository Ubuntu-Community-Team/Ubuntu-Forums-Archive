---
title: "missing mail(-command) on ubuntu 6.06 server"
date: 2007-02-23
forum: Server Platforms
---

### Post by cyber_bushi on 2007-02-23
Hey folks,

i usually do a quick
```
cat foobar.txt|mail boss@company.com
```
to send logs around BUT I now use ubuntu6.06LTSserver and it seems that my beloved mail command is missing. I now installed sendmail cause I think I remembered that it is somehow connected with this mta. But still no mail... any ideas?

regards,

cb

---

### Post by yota on 2007-02-23
Hi, the mail command is in the mailx package, just install it and you're set.

Hope this helps!

---

### Post by dannyboy79 on 2007-02-23
yota, I sent you a PM I thought but you didn't respond. I need some help because I am getting the VIA PT880 chipset with the bad AGP port. The file you mentioned to modify  prior to compiling a new kernel is pci_ids.h and it's located in 5 places:

/usr/include/linux/pci_ids.h
/usr/src/linux-headers-2.6.15-27-686/include/linux/pci_ids.h
/usr/src/linux-headers-2.6.15-27/include/linux/pci_ids.h
/usr/src/linux-headers-2.6.15-28-686/include/linux/pci_ids.h
/usr/src/linux-headers-2.6.15-28/include/linux/pci_ids.h

So I am not sure which 1 I need to modify? I have never compiled a kernel and I have no idea how to? ALso, I beleive I need to compile in SMP because I am getting the core 2 duo E4300. Can we discuss this sometime over irc chat or instant messaging? My email is [email]darfsten@wi.rr.com[/email]. please contact me I would really appreciate it.

---

### Post by cyber_bushi on 2007-02-23
thanks a lot! it works! :D

---

