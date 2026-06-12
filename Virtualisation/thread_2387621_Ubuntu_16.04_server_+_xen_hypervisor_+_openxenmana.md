---
title: "Ubuntu 16.04 server + xen hypervisor + openxenmanager no connect"
date: 2018-03-21
forum: Virtualisation
---

### Post by getut on 2018-03-21
I have a fresh install of Ubuntu 16.04 server and have installed xen-hypervisor-4.9-amd64 from the default ubuntu repos. I also have a pre-existing client PC running 16.04 desktop that I installed openxenmanager on.

I have not been able to find any documentation on how to get openxenmanager connected. Everything I find deals xenserver 6 series which appears to be a different product. I'm sure I'm just missing either some small add on package or setting a listen line in some config file somewhere but have been searching for 2 days unable to find it. xen is up and running with no VM's in it yet as proven by running
cat /proc/xen/capabilities and getting control_d returned. Also I show dom0 with xl list.

---

