---
title: "how to configure port forwarding between Ubuntu host and Solaris guest in VirtualBox?"
date: 2009-03-15
forum: Virtualisation
---

### Post by legolas_w on 2009-03-15
Hi
Thank you for reading my post
I must use NAT for networking type of virtualBox because I need the guest os to use the HOST network interface communicate with outside word (USE host as the gateway) .
Now I need to have SSH connection to guest OS from host OS which is ubuntu 8.10. I know that something like port forwarding is required but I do not know how to configure it.

If you know any other method except NAT which result in the guest OS using the HOST os as its gateway, please let me know.

If you know how to configure the port forwarding to have ssh let me know again.

Thanks

---

### Post by namaku0 on 2009-03-15
You may want to consult the Help file first.

In main VirtualBox windows choose Help > Contents... > Sun xVM VirtualBox® > Virtual Networking > Network Address Translation (NAT)

BTW, why would you use SSH while you have access to the virtual
machine directly? Even though that VM is headless, normally peoples
still activates the VRDP (Virtual Remote Desktop Protocol).

---

