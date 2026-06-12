---
title: "Configuration of libvirt / webvirtmgr"
date: 2013-06-01
forum: Server Platforms
---

### Post by Toxic64 on 2013-06-01
I have a little network configuration problem with webvirtmgr and libvirt.

Here is  the point:

I have an Ubuntu server 12.04.2 LTS Using samba 4 as an Active  Directory DC/DNS so it has to remain on static IP 192.168.0.16

  

 config is:
  
 auto etho
 iface eth0 inet static 
 address 192.168.0.16
 netmask 255.255.255.0
 network 192.168.0.0
 gateway 192.168.0.1
 dns search irisit.fr
 nameservers 192.168.0.16 8.8.8.8
  
  
 
I installed Webvirtmgr + libvirt  etc following guides   and it seems to work (accessing the site, creating VMs etc.

[https://www.webvirtmgr.net/docs/ ]("https://www.webvirtmgr.net/docs/")
[https://github.com/retspen/webvirtmgr](https://github.com/retspen/webvirtmgr)

The network  pool  is set to default and off /Isolate. it throws an error500 when trying to  start it so I guess my network config is wrong but I don’t no where (I’m kind of  a newbie to this)

  
 how should I configure my /etc/network/interfaces file for this to  work?

  
 Also anybody knows if there is any possibility to use active directory authentication to  login to the administration site? 

  
 thanks a lot for you help.

---

### Post by JnPson on 2013-06-02
> **Toxic64 said:**
> I have a little network configuration problem with webvirtmgr and libvirt.

Here is  the point:

I have an Ubuntu server 12.04.2 LTS Using samba 4 as an Active  Directory DC/DNS so it has to remain on static IP 192.168.0.16

  

 config is:
  
 auto etho
 iface eth0 inet static 
 address 192.168.0.16
 netmask 255.255.255.0
 network 192.168.0.0
 gateway 192.168.0.1
 dns search irisit.fr
 nameservers 192.168.0.16 8.8.8.8
  
  
 
I installed Webvirtmgr + libvirt  etc following guides   and it seems to work (accessing the site, creating VMs etc.

[https://www.webvirtmgr.net/docs/ ]("https://www.webvirtmgr.net/docs/")
[https://github.com/retspen/webvirtmgr](https://github.com/retspen/webvirtmgr)

The network  pool  is set to default and off /Isolate. it throws an error500 when trying to  start it so I guess my network config is wrong but I don’t no where (I’m kind of  a newbie to this)

  
 how should I configure my /etc/network/interfaces file for this to  work?

  
 Also anybody knows if there is any possibility to use active directory authentication to  login to the administration site? 

  
 thanks a lot for you help.

I don't know if this is just a typo or if you actually have this error in your interfaces-file, but it should look like this:
auto **eht0 **
 iface eth0 inet static 
 address 192.168.0.16
 netmask 255.255.255.0
 network 192.168.0.0
 gateway 192.168.0.1
 dns**-**search irisit.fr
 **dns-**nameservers 192.168.0.16 8.8.8.8

---

### Post by Toxic64 on 2013-06-02
yep that were simple typos sorry . My interfaces file is correct.

---

