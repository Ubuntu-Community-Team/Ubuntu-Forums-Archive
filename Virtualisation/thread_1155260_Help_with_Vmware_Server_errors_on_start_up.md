---
title: "Help with Vmware Server errors on start up"
date: 2009-05-10
forum: Virtualisation
---

### Post by Julian David Pitt on 2009-05-10
When I try to start Vmware I get the following error 
```
julian@Hardy:~$ vmware
Unable to alloc client: Cannot open file "/home/julian/.vmware/preferences": Permission denied.

VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: Cannot open file "/home/julian/.vmware/preferences": Permission denied.

A log file is available in "/tmp/vmware-julian/ui-8748.log".  Please request support and include the contents of the log file.  
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.
```
I should point out that I am running kernel 2.6.28.12 and I have run Vmware-config.pl. I have no idea what the errors mean and would really appreciate some help please.

---

### Post by veloce on 2009-05-11
try "sudo vmware"

if that works, find that file and change it's permissions.

---

