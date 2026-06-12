---
title: "Virtual Ethernet Failed VMWare Workstation"
date: 2014-11-26
forum: Virtualisation
---

### Post by seabird22 on 2014-11-26
Hello to all, 

I decided to switch over to VMWare workstation 10 from qemu/kvm because it had the features I needed. The host OS is 14.04 desktop. When trying to create a machine, I receive an error, [COLOR=#ff0000]**Could not connect ethernet0 to virtual network "/dev/vmnet8**[/COLOR]", and therefore non of the virtual network interfaces are created. Checked host machine with ifconfig, and vmnet8 does not appear. When I try to access the Virtual Network Editor, I get an error message 'network configuration is missing, ensure that /etc/vmware/networking exists. I checked and it does ***NOT ***exist. Can anyone steer me in the right direction as to how to go about fixing this? 

By the way, I have searched this site through Google, and it seems that many others have had this problem, however, all the threads are archived, and they don't solve my problem. Any help would be greatly appreciated.

---

