---
title: "New mac address kills host network [KVM]"
date: 2010-03-20
forum: Virtualisation
---

### Post by robinharvey on 2010-03-20
Hi,

I have a problem with my KVM / Bridged networking setup - most times that I start a VM I loose network connectivity on the host OS, although the VMs can always see the network.  The problem seems to be that when the VMs start, if the mac address which is assigned to the virtual interface is lower than the mac address of eth0, the bridge mac switches to be the same as the VM mac.  I've currently got a single VM running, and I can see this:
```
[15:51:39]robin@robin-desk:~$ ifconfig | grep HW
br0       Link encap:Ethernet  HWaddr e0:cb:4e:bb:99:07  
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:bb:99:07  
vnet0     Link encap:Ethernet  HWaddr f2:70:12:75:50:02
```  
However, if I bring up another VM, I'll get this:
```
[16:02:04]robin@robin-desk:~$ ifconfig | grep HW
br0       Link encap:Ethernet  HWaddr 5e:f1:3c:e9:6b:36  
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:bb:99:07  
vnet0     Link encap:Ethernet  HWaddr f2:70:12:75:50:02  
vnet1     Link encap:Ethernet  HWaddr 5e:f1:3c:e9:6b:36
```  
See how br0's mac has now changed to be the same as vnet1?  If vnet0 had started with a mac lower than e0:cb:4e:bb:99:07 then this vm would have killed the host connection.

Any ideas on why this happens or how to stop it happening?

Thanks,
--Robin

---

### Post by 1ng0 on 2010-10-20
I experience this problem too, have you found a solution ?

Does the started guest (vnet*) get the MAC as specified in its xml descriptor (in /etc/libvirt/qemu/<name>.xml) ?

best regards, ingo.

---

### Post by Irregular Joe on 2010-10-20
I had the same problem with VirtualBox when I changed MAC addresses on a virtual interface.  I would expect the same applies to KVM.  This worked for me:

sudo vi /etc/udev/rules.d/70-persistent-net.rules

Find the entry that has 'NAME="eth0"' (or whichever interface you may have changed) and delete the line.  The next time you boot, the entry will be recreated with the new MAC address.


I guess the reason Ubuntu does this is so that multiple network interfaces always get assigned to the same name (eth0, eth1,...).  This makes it easier to write iptables rules and other geeky things.

I have configured a virtual server that I use to clone other test servers.  One step before I save the 'gold' copy is to delete this file altogether, it will get rebuilt at boot time.  I generate a new MAC for the interface before starting the new replica for the first time.

Hope this helps!

---

### Post by nikro on 2010-10-29
I have exactly the same issue. I'm searching for a solution. Hints welcome!

---

### Post by Nevill.Burn on 2010-10-30
As of today, Facebook now runs smoothly.  I can log in, move from page  to page.  I truly think this backdoor.hackdoor is the issue.

---

### Post by sendmoreinfo on 2010-11-29
sounds like the same problem as [https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/579892](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/579892) (fix released)

---

