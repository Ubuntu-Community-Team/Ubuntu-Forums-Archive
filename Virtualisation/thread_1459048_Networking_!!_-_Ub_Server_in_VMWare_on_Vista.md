---
title: "Networking !! - Ub Server in VMWare on Vista ?"
date: 2010-04-20
forum: Virtualisation
---

### Post by southof40 on 2010-04-20
Hi - I want to run Ubuntu Server within VMWare Server on Vista Ultimate. I downloaded Ubuntu Server 8.04 TLS - configured a virtual machine within VMWare server (as best I can I'm not experienced in this) and VMWare says the virtual machine has started.

**H**ow do I now access this machine ? I was expecting there to be an IP address allocated within my usual sub-net range which would be associated with the virtual server.

**I** want to be able to access the Ubuntu server from Vista using PuTTy and run a web server on Ubuntu. I also want the Ubuntu server to be able to access network resources on the internet.

**M**achines on my LAN generally use IP addresses in the 192.168.10.x range. Some machines are allocated IP addresses from a local DHCP server, others are fixed IP addresses.

**T**he Virtual Machine is currently set up using Bridged access but I've tried NAT and Host-only as well.

**W**hen I try to use the VMWare server console it times out.

Any help/suggestions appreciated.

---

### Post by southof40 on 2010-04-21
Just answering my own question here (to some extent at least). The problem with the Console timeout was solved by using the 'Generate Virtual Machine Shortcut' and using the URL in a different browser allowed me to use the Console without a timeout. No idea why. It did mean I could go ahead with configuring Ubuntu in the normal way.

---

### Post by southof40 on 2010-04-21
> was solved by using the 'Generate Virtual Machine Shortcut' *should have read*
> was solved by using the 'Generate Virtual Machine Shortcut' within the VMWare Server Control Panel

---

