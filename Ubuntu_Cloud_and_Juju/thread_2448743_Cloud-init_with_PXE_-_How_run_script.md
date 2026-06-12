---
title: "Cloud-init with PXE - How run script ?"
date: 2020-08-13
forum: Ubuntu Cloud and Juju
---

### Post by piwako on 2020-08-13
Hi,

I would like to install several physical machines with PXE and cloud-init and then customize some stuff inside.

I've read the documentation and now I'm here : 


[LIST]
[*] install "PXE" server : **[COLOR=#008000]OK[/COLOR]**  *(APPEND initrd=ISO/ubuntu20.04/casper/initrd autoinstall  url=http://10.0.0.1/ubuntu20.04.iso net.ifnames=0 biosdevname=0 ip=dhcp  ipv6.disable=1 ds=nocloud-net;s=http://10.0.0.1/cloudinit/)* 
[*] customize install with user-data : **[COLOR=#008000]OK[/COLOR]** 
[*] run post installation scripts or "push" some configuration files during installation : **[COLOR=#ff0000]NOK [/COLOR]** 
[/LIST]

I can't find how to run some scripts or write some files :  I tried the *write_files* directive but it didn't work. I read this page : [https://ubuntu.com/server/docs/install/autoinstall-reference](https://ubuntu.com/server/docs/install/autoinstall-reference) but I don't find the solution. I don't know how writing my user-data file, I think I misunderstood something

Can you help me please ?

Thanks a lot.

---

