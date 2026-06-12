---
title: "Networking in XP Guest"
date: 2010-01-21
forum: Virtualisation
---

### Post by valros on 2010-01-21
I cannot get networking up in a guest XP under Ubuntu 9.10. I've tried NAT and bridged and within XP no network devices are present and ipconfig returns nothing. Virtualbox 3.0.8 Any faults or simple guides? The host is using eth0.

---

### Post by fouadatmeh on 2010-01-22
Hello,
Is the "Enable Network Adapter" selected in the VM settings for at least one adapter?
Also, are the guest additions installed?
If the above checks, try to change the adapter type in the advanced settings; "PCnet-FAST III" works for XP with me.

---

### Post by valros on 2010-01-25
I did not have the guest additions installed, however its installation changed nothing, using PC-FAST(III) and NAT, no devices appear in XP and ipconfig returns nothing.

---

### Post by valros on 2010-01-25
Ok, looking in the Device Manager of XP there is a network adapter listed as VMware Accelerated AMD PCNet Adapter, a driver is listed but there is an error, error code 10, the device cannot start.

---

### Post by fouadatmeh on 2010-01-27
Try to uninstall this driver and then restart the guest.. 
** did you move this machine from vmware? if so try to uninstall vmware's guest additions..

---

