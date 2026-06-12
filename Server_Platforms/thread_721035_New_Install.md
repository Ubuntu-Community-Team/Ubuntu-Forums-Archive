---
title: "New Install"
date: 2008-03-10
forum: Server Platforms
---

### Post by DIGGER_NZ on 2008-03-10
Hi All,
I have recently acquired an older thin client PC which I want to install Ubuntu Server on. I am a server tech who has worked with Windows all his life and have a couple of questions before I decide if this is the right direction:

1. Can multiple roles (web / dhcp / ftp) be installed onto a single install?
2. Is there any terminal services / vpn like functionality. Wanting to be able to send WOL packets from this server to my MS MCE2005 to bring it online.
3. Is there a firewall solution that can be installed also?

Thanks for the help :-)

---

### Post by netlogic on 2008-03-11
answers
========
1. YES. Do a lamp install or use apt-get to install all at once. 
2. terminal service - built into the Xserver. SSL VPN - openvpn. ipsec vpn -FreeS/WAN,  WOL - EVERY oses support them if your nic supports it.
3. firewall - it is already compiled in the kernel. there are various front-end tools based on your needs. do "apt-cache search firewall" on the command line.

---

