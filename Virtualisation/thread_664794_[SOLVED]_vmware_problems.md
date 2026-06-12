---
title: "[SOLVED] vmware problems"
date: 2008-01-11
forum: Virtualisation
---

### Post by satipera on 2008-01-11
I have a core 2 duo laptop with gutsy, but when i try to install vmware player i receive an error which says it will not install on an AMD based system, any ideas anyone? I am aware my system is intel  and not AMD

---

### Post by dcstar on 2008-01-11
> **satipera said:**
> I have a core 2 duo laptop with gutsy, but when i try to install vmware player i receive an error which says it will not install on an AMD based system, any ideas anyone? I am aware my system is intel  and not AMD

You have not given any details about how you are installing so it is just about impossible to assist you.

Vmware server is available in the repositories (enable the Third-party "Partner" option), and is installed easily (like any other package).

There is a separate Virtualisation forum for these questions:

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by satipera on 2008-01-12
yes thanks i have just installed vmware server no problem, but originally i tried to install vmware player from aplications aadd/remove but it is recognizizing my intel system as AMD and refusing to continue, I amjust trying to try this out and have no experience in this software and only a vague idea of what it does

---

### Post by popch on 2008-01-12
> **satipera said:**
> ... originally i tried to install vmware player from aplications aadd/remove but it is recognizizing my intel system as AMD and refusing to continue, ...

Apparently, it does not 'recognize' your system as AMD. It refuses to be installed on any system, it seems.

---

### Post by satipera on 2008-01-12
The exact error message is:-                                                                                                   

"VMware Player cannot be installed on your computer type (amd64).Either the application requires special hardware features or the vendor decided not to support your computer type."

---

### Post by popch on 2008-01-12
> **satipera said:**
> The exact error message is:-                                                                                                   

"VMware Player cannot be installed on your computer type (amd64).Either the application requires special hardware features or the vendor decided not to support your computer type."

Yes, it apparently says that for every kind of computer. It is a known bug. The VMWare Player provided in the repositories can not be installed.

Use another application (such as the VMWare server), try and install the Player from the package provided at VMWare.com (I seem to remember that they have a .deb package) or wait until someone fixes the package in the repository. Don't hold your breath, though.

---

### Post by satipera on 2008-01-12
thanks for reply, forgive my ignorance but is vm server the same as vm payer with the addition of networking?

---

### Post by popch on 2008-01-12
I have been using Player quite a lot, but I have never used VMWare Server, so I can not really tell.

However, you can find in this forum quite a few people who apparantly are using VMWare server in exactly this way.

Perhaps one of them comes forward and tells us?

---

### Post by fjgaude on 2008-01-12
I've never used Player but Server can create clients, not just use them. It is full-featured and works fine in 32- and 64-bit Ubuntu.

---

### Post by satipera on 2008-01-12
Thanks to everyone for their help i will have a play with vmware server .

---

