---
title: "Hyper-V networking issue after migration"
date: 2012-05-01
forum: Virtualisation
---

### Post by sixstringssteve on 2012-05-01
I have been running Ubuntu 10:04 LTS for a while in Hyper-V with some module modifications.  After installation of 12:04 I have run into some issues.  The install went great and the server ran perfect.  This issue is after migration.  I build the VM on my deployment host and then migrated to the home host.  After migration I cannot get network connectivity.  It is not the old 70-persistant-rule issue.  I even tried adding a new network interface and I can enable it and set an IP, but it will not come online.   When I try to give the NIC a DHCP setting and dhclient the VM, the result is a failure to bring up eth#.   Everything looks to be running like a top, but I cannot ping in or out and have no access to Apache.  Migration was a simple export/import as I have found SCVMM does not like quick migrating Ubuntu.
 
Any ideas guys?

---

### Post by hasan.akgoz on 2012-05-06
Which add NIC hardware ? Legacy or Normal Network adapter ?

---

### Post by CharlesA on 2012-05-06
Open /etc/udev/rules.d/70-persistent-net.rules

Remove all lines and reboot.

If it detects the interface, it'll show up, but you can also check the interface with ifconfig and see if it's set right.

---

