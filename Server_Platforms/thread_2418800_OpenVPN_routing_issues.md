---
title: "OpenVPN routing issues"
date: 2019-05-11
forum: Server Platforms
---

### Post by stefangrosaru on 2019-05-11
I'm having issues when connecting to my OpenVPN server, I can connect to it and also ping while connected, but I can't access any websites from my client. My guess is that I'm missing some routing settings.
Here is my current iptables config, I've also made sure that forwarding is enabled in sysctl.conf
```
iptables -L -n -v
Chain INPUT (policy ACCEPT 6498 packets, 903K bytes)
 pkts bytes target     prot opt in     out     source               destination         
   24  2016            all  --  tun0   *       0.0.0.0/0            0.0.0.0/0           


Chain FORWARD (policy ACCEPT 564 packets, 54808 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  497 35530            all  --  tun0   *       0.0.0.0/0            0.0.0.0/0           


Chain OUTPUT (policy ACCEPT 5913 packets, 1361K bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

```

iptables -t nat -L -n -v
Chain PREROUTING (policy ACCEPT 3316 packets, 409K bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain INPUT (policy ACCEPT 3050 packets, 389K bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 862 packets, 78391 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain POSTROUTING (policy ACCEPT 862 packets, 78391 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  220 15276 MASQUERADE  all  --  *      eth0    10.8.0.0/24          0.0.0.0/0 
          
```

---

### Post by darkod on 2019-05-11
Please post the content of your server.conf file from the openvpn server.

Also post the ifconfig output from the server.

---

### Post by stefangrosaru on 2019-05-11
```

ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.6  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::f2d6:623e:4dd4:54bd  prefixlen 64  scopeid 0x20<link>
        ether b8:27:eb:78:e2:ad  txqueuelen 1000  (Ethernet)
        RX packets 51932  bytes 7891046 (7.5 MiB)
        RX errors 0  dropped 3  overruns 0  frame 0
        TX packets 50925  bytes 12756251 (12.1 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 16  bytes 1622 (1.5 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16  bytes 1622 (1.5 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.8.0.1  netmask 255.255.255.255  destination 10.8.0.2
        inet6 fe80::bd93:e33a:2ef5:78d0  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 567  bytes 42562 (41.5 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 103  bytes 22270 (21.7 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlan0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether b8:27:eb:2d:b7:f8  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
```

port 1194
proto udp
dev tun
ca /etc/openvpn/certs/keys/ca.crt
cert /etc/openvpn/certs/keys/server.crt
key /etc/openvpn/certs/keys/server.key  
dh /etc/openvpn/dh4096.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
tls-auth /etc/openvpn/certs/keys/ta.key 0
cipher AES-256-CBC
user openvpn
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
explicit-exit-notify 1
auth SHA512
tls-cipher TLS-DHE-RSA-WITH-AES-256-GCM-SHA384:TLS-DHE-RSA-WITH-AES-128-GCM-SHA256:TLS-DHE-RSA-WITH-AES-256-CBC-SHA:TLS-DHE-RSA-WITH-CAMELLIA-256-CBC-SHA:TLS-DHE-RSA-WITH-AES-128-CBC-SHA:TLS-DHE-RSA-WITH-CAMELLIA-128-CBC-SHA

```

---

### Post by darkod on 2019-05-11
I notice the server has a private LAN IP for eth0. Is it at your home? How are you connecting to it, from the same LAN?

At first look everything looks correct. You have the redirect gateway command in the server.conf, so the client is told to use the tunnel as default gateway once connected.

Is the client ubuntu too? Can you test the routes on it after it is connected to the VPN?

If it is ubuntu client, something like this should show you the routes:
```
route -n
```

You can also try traceroute to google dns 8.8.8.8 from the client, it can maybe show how it is trying to reach the internet.

I would disable ipv6 if you are not using it, just to make sure it doesn't interfere.

---

### Post by stefangrosaru on 2019-05-11
After trying it out without ipv6 it seems to work just fine, any ideas why that's an issue?

Also is there any way to make ipv6 work too?

---

### Post by darkod on 2019-05-11
I can't be sure, but my theory is this:
The client sends its traffic to the openvpn server, and the server forwards it to the internet. For the return traffic, it needs to know how to send it back to the client (this is why the MASQUERADE iptables rule is used). If the client is on ipv4 and the server on ipv6 maybe this return traffic is not correctly directed to the client.

If you want to work with ipv6 (I don't see it necessary personally), then try to setup the server.conf to use ipv6 too, not the 10.8.0.0/24 subnet.

I have never tried setting up OpenVPN with ipv6 yet.

---

### Post by stefangrosaru on 2019-05-11
Sorry, my answer wasn't clear enough. My current situation is as follows: the server is on an ipv4 only network and the client that I'm connecting from is running on an ipv6 network.

---

### Post by darkod on 2019-05-11
Well, I asked for ifconfig from the server and what you posted I can see ipv6 IP assigned to eth0 and tun0, in addition to the ipv4 IP.

With a mix lke that, the traffic can sometimes take another preferred route than the one you expect.

Anyway, my point was to avoid mixing ipv4 and ipv6 if you can. And I don't see a need for ipv6 if eevrything is on private subnets. ipv6 was introduced mainly for public IPs because ipv4 is running out. But for private subnets, you never really need to use it.

You can if you want, but then do everything with ipv6.

---

### Post by stefangrosaru on 2019-05-11
So then the question is,  if my client is running on both ipv4 and ipv6 how do I get it to use ipv4 when connected to the vpn?

---

### Post by darkod on 2019-05-12
I can't help you much there. I don't use a mix of ipv4 and ipv6. In fact, I see no reason any client to have both ipv4 and ipv6 on the same adapter. Either the LAN is ipv4 or ipv6.

Is the client on two different networks?

Did you try setting up OpenVPN subnet with ipv6?

I can't help you much more than those suggestions.

---

### Post by stefangrosaru on 2019-05-12
> **darkod said:**
> I can't help you much there. I don't use a mix of ipv4 and ipv6. In fact, I see no reason any client to have both ipv4 and ipv6 on the same adapter. Either the LAN is ipv4 or ipv6.

Is the client on two different networks?

Did you try setting up OpenVPN subnet with ipv6?

I can't help you much more than those suggestions.

First of all let me further explain the situation: the server is on an ipv4 network and I'm trying to connect to it from outside(not from local network) and sometimes my client might be using ipv4 or ipv6 or both.

From testing different clients this is what I've noticed: with the same server and client config Windows and Android both work perfectly fine even when on ipv6, it's just Linux that has an issue when I'm on ipv6. This makes me think that there's something missing on Linux in order to make this work.

---

### Post by darkod on 2019-05-13
Well, you say your server is on ipv4 network but in your ifconfig output it shows both ipv4 and ipv6 IP assigned to eth0 of the server. And on tun0 too.

---

### Post by The Cog on 2019-05-15
My guess is that your Linux is trying to use IPv6 to connect to the IPv4-only server when it's connected on an IPv6 capable network. This will only be happening if the client knows of an IPv6 address for the server. The command "host <server-name>" will show you the addresses that the cliient thinks the server has. 

I don't know of any way to make Linux use IPv4 to connect to a name when it has valid IPv4 and IPv6 addresses - using IPv6 in that situation is the proper thing to do. Maybe you should configure the client to use the IPv4 address, or make an entry in /etc/hosts for it that only lists the IPv4 address.

---

