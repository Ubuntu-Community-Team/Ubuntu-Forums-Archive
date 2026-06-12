---
title: "OpenVpn: Can Connect to Server But get no Internet Connection"
date: 2016-11-27
forum: Server Platforms
---

### Post by casey8 on 2016-11-27
Last week I set up an Ubuntu 10.04 server at home in order to set up OpenVpn, I followed a guide and everything was going fine. I got it set up and my clients can connect, but after I connect to any websites. I can ping my server from the client, but the server cannot ping the client. The client also cannot ping google (8.8.8.8) when connected. Here are my settings..


server.conf
```
port 1194
proto udp
dev tun
sndbuf 0
rcvbuf 0
ca ca.crt
cert server.crt
key server.key
dh dh.pem
tls-auth ta.key 0
topology subnet
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
cipher AES-128-CBC
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
crl-verify crl.pem

```


client.ovpn
```

client
dev tun
proto udp
sndbuf 0
rcvbuf 0
remote SERVER IP 1194
resolv-retry infinite
nobind
persist-key
persist-tun
remote-cert-tls server
cipher AES-128-CBC
comp-lzo
setenv opt block-outside-dns
key-direction 1
verb 3

```


firewall settings
```

iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -j SNAT --to SERVER IP

```




 I believe that I have some sort of routing problem as when I run "route -n" I get
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 enp2s0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 enp2s0
10.8.0.0        0.0.0.0         255.255.255.0   U     0      0        0 tun0

```


I get this both when the client is connected and when it's disconnected.


I also have ipv4 forwarded and the 1194 forwarded.


I'm fairly new to this and I've been troubleshooting for days with no avail, any help would be greatly appreciated.

---

### Post by wildmanne39 on 2016-11-27
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2016-11-28
Did you allow ipv4 forward in sysctl.conf?
```
cat /etc/sysctl.conf | grep forward
```

Does that show the line as commented or not?

If you had allowed that, try with this masquerade rule on the server (I usually use that although your snat rule should work too):
```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
```

Also, you are aware that iptables rules set up like that on the command line do not survive a reboot unless you make them permanent in another way, right? So if you rebooted your iptables rule would be lost and the server will not forward the traffic correctly.

PS. And you might need few more iptables rules on the server. Show us this:
```
sudo iptables -L -n -v
```

---

### Post by bearlake on 2016-11-28
10.04 ??

Would move to 14.04 or 16.04.

10.04 has been dead for some time now and are not getting updates.

---

### Post by casey8 on 2016-11-28
> **bearlake said:**
> 10.04 ??

Would move to 14.04 or 16.04.

10.04 has been dead for some time now and are not getting updates.

You're right, my mistake, its 16.04.1

> **darkod said:**
> Did you allow ipv4 forward in sysctl.conf?
```
cat /etc/sysctl.conf | grep forward
```

Does that show the line as commented or not?

If you had allowed that, try with this masquerade rule on the server (I usually use that although your snat rule should work too):
```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
```

Also, you are aware that iptables rules set up like that on the command line do not survive a reboot unless you make them permanent in another way, right? So if you rebooted your iptables rule would be lost and the server will not forward the traffic correctly.

PS. And you might need few more iptables rules on the server. Show us this:
```
sudo iptables -L -n -v
```

My ipv4 line is uncommented, my ipv6 is not but I still get no internet connection whether or not its commented.

Yes, I know that it doesnt save, what I listed is what is in my /etc/rc.local
I tried using the command that you posted, but I couldn't even connect to the server from my client after that.

(I do think it is a routing problem) Here is my [COLOR=#000000][FONT=&amp]sudo iptables -L -n -v
[/FONT][/COLOR]```
Chain INPUT (policy DROP 362 packets, 33891 bytes) pkts bytes target     prot opt in     out     source               destination
41758   15M ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
41758   15M ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
  362 33891 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
  362 33891 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
  362 33891 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0
  362 33891 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain FORWARD (policy ACCEPT 62 packets, 3152 bytes)
 pkts bytes target     prot opt in     out     source               destination
61068   28M ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
61068   28M ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 2483  385K ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 2483  385K ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 2483  385K ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0
 2483  385K ufw-track-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
38986   21M ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
38986   21M ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
   31  2638 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
   31  2638 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
   31  2638 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0
   31  2638 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
    0     0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
  103  5408 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination
58585   28M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
 2483  385K ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
  434 41570 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
40512   14M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
  209 11280 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
  209 11280 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
  603 48207 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
  603 48207 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination
  448 43754 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0
38507   21M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
   31  2638 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination
   39  2668 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
   29  1978 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination
  529 45543 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
   74  2664 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-track-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination
  665 38851 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
 1756  343K ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW


Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination
   10   600 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
   21  2038 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW


Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
    6   420 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:1194
  235 13896 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22 /* 'dapp_OpenSSH' */
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:1194
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:1194
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:22
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22


Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0


Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination


Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination

```

Again, thanks for any help :)

---

### Post by darkod on 2016-11-29
Ah, you are using ufw... Didn't know that.

Honestly, for simple openvpn connection, I suggest you better try iptables directly. This ufw output is too much to decypher. So many lines when in fact you probably have only few important rules. That get lost in all this ufw output...

I have done plenty of openvpn server-client connections, with or without the client routing all traffic thorugh the vpn connection, but I have only done it directly with iptables. I don't know how it should look in ufw.

In iptables it is easy with only couple of rules...

---

### Post by casey8 on 2016-11-29
Okay! So I went ahead and disabled ufw and set up iptables. Here is my new "sudo iptables -L -n -v" (I followed this: [https://arashmilani.com/post?id=53](https://arashmilani.com/post?id=53))

```

Chain INPUT (policy ACCEPT 53 packets, 5056 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            state NEW udp dpt:1194
    0     0 ACCEPT     all  --  tun+   *       0.0.0.0/0            0.0.0.0/0


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  tun+   *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  tun+   *       0.0.0.0/0            0.0.0.0/0
    0     0 ACCEPT     all  --  tun+   eth0    0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  eth0   tun+    0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED


Chain OUTPUT (policy ACCEPT 47 packets, 11454 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  *      tun+    0.0.0.0/0            0.0.0.0/0

```

I can still connect to the server after having this, but still have no connection to the internet.

I have very little experience with iptables, so I don't really know what I'm working with, but I'm willing to try anything.

---

### Post by darkod on 2016-11-29
For routing the nat table is also important. You can check it with:
```
sudo iptables -t nat -L -n -v
```

Otherwise, the current setup as it is is pretty worthless. If you notice all your policies are ACCEPT which means iptables is not blocking anything.

Do this. Create a file called for example /etc/iptables.rules
```
sudo nano /etc/iptables.rules
```

and copy the following into it:
```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]


-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p udp --dport 1194 -j ACCEPT
-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -i tun0 -s 10.8.200.0/24 -j ACCEPT
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
-A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT


COMMIT


*nat
:POSTROUTING ACCEPT [0:0]


-A POSTROUTING -j MASQUERADE


COMMIT
```

These are basic iptables rules for openvpn server and work 100% if you have enabled forwarding in /etc/sysctl.conf (which you already confirmed).

Few modifications that you might need to do:
1. In most INPUT -i rules I used eth0 but in 16.04 ubuntu has changed how it calls the interfaces. So you might need to adjust them for your interface name that has the public IP. You can check it with ifconfig.
2. In the FORWARD -i tun0 rule, it assumes your tunnel will be called tun0 and it allows forwarding from any traffic coming from 10.8.200.0/24 subnet (one of the subnets used for the openvpn clients). If you use different subnet, just modify that.

Once the file exists, you can apply these rules with:
```
sudo iptables-restore < /etc/iptables.rules
```

If the rules work for you, we can talk how to make them load each boot.

Don't forget that the problem might be on the client end too, but lets sort out the setup of the server first.

---

### Post by SeijiSensei on 2016-11-29
I generally prefer to bind masquerading to only the Internet-facing interface like this:
```

*nat
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING **-o eth0** -j MASQUERADE

```
This limits the effect of masquerading to outbound traffic.

---

### Post by darkod on 2016-11-29
Good comment by Sensei, do it like that.

I copied that from a server where I needed forwarding between more different interfaces, and I didn't edit it before posting. It's better to limit it when you can.

---

### Post by casey8 on 2016-11-29
Here is my "sudo iptables -t nat -L -n -v"

```
Chain PREROUTING (policy ACCEPT 123 packets, 23416 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 MASQUERADE  all  --  *      eth0    0.0.0.0/0            0.0.0.0/0

```

And my current "sudo iptables -L -n -v"
```
Chain INPUT (policy DROP 127 packets, 7612 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
   16   992 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    0     0 ACCEPT     udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            udp dpt:1194
    0     0            tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22 state NEW recent: SET name: SSH side: source mask: 255.255.255.255
    0     0 DROP       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22 state NEW recent: UPDATE seconds: 60 hit_count: 4 TTL-Match name: SSH side: source mask: 255.255.255.255
    0     0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  tun0   *       10.8.0.0/24          0.0.0.0/0


Chain OUTPUT (policy ACCEPT 18 packets, 5952 bytes)
 pkts bytes target     prot opt in     out     source               destination

```


I set up my /etc/iptables.rules like this
```

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]




-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p udp --dport 1194 -j ACCEPT
-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -i tun0 -s 10.8.0.0/24 -j ACCEPT
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hi$
-A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT




COMMIT




*nat
:POSTROUTING ACCEPT [0:0]


-A POSTROUTING -o eth0 -j MASQUERADE




COMMIT

```

But after I pushed it, I can no longer connect to the vpn at all. I get stuck at "MANAGEMENT: >STATE:1480451610,WAIT,,,"

I changed the the "-A FORWARD" line to my subnet.
I also changed the "-A POSTROUTING" line to what sensei said (Thanks for that)

I don't understand what you mean when you say 
> **darkod said:**
> 
1. In most INPUT -i rules I used eth0 but in 16.04 ubuntu has changed how it calls the interfaces. So you might need to adjust them for your interface name that has the public IP. You can check it with ifconfig.

So I may still have something misconfigured..

Finally, just for reference, here is my ifconfig
```

enp2s0    Link encap:Ethernet  HWaddr 10:c3:7b:92:a6:0e
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:5ce:4201:1ac0:12c3:7bff:fe92:a60e/64 Scope:Global
          inet6 addr: fe80::12c3:7bff:fe92:a60e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:925456 (925.4 KB)  TX bytes:429844 (429.8 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:20162 (20.1 KB)  TX bytes:20162 (20.1 KB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Thank you so much for the help - it means a lot

---

### Post by darkod on 2016-11-29
Ok, so your interface name is enp2s0. Use that instead of eth0.
Also, that interface has ip 10.0.0.3 which is private ip. How is internet traffic reaching this server? I thought it's directly on the internet which it obviously isn't.

---

