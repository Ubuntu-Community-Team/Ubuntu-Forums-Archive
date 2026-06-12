---
title: "IPTABLES routing for PPTP issue"
date: 2010-07-02
forum: Server Platforms
---

### Post by twistedtwig on 2010-07-02
Hi all,

I have a new ubuntu box as my firewall.  I am trying to setup a simple pptp vpn so I can access some boxes remotely.  I seem to be able to authenticate but can not ping anyone in my network.

the local dhcp uses 192.168.10.* so I setup the pptp to have a range of 192.168.10.21-25 (not used by dhcp).

when they connect I can see them in ifconfig:

```
ppp0      Link encap:Point-to-Point Protocol
          inet addr:192.168.10.20  P-t-P:192.168.10.21  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1646 (1.6 KB)  TX bytes:108 (108.0 B)


```

when I look at the syslog it is not a pretty picture:

```
jon@firewig:~$ tail -n 100 /var/log/syslog
Jul  3 00:28:02 firewig pppd[6117]: pptpd-logwtmp: $Version$
Jul  3 00:28:02 firewig pppd[6117]: pppd 2.4.5 started by root, uid 0
Jul  3 00:28:02 firewig pppd[6117]: using channel 21
Jul  3 00:28:02 firewig pppd[6117]: Using interface ppp0
Jul  3 00:28:02 firewig pppd[6117]: Connect: ppp0 <--> /dev/pts/2
Jul  3 00:28:02 firewig pppd[6117]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x511abb24> <pcomp> <accomp>]
Jul  3 00:28:02 firewig pptpd[6116]: GRE: Bad checksum from pppd.
Jul  3 00:28:02 firewig pppd[6117]: rcvd [LCP ConfReq id=0x0 <mru 1400> <magic 0x8dd6215> <pcomp> <accomp> <callback CBCP>]
Jul  3 00:28:02 firewig pppd[6117]: sent [LCP ConfRej id=0x0 <callback CBCP>]
Jul  3 00:28:02 firewig pppd[6117]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x511abb24> <pcomp> <accomp>]
Jul  3 00:28:02 firewig pppd[6117]: rcvd [LCP ConfReq id=0x1 <mru 1400> <magic 0x8dd6215> <pcomp> <accomp>]
Jul  3 00:28:02 firewig pppd[6117]: sent [LCP ConfAck id=0x1 <mru 1400> <magic 0x8dd6215> <pcomp> <accomp>]
Jul  3 00:28:02 firewig pppd[6117]: sent [LCP EchoReq id=0x0 magic=0x511abb24]
Jul  3 00:28:02 firewig pppd[6117]: sent [CHAP Challenge id=0x92 <2a754f257a1703e26c224dbfa042c463>, name = "pptpd"]
Jul  3 00:28:02 firewig pptpd[6116]: CTRL: Ignored a SET LINK INFO packet with real ACCMs!
Jul  3 00:28:02 firewig pppd[6117]: rcvd [LCP Ident id=0x2 magic=0x8dd6215 "MSRASV5.20"]
Jul  3 00:28:02 firewig pppd[6117]: rcvd [LCP Ident id=0x3 magic=0x8dd6215 "MSRAS-0-FALMER"]
Jul  3 00:28:02 firewig pppd[6117]: rcvd [LCP EchoRep id=0x0 magic=0x8dd6215]
Jul  3 00:28:02 firewig pppd[6117]: rcvd [CHAP Response id=0x92 <1e0aabac231ba340666e20a50f3daf2e0000000000000000bc71b71f63074ee1d1e81f4b7262fd363db6e161ba8fa85900>, name = "jon"]
Jul  3 00:28:02 firewig pppd[6117]: sent [CHAP Success id=0x92 "S=F915F41C7469C75EBAFA4D71216D9136A7F6594A M=Access granted"]
Jul  3 00:28:02 firewig pppd[6117]: sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
Jul  3 00:28:02 firewig pppd[6117]: rcvd [CCP ConfReq id=0x4 <mppe +H +M +S +L -D -C>]
Jul  3 00:28:02 firewig pppd[6117]: sent [CCP ConfNak id=0x4 <mppe +H -M +S -L -D -C>]
Jul  3 00:28:02 firewig pppd[6117]: rcvd [IPCP ConfReq id=0x5 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns2 0.0.0.0> <ms-wins 0.0.0.0>]
Jul  3 00:28:02 firewig pppd[6117]: sent [IPCP TermAck id=0x5]
Jul  3 00:28:02 firewig pppd[6117]: rcvd [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
Jul  3 00:28:03 firewig pppd[6117]: rcvd [CCP ConfReq id=0x6 <mppe +H -M +S -L -D -C>]
Jul  3 00:28:03 firewig pppd[6117]: sent [CCP ConfAck id=0x6 <mppe +H -M +S -L -D -C>]
Jul  3 00:28:03 firewig pppd[6117]: MPPE 128-bit stateless compression enabled
Jul  3 00:28:03 firewig pppd[6117]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.10.20>]
Jul  3 00:28:03 firewig pppd[6117]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
Jul  3 00:28:03 firewig pppd[6117]: sent [IPCP ConfReq id=0x2 <addr 192.168.10.20>]
Jul  3 00:28:03 firewig pppd[6117]: rcvd [IPCP ConfAck id=0x2 <addr 192.168.10.20>]
Jul  3 00:28:04 firewig pppd[6117]: rcvd [IPCP ConfReq id=0x7 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns2 0.0.0.0> <ms-wins 0.0.0.0>]
Jul  3 00:28:04 firewig pppd[6117]: sent [IPCP ConfRej id=0x7 <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns2 0.0.0.0> <ms-wins 0.0.0.0>]
Jul  3 00:28:04 firewig pppd[6117]: rcvd [IPCP ConfReq id=0x8 <addr 0.0.0.0>]
Jul  3 00:28:04 firewig pppd[6117]: sent [IPCP ConfNak id=0x8 <addr 192.168.10.21>]
Jul  3 00:28:04 firewig pppd[6117]: rcvd [IPCP ConfReq id=0x9 <addr 192.168.10.21>]
Jul  3 00:28:04 firewig pppd[6117]: sent [IPCP ConfAck id=0x9 <addr 192.168.10.21>]
Jul  3 00:28:04 firewig pppd[6117]: found interface eth2 for proxy arp
Jul  3 00:28:04 firewig pppd[6117]: local  IP address 192.168.10.20
Jul  3 00:28:04 firewig pppd[6117]: remote IP address 192.168.10.21
Jul  3 00:28:04 firewig pppd[6117]: pptpd-logwtmp.so ip-up ppp0 jon 62.133.24.54
Jul  3 00:28:04 firewig pppd[6117]: Script /etc/ppp/ip-up started (pid 6120)
Jul  3 00:28:04 firewig named[928]: received control channel command 'reconfig'
Jul  3 00:28:04 firewig named[928]: loading configuration from '/etc/bind/named.conf'
Jul  3 00:28:04 firewig named[928]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Jul  3 00:28:04 firewig named[928]: using default UDP/IPv4 port range: [1024, 65535]
Jul  3 00:28:04 firewig named[928]: using default UDP/IPv6 port range: [1024, 65535]
Jul  3 00:28:04 firewig named[928]: listening on IPv4 interface ppp0, 192.168.10.20#53
Jul  3 00:28:04 firewig named[928]: reloading configuration succeeded
Jul  3 00:28:04 firewig named[928]: any newly configured zones are now loaded
Jul  3 00:28:05 firewig kernel: [628825.360604] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=30665 PROTO=UDP SPT=68 DPT=67 LEN=308
Jul  3 00:28:05 firewig postfix/master[1657]: reload -- version 2.7.0, configuration /etc/postfix
Jul  3 00:28:05 firewig pppd[6117]: Script /etc/ppp/ip-up finished (pid 6120), status = 0x0
Jul  3 00:28:05 firewig kernel: [628825.420961] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30667 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:05 firewig kernel: [628826.168553] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30674 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:06 firewig kernel: [628826.912572] Dropped by firewall: IN=ppp0 OUT=eth2 SRC=192.168.10.21 DST=192.168.10.96 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=30681 PROTO=ICMP TYPE=8 CODE=0 ID=1536 SEQ=256
Jul  3 00:28:06 firewig kernel: [628826.920547] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30684 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:07 firewig kernel: [628827.668560] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30688 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:08 firewig kernel: [628828.420556] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30692 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:08 firewig kernel: [628829.168554] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30698 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:09 firewig kernel: [628829.360557] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=128 ID=30701 PROTO=UDP SPT=68 DPT=67 LEN=308
Jul  3 00:28:09 firewig kernel: [628829.920559] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30706 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:10 firewig kernel: [628830.668557] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30711 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:11 firewig kernel: [628831.420567] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30715 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:11 firewig kernel: [628831.420587] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30717 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:11 firewig kernel: [628832.168554] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30738 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:11 firewig kernel: [628832.172537] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30739 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:11 firewig kernel: [628832.336549] Dropped by firewall: IN=ppp0 OUT=eth2 SRC=192.168.10.21 DST=192.168.10.96 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=30743 PROTO=ICMP TYPE=8 CODE=0 ID=1536 SEQ=512
Jul  3 00:28:12 firewig kernel: [628832.920574] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30750 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:12 firewig kernel: [628832.920594] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30751 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:13 firewig kernel: [628833.672565] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30759 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:13 firewig kernel: [628833.672587] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=96 TOS=0x00 PREC=0x00 TTL=128 ID=30760 PROTO=UDP SPT=137 DPT=137 LEN=76
Jul  3 00:28:14 firewig kernel: [628834.420565] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=128 ID=30770 PROTO=UDP SPT=138 DPT=138 LEN=185
Jul  3 00:28:15 firewig kernel: [628835.920564] Dropped by firewall: IN=ppp0 OUT= MAC= SRC=192.168.10.21 DST=255.255.255.255 LEN=205 TOS=0x00 PREC=0x00 TTL=128 ID=30783 PROTO=UDP SPT=138 DPT=138 LEN=185
Jul  3 00:28:17 firewig pppd[6117]: rcvd [LCP TermReq id=0xa 08 dd 62 15 00 3c cd 74 00 00 00 00]
Jul  3 00:28:17 firewig pppd[6117]: LCP terminated by peer (^HM-]b^U^@<M-Mt^@^@^@^@)
Jul  3 00:28:17 firewig pppd[6117]: pptpd-logwtmp.so ip-down ppp0
Jul  3 00:28:17 firewig pppd[6117]: Connect time 0.3 minutes.
Jul  3 00:28:17 firewig pppd[6117]: Sent 0 bytes, received 2722 bytes.
Jul  3 00:28:17 firewig pppd[6117]: Script /etc/ppp/ip-down started (pid 6159)
Jul  3 00:28:17 firewig pppd[6117]: sent [LCP TermAck id=0xa]
Jul  3 00:28:17 firewig named[928]: received control channel command 'reconfig'
Jul  3 00:28:17 firewig named[928]: loading configuration from '/etc/bind/named.conf'
Jul  3 00:28:17 firewig named[928]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Jul  3 00:28:17 firewig named[928]: using default UDP/IPv4 port range: [1024, 65535]
Jul  3 00:28:17 firewig named[928]: using default UDP/IPv6 port range: [1024, 65535]
Jul  3 00:28:17 firewig named[928]: no longer listening on 192.168.10.20#53
Jul  3 00:28:17 firewig named[928]: reloading configuration succeeded
Jul  3 00:28:17 firewig named[928]: any newly configured zones are now loaded
Jul  3 00:28:17 firewig pptpd[6116]: CTRL: Reaping child PPP[6117]
Jul  3 00:28:17 firewig pppd[6117]: Modem hangup
Jul  3 00:28:17 firewig pppd[6117]: Connection terminated.
Jul  3 00:28:17 firewig pppd[6117]: Waiting for 1 child processes...
Jul  3 00:28:17 firewig pppd[6117]:   script /etc/ppp/ip-down, pid 6159
Jul  3 00:28:17 firewig postfix/master[1657]: reload -- version 2.7.0, configuration /etc/postfix
Jul  3 00:28:17 firewig pppd[6117]: Script /etc/ppp/ip-down finished (pid 6159), status = 0x0
Jul  3 00:28:17 firewig pppd[6117]: Exit.
Jul  3 00:28:17 firewig pptpd[6116]: CTRL: Client 62.133.24.54 control connection finished

```

here is my firewall:

```
#!/bin/sh

iptables="/sbin/iptables"
modprobe="/sbin/modprobe"
depmod="/sbin/depmod"

EXTIF="eth1"
INTIF="eth2"

load () {

        $depmod -a

        $modprobe ip_tables
        $modprobe ip_conntrack
        $modprobe ip_conntrack_ftp
        $modprobe ip_conntrack_irc
        $modprobe iptable_nat
        $modprobe ip_nat_ftp
        $modprobe ip_conntrack_pptp
        $modprobe ip_nat_pptp

echo "enable forwarding..."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "enable dynamic addr"
echo "1" > /proc/sys/net/ipv4/ip_dynaddr

#  start firewall

        #default policies
        $iptables -P INPUT DROP
        $iptables -F INPUT
        $iptables -P OUTPUT DROP
        $iptables -F OUTPUT
        $iptables -P FORWARD DROP
        $iptables -F FORWARD
        $iptables -t nat -F


echo "  opening loopback interface for socket based services."
$iptables -A INPUT -i lo -j ACCEPT
$iptables -A OUTPUT -o lo -j ACCEPT

echo "  allow all connections OUT and ONLY existing related ones IN"
$iptables -A INPUT -i $INTIF -j ACCEPT
$iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$iptables -A OUTPUT -o $EXTIF -j ACCEPT
$iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$iptables -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$iptables -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$iptables -A FORWARD -j LOG --log-level 7 --log-prefix "Dropped by firewall: "

$iptables -A INPUT -j LOG --log-level 7 --log-prefix "Dropped by firewall: "
$iptables -A OUTPUT -j LOG --log-level 7 --log-prefix "Dropped by firewall: "

echo "  enabling SNAT (MASQUERADE) functionality on $EXTIF"
$iptables -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

$iptables -A INPUT -i $INTIF -j ACCEPT
$iptables -A OUTPUT -o $INTIF -j ACCEPT

echo "  Allowing packets with ICMP data (pings)"
$iptables -A INPUT -p icmp -j ACCEPT
$iptables -A OUTPUT -p icmp -j ACCEPT

$iptables -A INPUT -p udp -i $INTIF --dport 67 -m state --state NEW -j ACCEPT

echo "  port 137 for netBios"
$iptables -A INPUT -i $INTIF -p udp --dport 137 -j ACCEPT
$iptables -A OUTPUT -o $INTIF -p udp --dport 137 -j ACCEPT

echo "  opening port 53 for DNS queries"
$iptables -A INPUT -p udp -i $EXTIF --sport 53 -j ACCEPT

#echo "  opening port 22 for internal ssh"
$iptables -A INPUT -i $INTIF -p tcp --dport 22 -j ACCEPT

echo "  opening port 80 for webserver"
$iptables -A INPUT -p tcp -i $EXTIF --dport 80 -m state --state NEW -j ACCEPT

echo "  opening port 21 for FTP Server"
$iptables  -A INPUT -p tcp -i $EXTIF --dport 21 -m state --state NEW -j ACCEPT

echo "  opening ssh for web on port 2609 for firewig"
$iptables -A INPUT -p tcp --dport 2609 -j ACCEPT
$iptables -A OUTPUT -p tcp --dport 2609 -j ACCEPT

echo "  opening ssh for web on port 22  for betty"
$iptables -A PREROUTING -t nat -i $EXTIF -p tcp --dport 22 -j DNAT  --to 192.168.10.96:2302
$iptables -A FORWARD -p tcp -m state --state NEW -d 192.168.10.96 --dport 2302 -j ACCEPT

#echo "  opening ssh for web on port 2302  for firewig 2302"
#$iptables -A PREROUTING -t nat -i $EXTIF -p tcp --dport 2302 -j DNAT  --to 192.168.10.96:2302
#$iptables -A FORWARD -p tcp -m state --state NEW -d 192.168.10.96 --dport 2302 -j ACCEPT

echo "  opening Apache webserver for HoH"
$iptables -A PREROUTING -t nat -i $EXTIF -p tcp --dport 80 -j DNAT --to 192.168.10.96:80
$iptables -A FORWARD -p tcp -m state --state NEW -d 192.168.10.96 --dport 80 -j ACCEPT

echo "  opening Hudson"
$iptables -A PREROUTING -t nat -i $EXTIF -p tcp --dport 81 -j DNAT --to 192.168.10.97:81
$iptables -A FORWARD -p tcp -m state --state NEW -d 192.168.10.97 --dport 81 -j ACCEPT

echo "  opening Target Process"
$iptables -A PREROUTING -t nat -i $EXTIF -p tcp --dport 90 -j DNAT --to 192.168.10.98:90
$iptables -A FORWARD -p tcp -m state --state NEW -d 192.168.10.98 --dport 90 -j ACCEPT

$iptables -A INPUT -i $EXTIF -p TCP --dport 1723 -j ACCEPT



echo "  This is designed to stop brute force attacks"
$iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 6/minute --limit-burst 5 -j ACCEPT

#  NOTE THE THREE LINES BELOW ALLOW ACCESS FOR THE VPN CONNECTION...Ry.

$iptables -A INPUT -p 47 -j ACCEPT
$iptables -A INPUT -i ppp+ -j ACCEPT
$iptables -A FORWARD -i ppp+ -o $INTIF -j ACCEPT
$iptables -A FORWARD -i $INTIF -o ppp+ -j ACCEPT
#$iptables -A OUTPUT -p ALL -o ppp+ -j ACCEPT

}
flush() {
        echo "flushing rules...."
        $iptables -P FORWARD ACCEPT
        $iptables -F INPUT
        $iptables -P INPUT ACCEPT
}

case "$1" in

        start|restart)
        flush
        load
        ;;
        stop)
        flush
        ;;
*)
        echo "usage: start|stop|restart."
;;

esac
exit 0
}

```

I am not sure what is wrong with the firewall that is dropping everything from the PPP.  I am assuming this is what is causing the vpn to be pretty useless atm.

Any and all advice would be great,

Thx

---

### Post by twistedtwig on 2010-07-04
/bump 

Does anyone have an idea why this isn't working please?

Thx

---

### Post by benderisgreat on 2010-07-04
> $iptables -A FORWARD -j LOG --log-level 7 --log-prefix "Dropped by firewall: " This rule is now third in your FORWARD chain after which you append a lot of rules. This should be the last rule in the chain so you can see which packets aren't matched by any rule and are therefore dropped as per policy.
Change this and then check the appropriate log to see which packets are dropped to debug.

---

### Post by twistedtwig on 2010-07-04
Hi,

Even after moving that single rule, or all the dropped by firewall message rules to the bottom I can not ping.

As I am writing this I just thought, what if it is just pings.. turns out I can see shares and mstsc, but not ping anyone.  In debug log I see

```
Jul  4 14:22:23 firewig kernel: [765283.880569] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.19 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=32500 DF PROTO=TCP SPT=6307 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 14:22:25 firewig kernel: [765286.192567] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.17 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=32525 DF PROTO=TCP SPT=6306 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 14:22:29 firewig kernel: [765289.916567] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.19 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=32530 DF PROTO=TCP SPT=6307 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 14:22:37 firewig kernel: [765298.172566] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.18 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=32564 DF PROTO=TCP SPT=6313 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 14:22:40 firewig kernel: [765300.380562] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.18 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=32568 DF PROTO=TCP SPT=6314 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 14:22:40 firewig kernel: [765301.180561] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.18 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=32574 DF PROTO=TCP SPT=6313 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 14:22:41 firewig kernel: [765301.888564] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.83 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=32580 DF PROTO=TCP SPT=6315 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 14:22:43 firewig kernel: [765303.392559] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.18 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=32586 DF PROTO=TCP SPT=6314 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 14:22:44 firewig kernel: [765304.904571] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.83 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=32589 DF PROTO=TCP SPT=6315 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 14:22:44 firewig kernel: [765305.188557] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.18 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=32607 DF PROTO=TCP SPT=6318 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 14:22:47 firewig kernel: [765308.120564] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.18 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=32613 DF PROTO=TCP SPT=6318 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 14:22:49 firewig kernel: [765309.428560] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.18 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=32617 DF PROTO=TCP SPT=6314 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0

```

Will continue to investigate

---

### Post by twistedtwig on 2010-07-04
turns out that didn't make any difference.  I could view shares and mstsc before hand, but can still not ping and get a lot of messages in the syslog.

---

### Post by twistedtwig on 2010-07-04
Here is the rout info when vpn is connected.

C:\Documents and Settings\jonathanh>route print

IPv4 Route Table
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...70 1a 04 46 e4 94 ...... Dell Wireless 1397 WLAN Mini-Card - AVG miniport driver
0x3 ...00 24 e8 e1 2a 05 ...... Realtek RTL8168D(P)/8111D(P) PCI-E Gigabit Ethernet NIC - AVG miniport driver
0x460005 ...00 53 45 00 00 00 ...... WAN (PPP/SLIP) Interface
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0        10.10.0.1      10.10.0.140     21
          0.0.0.0          0.0.0.0    192.168.10.21    192.168.10.21      1
        10.10.0.0    255.255.255.0      10.10.0.140      10.10.0.140     20
      10.10.0.140  255.255.255.255        127.0.0.1        127.0.0.1     20
      10.10.0.141  255.255.255.255        127.0.0.1        127.0.0.1     20
      10.10.0.142  255.255.255.255        127.0.0.1        127.0.0.1     20
   10.255.255.255  255.255.255.255      10.10.0.140      10.10.0.140     20
       94.2.36.95  255.255.255.255        10.10.0.1      10.10.0.140     20
        127.0.0.0        255.0.0.0        127.0.0.1        127.0.0.1      1
    192.168.10.21  255.255.255.255        127.0.0.1        127.0.0.1     50
   192.168.10.255  255.255.255.255    192.168.10.21    192.168.10.21     50
        224.0.0.0        240.0.0.0      10.10.0.140      10.10.0.140     20
        224.0.0.0        240.0.0.0    192.168.10.21    192.168.10.21      1
  255.255.255.255  255.255.255.255      10.10.0.140                2      1
  255.255.255.255  255.255.255.255      10.10.0.140      10.10.0.140      1
  255.255.255.255  255.255.255.255    192.168.10.21    192.168.10.21      1
Default Gateway:     192.168.10.21
===========================================================================
Persistent Routes:
  None

---

### Post by twistedtwig on 2010-07-04
here is ifconfig from vpn server when connected:


jon@firewig:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0c:f1:7c:45:5b
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe7c:455b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11915191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9505612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2058692526 (2.0 GB)  TX bytes:2461784935 (2.4 GB)

eth2      Link encap:Ethernet  HWaddr 00:22:b0:cf:4a:1c
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::222:b0ff:fecf:4a1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10406528 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11768587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2537946843 (2.5 GB)  TX bytes:2039739521 (2.0 GB)
          Interrupt:17 Base address:0xb00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:835630 (835.6 KB)  TX bytes:835630 (835.6 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:192.168.10.1  P-t-P:192.168.10.21  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:8052 (8.0 KB)  TX bytes:108 (108.0 B)

---

### Post by benderisgreat on 2010-07-04
moving the LOG rule won't change what packages are forwared but it will allow you to better see which packets are dropped. You have to look at what the log messages say.
> Jul  4 14:22:23 firewig kernel: [765283.880569] Dropped by firewall: IN=ppp0 OUT=**eth1** SRC=192.168.10.21 DST=209.85.227.19 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=32500 DF PROTO=TCP SPT=6307 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
compare that with your firewall rules:
> INTIF="eth2"
...
$iptables -A FORWARD -i ppp+ -o $INTIF -j ACCEPT
$iptables -A FORWARD -i $INTIF -o ppp+ -j ACCEPT

---

### Post by twistedtwig on 2010-07-04
Oh... sorry misunderstood the purpose.  Thanks

Looking at what you highlighted it would suggest the VPN traffic is going out through the external interface rather than the internal.

That doesn't sound right or good to me.

---

### Post by twistedtwig on 2010-07-04
so here is the tail of /var/log/debug:

```
Jul  4 15:57:09 firewig pppd[3992]: rcvd [LCP TermReq id=0xa "7\002q\37777777712\000<\37777777715t\000\000\000\000"]
Jul  4 15:57:09 firewig pppd[3992]: Script /etc/ppp/ip-down started (pid 4283)
Jul  4 15:57:09 firewig pppd[3992]: sent [LCP TermAck id=0xa]
Jul  4 15:57:09 firewig pptpd[3991]: CTRL: Reaping child PPP[3992]
Jul  4 15:57:09 firewig pppd[3992]: Waiting for 1 child processes...
Jul  4 15:57:09 firewig pppd[3992]:   script /etc/ppp/ip-down, pid 4283
Jul  4 15:57:09 firewig pppd[3992]: Script /etc/ppp/ip-down finished (pid 4283), status = 0x0
Jul  4 15:57:13 firewig pppd[4318]: using channel 38
Jul  4 15:57:13 firewig pppd[4318]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x15176852> <pcomp> <accomp>]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [LCP ConfReq id=0x0 <mru 1400> <magic 0x1b2765db> <pcomp> <accomp> <callback CBCP>]
Jul  4 15:57:13 firewig pppd[4318]: sent [LCP ConfRej id=0x0 <callback CBCP>]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x15176852> <pcomp> <accomp>]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [LCP ConfReq id=0x1 <mru 1400> <magic 0x1b2765db> <pcomp> <accomp>]
Jul  4 15:57:13 firewig pppd[4318]: sent [LCP ConfAck id=0x1 <mru 1400> <magic 0x1b2765db> <pcomp> <accomp>]
Jul  4 15:57:13 firewig pppd[4318]: sent [LCP EchoReq id=0x0 magic=0x15176852]
Jul  4 15:57:13 firewig pppd[4318]: sent [CHAP Challenge id=0x93 <b4353d1434dacf1a6a9e0f699f433a77>, name = "pptpd"]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [LCP Ident id=0x2 magic=0x1b2765db "MSRASV5.20"]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [LCP Ident id=0x3 magic=0x1b2765db "MSRAS-0-FALMER"]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [LCP EchoRep id=0x0 magic=0x1b2765db]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [CHAP Response id=0x93 <fcfabebc2aac6061a635daa3919c4cbc000000000000000060799ce7784068f919a9d249f62a0014ec766beb7101472100>, name = "jon"]
Jul  4 15:57:13 firewig pppd[4318]: sent [CHAP Success id=0x93 "S=1B5736F0A3714D8FF0ABD9335FF48DCD767B0BBB M=Access granted"]
Jul  4 15:57:13 firewig pppd[4318]: sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [CCP ConfReq id=0x4 <mppe +H +M +S +L -D -C>]
Jul  4 15:57:13 firewig pppd[4318]: sent [CCP ConfNak id=0x4 <mppe +H -M +S -L -D -C>]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [IPCP ConfReq id=0x5 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns2 0.0.0.0> <ms-wins 0.0.0.0>]
Jul  4 15:57:13 firewig pppd[4318]: sent [IPCP TermAck id=0x5]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [CCP ConfReq id=0x6 <mppe +H -M +S -L -D -C>]
Jul  4 15:57:13 firewig pppd[4318]: sent [CCP ConfAck id=0x6 <mppe +H -M +S -L -D -C>]
Jul  4 15:57:13 firewig pppd[4318]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.10.1>]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
Jul  4 15:57:13 firewig pppd[4318]: sent [IPCP ConfReq id=0x2 <addr 192.168.10.1>]
Jul  4 15:57:13 firewig pppd[4318]: rcvd [IPCP ConfAck id=0x2 <addr 192.168.10.1>]
Jul  4 15:57:15 firewig pppd[4318]: rcvd [IPCP ConfReq id=0x7 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns2 0.0.0.0> <ms-wins 0.0.0.0>]
Jul  4 15:57:15 firewig pppd[4318]: sent [IPCP ConfRej id=0x7 <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns2 0.0.0.0> <ms-wins 0.0.0.0>]
Jul  4 15:57:15 firewig pppd[4318]: rcvd [IPCP ConfReq id=0x8 <addr 0.0.0.0>]
Jul  4 15:57:15 firewig pppd[4318]: sent [IPCP ConfNak id=0x8 <addr 192.168.10.21>]
Jul  4 15:57:15 firewig pppd[4318]: rcvd [IPCP ConfReq id=0x9 <addr 192.168.10.21>]
Jul  4 15:57:15 firewig pppd[4318]: sent [IPCP ConfAck id=0x9 <addr 192.168.10.21>]
Jul  4 15:57:15 firewig pppd[4318]: Script /etc/ppp/ip-up started (pid 4326)
Jul  4 15:57:15 firewig pppd[4318]: Script /etc/ppp/ip-up finished (pid 4326), status = 0x0
Jul  4 15:57:26 firewig kernel: [770986.860560] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.18 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=14004 DF PROTO=TCP SPT=8128 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 15:57:26 firewig kernel: [770987.100564] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.18 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=14014 DF PROTO=TCP SPT=8129 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 15:57:29 firewig kernel: [770989.780555] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.18 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=14024 DF PROTO=TCP SPT=8128 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 15:57:29 firewig kernel: [770990.084569] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.18 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=14027 DF PROTO=TCP SPT=8129 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 15:57:34 firewig kernel: [770994.524578] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.138 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=14036 DF PROTO=TCP SPT=8130 DPT=80 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  4 15:57:34 firewig kernel: [770994.764555] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.138 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=14044 DF PROTO=TCP SPT=8132 DPT=80 WINDOW=65535 RES=0x00 SYN URGP=0

```

It seems it it trying to go directly out on eth1 (external if) rather than coming into the network on eth2. (I think).

---

### Post by twistedtwig on 2010-07-04
in the pptp.config file there is the local and remote ip settings

i have

localip 192.168.10.1
remoteip 192.168.10.21-25

the localip setting, should this be my gateway / dns / dhcp server?

---

### Post by benderisgreat on 2010-07-04
> Jul 4 14:22:23 firewig kernel: [765283.880569] Dropped by firewall: IN=ppp0 OUT=eth1 SRC=192.168.10.21 DST=209.85.227.19 LEN=52 TOS=0x00 PREC=0x00 TTL=127 ID=32500 DF PROTO=TCP SPT=6307 DPT=443 WINDOW=65535 RES=0x00 SYN URGP=0

what you are seeing here is your pptp client machine trying to initiate a https connection with 209.85.227.19. This is likely because you have configured your remote pptp client to use your ubuntubox/pptp access point as its default gateway or your ubuntu box forces that configuration on your client machine. This causes the client machine to route any traffic not on its local network over your 'firewig' ubuntubox. In this case 209.85.227.19 which is on the internet. This packet comes in over the vpn interface (ppp0) and since the destination is on the internet it has to be routed over the external interface. Which is in this case denied by your firewall. 
If you would just like to use your vpn to connect to the machines behind your firewall, the client machine should not have its default gateway configured as it is.

Currently however you have configured your firewall so that you don't need a vpn to connect to those machines:

> echo "  opening Apache webserver for HoH"
$iptables -A PREROUTING -t nat -i $EXTIF -p tcp --dport 80 -j DNAT --to 192.168.10.96:80
$iptables -A FORWARD -p tcp -m state --state NEW -d 192.168.10.96 --dport 80 -j ACCEPT

These two rules for example make it so that any web traffic directed to your 'firewig' machine's external ip (which may be accessible over the internet) is redirected  to 192.168.10.96 without the need for any vpn.

If you only want to be able to reach the internal machines over your vpn you should configure the vpn as a bridged network so that you are on the same subnet (192.168.10.0/24) and can access the machines by their own ip address. You may already have set this up correctly.
Alternatively you can access them by directing traffic to your ubuntubox' pptp ip address and have DNAT rules to route the traffic like so:

```
$iptables -A PREROUTING -t nat -i ${yourmachinespptpipaddress} -p tcp --dport 80 -j DNAT --to 192.168.10.96:80
```

Your pptp client/server don't have to use the same subnet as the internal machines for this to work.

---

### Post by twistedtwig on 2010-07-04
Hi,

Thanks for all the help.  I am remoting onto my machine at work to do this testing and forgot I had Chrome open in another session which was making those requests.

It would have been nice to be able to connect to the web via the VPN (secure browsing etc).  But the main goal has been to mstsc onto various machines in the network and access file shares.  The webservers are already exposed as much as I require them.

It is just bugging me why I can not ping anything but can do the other bits.

Really grateful for the help and advice, has helped a lot.

---

### Post by benderisgreat on 2010-07-04
you can check if it is in fact the firewall that is blocking the pings by grepping the log:
```
grep "PROTO=ICMP" /var/log/syslog
```

---

### Post by twistedtwig on 2010-07-04
your right:

```
Jul  4 17:10:19 firewig kernel: [775359.595613] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.102 LEN=48 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=19670 SEQ=0
Jul  4 18:42:28 firewig kernel: [780888.570049] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.102 LEN=48 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=19670 SEQ=0
Jul  4 19:24:57 firewig kernel: [783437.554418] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.20 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=36662 SEQ=1
Jul  4 19:24:58 firewig kernel: [783438.562109] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.20 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=36662 SEQ=2
Jul  4 19:24:59 firewig kernel: [783439.570100] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.20 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=36662 SEQ=3
Jul  4 19:25:53 firewig kernel: [783493.794504] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.96 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=47414 SEQ=1
Jul  4 19:25:54 firewig kernel: [783494.802121] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.96 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=47414 SEQ=2
Jul  4 19:25:55 firewig kernel: [783495.810115] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.96 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=47414 SEQ=3
Jul  4 19:25:56 firewig kernel: [783496.818116] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.96 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=47414 SEQ=4
Jul  4 19:25:57 firewig kernel: [783497.826113] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.96 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=47414 SEQ=5
Jul  4 19:25:58 firewig kernel: [783498.834109] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.96 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=47414 SEQ=6
Jul  4 19:25:59 firewig kernel: [783499.842110] Dropped by firewall: IN= OUT=eth2 SRC=192.168.10.1 DST=192.168.10.96 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=ICMP TYPE=8 CODE=0 ID=47414 SEQ=7

```

I ran the following ping from the firewall machine to an internal webserver.

```
PING 192.168.10.96 (192.168.10.96) 56(84) bytes of data.
^C
--- 192.168.10.96 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms

```

Does this mean that the following rule is not working correctly?  I can ping my domain name from outside.

echo "  Allowing packets with ICMP data (pings)"
$iptables -A INPUT -p icmp -j ACCEPT
$iptables -A OUTPUT -p icmp -j ACCEPT

---

### Post by benderisgreat on 2010-07-04
those rules should indeed match the packets in the log entries.
with ```
iptables -vnL OUTPUT
``` you can check if the LOG rule is indeed the last. If your local firewall rules (that is on the machine you are trying to ping from) would deny those packets you would likely see something like:


```
PING 192.168.10.96 (192.168.10.96) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
..
```
if it's not the firewall then 192.168.10.96 is likely just not responding to the pings.

---

### Post by twistedtwig on 2010-07-04
Thank you for your help.  The info you have given showed me how to fix this and I learnt a good number of tips and tricks.  Going to make a note of them so I can have a look next time I forget iptables stuff.

Thx again

---

