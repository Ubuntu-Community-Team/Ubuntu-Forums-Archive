---
title: "ip_conntrack_ftp module missing? Do i even need it?"
date: 2007-05-25
forum: Server Platforms
---

### Post by johnman145 on 2007-05-25
I want to enable passive ftp access to my server through my shorewall firewall. The shorewall documentation states there should be a ip_conntrack_ftp module available. This module supposedly opens a port on the firewall on a ftp connection from a client (?). However, if i enter lsmod a lot of modules are shown but no *ftp* modules of any kind.

Can i apt-get this module? Do i need this module if i want to use my ftp server behind shorewall? 
If this module is important why isnt it loaded in my ubutnu 7.04 server edition?

---

### Post by turinglabs on 2007-05-25
The module is useful so that connections on both FTP data and control ports are considered state 'related', whether you are using active or passive mode. The module is part of the stock Ubuntu server kernels.

Just try 'modprobe ip_conntrack_ftp', it should load the module.

You can add ip_conntrack_ftp  to /etc/modules to get it to load at boot.

---

### Post by johnman145 on 2007-05-25
Thx a lot :D

Finally, after hours of trying my ftp server works behind the firewall. I read on the site of shorewall :"Including FTP connection-tracking and NAT support normally means that the modules &#8220;ip_conntrack_ftp&#8221; and &#8220;ip_nat_ftp&#8221; need to be loaded. Shorewall automatically loads these &#8220;helper&#8221; modules"

I thought since i was running an ubuntu SERVER these would probabely be okay but it seems the module is not loaded @ default.  I wonder, why does shorewall not load this module, and why am i not informed by the firewall this module isn't running ? 

Also i noticed after i run the module i get a new entry called "nf_conntrack_ftp". Why is the name different from "ip_conntrack_ftp" and does this matter?

---

### Post by turinglabs on 2007-05-25
The FTP connection-tracking helper is not loaded by default because not everyone uses it, but it is there if you need it. nf_conntrack_ftp is protcol-independent FTP connection tracking, AFAIK this is still experimental, it seems this is now the default in Feisty's 2.6.20 kernel.

---

### Post by johnman145 on 2007-05-25
Im still kind of a noob when it comes to linux, but why is there an experimental module in the ubuntu server edition? Is the ubuntu server really appropriate for a real server or should i switch to good old debian? 

I searched on google for the nf version but i dont even know who made it or where to look for more info on its stability.

---

### Post by turinglabs on 2007-05-28
> **johnman145 said:**
> Im still kind of a noob when it comes to linux, but why is there an experimental module in the ubuntu server edition? Is the ubuntu server really appropriate for a real server or should i switch to good old debian? 

I searched on google for the nf version but i dont even know who made it or where to look for more info on its stability.

I have to say I thought the same thing  initially, and the docs are sparse. Going through the kernel config in feisty's 2.6.20 kernel, I see only the NF_* module options. The help text says that the old framework is now 'obsolete', but is still available if you want it, but you would have to re-build your kernel with ' CONFIG_IP_NF_CONNTRACK_SUPPORT'. The help text for the NF framework says this:

" CONFIG_NF_CONNTRACK_SUPPORT:                                                                                                                                                                              
&#9474;  
  &#9474; Layer 3 independent connection tracking is experimental scheme                                                                                                                                            &#9474;  
  &#9474; which generalize ip_conntrack to support other layer 3 protocols.                                                                                                                                         ..."

Still says 'experimental'. I went through some of the netfilter mailng lists, it seems the 2.6.20 kernel had some major netfilter changes. I'm not sure of the stability, however.

---

