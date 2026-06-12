---
title: "Cloud Based Samba Share Over VPN Only"
date: 2013-04-26
forum: Security
---

### Post by variuxdavid on 2013-04-26
I have setup a base Ubuntu 12.04 virtual server, then followed the instructions  here:  [https://raymii.org/s/tutorials/IPSEC_L2TP_vpn_with_Ubuntu_12.04.html](https://raymii.org/s/tutorials/IPSEC_L2TP_vpn_with_Ubuntu_12.04.html) to  setup a VPN. The VPN works perfect.  

I've also setup a basic Samba Share, which works over VPN.  

However, I would like to  use iptables to make sure that all ports  are blocked to the public Internet except the VPN and SSH, and then the  SAMBA server is only available to clients of the VPN.

The virtual machine has a static public ip and one eth adapter. Right now if I try to access the samba share over the public IP, it doesn't work. But if I do a port scan it shows the samba ports open. I just want to make sure I've hardened this service as tight as possible. Any advice appreciated:

---

