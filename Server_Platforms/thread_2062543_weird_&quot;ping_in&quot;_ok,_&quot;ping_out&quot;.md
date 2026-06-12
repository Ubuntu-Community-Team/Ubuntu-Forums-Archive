---
title: "weird: &quot;ping in&quot; ok, &quot;ping out&quot; not ok"
date: 2012-09-25
forum: Server Platforms
---

### Post by Fraaik on 2012-09-25
Hello all!

I've set up an Ubuntu 12.04 Server as a database server.
Network is runing at address-range 172.16.254.x.
Server address is 172.16.254.98

DB-Clients are able to connecto to database.
If I ping from a client TO server address it works fine.

If I do a ping FROM the server to any client, I get 100% loss.
If I do a scan with nmap it says "no hosts".

**That meens: the server can't reach the gateway nor the nameserver.**

Does anyone have an idea what is goning wrong here???

Thank you
Fraaik

---

### Post by HugoSerrano on 2012-09-25
Hello!

Can you ping the gateway?
Check your netmask.

Best Regards!

---

### Post by albandy on 2012-09-25
Are the clients in the same subnet?

---

### Post by Fraaik on 2012-09-25
Hello Hugo, hello albandy!

Ping to gateway is also negativ,
Netmask is 255.255.255.0
Yes, all clients are in the same subnet.

Strange, isn't it?

---

### Post by albandy on 2012-09-25
Please, type the following commands and send us the result:

ifconfig
route -n
sudo mii-tool

---

### Post by Fraaik on 2012-09-25
Here it is:


```

ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:1b:fc:38:15:90  
          inet Adresse:172.16.254.98  Bcast:172.16.254.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21b:fcff:fe38:1590/64 GÃ¼ltigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:10 errors:0 dropped:2 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX-Bytes:640 (640.0 B)  TX-Bytes:1964 (1.9 KB)
          Interrupt:17 Speicher:cffe0000-d0000000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX-Bytes:1148 (1.1 KB)  TX-Bytes:1148 (1.1 KB)

route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.254.250  0.0.0.0         UG    100    0        0 eth0
172.16.254.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0

route -n
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
default         172.16.254.250  0.0.0.0         UG    100    0        0 eth0
172.16.254.0    *               255.255.255.0   U     0      0        0 eth0

mii-tool:
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
eth0: negotiated 100baseTx-FD, link ok


nmap 172.16.254.1-250
Starting Nmap 5.21 ( http://nmap.org ) at 2012-09-25 15:13 CEST
Nmap scan report for 172.16.254.98
Host is up (0.00059s latency).
Not shown: 998 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
3306/tcp open  mysql

Nmap done: 250 IP addresses (1 host up) scanned in 38.68 seconds


```

Cheers,
Fraaik

---

### Post by HugoSerrano on 2012-09-25
do u got any iptables rules?
show us the output of 
iptables -L

---

### Post by albandy on 2012-09-26
You said you can connect from clients to server.
Can you try to transfer a big file (>500MB) from a client to the server throught ssh?

On client: 
scp /home/user/myfile.iso user@server_ip:/tmp

if works try this from client too:

scp [email]user@server_ip:/tmp/myfile.iso[/email] /tmp


if it's transfered at the same speed, the network interface is working well and probably is a software configuration problem.

But if is too slow, can be a kernel driver error with your netork interface or a damaged interface.

---

### Post by Fraaik on 2012-09-28
Hello again!

What a shame - I can't believe it: I've transposed digits in my addess room:
the right one is 172.16.**245**.x and NOT 172.16.**254**.x.
Three days of work for nothing!

But now all works as expected.

Why ping worked and mii-toll says 
SIOCGMIIREG on eth0 failed: Input/output error
is inexplainable for me.

Anyway: thank you very much HugoSerrano and albandy for yr support!!!

Cheers,
Fraaik

---

### Post by albandy on 2012-09-29
> **Fraaik said:**
> Hello again!

What a shame - I can't believe it: I've transposed digits in my addess room:
the right one is 172.16.**245**.x and NOT 172.16.**254**.x.
Three days of work for nothing!

But now all works as expected.

Why ping worked and mii-toll says 
SIOCGMIIREG on eth0 failed: Input/output error
is inexplainable for me.

Anyway: thank you very much HugoSerrano and albandy for yr support!!!

Cheers,
Fraaik

You're welcome. But don't forget to mark this as "Solved"

---

