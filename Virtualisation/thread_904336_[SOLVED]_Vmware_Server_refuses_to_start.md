---
title: "[SOLVED] Vmware Server refuses to start"
date: 2008-08-29
forum: Virtualisation
---

### Post by Julian David Pitt on 2008-08-29
I have Vmware Server installed after following a guide on Ubuntu Geek, since I last had it working the kernel version has changed to 2.6.24.21 and now it refuses to start. I get no error message at all so I have no idea where to start fault finding, help!!

---

### Post by veloce on 2008-08-29
After every kernel upgrade you need to rerun vmware-config.pl

---

### Post by tact on 2008-08-29
if you open a terminal window and type "vmware" you will get to see an error message (something like no vmware modules for your running kernel) and advice to run the vmware config again.   The commandline in the error message is correct - just cut and paste it.   Accept all defaults..  good to go.

Cheers

---

### Post by Julian David Pitt on 2008-08-31
Hi Tact and Veloce
That sorted it out so thanks very much, it is much appreciated.
Cheers

---

