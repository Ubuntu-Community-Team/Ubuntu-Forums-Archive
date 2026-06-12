---
title: "What virtualization software to use?"
date: 2010-05-02
forum: Server Platforms
---

### Post by orengolan on 2010-05-02
I am reading 'Deploying Rails Applications' and want to create a Rails clustered deployment setup as described in page 141:
Host: Ubuntu server
Guests: 2 Ubuntu vms, each with Nginx on port 80, a few mongrels (app server for rails) and MySQL

What open source virtualization software do you recommend for this purpose?
I am trying virtualbox but heard good things about KVM.

I have some questions regarding vbox and posted them on vbox forums - [http://forums.virtualbox.org/viewtopic.php?f=7&t=30427](http://forums.virtualbox.org/viewtopic.php?f=7&t=30427)
(in case anyone want to help there)


Thanks

---

### Post by spynappels on 2010-05-02
Have you looked at VMWare ESXi? Full featured free version and works very well for me.

---

