---
title: "ssh issue"
date: 2010-02-06
forum: Server Platforms
---

### Post by rdema19403 on 2010-02-06
i am running ubuntu 9.04 desktop and i have a headless server running 9.10 i used to able to open a terminal from my desktop and connect to the server now i get this error message ssh: connect to host 192.168.1.107 port 22: No route to host what would cause that? i disconnecter the network cable and hooked it up to my laptop i can connect to the internet. Could the network interface card be bad ? any suggestions ?
Thanks in advance

---

### Post by CharlesA on 2010-02-06
Are you able to ping the server?

---

### Post by rdema19403 on 2010-02-06
i am not really sure how to do that.could you tell me how to do that?

---

### Post by CharlesA on 2010-02-06
ping ip address

e.g., ping -c 4 192.168.1.1

---

### Post by BkkBonanza on 2010-02-07
Usually "no route to host" is caused by incorrect network settings. 
Show us output from,

cat /etc/networking/interfaces

for both ends, server and client. The values need to make sense for a routing to work, and if a router is in the mix it needs to jive as well.

---

### Post by Rob@ThePCWiz.info on 2010-02-07
how exactly is your network set up?
how does your server connect to the internet?

in the case that you are behind a router (i hope you would have a better setup).
you should make sure that port 22 is forwarded to the correct IP within the network.

ex. - if your server runs on internal ip: 192.168.1.100
make sure port 22 routes to 100, also make sure the IP is correct.

feedback please

---

### Post by rdema19403 on 2010-02-07
I am new to ubuntu  community do not know to much about networking or anything like that .
I have the server behind my router 
cable from comcast come in the house 
cable modem first 
linksys wireless router 
vonage is hard wired to the router 
server is hard wired to the router 

I  had an old computer at home and decided to put ubuntu server 9.10 to see how it works 
well I have the server in my basement decided ot hook the monitor back up to the server rebooted the server now everything seems to be ok.
I just wanted the server to back up some files and maybe to use it as a printer server wright now (just as a local area network)and maybe download some tv shows and stream them to my tv set .
I am really on a big learning curve with the server .
I have to laptops with ubuntu and a desktop with xp home on it
Thanks in advance Ralph

---

### Post by 2hot6ft2 on 2010-02-07
> **Rob@ThePCWiz.info said:**
> (i hope you would have a better setup).
Sounds like you should go thru the guide for SSH just like Rob I am surprised you're using port 22. That's one of the first things that should be changed when setting up SSH. Here's a guide:
[http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html](http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html)

Did you set up a static IP Address for the server? That would be done on the router. So start by running this on the server and finding out if you're trying to connect to it on **the IP Address it currently has**.
```
ifconfig
```
That will show you it's IP Address and if you didn't give it a static IP Address then it may not be 192.168.1.107 now.

What model is the Linksys router? Just wondering if dd-wrt could go on it for more control.

---

### Post by Rob@ThePCWiz.info on 2010-02-07
22 is just the common port to use, therefore I use it as an example.
Should really be changed, because
1. It's like handing over your system to an attacker.
2. Comcast limits connections out-going & incoming on ports 21, 22, 80, 6667

---

### Post by stlsaint on 2010-02-07
> **Rob@ThePCWiz.info said:**
> 22 is just the common port to use, therefore I use it as an example.
Should really be changed, because
1. It's like handing over your system to an attacker.
2. Comcast limits connections out-going & incoming on ports 21, 22, 80, 6667

I strongly feel opposite of your assumption of port 22. I use port 22 on my server for the past year+ just fine with key authentication and iptables. So IMO it is NOT handing over your server. So though it may be useful to change ports in general it is not something that should be preached to new users as a "Requirement" to running ssh. Again using port 22 on password authentication is not smart but even that can be fought against properly if need be! NOTE: This is not intended to start a flame war on whos setup is better...we are all here to help the poster.

You can even take it a step further and use fail2ban.

---

### Post by rdema19403 on 2010-02-08
linysy router model WRT54G

---

### Post by CharlesA on 2010-02-08
> **rdema19403 said:**
> linysy router model WRT54G

Ok. What is the IP/subnet of the server and what is the IP/subnet of the client that is having problems?

---

### Post by koenn on 2010-02-08
> **stlsaint said:**
> so though it may be useful to change ports in general it is not something that should be preached to new users as a "requirement" to running ssh. 
+1

---

### Post by rdema19403 on 2010-02-08
Destination LAN IP  	Subnet Mask  	Gateway  	Interface
192.168.1.0	255.255.255.0	0.0.0.0	LAN & Wireless
98.225.248.0	255.255.248.0	0.0.0.0	WAN (Internet)
0.0.0.0	0.0.0.0	98.225.248.1	WAN (Internet)
  	  	  	routing table from router
DHCP Active IP Table  	   	   	 
DHCP Server IP Address:   192.168.1.1 	
Client Host Name 	IP Address 	MAC Address 	Expires 	
 	192.168.1.102	00:0C:E5:C6:18:1E	13:49:33	
rd-laptop	192.168.1.103	00:06:25:01:BB:CD	23:53:10	
rd(server)	192.168.1.107	00:04:5A:63:69:2C	23:49:59

---

### Post by CharlesA on 2010-02-08
```
Destination LAN IP  	Subnet Mask  	Gateway  	Interface
192.168.1.0	255.255.255.0	0.0.0.0	LAN & Wireless
98.225.248.0	255.255.248.0	0.0.0.0	WAN (Internet)
0.0.0.0	0.0.0.0	98.225.248.1	WAN (Internet)
  	  	  	routing table from router
DHCP Active IP Table  	   	   	 
DHCP Server IP Address:   192.168.1.1 	
Client Host Name 	IP Address 	MAC Address 	Expires 	
 	192.168.1.102	00:0C:E5:C6:18:1E	13:49:33	
rd-laptop	192.168.1.103	00:06:25:01:BB:CD	23:53:10	
rd(server)	192.168.1.107	00:04:5A:63:69:2C	23:49:59
```

IP addresses look fine. Were you able to ping the server from the laptop?

---

### Post by rdema19403 on 2010-02-08
yes iam able to what is really wierd if i disconnect the monitor from and key board from the server reboot the server then i cannot connect to it from my laptop id not quite understand that.here are the ping results
rd@rd-laptop:~$ ping 192.168.1.107
PING 192.168.1.107 (192.168.1.107) 56(84) bytes of data.
64 bytes from 192.168.1.107: icmp_seq=1 ttl=64 time=2.59 ms
64 bytes from 192.168.1.107: icmp_seq=2 ttl=64 time=2.14 ms
64 bytes from 192.168.1.107: icmp_seq=3 ttl=64 time=2.40 ms
64 bytes from 192.168.1.107: icmp_seq=4 ttl=64 time=2.68 ms
64 bytes from 192.168.1.107: icmp_seq=5 ttl=64 time=2.39 ms
64 bytes from 192.168.1.107: icmp_seq=6 ttl=64 time=2.30 ms
64 bytes from 192.168.1.107: icmp_seq=7 ttl=64 time=2.53 ms
64 bytes from 192.168.1.107: icmp_seq=8 ttl=64 time=2.44 ms
64 bytes from 192.168.1.107: icmp_seq=9 ttl=64 time=4.97 ms
64 bytes from 192.168.1.107: icmp_seq=10 ttl=64 time=2.49 ms
64 bytes from 192.168.1.107: icmp_seq=11 ttl=64 time=2.13 ms
64 bytes from 192.168.1.107: icmp_seq=12 ttl=64 time=2.25 ms
64 bytes from 192.168.1.107: icmp_seq=13 ttl=64 time=2.14 ms
64 bytes from 192.168.1.107: icmp_seq=14 ttl=64 time=2.21 ms
64 bytes from 192.168.1.107: icmp_seq=15 ttl=64 time=2.63 ms
64 bytes from 192.168.1.107: icmp_seq=16 ttl=64 time=2.22 ms
64 bytes from 192.168.1.107: icmp_seq=17 ttl=64 time=2.11 ms
64 bytes from 192.168.1.107: icmp_seq=18 ttl=64 time=3.05 ms
64 bytes from 192.168.1.107: icmp_seq=19 ttl=64 time=2.26 ms
64 bytes from 192.168.1.107: icmp_seq=20 ttl=64 time=2.47 ms
64 bytes from 192.168.1.107: icmp_seq=21 ttl=64 time=2.67 ms
64 bytes from 192.168.1.107: icmp_seq=22 ttl=64 time=2.50 ms
64 bytes from 192.168.1.107: icmp_seq=23 ttl=64 time=2.21 ms
64 bytes from 192.168.1.107: icmp_seq=24 ttl=64 time=2.24 ms
64 bytes from 192.168.1.107: icmp_seq=25 ttl=64 time=2.12 ms
64 bytes from 192.168.1.107: icmp_seq=26 ttl=64 time=2.14 ms
64 bytes from 192.168.1.107: icmp_seq=27 ttl=64 time=2.21 ms
64 bytes from 192.168.1.107: icmp_seq=28 ttl=64 time=2.30 ms
64 bytes from 192.168.1.107: icmp_seq=29 ttl=64 time=3.07 ms
64 bytes from 192.168.1.107: icmp_seq=30 ttl=64 time=2.05 ms
64 bytes from 192.168.1.107: icmp_seq=31 ttl=64 time=2.63 ms
64 bytes from 192.168.1.107: icmp_seq=32 ttl=64 time=2.47 ms
64 bytes from 192.168.1.107: icmp_seq=33 ttl=64 time=2.32 ms
64 bytes from 192.168.1.107: icmp_seq=34 ttl=64 time=2.37 ms
64 bytes from 192.168.1.107: icmp_seq=35 ttl=64 time=2.25 ms
64 bytes from 192.168.1.107: icmp_seq=36 ttl=64 time=2.40 ms
64 bytes from 192.168.1.107: icmp_seq=37 ttl=64 time=2.38 ms
64 bytes from 192.168.1.107: icmp_seq=38 ttl=64 time=2.30 ms
64 bytes from 192.168.1.107: icmp_seq=39 ttl=64 time=2.28 ms
64 bytes from 192.168.1.107: icmp_seq=40 ttl=64 time=2.61 ms
64 bytes from 192.168.1.107: icmp_seq=41 ttl=64 time=3.48 ms
64 bytes from 192.168.1.107: icmp_seq=42 ttl=64 time=2.47 ms
64 bytes from 192.168.1.107: icmp_seq=43 ttl=64 time=2.17 ms
64 bytes from 192.168.1.107: icmp_seq=44 ttl=64 time=2.17 ms
64 bytes from 192.168.1.107: icmp_seq=45 ttl=64 time=2.15 ms
64 bytes from 192.168.1.107: icmp_seq=46 ttl=64 time=3.57 ms
64 bytes from 192.168.1.107: icmp_seq=47 ttl=64 time=2.64 ms
64 bytes from 192.168.1.107: icmp_seq=48 ttl=64 time=2.25 ms

---

### Post by koenn on 2010-02-08
> **rdema19403 said:**
> yes iam able to what is really wierd if i disconnect the monitor from and key board from the server reboot the server then i cannot connect to it from my laptop id not quite understand that.

are you quite sure the server actually boots if it doesn'y have monitor or keyboard ?

you can verify by booting it (no monitor, no keyb), and after a few minutes, when you think it should be up, attach a monitor

---

### Post by CharlesA on 2010-02-08
The ping results look fine.

Maybe it errors out becuz there is no keyboard attached?

I remember a thread about how a machine wouldn't be accessable from the network if it didn't have a keyboard/monitor hooked up. I cannot remember where it was, but you can probably search for it.

---

### Post by wirelessmonkey on 2010-02-08
On a security configured server, changing the default ssh port does nothing except decrease log noise.

---

