---
title: "How to check Virtualbox Guest OS IP in bridge mode?"
date: 2018-06-27
forum: Virtualisation
---

### Post by jtodd5527 on 2018-06-27
Long time ago when using virtualbox, I can check guest's IP address with command `VBoxManage guestproperty enumerate <guest_vm_name> | grep -i IP`. But this looks like not working any more because this command now returns nothing. What is the correct way to obtain guest vm's  IP, which is configured to **Bridge Adapter**? 

virtualbox 5.1.34_Ubuntu r121010 © 2004-2018 Oracle Corporation (Qt5.5.1) in Ubuntu 16.04 LTS


Thanks

---

### Post by TheFu on 2018-06-27
Correct?  IDK.

I'd use static IPs so I know the IP already.
Or 
use DHCP reservations based on the MAC, which make static IPs.
Or
use arp and filter on the MAC,which returns something like this:
```
$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
172.22.22.220            ether   b8:3e:59:55:dd:d3   C                     enx000exxxxxxxx
```

But as far as using vboxmanage, if the method you are using now doesn't seem to be working, have you verified from inside the VM that it actually has an IP (use **ip a**)?

---

