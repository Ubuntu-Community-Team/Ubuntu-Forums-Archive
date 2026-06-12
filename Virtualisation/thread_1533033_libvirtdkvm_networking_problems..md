---
title: "libvirtd/kvm networking problems."
date: 2010-07-17
forum: Virtualisation
---

### Post by markp1989 on 2010-07-17
i used the how tos here [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking) to make a bridged interface so i can have virtual machines access the network directly. 

it worked fine, till i reboted the host, and now the virtual machines cannot get internet access. 

this is the interfaces file on the host machine: 
```
mark@torrentslave:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto br0
iface br0 inet dhcp
        bridge_ports eth2
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
mark@torrentslave:~$ 
```

before i reboted i had it set to "bridge_ports eth1" and it was working, after the reboot, when i started having problems i changed it to eth2 as there is no eth1 on this system, but it didnt help

any ideas?

thanks, mark

---

### Post by markp1989 on 2010-07-17
ok, new problem, i have got networking working on the virtual machine, but i cannot connect to the interent using the host.

if i ssh in to the host, i cannot ping google.com or ebay.
```


mark@torrentslave:~$ ping google.com
PING google.com (209.85.229.99) 56(84) bytes of data.
^C
--- google.com ping statistics ---
22 packets transmitted, 0 received, 100% packet loss, time 21015ms

mark@torrentslave:~$
```
dns is working, but i sitll cannot ping hosts.
```
mark@torrentslave:~$ dig google.com

; <<>> DiG 9.7.0-P1 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44720
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             262     IN      A       209.85.229.104
google.com.             262     IN      A       209.85.229.147
google.com.             262     IN      A       209.85.229.99

;; Query time: 10 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Jul 17 18:41:46 2010
;; MSG SIZE  rcvd: 76

mark@torrentslave:~$ 
```


here is ifconfig output:
```

mark@torrentslave:~$ ifconfig 
br0       Link encap:Ethernet  HWaddr 00:01:2e:2c:17:f5  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2eff:fe2c:17f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29994 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3464132 (3.4 MB)  TX bytes:7944953 (7.9 MB)

eth2      Link encap:Ethernet  HWaddr 00:01:2e:2c:17:f5  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2eff:fe2c:17f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3917509 (3.9 MB)  TX bytes:8164875 (8.1 MB)
          Interrupt:22 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:841274 (841.2 KB)  TX bytes:841274 (841.2 KB)

virbr0    Link encap:Ethernet  HWaddr 8a:6a:15:03:f1:23  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::886a:15ff:fe03:f123/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:15181 (15.1 KB)

vnet0     Link encap:Ethernet  HWaddr 2e:52:d7:2c:cc:95  
          inet6 addr: fe80::2c52:d7ff:fe2c:cc95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:11486 (11.4 KB)  TX bytes:22143 (22.1 KB)

mark@torrentslave:~$ 
```

thanks for any pointers, mark

---

### Post by sh1ny on 2010-07-17
Don't put ip on eth2. Make your /etc/network/interfaces look like this :


```
shiny@blackwing:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto br0
iface br0 inet static
        address put.ip.here
        netmask 255.255.255.240
        broadcast put.broadcast.here
        gateway put.gateway.here
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
```

Change eth0 for eth2 in the above.

---

### Post by bodhi.zazen on 2010-07-17
> **sh1ny said:**
> Don't put ip on eth2.


Remove the eth2 stanza. You do not set a static IP or use dhcp with eth2, just set the bridge + bridge_ports eth2

---

