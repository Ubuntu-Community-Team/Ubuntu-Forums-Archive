---
title: "Hangs in boot"
date: 2009-07-26
forum: Server Platforms
---

### Post by torsson on 2009-07-26
Hi im having problem with ubuntu server, when im using static local-ip on eth1 and crosswired cable between 2 machines ubuntu hangs at "Configuring Network" at boot and dosent continue and i need to boot in failsafe and remove it from the interfaces file, but if i do if-up when the machine is online it works just fine, any idea how i can fix this? some timeout time or somthing?

My eth1 setup looks like this
( i have tryed some diffrent with broadcast and such )
auto eth1
iface eth1 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.0

---

### Post by kennedy7 on 2009-07-26
what version of Ubuntu are you using? If you are using Ubuntu 9.04 server then boot into recovery mode and select option "root with network" and the it will auto configure your eth1 and it should work fine. It happened to me before

---

### Post by torsson on 2009-07-26
Thanks for the reply.

My ubuntu version is
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty


im gona try your suggestion and se if it will work. my servers are located 450 km from me so i will do it next time im there

---

