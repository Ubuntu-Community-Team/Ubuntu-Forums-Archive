---
title: "Ubuntu Server 16.04 Openvpn Connection Refused"
date: 2016-08-14
forum: Server Platforms
---

### Post by Baldry on 2016-08-14
[COLOR=#111111][FONT=Ubuntu]Hi, 

i am running a Openvpn server (Ubuntu 16.04) and Client (Ubuntu Server 14.04) but i suddendly could not connect to the tun after a reboot.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]TCP: connect to [AF_INET]xxxx:1194 failed, will try again in 5 seconds: Connection refused[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The openvpn server is running.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I did not chance any settings and thats why i am really confused. I always get the same error whitought any code like other people (verbose 6)

Server config:

[/FONT][/COLOR]```

 port 1194
 proto tcp
 dev tun2
 link-mtu 1420
 ca /etc/openvpn/keys/ca.crt
 cert /etc/openvpn/keys/server1.crt
 key /etc/openvpn/keys/server1.key
 dh /etc/openvpn/keys/dh1024.pem
 server 10.2.0.0 255.255.255.0
 ifconfig-pool-persist ipp.txt
 push "route 192.168.3.0 255.255.255.0"
 keepalive 10 120
 auth SHA1
 cipher AES-256-CBC
 user nobody
 group nogroup
 persist-key
 persist-tun 
 verb 3
```[COLOR=#111111][FONT=Ubuntu]

Client Config:
[/FONT][/COLOR]
```

client
 dev tun2
 link-mtu 1420
 remote xxxxx 1194
 resolv-retry infinite
 nobind
 persist-key
 persist-tun
 ca /etc/openvpn/keys3/ca.crt
 cert /etc/openvpn/keys3/client2.crt
 key /etc/openvpn/keys3/client2.key
 cipher AES-256-CBC
 verb 6
```[COLOR=#111111][FONT=Ubuntu]

IP-Forwarding is activ and Port is open

[/FONT][/COLOR]```

tcp        0      0 0.0.0.0:1194            0.0.0.0:*               LISTEN      5759/openvpn[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]

iptables:

[/FONT][/COLOR]```

[CENTER][COLOR=#000000][FONT=&amp]**vergrößern**[/FONT][/COLOR][/CENTER]
Chain INPUT (policy ACCEPT 2873 packets, 294K bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 147 packets, 29891 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  enp2s0 tun0    10.1.0.0/24          192.168.3.0/24       ctstate NEW
    0     0 ACCEPT     all  --  enp2s0 tun2    10.2.0.0/24          192.168.3.0/24       ctstate NEW
    0     0 ACCEPT     all  --  tun2   enp2s0  10.2.0.0/24          0.0.0.0/0            ctstate NEW
30471 5461K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  tun0   enp2s0  10.1.0.0/24          0.0.0.0/0            ctstate NEW

Chain OUTPUT (policy ACCEPT 1938 packets, 346K bytes)
 pkts bytes target     prot opt in     out     source               destination
```[COLOR=#111111][FONT=Ubuntu]

btw i am running 2 different tun and tun2 is not working (10.2.0.0)
Did i miss something?

Is it because of Sunday no one answers or no one knows why it isnt working? just wondering if people just cant help or no one is here :D Thanks anyway![/FONT][/COLOR]

---

### Post by wildmanne39 on 2016-08-14
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2016-08-14
Are you running two openvpn servers on the same port 1194 or on different ports?

---

### Post by Baldry on 2016-08-14
3 PCs
PC 1 = Server 1 
PC 2 = Server 2 and Client 1 (server1)
PC 3 = Client 1 (server 2) and Client 2 (server 1)

The thing that doesn't work is PC 3 Client 1 (server 2) connection i get a Refused from the Client 1 (server2) and everything runs through Port 1194 (TCP)

Like i said befor i rebooted everything worked just fine. I need the LAN from PC 2 and PC 1 at the PC 3 and with only 1 openvpn server the LAN from PC 2 is missing at PC 3 (even with client-to-client and iroute/route in the config it just didn't work)

any idee?

---

### Post by darkod on 2016-08-14
Try with different port for server2 conf file. Basically it's like running two separate vpns. I don't think you can run them on same port.
Change the port in server and client conf files, and don't forget to adjust iptables too if needed.
I think it should work like that.

---

### Post by Baldry on 2016-08-14
I switched to 1195 and now i am getting

TCP: connect to [AF_INET]:1195 failed, will try again in 5 seconds: No route to host

iptables 

```

Chain INPUT (policy ACCEPT 28 packets, 2202 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:1195


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  enp2s0 tun0    10.1.0.0/24          192.168.3.0/24       ctstate NEW
    0     0 ACCEPT     all  --  enp2s0 tun2    10.2.0.0/24          192.168.3.0/24       ctstate NEW
    0     0 ACCEPT     all  --  tun2   enp2s0  10.2.0.0/24          0.0.0.0/0            ctstate NEW
51462 9174K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     all  --  tun0   enp2s0  10.1.0.0/24          0.0.0.0/0            ctstate NEW


Chain OUTPUT (policy ACCEPT 14 packets, 2032 bytes)
 pkts bytes target     prot opt in     out     source               destination

```


netstat 
```

tcp        0      0 0.0.0.0:1195            0.0.0.0:*               LISTEN      3354/openvpn

```

like i said it did work befor for 1 week. Well i don't really care which port as long as it works :( sitting here for 4 days because of that reboot :(

Do i need to add routes to the client too? i can't make a mistake there because it's an Online server with shops running.

---

### Post by darkod on 2016-08-14
Sorry, I didn't notice you are talking about two different machines configured as openvpn servers. I thought it's on the same machine and same port. In your case you can use 1194 on the second server too, no need to change the port.

Few more things:
1. Your iptables are open (ACCEPT) so you don't need to worry about them blocking the connection. But if the servers are on public IP note that you actually have no firewall protection if the policies are ACCEPT. But we can talk about that later.

2. You say forwarding is working on the second server but still do these checks:
Check with ifconfig if tun2 interface is up.
Check if forwarding is enabled and the nat masquerade:
```
cat /etc/sysctl.conf | grep forward
sudo iptables -t nat -L -n -v
```

Post that output and we can have a look.

I assume all certificates are correct (server and client side).

PS. On the client side in the conf file add also:
```
proto tcp
```

You decided to use tcp instead of the default udp and if the client doesn't have this info it will not work correctly. Maybe it worked on udp until you rebooted or it connected somehow the first time and now after the reboot it can't any more. The protocol used on both sides has to be same and openvpn default is udp.

---

### Post by Baldry on 2016-08-14
> **darkod said:**
> Sorry, I didn't notice you are talking about two different machines configured as openvpn servers. I thought it's on the same machine and same port. In your case you can use 1194 on the second server too, no need to change the port.

Few more things:
1. Your iptables are open (ACCEPT) so you don't need to worry about them blocking the connection. But if the servers are on public IP note that you actually have no firewall protection if the policies are ACCEPT. But we can talk about that later.

2. You say forwarding is working on the second server but still do these checks:
Check with ifconfig if tun2 interface is up.
Check if forwarding is enabled and the nat masquerade:
```
cat /etc/sysctl.conf | grep forward
sudo iptables -t nat -L -n -v
```

Post that output and we can have a look.

I assume all certificates are correct (server and client side).

PS. On the client side in the conf file add also:
```
proto tcp
```

You decided to use tcp instead of the default udp and if the client doesn't have this info it will not work correctly. Maybe it worked on udp until you rebooted or it connected somehow the first time and now after the reboot it can't any more. The protocol used on both sides has to be same and openvpn default is udp.


IP-Forwarding

```

#net.ipv4.ip_forward=1
# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1
net.ipv4.ip_forward=1

```


iptables

```

 pkts bytes target     prot opt in     out     source               destination


Chain INPUT (policy ACCEPT 9216 packets, 1524K bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 39 packets, 2688 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
  624  206K MASQUERADE  all  --  *      enp2s0  0.0.0.0/0            0.0.0.0/0
    7   492 MASQUERADE  all  --  *      tun0    0.0.0.0/0            0.0.0.0/0
    0     0 MASQUERADE  all  --  *      tun2    0.0.0.0/0            0.0.0.0/0

```

Ofcourse all cert are correct (like i said this setup worked withought a problem befor the reboot) can the reboot effect that? i don't really know.

in the client config 
proto tcp is set
i must have delete it while removing the comments to post here.

Oh jeah ifconfig:

```


enp2s0    Link encap:Ethernet  Hardware Adresse 
          inet Adresse:192.168.3.3  Bcast:192.168.3.255  Maske:255.255.255.0
          inet6-Adresse: Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX-Pakete:137195 Fehler:0 Verloren:132 Überläufe:0 Fenster:0
          TX-Pakete:100177 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX-Bytes:21547435 (21.5 MB)  TX-Bytes:16755658 (16.7 MB)


lo        Link encap:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:65536  Metrik:1
          RX-Pakete:160 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:160 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:1
          RX-Bytes:11840 (11.8 KB)  TX-Bytes:11840 (11.8 KB)


tun0      Link encap:UNSPEC  Hardware Adresse 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet Adresse:10.1.0.26  P-z-P:10.1.0.25  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1361  Metrik:1
          RX-Pakete:7 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:8 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:100
          RX-Bytes:468 (468.0 B)  TX-Bytes:556 (556.0 B)


tun2      Link encap:UNSPEC  Hardware Adresse 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet Adresse:10.2.0.1  P-z-P:10.2.0.2  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1361  Metrik:1
          RX-Pakete:0 Fehler:0 Verloren:0 Überläufe:0 Fenster:0
          TX-Pakete:0 Fehler:0 Verloren:0 Überläufe:0 Träger:0
          Kollisionen:0 Sendewarteschlangenlänge:100
          RX-Bytes:0 (0.0 B)  TX-Bytes:0 (0.0 B)

```
removed some parts that are not importent.

---

### Post by darkod on 2016-08-14
No, the reboot should not affect certificates.

You seem to have everything configured correctly.

Did you try ping and telnet from the client to the server, to make sure it can reach it? I don't know if you use IP or hostname for the server, so try telnet the port 1194 (or 1195) from the client.

You did check that the corresponding tun interface is up on the server, right?

---

### Post by Baldry on 2016-08-14
I am using a hostname and if i ping the Hostname that i set up in the client settings i get the IP back that my server have. (it's not a Online server so i set up a hopto.org domainname to the ip from the server)

EDIT: you can see my ifconfig in the last post

Never used telnet let me google it first.

if i use telnet this comes out

Trying xxxxx...
telnet: Unable to connect to remote host: Connection refused
thats the same error that i have in the config at the client. i don't get it what is blocking it :(

I hope thats not important but at the openvpn client i don't have telnet and i can't install it. However i have it on another server where i tried it.

---

### Post by darkod on 2016-08-14
Unfortunately it's late in my time zone so I have to go... I can try helping you tomorrow if you still have the issue.

If the server is not online (if it's behind router/firewall and with private IP), check all the steps how the traffic would go...

1. Check that the public router has the port 1194 open and forwarded to the server private IP.
2. The server private IP is static, right? It doesn't change? That is important for the router to do the forwarding correctly.

Somewhere along the line something seems to have changed. Because your server is not publicly online, test all steps where the traffic might get blocked/lost.

---

### Post by Baldry on 2016-08-14
Yes i will check all the routes again thanks for your time.

I need that working in 8 hours so i will have to try harder :D i have set it up so that my domainname gets updated with the new ip everytime my isp switches it.

ITS WORKING ..... it was a SMALLL port opening on my fritz.box router.. how do i have that not set up befor? i can't belive it was that for 4 days ... thank you really for that tip i would have never looked because i thought i already did that step (and prob removed it afterwords why ever)

---

### Post by darkod on 2016-08-15
Perfect, glad you got it working... :)

---

