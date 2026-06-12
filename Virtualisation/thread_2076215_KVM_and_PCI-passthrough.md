---
title: "KVM and PCI-passthrough"
date: 2012-10-25
forum: Virtualisation
---

### Post by punktik on 2012-10-25
Hi, 

i got ubuntu-server with precise and kvm (installed via tasksel at install time), a virtual windows machine  (windows 2003 r2 x64), and sas-hba with lto-4 drive on it, which i want to pass to windows-guest, as there are plenty of nt-backups to restore. So far i managed to have the sas-hba as passthrough to winodows, installed the drivers, but as soon as i power up the lto drive everything freezes, and sometimes i can see "BUG: soft lockup - CPU#5 stuck for 23s!" on the screen attached direct to the server. 

I tried almost everything from kvm site - no help. 
Where should i search the "dead body" now? 
Any hints are welcome!
Thanks in advance.

---

