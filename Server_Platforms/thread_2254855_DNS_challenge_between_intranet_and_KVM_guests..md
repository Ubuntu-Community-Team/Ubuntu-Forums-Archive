---
title: "DNS challenge between intranet and KVM guests."
date: 2014-11-30
forum: Server Platforms
---

### Post by MAFoElffen on 2014-11-30
Okay, this is just weird.

I'm intending to run some of my intranet services from KVM guests, to downsize my iron.

I just got two of my servers reconfigured (moved their LVM roots from smaller MBR disks to larger 2TB GPT disks). These 2 servers are my Master DNS and Slave DNS. They also are ssh server and KVM servers.

I have a virt bridge installed to treat the KMS guests as being on the Host NID. I have that bridge pointed to separate NICs, instead of sharing the server's main NICs, w/ static IP's as being on the intranet NID and dns-nameservers pointing to my intranet DNS master, slave and open-dns (in that order).

From the Host network,  I can ping to the Host via servername or IP. I can ping the KMS guest.

From KMS guest, I can ping and have FQNS DNS to the internet, but not to my Host NID. I cannot get to the Host network via severnames. I cannot get the guest to access my own host network. 

Like I said, just weird.

---

### Post by newbie-user on 2014-12-01
Hi, I got a little confused reading through your post. Did you mean that you assigned the guest a static ip address and set its nameservers to your DNS?

---

### Post by MAFoElffen on 2014-12-01
When I get home tonight, I'll get on that server and post the associated config files.

For now, basically. I'll just talk about a single server to simplify things. As, when I get one working right, the other will follow suit.

I had my guest servers as islands within the chain. The guests were previously set as static on the KVM's default 192.168.122.0/24 network. They could talk with each other, and the outside world, but where not on the same network as my host. Within the last few days, I installed bridge-utils and set the host's br0 and referred it to eth3. Why eth3, instead of eth1? Moot point, as for some reason, this host comes up starting with eth2 and up from there... and does not recognize anything as eth0 and eth1. I know that the instructions for br0 (bridge utils) said to set br0 to eth0, but I figured if I set it to my secondary NIC, it would be on the same network and increase the bandwidth for any virtual hosts.

On the Host Server (that is running KVM), it has local Bind9, KVM, SSH server services, running. I installed bridge-utils on the host, configured with static IP's on my local 192.168.2.0/24 network. I have static eth2 set to my network. I have br0 set as static on my local network, and pointed it to eth3. 

On the KVM guess server, I pointed to the same host network. The guests seem to see out, but but do not see anything else on my local network. My local network see's them by IP, but not by fully qualified name. So my local DNS does not see them. 

The other hard host mentioned, is a DNS slave of this host. Intent is to set up kerberos as a kvm guest, but it needs to be connected in the same network as the host first. No need to install that, until that guest server has connectivity first.

This is what I read as what to do. Logically, I have something wrong. Do I have two networks with the same NIDs that are conflicting with each other... instead of one network segment? By adding a "bridge" instead of a virtual "switch"... did I create two conflicting broadcast domains? I know that is what it says to do, but something is just not working as planned. I'm missing something in my config somewhere.

---

### Post by MAFoElffen on 2014-12-02
Host:
On login
```
IP address for eth2:    192.168.2.15IP address for br0:     192.168.2.17
IP address for docker0: 172.17.42.1
IP address for virbr0:  192.168.122.1

```
Stats:
```
mafoelffen@snoopy:~$ ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:1c:23:da:25:d8  
          inet addr:192.168.2.17  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:feda:25d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:96457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28603956 (28.6 MB)  TX bytes:900 (900.0 B)


docker0   Link encap:Ethernet  HWaddr 56:84:7a:fe:97:99  
          inet addr:172.17.42.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth2      Link encap:Ethernet  HWaddr 00:1c:23:da:25:d6  
          inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:feda:25d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8082308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8023600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1227786106 (1.2 GB)  TX bytes:1960853299 (1.9 GB)


eth3      Link encap:Ethernet  HWaddr 00:1c:23:da:25:d8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2046 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34784550 (34.7 MB)  TX bytes:186070 (186.0 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:53104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5488039 (5.4 MB)  TX bytes:5488039 (5.4 MB)


virbr0    Link encap:Ethernet  HWaddr fe:01:e8:f4:46:e3  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vnet0     Link encap:Ethernet  HWaddr fe:54:00:4c:3f:ea  
          inet6 addr: fe80::fc54:ff:fe4c:3fea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:173984 (173.9 KB)  TX bytes:27004705 (27.0 MB)

mafoelffen@snoopy:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# snoopy is eth2 & eth 3
# The primary network interface
auto eth2
#iface eth2 inet dhcp
iface eth2 inet static
    address 192.168.2.15
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.1
    # dns-* options are implemented by the resolvconf package, if installed
    #dns-nameservers 205.171.3.66 205.141.202.166 8.8.8.8
    dns-nameservers 205.171.3.66 205.141.202.166. 8.8.8.8 208.67.222.222 198.168.2.16
        dns-search ferreiraent.com


# secondary backup
#auto eth3
#iface eth3 inet dhcp
auto br0
iface br0 inet static
    address 192.168.2.17
    broadcast 192.168.2.255
    netmask 255.255.255.0
    gateway 192.168.2.1
    dns-nameservers 8.8.8.8 8.8.4.4 192.168.2.16
    metric 1
    bridge_ports eth3
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off

mafoelffen@snoopy:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 eth2
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 br0
172.17.0.0      0.0.0.0         255.255.0.0     U         0 0          0 docker0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 br0
192.168.122.0   0.0.0.0         255.255.255.0   U         0 0          0 virbr0



```

Guest:

On login: IP address for eth0: 192.168.2.20
```

mafoelffen@max:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# This guest is bridged to the outside host network
# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
    address 192.168.2.20
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.1
    dns-search ferreiraent.com
    # Just the two Local DNS Servers
    dns-nameservers 192.168.2.15 192.168.2.16 8.8.8.8 8.8.4.4

mafoelffen@max:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 52:54:00:4c:3f:ea  
          inet addr:192.168.2.20  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::5054:ff:fe4c:3fea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47893 (47.8 KB)  TX bytes:20094 (20.0 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mafoelffen@max:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0

```

---

### Post by nerdtron on 2014-12-06
Do you use the two network interfaces of the HOST?

I would do this and this should work:
HOST:
eth2 is connected on your LAN 192.168.2.0/24 network, eth3 is not use (or if you use it, be sure it is not on 192.168.2.0/24 netowrk)
configure eth2 to be bridge br0 and set static IP address:
```

####loopback here####

####eth2####
auto eth2
iface eth2 inet manual

####bridging eth2####
auto br0
iface br0 inet static
    address 192.168.2.17
    broadcast 192.168.2.255
    netmask 255.255.255.0
    gateway 192.168.2.1
    dns-nameservers 8.8.8.8 8.8.4.4 192.168.2.16
    metric 1
    bridge_ports eth2
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off

###eth3 config here if any ###

```

To confirm that the bridge is working on the host:
```
brctl show
```

Now a sample config on the GUESTS, they all should be on the same IP block 192.168.2.0/24

Also, check your Virtual Machine settings for the Guests. They should be using the bridge mode, and interface **br0**. I think you should manually enter this on the virtual machine settings.

---

### Post by MAFoElffen on 2014-12-10
No- That last suggested failed. Lost all connect with the network altogether with that- at the host server, so all guests went down with it.

---

### Post by MAFoElffen on 2014-12-11
I think my problem is somewhere in my open ldap configs. I checked for orphaned processes and found these:
```

mafoelffen@snoopy:~$ ps -elf | head -1; ps -elf | awk '{if ($5 == 1 && $3 != "root") {print $0}}' | head
F S UID        PID  PPID  C PRI  NI ADDR SZ WCHAN  STIME TTY          TIME CMD
5 S message+   743     1  0  80   0 -  9810 ep_pol 08:02 ?        00:00:00 dbus-daemon --system --fork
5 S syslog     745     1  0  80   0 - 63961 poll_s 08:02 ?        00:00:00 rsyslogd
4 S dhcpd     1412     1  0  80   0 -  4877 poll_s 08:02 ?        00:00:00 dhcpd -user dhcpd -group dhcpd -f -q -4 -pf /run/dhcp-server/dhcpd.pid -cf /etc/dhcp/dhcpd.conf
1 S daemon    1454     1  0  80   0 -  4785 hrtime 08:02 ?        00:00:00 atd
5 S bind      1461     1  0  80   0 - 137953 sigsus 08:02 ?       00:00:00 /usr/sbin/named -u bind -4
1 S openldap  1536     1  0  80   0 - 64937 futex_ 08:02 ?        00:00:00 /usr/sbin/slapd -h ldap:/// ldapi:/// -g openldap -u openldap -F /etc/ldap/slapd.d
5 S libvirt+  1761     1  0  80   0 -  7052 poll_s 08:02 ?        00:00:00 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf
5 S ntp       1921     1  0  80   0 -  7861 poll_s 08:02 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 111:118

```
Not sure exactly what that means yet, but gives me a direction to start from, right? I'm suspecting that service, as I can remeber that I was having a challenge debug syntax error with that when I set that up... so I never was able to confirm that I was right with those. I think I need to go back through that service...

---

### Post by MAFoElffen on 2014-12-13
Still NOT working "completely."

Final /etc/network/interfaces ended up like this:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# snoopy is eth2 & eth 3

# The primary network interface
auto eth2
iface eth2 inet static
    address 192.168.2.15
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.1
    dns-search ferreiraent.com

# The secondary interface
auto br0
iface br0 inet static
    address 192.168.2.17
    netmask 255.255.255.0
    network 192.168.2.0
    gateway 192.168.2.1
    broadcast 192.168.2.255
    metric 1
    bridge_ports eth3
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off

```
Moved dns-namservers to the /etc/resolvconf/resolv.conf.d/head:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 192.168.2.15
nameserver 192.168.2.16

```
Disabled the netfilter in the bridge to use the iptables of the host (in /etc/sysctl.conf) to allow all traffic to be forwarded across the bridge:
```

net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0

```
Then added a rule to the host's iptables script:
```

sudo /sbin/iptables -I FORWARD -m physdev --physdev-is-bridged -j ACCEPT

```
Then tested it from the guest:
```

mafoelffen@max:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:4c:3f:ea brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.20/24 brd 192.168.2.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::5054:ff:fe4c:3fea/64 scope link 
       valid_lft forever preferred_lft forever


mafoelffen@max:~$ ip route
default via 192.168.2.1 dev eth0 
192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.20 

mafoelffen@max:~$ dig snoopy.ferreiraent.com


; <<>> DiG 9.9.5-3ubuntu0.1-Ubuntu <<>> snoopy.ferreiraent.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 6458
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;snoopy.ferreiraent.com.        IN    A


;; AUTHORITY SECTION:
ferreiraent.com.    604800    IN    SOA    ferreiraent.com. root.ferreiraent.com. 2014071100 604800 86400 2419200 604800


;; Query time: 1 msec
;; SERVER: 192.168.2.15#53(192.168.2.15)
;; WHEN: Fri Dec 12 21:09:46 PST 2014
;; MSG SIZE  rcvd: 92


mafoelffen@max:~$ ping -c 3 snoopy.ferreiraent.com
PING snoopy.ferreiraent.com.ferreiraent.com (192.168.2.15) 56(84) bytes of data.
64 bytes from 192.168.2.15: icmp_seq=1 ttl=64 time=0.201 ms
64 bytes from 192.168.2.15: icmp_seq=2 ttl=64 time=0.243 ms
64 bytes from 192.168.2.15: icmp_seq=3 ttl=64 time=0.279 ms


--- snoopy.ferreiraent.com.ferreiraent.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.201/0.241/0.279/0.031 ms



```
Tested it from the Host:
```

mafoelffen@snoopy:~$ brctl show
bridge name  bridge id                    STP enabled  interfaces
br0                8000.001c23da25d8  no                    eth3
docker0         8000.56847afe9799   no                    vnet0
virbr0            8000.000000000000  yes

mafoelffen@snoopy:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:1c:23:da:25:d6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.15/24 brd 192.168.2.255 scope global eth2
       valid_lft forever preferred_lft forever
    inet6 fe80::21c:23ff:feda:25d6/64 scope link 
       valid_lft forever preferred_lft forever
3: eth3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 00:1c:23:da:25:d8 brd ff:ff:ff:ff:ff:ff
4: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 56:84:7a:fe:97:99 brd ff:ff:ff:ff:ff:ff
    inet 172.17.42.1/16 scope global docker0
       valid_lft forever preferred_lft forever
5: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 00:1c:23:da:25:d8 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.17/24 brd 192.168.2.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::21c:23ff:feda:25d8/64 scope link 
       valid_lft forever preferred_lft forever
6: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 2e:5b:3b:ef:e5:2c brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
7: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500
    link/ether fe:54:00:4c:3f:ea brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fe4c:3fea/64 scope link 
       valid_lft forever preferred_lft forever

mafoelffen@snoopy:~$ ip route
default via 192.168.2.1 dev eth2 
default via 192.168.2.1 dev br0  metric 1 
172.17.0.0/16 dev docker0  proto kernel  scope link  src 172.17.42.1 
192.168.2.0/24 dev eth2  proto kernel  scope link  src 192.168.2.15 
192.168.2.0/24 dev br0  proto kernel  scope link  src 192.168.2.17 
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1 

mafoelffen@snoopy:~$ ping -c 3 192.168.2.20
PING 192.168.2.20 (192.168.2.20) 56(84) bytes of data.
64 bytes from 192.168.2.20: icmp_seq=1 ttl=64 time=0.396 ms
64 bytes from 192.168.2.20: icmp_seq=2 ttl=64 time=0.321 ms
64 bytes from 192.168.2.20: icmp_seq=3 ttl=64 time=0.322 ms


--- 192.168.2.20 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.321/0.346/0.396/0.038 ms

mafoelffen@snoopy:~$ man nslookup
mafoelffen@snoopy:~$ nslookup max.ferreiraent.com snoopy.ferreiraent.com
Server:        snoopy.ferreiraent.com
Address:    192.168.2.15#53

[COLOR=#ff0000]** server can't find max.ferreiraent.com: NXDOMAIN[/COLOR]




mafoelffen@snoopy:~$ ping -c 3 max.ferreiraent.com
[COLOR=#ff0000]ping: unknown host max.ferreiraent.com[/COLOR]

```
 I don't know... I get from my net to all hard boxes. From KVM guests to all. But no DNS from the Local net for the KVM Guests. Here's my query log on the Host. The 127.0.01 <> ubuntu was an upgrade from the KVM guest server max.ferreiraent.com:
```

mafoelffen@snoopy:~$ cat /var/log/query.log | more
client 192.168.2.16#59370 (2.168.192.in-addr.arpa): query: 2.168.192.in-addr.arpa IN SOA -E (192.168.2.15)
client 192.168.2.16#35151 (2.168.192.in-addr.arpa): query: 2.168.192.in-addr.arpa IN AXFR -T (192.168.2.15)
client 192.168.2.16#62766 (ferreiraent.com): query: ferreiraent.com IN SOA -E (192.168.2.15)
client 192.168.2.16#57568 (ferreiraent.com): query: ferreiraent.com IN AXFR -T (192.168.2.15)
client 192.168.2.20#40874 (ntp.ubuntu.com): query: ntp.ubuntu.com IN A + (192.168.2.15)
client 192.168.2.20#40874 (ntp.ubuntu.com): query: ntp.ubuntu.com IN AAAA + (192.168.2.15)
client 192.168.2.20#46769 (changelogs.ubuntu.com): query: changelogs.ubuntu.com IN AAAA + (192.168.2.15)
client 192.168.2.20#46769 (changelogs.ubuntu.com): query: changelogs.ubuntu.com IN A + (192.168.2.15)
client 192.168.2.20#36967 (ntp.ubuntu.com): query: ntp.ubuntu.com IN A + (192.168.2.15)
client 192.168.2.20#36967 (ntp.ubuntu.com): query: ntp.ubuntu.com IN AAAA + (192.168.2.15)
client 192.168.2.20#32979 (snoopy.ferreiraent.com): query: snoopy.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#34069 (snoopy.ferreiraent.com.ferreiraent.com): query: snoopy.ferreiraent.com.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#48848 (snoopy.ferreiraent.com): query: snoopy.ferreiraent.com IN A +E (192.168.2.15)
client 192.168.2.20#35845 (16.2.168.192.in-addr.arpa): query: 16.2.168.192.in-addr.arpa IN PTR + (192.168.2.15)
client 192.168.2.20#48462 (snoopy.ferreiraent.com): query: snoopy.ferreiraent.com IN A +E (192.168.2.15)
client 192.168.2.20#34581 (lassie.ferreiraent.com): query: lassie.ferreiraent.com IN A +E (192.168.2.15)
client 192.168.2.20#47534 (max.ferreiraent.com): query: max.ferreiraent.com IN A +E (192.168.2.15)
client 192.168.2.20#50709 (snoopy.ferreiraent.com): query: snoopy.ferreiraent.com IN A +E (192.168.2.15)
client 192.168.2.20#58859 (snoopy.ferreiraent.comm): query: snoopy.ferreiraent.comm IN A + (192.168.2.15)
client 192.168.2.20#44162 (snoopy.ferreiraent.comm.ferreiraent.com): query: snoopy.ferreiraent.comm.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#52796 (snoopy.ferreiraent.com): query: snoopy.ferreiraent.com IN A +E (192.168.2.15)
client 192.168.2.20#34036 (6.2.168.192.in-addr.arpa): query: 6.2.168.192.in-addr.arpa IN PTR + (192.168.2.15)
client 192.168.2.20#43176 (ferreiraent.com): query: ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#54740 (ferreiraent.com): query: ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#54496 (ferreiraent.com): query: ferreiraent.com IN A +E (192.168.2.15)
client 192.168.2.20#32881 (snoopy.ferreiraent.com): query: snoopy.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#52703 (snoopy.ferreiraent.com.ferreiraent.com): query: snoopy.ferreiraent.com.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.16#63628 (ferreiraent.com): query: ferreiraent.com IN SOA -E (192.168.2.15)
client 192.168.2.16#45762 (ferreiraent.com): query: ferreiraent.com IN AXFR -T (192.168.2.15)
client 192.168.2.16#20851 (2.168.192.in-addr.arpa): query: 2.168.192.in-addr.arpa IN SOA -E (192.168.2.15)
client 192.168.2.16#41733 (2.168.192.in-addr.arpa): query: 2.168.192.in-addr.arpa IN AXFR -T (192.168.2.15)
client 192.168.2.16#3645 (ferreiraent.com): query: ferreiraent.com IN SOA -E (192.168.2.15)
client 192.168.2.16#39013 (ferreiraent.com): query: ferreiraent.com IN AXFR -T (192.168.2.15)
client 192.168.2.16#44001 (2.168.192.in-addr.arpa): query: 2.168.192.in-addr.arpa IN SOA -E (192.168.2.15)
client 192.168.2.16#41023 (2.168.192.in-addr.arpa): query: 2.168.192.in-addr.arpa IN AXFR -T (192.168.2.15)
client 127.0.0.1#49684 (6.2.168.192.in-addr.arpa): query: 6.2.168.192.in-addr.arpa IN PTR + (127.0.0.1)
client 127.0.0.1#40226 (0.ubuntu.pool.ntp.org): query: 0.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#40226 (0.ubuntu.pool.ntp.org): query: 0.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#40479 (1.ubuntu.pool.ntp.org): query: 1.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#40479 (1.ubuntu.pool.ntp.org): query: 1.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#42999 (2.ubuntu.pool.ntp.org): query: 2.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#42999 (2.ubuntu.pool.ntp.org): query: 2.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#53879 (3.ubuntu.pool.ntp.org): query: 3.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#53879 (3.ubuntu.pool.ntp.org): query: 3.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#34465 (ntp.ubuntu.com): query: ntp.ubuntu.com IN A + (127.0.0.1)
client 127.0.0.1#34465 (ntp.ubuntu.com): query: ntp.ubuntu.com IN AAAA + (127.0.0.1)
client 127.0.0.1#45354 (0.ubuntu.pool.ntp.org): query: 0.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#45354 (0.ubuntu.pool.ntp.org): query: 0.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#44503 (1.ubuntu.pool.ntp.org): query: 1.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#44503 (1.ubuntu.pool.ntp.org): query: 1.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#51489 (2.ubuntu.pool.ntp.org): query: 2.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#51489 (2.ubuntu.pool.ntp.org): query: 2.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#47409 (3.ubuntu.pool.ntp.org): query: 3.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#47409 (3.ubuntu.pool.ntp.org): query: 3.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#55435 (ntp.ubuntu.com): query: ntp.ubuntu.com IN A + (127.0.0.1)
client 127.0.0.1#55435 (ntp.ubuntu.com): query: ntp.ubuntu.com IN AAAA + (127.0.0.1)
client 127.0.0.1#35240 (0.ubuntu.pool.ntp.org): query: 0.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#35240 (0.ubuntu.pool.ntp.org): query: 0.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#52395 (1.ubuntu.pool.ntp.org): query: 1.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#52395 (1.ubuntu.pool.ntp.org): query: 1.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#53189 (2.ubuntu.pool.ntp.org): query: 2.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#53189 (2.ubuntu.pool.ntp.org): query: 2.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#42053 (3.ubuntu.pool.ntp.org): query: 3.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#42053 (3.ubuntu.pool.ntp.org): query: 3.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#45398 (ntp.ubuntu.com): query: ntp.ubuntu.com IN A + (127.0.0.1)
client 127.0.0.1#45398 (ntp.ubuntu.com): query: ntp.ubuntu.com IN AAAA + (127.0.0.1)
client 127.0.0.1#40216 (0.ubuntu.pool.ntp.org): query: 0.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#40216 (0.ubuntu.pool.ntp.org): query: 0.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#46022 (1.ubuntu.pool.ntp.org): query: 1.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#46022 (1.ubuntu.pool.ntp.org): query: 1.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#57283 (2.ubuntu.pool.ntp.org): query: 2.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#57283 (2.ubuntu.pool.ntp.org): query: 2.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#52236 (3.ubuntu.pool.ntp.org): query: 3.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#52236 (3.ubuntu.pool.ntp.org): query: 3.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#59540 (ntp.ubuntu.com): query: ntp.ubuntu.com IN A + (127.0.0.1)
client 127.0.0.1#59540 (ntp.ubuntu.com): query: ntp.ubuntu.com IN AAAA + (127.0.0.1)
client 127.0.0.1#33097 (0.ubuntu.pool.ntp.org): query: 0.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#33097 (0.ubuntu.pool.ntp.org): query: 0.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#33530 (1.ubuntu.pool.ntp.org): query: 1.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#33530 (1.ubuntu.pool.ntp.org): query: 1.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#32986 (2.ubuntu.pool.ntp.org): query: 2.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#32986 (2.ubuntu.pool.ntp.org): query: 2.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#58135 (3.ubuntu.pool.ntp.org): query: 3.ubuntu.pool.ntp.org IN A + (127.0.0.1)
client 127.0.0.1#58135 (3.ubuntu.pool.ntp.org): query: 3.ubuntu.pool.ntp.org IN AAAA + (127.0.0.1)
client 127.0.0.1#60154 (ntp.ubuntu.com): query: ntp.ubuntu.com IN AAAA + (127.0.0.1)
client 127.0.0.1#60154 (ntp.ubuntu.com): query: ntp.ubuntu.com IN A + (127.0.0.1)
client 127.0.0.1#44583 (lassie.ferreiraent.com): query: lassie.ferreiraent.com IN A +E (127.0.0.1)
client 127.0.0.1#58074 (lassie.ferreiraent.com): query: lassie.ferreiraent.com IN A +E (127.0.0.1)
client 192.168.2.16#23117 (ferreiraent.com): query: ferreiraent.com IN SOA -E (192.168.2.15)
client 192.168.2.16#50143 (ferreiraent.com): query: ferreiraent.com IN AXFR -T (192.168.2.15)
client 192.168.2.16#64107 (2.168.192.in-addr.arpa): query: 2.168.192.in-addr.arpa IN SOA -E (192.168.2.15)
client 192.168.2.16#33674 (2.168.192.in-addr.arpa): query: 2.168.192.in-addr.arpa IN AXFR -T (192.168.2.15)
client 192.168.2.20#39114 (ntp.ubuntu.com): query: ntp.ubuntu.com IN A + (192.168.2.15)
client 192.168.2.20#39114 (ntp.ubuntu.com): query: ntp.ubuntu.com IN AAAA + (192.168.2.15)
client 192.168.2.20#45790 (ntp.ubuntu.com): query: ntp.ubuntu.com IN A + (192.168.2.15)
client 192.168.2.20#45790 (ntp.ubuntu.com): query: ntp.ubuntu.com IN AAAA + (192.168.2.15)
client 192.168.2.20#53158 (www.google.com): query: www.google.com IN A + (192.168.2.15)
client 192.168.2.20#35121 (103.28.125.74.in-addr.arpa): query: 103.28.125.74.in-addr.arpa IN PTR + (192.168.2.15)
client 192.168.2.20#48790 (snoopy.ferreiraent.com): query: snoopy.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#52404 (snoopy.ferreiraent.com.ferreiraent.com): query: snoopy.ferreiraent.com.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#49666 (15.2.168.192.in-addr.arpa): query: 15.2.168.192.in-addr.arpa IN PTR + (192.168.2.15)
client 192.168.2.20#51111 (security.ubuntu.com): query: security.ubuntu.com IN A + (192.168.2.15)
client 192.168.2.20#51111 (security.ubuntu.com): query: security.ubuntu.com IN AAAA + (192.168.2.15)
client 192.168.2.20#53633 (us.archive.ubuntu.com): query: us.archive.ubuntu.com IN AAAA + (192.168.2.15)
client 192.168.2.20#53633 (us.archive.ubuntu.com): query: us.archive.ubuntu.com IN A + (192.168.2.15)
client 192.168.2.20#44728 (us.archive.ubuntu.com): query: us.archive.ubuntu.com IN A + (192.168.2.15)
client 192.168.2.20#44728 (us.archive.ubuntu.com): query: us.archive.ubuntu.com IN AAAA + (192.168.2.15)
client 192.168.2.20#42213 (snoopy.ferreiraent.com): query: snoopy.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#49941 (snoopy.ferreiraent.com.ferreiraent.com): query: snoopy.ferreiraent.com.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#38742 (15.2.168.192.in-addr.arpa): query: 15.2.168.192.in-addr.arpa IN PTR + (192.168.2.15)
client 192.168.2.15#40190 (max.ferreiraent.com): query: max.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#39521 (6.2.168.192.in-addr.arpa): query: 6.2.168.192.in-addr.arpa IN PTR + (192.168.2.15)
client 192.168.2.20#50780 (changelogs.ubuntu.com): query: changelogs.ubuntu.com IN A + (192.168.2.15)
client 192.168.2.20#50780 (changelogs.ubuntu.com): query: changelogs.ubuntu.com IN AAAA + (192.168.2.15)
client 192.168.2.20#40265 (snoopy.ferreiraent.com): query: snoopy.ferreiraent.com IN A +E (192.168.2.15)
client 192.168.2.20#42413 (snoopy.ferreiraent.com): query: snoopy.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#36712 (snoopy.ferreiraent.com.ferreiraent.com): query: snoopy.ferreiraent.com.ferreiraent.com IN A + (192.168.2.15)
client 192.168.2.20#33451 (15.2.168.192.in-addr.arpa): query: 15.2.168.192.in-addr.arpa IN PTR + (192.168.2.15)

```



*** Any ideas anyone? ***

---

### Post by MAFoElffen on 2014-12-14
Solved. Found the problem. There was an extraneous character in my domain zone db file for Bind9. It must have taken Bind down when I added the info in for that new (Guest) Server. Now the DNS is flowing in to that KVM guest server and more...

Thanks for the ideas. It's been bugging me with it not working.

---

