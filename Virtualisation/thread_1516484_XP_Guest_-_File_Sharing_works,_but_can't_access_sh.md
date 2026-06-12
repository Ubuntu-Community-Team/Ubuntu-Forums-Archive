---
title: "XP Guest - File Sharing works, but can't access share"
date: 2010-06-23
forum: Virtualisation
---

### Post by larry.said on 2010-06-23
Hey guys,

  I just enabled file sharing and created a network drive on my XP VM with the correct folder path and everything. Unfortunately, I cannot access the drive as it says the network is not connected... 

 I am running a NAT network on my VM if that helps 

 thanks for the help guys

---

### Post by TheFu on 2010-06-26
Don't run NAT. You want bridged networking if you expect any system outside the VM machine to be able to see those network files.
1) In the VM Network Settings, selected bridged.
2) Be certain you have a DHCP server on the network or set the static IP address.

I don't think you need to change anything else in the XP client related to sharing, unless your XP firewall is blocking outside connections.

---

