---
title: "LXD br_netfilter module in network namespaces"
date: 2019-03-19
forum: Server Platforms
---

### Post by shota2 on 2019-03-19
Hello all
I have ubuntu machine with lxd installed and I am playing with containers and I want to test some apps like docker or k8s inside LXD environment [COLOR=#000000]that require the br_netfilter module in [/COLOR][COLOR=#000000]network namespaces

because I was not able to enable it inside running container I cant install k8s and other applications which require this module
[/COLOR]/proc/sys/net/bridge dir is missing inside container network namespace, however it is enabled and loaded on the host machine

here are my configurations:

HOSTMACHINE:~$ lxc profile show default
config:
  linux.kernel_modules: bridge,ip_tables,nf_nat,overlay,br_netfilter
  security.privileged: "true"
description: Default LXD profile
devices:
  br0:
    nictype: bridged
    parent: br0
    type: nic
  root:                                                                                                                                                
    path: /                                                                                                                                            
    pool: lxd                                                                                                                                          
    type: disk
  src:
    path: /usr/src/
    source: /usr/src/
    type: disk
name: default
used_by:
- /1.0/containers/tmp
- /1.0/containers/kubetmp
- /1.0/containers/kubemastertmp
- /1.0/containers/centosTMPL
- /1.0/containers/centest


--------------------------------------


HOSTMACHINE:~# modinfo br_netfilter 
filename:       /lib/modules/4.18.0-16-generic/kernel/net/bridge/br_netfilter.ko
description:    Linux ethernet netfilter firewall bridge
author:         Bart De Schuymer <bdschuym@pandora.be>
author:         Lennert Buytenhek <buytenh@gnu.org>
license:        GPL
srcversion:     46DE53B0B0A82CBC5B9DD7D
depends:        bridge
retpoline:      Y
intree:         Y
name:           br_netfilter
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


------------------------------------------

HOSTMACHINE:~$ ll /proc/sys/net/
total 0
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 09:52 ./
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 09:52 ../
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 09:52 bridge/
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 09:52 core/
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 09:52 ipv4/
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 09:52 ipv6/
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 13:00 netfilter/
-rw-r--r-- 1 root root 0 &#4315;&#4304;&#4320; 19 13:00 nf_conntrack_max
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 09:52 unix/

--------------------------------------------


CONTAINER ~]# modinfo br_netfilter
modinfo: ERROR: Module alias br_netfilter not found.
CONTAINER ~]# ll /proc/sys/net/
total 0
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 08:47 core
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 05:53 ipv4
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 05:53 ipv6
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 05:53 netfilter
dr-xr-xr-x 1 root root 0 &#4315;&#4304;&#4320; 19 05:53 unix




Any idea? plz help 
Thank you

---

