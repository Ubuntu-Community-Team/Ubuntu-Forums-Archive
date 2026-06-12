---
title: "APF firewall not working on 8.04 was fine on 6.06"
date: 2008-04-29
forum: Server Platforms
---

### Post by Linux7 on 2008-04-29
Hi, I had apf firewall working great on Ubuntu 6.06 LTS but after installing on Ubuntu 8.04 LTS I get the errors below.  This in on an OpenVZ/Ubuntu 8.04 VPS server.


This is how I installed:

tar -zxvf apf*.gz
change directory to apf install directory
mkdir /etc/rc.d
ln -s /etc/init.d/ /etc/rc.d/init.d
cp apf.init /etc/init.d/apf
chmod 755 /etc/init.d/apf
update-rc.d apf defaults
./install.sh
edit /etc/apf/conf.apf and set "DEVEL_MODE="0" and add TCP ports

apf -s







When restarting APF I get:

root@?:/etc/apf# apf -r
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
apf(15980): {glob} flushing & zeroing chain policies
apf(15980): {glob} firewall offline
apf(16019): {glob} activating firewall
apf(16060): {glob} determined (IFACE_IN) venet0 has address 127.0.0.1
apf(16060): {glob} determined (IFACE_OUT) venet0 has address 127.0.0.1
apf(16060): {glob} loading preroute.rules
apf(16060): {resnet} downloading
apf(16060): {resnet} parsing reserved.networks into /etc/apf/internals/reserved.networks
apf(16060): {glob} loading reserved.networks
apf(16060): {glob} SET_REFRESH is set to 10 minutes
apf(16060): {glob} loading bt.rules
apf(16060): {dshield} downloading
apf(16060): {dshield} parsing top10-2.txt into /etc/apf/ds_hosts.rules
apf(16060): {dshield} loading ds_hosts.rules
apf(16060): {sdrop} downloading
apf(16060): {sdrop} parsing drop.lasso into /etc/apf/sdrop_hosts.rules
apf(16060): {sdrop} loading sdrop_hosts.rules
apf(16060): {glob} loading common drop ports
apf(16060): {blk_ports} deny all to/from tcp port 135:139
apf(16060): {blk_ports} deny all to/from udp port 135:139
apf(16060): {blk_ports} deny all to/from tcp port 111
apf(16060): {blk_ports} deny all to/from udp port 111
apf(16060): {blk_ports} deny all to/from tcp port 513
apf(16060): {blk_ports} deny all to/from udp port 513
apf(16060): {blk_ports} deny all to/from tcp port 520
apf(16060): {blk_ports} deny all to/from udp port 520
apf(16060): {blk_ports} deny all to/from tcp port 445
apf(16060): {blk_ports} deny all to/from udp port 445
apf(16060): {blk_ports} deny all to/from tcp port 1433
apf(16060): {blk_ports} deny all to/from udp port 1433
apf(16060): {blk_ports} deny all to/from tcp port 1434
apf(16060): {blk_ports} deny all to/from udp port 1434
apf(16060): {blk_ports} deny all to/from tcp port 1234
apf(16060): {blk_ports} deny all to/from udp port 1234
apf(16060): {blk_ports} deny all to/from tcp port 1524
apf(16060): {blk_ports} deny all to/from udp port 1524
apf(16060): {blk_ports} deny all to/from tcp port 3127
apf(16060): {blk_ports} deny all to/from udp port 3127
apf(16060): {pkt_sanity} set active PKT_SANITY
apf(16060): {pkt_sanity} deny inbound tcp-flag pairs ALL NONE
apf(16060): {pkt_sanity} deny inbound tcp-flag pairs SYN,FIN SYN,FIN
apf(16060): {pkt_sanity} deny inbound tcp-flag pairs SYN,RST SYN,RST
apf(16060): {pkt_sanity} deny inbound tcp-flag pairs FIN,RST FIN,RST
apf(16060): {pkt_sanity} deny inbound tcp-flag pairs ACK,FIN FIN
apf(16060): {pkt_sanity} deny inbound tcp-flag pairs ACK,URG URG
apf(16060): {pkt_sanity} deny inbound tcp-flag pairs ACK,PSH PSH
apf(16060): {pkt_sanity} deny inbound tcp-flag pairs ALL FIN,URG,PSH
apf(16060): {pkt_sanity} deny inbound tcp-flag pairs ALL SYN,RST,ACK,FIN,URG
apf(16060): {pkt_sanity} deny inbound tcp-flag pairs ALL ALL
apf(16060): {pkt_sanity} deny inbound tcp-flag pairs ALL FIN
apf(16060): {pkt_sanity} deny outbound tcp-flag pairs ALL NONE
apf(16060): {pkt_sanity} deny outbound tcp-flag pairs SYN,FIN SYN,FIN
apf(16060): {pkt_sanity} deny outbound tcp-flag pairs SYN,RST SYN,RST
apf(16060): {pkt_sanity} deny outbound tcp-flag pairs FIN,RST FIN,RST
apf(16060): {pkt_sanity} deny outbound tcp-flag pairs ACK,FIN FIN
apf(16060): {pkt_sanity} deny outbound tcp-flag pairs ACK,PSH PSH
apf(16060): {pkt_sanity} deny outbound tcp-flag pairs ACK,URG URG
apf(16060): {pkt_sanity} deny all fragmented udp
apf(16060): {pkt_sanity} deny inbound tcp port 0
apf(16060): {pkt_sanity} deny outbound tcp port 0
apf(16060): {blk_p2p} set active BLK_P2P
apf(16060): {blk_p2p} deny all to/from tcp port 1214
apf(16060): {blk_p2p} deny all to/from udp port 1214
apf(16060): {blk_p2p} deny all to/from tcp port 2323
apf(16060): {blk_p2p} deny all to/from udp port 2323
apf(16060): {blk_p2p} deny all to/from tcp port 4660:4678
apf(16060): {blk_p2p} deny all to/from udp port 4660:4678
apf(16060): {blk_p2p} deny all to/from tcp port 6257
apf(16060): {blk_p2p} deny all to/from udp port 6257
apf(16060): {blk_p2p} deny all to/from tcp port 6699
apf(16060): {blk_p2p} deny all to/from udp port 6699
apf(16060): {blk_p2p} deny all to/from tcp port 6346
apf(16060): {blk_p2p} deny all to/from udp port 6346
apf(16060): {blk_p2p} deny all to/from tcp port 6347
apf(16060): {blk_p2p} deny all to/from udp port 6347
apf(16060): {blk_p2p} deny all to/from tcp port 6881:6889
apf(16060): {blk_p2p} deny all to/from udp port 6881:6889
apf(16060): {blk_p2p} deny all to/from tcp port 6346
apf(16060): {blk_p2p} deny all to/from udp port 6346
apf(16060): {blk_p2p} deny all to/from tcp port 7778
apf(16060): {blk_p2p} deny all to/from udp port 7778
apf(16060): {glob} loading log.rules
apf(16060): {glob} virtual net subsystem disabled.
apf(16060): {glob} loading main.rules
apf(16060): {glob} opening inbound tcp port 21 on 0/0
apf(16060): {glob} opening inbound tcp port 22 on 0/0
apf(16060): {glob} opening inbound tcp port 25 on 0/0
apf(16060): {glob} opening inbound tcp port 53 on 0/0
apf(16060): {glob} opening inbound tcp port 80 on 0/0
apf(16060): {glob} opening inbound tcp port 110 on 0/0
apf(16060): {glob} opening inbound tcp port 143 on 0/0
apf(16060): {glob} opening inbound tcp port 443 on 0/0
apf(16060): {glob} opening inbound tcp port 465 on 0/0
apf(16060): {glob} opening inbound tcp port 587 on 0/0
apf(16060): {glob} opening inbound tcp port 888 on 0/0
apf(16060): {glob} opening inbound tcp port 993 on 0/0
apf(16060): {glob} opening inbound tcp port 995 on 0/0
apf(16060): {glob} opening inbound tcp port 3306 on 0/0
apf(16060): {glob} opening inbound tcp port 10000 on 0/0
apf(16060): {glob} opening inbound tcp port 44177 on 0/0
apf(16060): {glob} opening inbound icmp type 3 on 0/0
apf(16060): {glob} opening inbound icmp type 5 on 0/0
apf(16060): {glob} opening inbound icmp type 11 on 0/0
apf(16060): {glob} opening inbound icmp type 0 on 0/0
apf(16060): {glob} opening inbound icmp type 30 on 0/0
apf(16060): {glob} opening inbound icmp type 8 on 0/0
apf(16060): {glob} resolv dns discovery for 64.79.200.111
apf(16060): {glob} resolv dns discovery for 64.79.200.113
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
apf(16060): {glob} loading postroute.rules
apf(16060): {glob} default (egress) output accept
apf(16060): {glob} default (ingress) input drop
apf(16019): {glob} firewall initalized
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.18-spry2ovz028stab053.5-smp/modules.dep: No such file or directory
apf(16019): {glob} fast load snapshot saved
root@?:/etc/apf#







Also get this at the end of running "/sbin/iptables -L -n":
.
.
.
DROP all -- 0.0.0.0/0 91.200.56.0/22
DROP all -- 91.200.72.0/22 0.0.0.0/0
DROP all -- 0.0.0.0/0 91.200.72.0/22

Chain TALLOW (2 references)
target prot opt source destination

Chain TDENY (2 references)
target prot opt source destination

Chain TGALLOW (2 references)
target prot opt source destination

Chain TGDENY (2 references)
target prot opt source destination

---

### Post by fchx on 2008-05-09
Same here. Our server is a real server (not virtual).

After upgraded it from 6.06LTS to 8.04LTS, apf doesn't start.

Does anyone know a substitute to APF + BFD that run in Ubuntu? (I prefer a .deb package).

Thanks in advance

---

### Post by basketcase on 2009-02-06
Did either of you get this working?  I'm thinking about setting up an Ubuntu server and I use APF + BFD on CentOS...Would love to use Ubuntu

---

