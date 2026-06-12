---
title: "netstat-nat command is not working on ubuntu server"
date: 2015-09-02
forum: Server Platforms
---

### Post by sytix on 2015-09-02
Hi everyone!

I have installed netstat-nat program to a ubuntu server, to monitor the current static NAT translations in the system (not the NAT entries in the iptables nat table).

My problem is when I run the command netstat-nat, it give back this result:
# netstat-nat
Could not read info about connections from the kernel, make sure netfilter is enabled in kernel or by modules.

My loaded modules are:
```
# lsmod | awk {'print $1'}
Module
nf_conntrack_netlink
nfnetlink
ebtable_broute
ebtable_filter
rte_kni
igb_uio
uio
xt_nat
veth
ipt_REJECT
ip6table_filter
ip6_tables
ebtable_nat
ebtables
xt_addrtype
xt_conntrack
aufs
xt_CHECKSUM
iptable_mangle
ipt_MASQUERADE
iptable_nat
nf_conntrack_ipv4
nf_defrag_ipv4
nf_nat_ipv4
nf_nat
nf_conntrack
xt_tcpudp
bridge
stp
llc
iptable_filter
ip_tables
x_tables
gpio_ich
coretemp
kvm_intel
ast
ttm
kvm
drm_kms_helper
drm
crct10dif_pclmul
crc32_pclmul
syscopyarea
ghash_clmulni_intel
aesni_intel
sysfillrect
aes_x86_64
lrw
gf128mul
glue_helper
sysimgblt
ablk_helper
joydev
cryptd
serio_raw
lpc_ich
i2c_ismt
mac_hid
ipmi_si
ipmi_msghandler
shpchp
lp
parport
hid_generic
usbhid
hid
igb
ixgbe
ahci
libahci
i2c_algo_bit
dca
ptp
pps_core
mdio
```

And my system is:
```
uname -a
Linux atom 3.16.0-37-generic #51~14.04.1-Ubuntu SMP Wed May 6 15:23:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
I have already cheked all the corresponding google/bing/yahoo search link to solve the promblem but they didn't help.

Do you have any idea how to make netstat-nat program work on my system or any alternative ways for gettin the current NAT tarnslations (not iptables flow entries)?

Best regards,
Sabi

---

### Post by Doug S on 2015-09-02
Hi, and welcome to Ubuntu forums.

It is not clear to me what is different between your system and mine.```
doug@doug-64:~$ netstat-nat
Could not read info about connections from the kernel, make sure netfilter is enabled in kernel or by modules.
doug@doug-64:~$ sudo netstat-nat
Proto NATed Address                  Destination Address            State
tcp   doug-xps2.smythies.com:60943   38.113.165.113:https           TIME_WAIT
tcp   doug-xps2.smythies.com:54154   bn3sch020010553.wns.wind:https ESTABLISHED
tcp   doug-xps2.smythies.com:60894   h-207-228-83-33.gen.cadvi:http TIME_WAIT
tcp   doug-xps2.smythies.com:56335   wolfe.freenode.net:ircd        ESTABLISHED
tcp   doug-xps2.smythies.com:60949   pe-in-f147.1e100.net:https     ESTABLISHED
tcp   doug-xps2.smythies.com:60892   pe-in-f100.1e100.net:http      TIME_WAIT
tcp   doug-xps2.smythies.com:60898   stackoverflow.com:https        ESTABLISHED
tcp   doug-xps2.smythies.com:60868   edge-star-shv-04-prn2.fa:https ESTABLISHED
tcp   doug-xps2.smythies.com:60889   103.31.6.35:https              TIME_WAIT
tcp   doug-xps2.smythies.com:60935   38.113.165.113:https           TIME_WAIT
``````
doug@doug-64:~$ lsmod | awk {'print $1'}
Module
xt_multiport
xt_u32
ext2
ipt_REJECT
xt_tcpudp
xt_state
xt_recent
ipt_LOG
iptable_nat
nf_nat
nf_conntrack_ipv4
nf_conntrack
nf_defrag_ipv4
iptable_filter
ip_tables
x_tables
i915
drm_kms_helper
psmouse
serio_raw
drm
ppdev
parport_pc
i2c_algo_bit
video
shpchp
dcdbas
mac_hid
lp
parport
floppy
via_rhine
usbhid
hid
tg3
```Sometimes I just look at the connection tracking table directly, however that includes all connections, not just NAT ones.```
doug@doug-64:~$ sudo cat /proc/net/ip_conntrack
```

---

### Post by sytix on 2015-09-16
My system doesn't have the any file named /proc/net/ip_conntrack.

---

### Post by Doug S on 2015-09-16
> **sytix said:**
> My system doesn't have the any file named /proc/net/ip_conntrack.Well no you wouldn't if it isn't needed by your iptables stuff. I'm not sure what else to say about your issue. I assume you noticed that I had to use "sudo" in my original posting for it to work.

---

