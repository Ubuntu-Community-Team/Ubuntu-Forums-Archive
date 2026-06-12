---
title: "Mouse Integration not working"
date: 2008-11-27
forum: Virtualisation
---

### Post by Damien Kane on 2008-11-27
Hi,

I run Vista Ultimate and use VirtualBox 2.0.4 running ubuntu 8.10 (would love to replace Vista with Ubuntu but I can't get some hadware working!)

Anyhow, I have GuestOS installed but no mouse integration. I have issues with seamless mode, but would prefer the mouse integration. Any ideas?

I saw this thread back in May and was wondering if perhaps anything else is known:

[http://ubuntuforums.org/showthread.php?t=788076&highlight=Mouse+Integration](http://ubuntuforums.org/showthread.php?t=788076&highlight=Mouse+Integration)

All the best!

---

### Post by bodhi.zazen on 2008-11-27
Mouse integration works on 8.10 guests on Linux hosts (and on 9.04 alpha). Did you install the additions into the guest and re-boot the guest ?

---

### Post by Damien Kane on 2008-11-28
Hi there,

yes, I installed the guess addons and rebooted with the same issue. Tried it again, but nothing has changed. I notice that 'Disable mouse integration' is greyed out, though, and can't be selected as an option.

---

### Post by bodhi.zazen on 2008-11-28
Ouch ...

Sounds as if you are on a Windows host, I suggest you might ant to search or post in the VirtualBox Forums.

---

### Post by axel206 on 2008-11-30
I had the same problem with Archlinux HostOS and Ubuntu 8.10 GuestOS. Problem solved after I fully updated Ubuntu and reinstalled Guest Additions.

---

