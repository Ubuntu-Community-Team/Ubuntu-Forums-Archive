---
title: "No ethernet in Jeos"
date: 2008-02-25
forum: Server Platforms
---

### Post by Trojanmon on 2008-02-25
Hi,
I'm trying to setup a vmware server using Jeos as the _host_. I'll probably eventually put Ubuntu Server in one of the VMs along with some other appliances, but I want a lightweight layer under it.

I managed to get Jeos 7.0.4 setup without too much trouble. The issue I'm having right now is that eth0 is not detected. The installer had no issues finding my ethernet and using dhcp to autoconfig. I checked the interface config and it's still set for dhcp, but ifconfig simply says there is no interface. 

Any suggestions? Is Jeos even meant for running as the host?

Thanks.

---

### Post by bluefrog on 2008-02-26
jeos is not supposed to be the host but the virtualized OS.

---

### Post by Gerbenh on 2008-03-31
[check this to enable ethernet0 in JeOS 7.10]("http://www.gerbenhoekstra.com/workaround-vmware-eth0-problems-with-ubuntu_jeos_710/")

---

