---
title: "Building OpenStack with NovaLXD using conjure-up and MAAS"
date: 2019-08-16
forum: Ubuntu Cloud and Juju
---

### Post by kjetil-fleten on 2019-08-16
Hi,

I'm trying to setup a small OpenStack, using conjure-up for the first time.

I want LXD instead of KVM, so I'm trying to use the NovaLXD option. Next, I want to “Configure a New Cloud” to live on “MAAS”, but the maas option is greyed out. This is most likely because I got this error during "lxd init": 
> Error: Failed to update server configuration: Couldn't find the specified machine: Josva
"Josva" is my MAAS region controller, which is on the same server as I try to run "lxd init". Is there any chance that I can make  conjure-up make an OpenStack LXD when MAAS and LXD live on the same server ?

---

### Post by db0west on 2019-09-07
Maybe this doesn't help so much but the NovaKVM option is available as an alternative. That one works with MAAS OOTB. Let me know if you get this to work. I tried the NovaKVM one and it has not completely worked for me. So I am also intered in the LXD deploy. It is an older relase currently, Queens compared to Rocky, however. 

Let me know what you find!

---

