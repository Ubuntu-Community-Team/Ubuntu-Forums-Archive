---
title: "Vmware-sever 1.0.6 Problem witch virtual nics....?"
date: 2008-08-06
forum: Virtualisation
---

### Post by Mary_Sue on 2008-08-06
Im a newbie in ubuntu. I have got a computer with Ubuntu server 8.04 with kernel 2.6.24-16-server. I compiled a Vmware-server-1.0.6 and I had got any problem. My configuration is a computer with 4 nics:eth0,eth1,eth2,eth3. When starting the servcice vmware:

Starting VMware services:
   Virtual machine monitor done
   Virtual ethernet done
   Bridged networking on /dev/vmnet0 done
   Host-only networking on /dev/vmnet1 (background) done
   Bridged networking on /dev/vmnet2 done
   Bridged networking on /dev/vmnet3 done
   Bridged networking on /dev/vmnet4 done
   Host-only networking on /dev/vmnet8 (background) done
   NAT service on /dev/vmnet8 done

Appear is all ok. but when I run:

root@fw-proxy:~# ifconfig | grep vmnet

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08

When I run vmware-config.pl I create the next configuration en vmware-server: 

vmnet1(eth0) --- mode bridge
vmnet2(eth1) --- mode bridge
vmnet3(eth2) --- mode bridge
vmnet4(eth3) --- mode bridge


I execute now, ifconfig | grep vmnet. Not apears vmnet2,vmnet3.vmnet4.

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08


P.D When I execute 

mknod -m 600 /dev/vmnet1 c 119 2
mknod -m 600 /dev/vmnet2 c 119 2
mknod -m 600 /dev/vmnet3 c 119 2
mknod -m 600 /dev/vmnet4 c 119 2

Appears : 

mknod: `/dev/vmnet1': File exists
mknod: `/dev/vmnet2': File exists
mknod: `/dev/vmnet3': File exists
mknod: `/dev/vmnet4': File exists




I dont understand why I can see vmnet1,vmnet2,vmnet3,vmnet4:confused::confused::confused: Can I help me , please ??? Thanks all lot.:)

---

