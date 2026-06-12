---
title: "upgrade to kernel 2.6.27-11 in 8.10 broke my VMWare workstation 6.5 networking"
date: 2009-02-04
forum: Virtualisation
---

### Post by pacanukeha on 2009-02-04
Every time there is a kernel upgrade, VMWare needs to recompile kernel modules. This time around, everything seems to go smoothly, but my winxp vm has no tcp/ip connectivity. From a command prompt in the vm I can get dns resolution (ping [www.google.com](www.google.com) gives an IP address) but I cannot telnet/browse anywhere (telnet [www.google.com](www.google.com) 80 times out). I have 2 network adapters configure - one NAT, one bridged. As I said, everything worked fine before. Any suggestions as to where to start looking to find out what might not be working properly? Where to look for error messages, &c? Certainly nothing is being presented as an error. Both network adapters are marked as working in the VM interface, the VMWare network service is up, the interfaces show up in ifconfig ... I am kind of stumped.

---

### Post by dcstar on 2009-02-05
> **pacanukeha said:**
> Every time there is a kernel upgrade, VMWare needs to recompile kernel modules. This time around, everything seems to go smoothly, but my winxp vm has no tcp/ip connectivity. From a command prompt in the vm I can get dns resolution (ping [www.google.com](www.google.com) gives an IP address) but I cannot telnet/browse anywhere (telnet [www.google.com](www.google.com) 80 times out). I have 2 network adapters configure - one NAT, one bridged. As I said, everything worked fine before. Any suggestions as to where to start looking to find out what might not be working properly? Where to look for error messages, &c? Certainly nothing is being presented as an error. Both network adapters are marked as working in the VM interface, the VMWare network service is up, the interfaces show up in ifconfig ... I am kind of stumped.

Make sure the bridge network config is actually eth0 (or 1) to match what your system actually is - don't assume it is correct.

---

