---
title: "isc-dhcp server running, but not giving out IP addresses"
date: 2012-12-30
forum: Server Platforms
---

### Post by Muk on 2012-12-30
I have some trouble getting an IP address out of my dhcp server.
I followed these instructions: [http://ubuntuforums.org/showthread.php?p=12428774#post12428774](http://ubuntuforums.org/showthread.php?p=12428774#post12428774)

i am using ubuntu 12.04 server version

this is my /network/intefaces
```

auto lo
iface lo inet loopback

#facing the inter net
auto eth0
iface eth0 inet static
address 10.0.0.254
network 10.0.0.0
netmask 255.255.255.0
broadcast 10.0.0.255
gateway 10.0.0.2

#secondary network card facing lan
auto eth1
iface eth1 inet static
address 192.168.0.1
network netmask 255.255.255.0
broadcast 192.168.0.255
dns-nameservers 192.168.1.1

```

my /etc/dhcp/dhcpd.conf:

```

ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;
authoriatative;
log-facility local7;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.0.1;
option domain-name-servers 192.168.1.1;
option domain-name "ubuntu.internal";
subnet 192.168.0.0 netmask 255.255.255.0{
range 192.168.0.11 192.168.0.100;
}


```

my /etc/default/isc-dhcp-server
```

INTERFACES="eth1"

```

my /etc/rc.local
```

/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE 

```

I am unsure what I need to do to get my dhcp server to give me IP addresses.

---

### Post by Muk on 2012-12-31
when i check the leases for isc-dhcp-server
tail /var/lib/dhcp/dhcpd.leases
```

#The format of this file is documented in the dhcpd.leases(5) manual page.
#This lease file was written by isc-dhcp-4.1-ESV-R4

server-druid "\000\001\000\001\030q\327L\000\340R\374\342\213";

```

---

### Post by SeijiSensei on 2013-01-01
Open a terminal on the server and run "sudo tail -f /var/log/syslog".  Then start up a client and see what gets logged during the DHCP exchange.  What do you see?

I assume there's nothing else on your network providing DHCP services, right?  Like a router perhaps?

---

### Post by jaimerosario on 2013-01-03
> **Muk said:**
> 
...
my /etc/rc.local
```

/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE 

```

I am unsure what I need to do to get my dhcp server to give me IP addresses.

Try
> iptables -t nat -A POSTROUTING -o eth0 -s 192.168.0.0/24 -j SNAT --to-source 10.0.0.254

---

### Post by Muk on 2013-01-05
> **SeijiSensei said:**
> Open a terminal on the server and run "sudo tail -f /var/log/syslog".  Then start up a client and see what gets logged during the DHCP exchange.  What do you see?

I assume there's nothing else on your network providing DHCP services, right?  Like a router perhaps?

```
# tail -f /var/log/syslogJan  5 15:47:23 SERVERLAN kernel: [ 3334.172416] [UFW BLOCK] IN=eth0 OUT=eth1 MAC=00:e0:52:fc:e2:8b:ec:9a:74:40:3b:1f:08:00 SRC=192.168.0.11 DST=2.22.61.66 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=218 DF PROTO=TCP SPT=57895 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
Jan  5 15:47:23 SERVERLAN kernel: [ 3334.340743] [UFW BLOCK] IN=eth0 OUT=eth1 MAC=00:e0:52:fc:e2:8b:ec:9a:74:40:3b:1f:08:00 SRC=192.168.0.11 DST=8.8.8.8 LEN=67 TOS=0x00 PREC=0x00 TTL=63 ID=219 PROTO=UDP SPT=64190 DPT=53 LEN=47 
Jan  5 15:47:23 SERVERLAN kernel: [ 3334.561361] [UFW BLOCK] IN=eth0 OUT=eth1 MAC=00:e0:52:fc:e2:8b:ec:9a:74:40:3b:1f:08:00 SRC=192.168.0.11 DST=103.7.30.142 LEN=115 TOS=0x00 PREC=0x00 TTL=63 ID=223 PROTO=UDP SPT=4010 DPT=8000 LEN=95 
Jan  5 15:47:36 SERVERLAN kernel: [ 3347.789827] [UFW BLOCK] IN=eth0 OUT=eth1 MAC=00:e0:52:fc:e2:8b:ec:9a:74:40:3b:1f:08:00 SRC=192.168.0.11 DST=112.90.84.117 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=336 DF PROTO=TCP SPT=57903 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
Jan  5 15:47:56 SERVERLAN kernel: [ 3367.395662] [UFW BLOCK] IN=eth0 OUT=eth1 MAC=00:e0:52:fc:e2:8b:ec:9a:74:40:3b:1f:08:00 SRC=192.168.0.11 DST=8.8.8.8 LEN=59 TOS=0x00 PREC=0x00 TTL=63 ID=473 PROTO=UDP SPT=57993 DPT=53 LEN=39 
Jan  5 15:48:12 SERVERLAN kernel: [ 3383.852698] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:22:b0:f2:52:fb:08:00 SRC=10.0.0.2 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=31047 PROTO=2 
Jan  5 15:48:17 SERVERLAN kernel: [ 3388.240168] [UFW BLOCK] IN=eth0 OUT=eth1 MAC=00:e0:52:fc:e2:8b:ec:9a:74:40:3b:1f:08:00 SRC=192.168.0.11 DST=8.8.8.8 LEN=63 TOS=0x00 PREC=0x00 TTL=63 ID=567 PROTO=UDP SPT=54210 DPT=53 LEN=43 
Jan  5 15:48:36 SERVERLAN kernel: [ 3407.387656] [UFW BLOCK] IN=eth0 OUT=eth1 MAC=00:e0:52:fc:e2:8b:ec:9a:74:40:3b:1f:08:00 SRC=192.168.0.11 DST=8.8.8.8 LEN=71 TOS=0x00 PREC=0x00 TTL=63 ID=634 PROTO=UDP SPT=58980 DPT=53 LEN=51 
Jan  5 15:48:40 SERVERLAN kernel: [ 3410.983659] [UFW BLOCK] IN=eth1 OUT= MAC=01:00:5e:00:00:01:00:12:bf:87:d2:b1:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=1920 PROTO=2 
Jan  5 15:48:56 SERVERLAN kernel: [ 3427.958196] [UFW BLOCK] IN=eth0 OUT=eth1 MAC=00:e0:52:fc:e2:8b:ec:9a:74:40:3b:1f:08:00 SRC=192.168.0.11 DST=119.188.23.47 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=705 DF PROTO=TCP SPT=57951 DPT=8000 WINDOW=8192 RES=0x00 SYN URGP=0 
Jan  5 15:49:17 SERVERLAN dhcpd: DHCPINFORM from 192.168.0.11 via eth0
Jan  5 15:49:17 SERVERLAN dhcpd: DHCPACK to 192.168.0.11 (ec:9a:74:40:3b:1f) via eth0


```

i think i got an ip address now, however my server isn't forwarding my laptop into the interweb. tried pinging google and didn't get a forward.

nvm i had ```
ufw enable
```

just disabled the firewall and was able to get internet :D thx

---

### Post by Doug S on 2013-01-05
Edit: I was writting this reply during the above post showing problem solved.
 
It looks as though UFW is blocking your desired traffic.
I do not use UFW, I use iptables directly.
If you post the output from```
sudo iptables -v -x -n -L
```and```
sudo iptables -t nat -v -x -n -L
```or just```
sudo iptables-save -c
```we should be able to figure out the issue with the iptables rule set (but I wouldn't know how to map the problem back to the UFW stuff that creates the rules).

---

