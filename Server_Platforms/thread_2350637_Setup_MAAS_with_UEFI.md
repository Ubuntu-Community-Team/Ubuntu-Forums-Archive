---
title: "Setup MAAS with UEFI"
date: 2017-01-26
forum: Server Platforms
---

### Post by xanvier2 on 2017-01-26
I am seting up an Ubuntu MAAS server to install my cluster. The nodes  in the cluster can only boot from UEFI, So I set up the (external) DHCP  server with this config:

 ```
dhcp-boot=grubnetx64.efi.signed,up01,192.168.1.137 
```  

But it didn't work, the file doesn't exist: 

[IMG]https://i.stack.imgur.com/WfS5U.jpg[/IMG]

When I change **grubnetx64.efi.signed** to **pxelinux.0** it works on a Virtual Machine, but I can't use that on my cluster for it only boots from UEFI:

[IMG]https://i.stack.imgur.com/a3VWC.png[/IMG]

The Maas server is sort of working because it does download the file, but can simply not execute it:
[IMG]https://i.stack.imgur.com/BC9iH.png[/IMG]

I've looked in the documentation to set it up for UEFI boot, but couldn't find anything that helped me.

---

