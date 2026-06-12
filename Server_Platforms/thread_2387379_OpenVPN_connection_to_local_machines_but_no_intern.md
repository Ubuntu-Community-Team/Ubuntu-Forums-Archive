---
title: "OpenVPN connection to local machines but no internet access"
date: 2018-03-18
forum: Server Platforms
---

### Post by olliek2 on 2018-03-18
Hi all!

I've been experiencing some issues with my OpenVPN server setup.
The server is running Ubuntu Server 16.04.

I am trying to connect to the OpenVPN server using a .ovpn file from an Android device.
This works fine and I am able to access various machines in the same network as the VPN server.
Unfortunately I am unable to access anything but the server's local network (eg. other websites).
The connections seems to simply timeout when trying to do this.
I've trying pinging to these websites directly but this also doesn't seem to work (so I suppose this is not a DNS issue).

Here are some logs:
```
cat /etc/sysctl.conf | grep forward
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1

```
```

iptables -L -n -v
Chain INPUT (policy ACCEPT 3774 packets, 3501K bytes)
 pkts bytes target     prot opt in     out     source               destination
  16M   18G ACCEPT     all  --  tun+   *       0.0.0.0/0            0.0.0.0/0


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  tun+   *       0.0.0.0/0            0.0.0.0/0


Chain OUTPUT (policy ACCEPT 994 packets, 51336 bytes)
 pkts bytes target     prot opt in     out     source               destination

```

```
iptables -t nat -L -n -v
Chain PREROUTING (policy ACCEPT 3 packets, 160 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain INPUT (policy ACCEPT 3 packets, 160 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 4 packets, 676 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 4 packets, 676 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 MASQUERADE  all  --  *      eno1    10.8.0.0/24          0.0.0.0/0

```

I also have UFW disabled.

Does anyone have any idea what I am doing wrong here?

Thanks.

---

### Post by darkod on 2018-03-18
1. You have all iptables policies to ACCEPT. This is not recommended for a server that is on the internet (your OpenVPN server). This is not why the clients wouldn't be able to access the internet but it is something to reconsider, leaving a server on the internet with ACCEPT.

2. Your setup looks correct. You have forwarding enabled in sysctl.conf and you have the MASQUERADE in the nat table. That is enough for routing to work on OpenVPN server.

Please post the server.conf to check the config there. Only the clean version, without any unused parameters, so that it is easier to read. Also post the server setup info:
```
ifconfig
route -n
```

In the above iptables listing you have no packets going through the FORWARD chain which is strange. The VPN traffic should show there, even if it's blocked by iptables. It looks like traffic from vpn clients is not routed correctly, maybe some setting in the server.conf.

---

### Post by olliek2 on 2018-03-18
Thanks for your extremely fast response!

This is my server configuration:
```

port 1487
proto tcp
dev tun
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"
keepalive 10 120
tls-auth ta.key 0 # This file is secret
key-direction 0
cipher AES-128-CBC   # AES
auth SHA256
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
log-append  openvpn.log
verb 3

```

ifconfig info:
```

ifconfig
eno1      Link encap:Ethernet  HWaddr 94:18:82:37:61:60
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::9618:82ff:fe37:6160/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:414022452 errors:0 dropped:146 overruns:0 frame:0
          TX packets:141873548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:362032845271 (362.0 GB)  TX bytes:22817845264 (22.8 GB)
          Interrupt:16


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4180403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4180403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:1008336091 (1.0 GB)  TX bytes:1008336091 (1.0 GB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:945 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:348261 (348.2 KB)  TX bytes:684716 (684.7 KB)


tun1      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.82.10.6  P-t-P:10.82.10.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:16083866 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12577734 errors:0 dropped:4262 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:17990709872 (17.9 GB)  TX bytes:1585968418 (1.5 GB)

```

tun1 is being used for the OpenVPN client that is running on the same machine as the OpenVPN server (could this be the culprit?).
Ideally I don't want the data pckets from clients connected to my OpenVPN server being redirected using the OpenVPN client running on the OpenVPN server's machine (starting to get a bit complex here).
I want data packets from the clients to be redicted to the eno1 interface and not to the tun1 interface.

route info:
```

 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.82.10.5      128.0.0.0       UG    0      0        0 tun1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eno1
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.82.10.1      10.82.10.5      255.255.255.255 UGH   0      0        0 tun1
10.82.10.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun1
128.0.0.0       10.82.10.5      128.0.0.0       UG    0      0        0 tun1
185.210.218.108 192.168.0.1     255.255.255.255 UGH   0      0        0 eno1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eno1

```



Thanks!

---

### Post by darkod on 2018-03-18
> I want data packets from the clients to be redicted to the eno1 interface and not to the tun1 interface.

But you could have the issue there... If the server is set up to use tun1 as default gateway, it will send all traffic from the clients over tun1 too. And it looks like this is the setup you have. Do you know if the vpn server you have connected your server to is also pushing the redirect-gateway? I can't figure it out from your route -n right now.

If it is, then your server is sending everything through tun1 including the client traffic. And since your masquerade rule covers only traffic through eno1, there is no NAT for tun1.

You can do a quick test of this, with temporary iptables rule:
```
sudo iptables -t nat -A POSTROUTING -o tun1 -s 10.8.0.0/24 -j MASQUERADE
```

If clients have internet after that, then their traffic is routed through tun1.

Since you are trying to nest vpn connections you should plan what you want to achieve exactly. And it might be complicated to control everything if the other vpn server is not managed by you.

---

### Post by olliek2 on 2018-03-18
Wow, seems like you're 100% correct!
I've ran the command you mentioned and the VPN clients now seem to be able to browse the internet.
It does look like the data is indeed being redirected through tun1 and I'm redirected to the local Google page of the VPN (foreign country).

I'll try to sketch the current setup.

I have a server running in my network (let's call this machine A).
I have an Android device (machine B).

On machine A, both a VPN server and a VPN client is running.
Basically I want all traffic to go through the VPN client (tun1) on the server.
I've made some exceptions on this using the mangle ip table.

I want machine B to be able to connect as a VPN client to the VPN server running on machine A.
As I am sketching this now, it seems logical that machine A is redirecting all traffic through tun1 as a VPN client (since everything is redirected to tun1 by default).
I would like data packets from machine B to be redirected to the eno1 interface instead so machine B is being able to browse the internet without the VPN client running on machine A interfering.

I am not quite sure how to approach this, since I don't think there is a specific port number to add to the mangle ip table to exclude this traffic from the VPN client running on machine A.

Do you have any idea on how to approach this?

Thanks for all your help up to this point!

---

### Post by darkod on 2018-03-18
A combination of these resources should help you configure new table and rule to route traffic from source 10.8.0.0/24 through eno1.

[https://superuser.com/questions/376667/how-to-route-only-specific-subnet-source-ip-to-a-particular-interface](https://superuser.com/questions/376667/how-to-route-only-specific-subnet-source-ip-to-a-particular-interface)
[https://serverfault.com/questions/487939/permanently-adding-source-policy-routing-rules](https://serverfault.com/questions/487939/permanently-adding-source-policy-routing-rules)
[http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.rpdb.simple.html](http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.rpdb.simple.html)

---

### Post by olliek2 on 2018-03-18
Thanks for the links. I was able to run a simple command at startup to get it working:
```

ip rule add from 10.8.0.0/24 table TABLE_NAME

```

Since I already had rules for the TABLE_NAME table to redirect through eno1, this worked perfectly.
I also previously added a script to /etc/network/if-up.d to execute when the network would be brought up during startup of the system.
The commands in this script would be executed when the interface would be equal to eno1.
I've added the command above to the file and it now seems to be working after a reboot too.

The only weird thing I noticed is that when I run 'ip rule list' after a reboot, the newly applied rules by the script aren't visible (also the ip rules that were always executed before aren't visible anymore).
When connecting to my server as a VPN client it does seem to be working though (eg. using a website to check my IP, which is the same as the server's).
Do you have any idea how it is possible that the rules don't show up with 'ip rule list' but do seem to be active?

Thanks!

---

### Post by darkod on 2018-03-18
No, I have no idea why they don't show. I have never actually worked with this until looking it up now for this thread.

---

### Post by olliek2 on 2018-03-18
Alright, no problem. Thanks for all the help!

---

