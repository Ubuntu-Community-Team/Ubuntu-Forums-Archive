---
title: "home server"
date: 2011-06-08
forum: Server Platforms
---

### Post by junovo on 2011-06-08
Can someone help with the following please :

Set up LAMP sever on ubuntu 11.04 . Localhost gives home page with no problems 
Altered the server /etc/network/interfaces file to show 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.5
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

Performed sudo /etc/init.d/networking restart

Configured my Sky router so that port forwarding HTTP port 80 sends to ip address 192.168.0.5

Then checked to see if could connect from internet using a tool on [http://www.dyndns.com/support/tools/openport.html](http://www.dyndns.com/support/tools/openport.html) and input the ip address showing on my ADSL port ip address. Results give "An attempted connection to 94.0.47.254:80 was refused. This typically indicates that there are no services available on that port, but that it is NOT being blocked by a firewall or your ISP"

What have i done wrong ?

---

### Post by a2j on 2011-06-08
what happens when you go to 192.168.0.5 from a different box on the same network? if you're able to access it, then router is not forwarding it right, or something..

---

### Post by jramshu on 2011-06-08
Is the site set up in /var/www?

---

### Post by ruffEdgz on 2011-06-08
I believe the way your did the port forwarding on your router isn't working. I have done this with my DD-WRT router I have at home and its worked when the port forwarding is done properly.

Link to DD-WRT Port-Forwarding page - [http://www.dd-wrt.com/wiki/index.php/Port_Forwarding#Configuring_Port_Forwarding](http://www.dd-wrt.com/wiki/index.php/Port_Forwarding#Configuring_Port_Forwarding)

If the DD-WRT guide doesn't help point you into the right direction, take a screenshot of your router's port forwarding configuration so we can get a better understanding of whats being done.

Thanks!

---

### Post by jramshu on 2011-06-08
Sure seems like a port forwarding issue.

Also, in the configs, I don't believe everything there is necessary.

Here's how mine is set up and it works fine in or out of the network.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.200
netmask 255.255.255.0
gateway 192.168.2.1
```

---

### Post by junovo on 2011-06-08
Hi 

**_PC on same network_**
ok I try to link to the server using another pc on the wireless network using [http://192.168.0.5](http://192.168.0.5) and it times out. If i ping the server from the pc i get :
Pinging 192.168.0.5 with 32 bytes of data:
Reply from 192.168.0.5: bytes=32 time<1ms TTL=128
Reply from 192.168.0.5: bytes=32 time<1ms TTL=128
Reply from 192.168.0.5: bytes=32 time<1ms TTL=128
Reply from 192.168.0.5: bytes=32 time<1ms TTL=128
Ping statistics for 192.168.0.5:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

On the pc in the network i get 
C:\Documents and Settings\Administrator>ipconfig
Windows IP Configuration
Ethernet adapter Bluetooth Network:
        Media State . . . . . . . . . . . : Media disconnected
Ethernet adapter Wireless Network Connection:
        Connection-specific DNS Suffix  . : home
        IP Address. . . . . . . . . . . . : 192.168.0.5
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
Ethernet adapter Local Area Connection:
        Media State . . . . . . . . . . . : Media disconnected


_**SERVER > **_
On the server itself I can see on [http://localhost](http://localhost) and [http://192.168.0.5](http://192.168.0.5) the following :
"It works!
This is the default web page for this server.
The web server software is running but no content has been added, yet."

**_SAGEM SKY  Router _**
ROUTER STATUS
Firmware Version	2.8Sky
ADSL Port
MAC Address	00:25:69:2d:3e:73
IP Address	94.0.47.247
Network Type	MER
IP Subnet Mask	255.255.255.192
Gateway IP Address	94.0.47.254
Domain Name Server	90.207.238.97    90.207.238.99
LAN Port
MAC Address	00:25:69:2d:3e:71
IP Address	192.168.0.1
DHCP	enable
IP Subnet Mask	255.255.255.0

[IMG]http://i216.photobucket.com/albums/cc47/s_ilko/firewall.jpg[/IMG]

[IMG]http://i216.photobucket.com/albums/cc47/s_ilko/firewall2.jpg[/IMG]

---

### Post by a2j on 2011-06-08
your windows pc and server both have the same 192.168.0.5 IP addresses? or I got that wrong?

---

### Post by collisionystm on 2011-06-08
> **a2j said:**
> your windows pc and server both have the same 192.168.0.5 ip addresses? Or i got that wrong?


> on the pc in the network i get 
c:\documents and settings\administrator>ipconfig
windows ip configuration
ethernet adapter bluetooth network:
        Media state . . . . . . . . . . . : Media disconnected
ethernet adapter wireless network connection:
        Connection-specific dns suffix  . : Home
        ip address. . . . . . . . . . . . : 192.168.0.5
        subnet mask . . . . . . . . . . . : 255.255.255.0
        default gateway . . . . . . . . . : 192.168.0.1
ethernet adapter local area connection:
        Media state . . . . . . . . . . . : Media disconnected



yup! Lol

---

### Post by jramshu on 2011-06-08
> On the pc in the network i get 
C:\Documents and Settings\Administrator>ipconfig
Windows IP Configuration
Ethernet adapter Bluetooth Network:
Media State . . . . . . . . . . . : Media disconnected
Ethernet adapter Wireless Network Connection:
Connection-specific DNS Suffix . : home
IP Address. . . . . . . . . . . . : 192.168.0.5
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.0.1
Ethernet adapter Local Area Connection:
Media State . . . . . . . . . . . : Media disconnected

I may be wrong but is this a windows machine with the same ip address as the lamp server?

---

### Post by jramshu on 2011-06-08
I think we all caught this at the exact same time! That would explain it.

LOL!!!!

EDIT: Not laughing at OP, just funny how three of us caught it around the same time frame.

---

### Post by junovo on 2011-06-08
Yep ur correct:oops: .... i did think that when i sent the last note so i changed it to 192.168.0.200 on both the server and the router and still get the same problem. 

for the /etc/resolv.conf I have nameserver 192.168.0.200 , is that correct ?

also on the server I am unable to browse the internet does that indicate its blocking outbound services ?

log from router if helps 
Jun  8 21:37:16 (none) user.alert kernel: Intrusion -> IN=nas_0_40 OUT= MAC=00:25:69:2d:3e:73:00:07:72:79:ea:21:08:00 SRC=94.255.55.187 DST=94.0.47.247 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=34246 DF PROTO=TCP SPT=16248 DPT=445 WINDOW=65535 RES=0x00 S

Jun  8 21:41:18 (none) user.alert kernel: Intrusion -> IN=nas_0_40 OUT= MAC=00:25:69:2d:3e:73:00:07:72:79:ea:21:08:00 SRC=94.50.168.165 DST=94.0.47.247 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=27090 DF PROTO=TCP SPT=2774 DPT=445 WINDOW=65535 RES=0x00 SY

Jun  8 21:43:41 (none) user.alert kernel: Intrusion -> IN=nas_0_40 OUT= MAC=00:25:69:2d:3e:73:00:07:72:79:ea:21:08:00 SRC=94.76.92.169 DST=94.0.47.247 LEN=64 TOS=0x00 PREC=0x00 TTL=119 ID=32837 DF PROTO=TCP SPT=47663 DPT=445 WINDOW=64380 RES=0x00 SY

Jun  8 21:47:24 (none) user.alert syslog: HTTP log in from LAN: 192.168.0.3

---

### Post by collisionystm on 2011-06-08
> **junovo said:**
> Yep ur correct:oops: .... i did think that when i sent the last note so i changed it to 192.168.0.200 on both the server and the router and still get the same problem. 

for the /etc/resolv.conf I have nameserver 192.168.0.200 , is that correct ?

also on the server I am unable to browse the internet does that indicate its blocking outbound services ?

log from router if helps 
Jun  8 21:37:16 (none) user.alert kernel: Intrusion -> IN=nas_0_40 OUT= MAC=00:25:69:2d:3e:73:00:07:72:79:ea:21:08:00 SRC=94.255.55.187 DST=94.0.47.247 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=34246 DF PROTO=TCP SPT=16248 DPT=445 WINDOW=65535 RES=0x00 S

Jun  8 21:41:18 (none) user.alert kernel: Intrusion -> IN=nas_0_40 OUT= MAC=00:25:69:2d:3e:73:00:07:72:79:ea:21:08:00 SRC=94.50.168.165 DST=94.0.47.247 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=27090 DF PROTO=TCP SPT=2774 DPT=445 WINDOW=65535 RES=0x00 SY

Jun  8 21:43:41 (none) user.alert kernel: Intrusion -> IN=nas_0_40 OUT= MAC=00:25:69:2d:3e:73:00:07:72:79:ea:21:08:00 SRC=94.76.92.169 DST=94.0.47.247 LEN=64 TOS=0x00 PREC=0x00 TTL=119 ID=32837 DF PROTO=TCP SPT=47663 DPT=445 WINDOW=64380 RES=0x00 SY

Jun  8 21:47:24 (none) user.alert syslog: HTTP log in from LAN: 192.168.0.3


Nothing on your network should have the same ip address!

Server should be 192.168.0.200
router 192.168.0.201
your pc 192.168.0.202

get it??? lol

You are giving yourself IP conflicts!

---

### Post by collisionystm on 2011-06-08
> **junovo said:**
> Yep ur correct:oops: .... i did think that when i sent the last note so i changed it to 192.168.0.200 on both the server and the router and still get the same problem. 

for the /etc/resolv.conf I have nameserver 192.168.0.200 , is that correct ?

also on the server I am unable to browse the internet does that indicate its blocking outbound services ?

log from router if helps 
Jun  8 21:37:16 (none) user.alert kernel: Intrusion -> IN=nas_0_40 OUT= MAC=00:25:69:2d:3e:73:00:07:72:79:ea:21:08:00 SRC=94.255.55.187 DST=94.0.47.247 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=34246 DF PROTO=TCP SPT=16248 DPT=445 WINDOW=65535 RES=0x00 S

Jun  8 21:41:18 (none) user.alert kernel: Intrusion -> IN=nas_0_40 OUT= MAC=00:25:69:2d:3e:73:00:07:72:79:ea:21:08:00 SRC=94.50.168.165 DST=94.0.47.247 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=27090 DF PROTO=TCP SPT=2774 DPT=445 WINDOW=65535 RES=0x00 SY

Jun  8 21:43:41 (none) user.alert kernel: Intrusion -> IN=nas_0_40 OUT= MAC=00:25:69:2d:3e:73:00:07:72:79:ea:21:08:00 SRC=94.76.92.169 DST=94.0.47.247 LEN=64 TOS=0x00 PREC=0x00 TTL=119 ID=32837 DF PROTO=TCP SPT=47663 DPT=445 WINDOW=64380 RES=0x00 SY

Jun  8 21:47:24 (none) user.alert syslog: HTTP log in from LAN: 192.168.0.3


is your router providing DNS? 

If so, yes your /etc/resolv.conf should have nameserver 192.168.0.200 ( or whatever your router is )

then try to ping google.com first ( this will test the dns ) if it fails try

ping 8.8.8.8 ( this is googles public dns server ) if this passes it means you can get out of your network and onto the web. if it fails... well check your ip's again!

---

### Post by junovo on 2011-06-08
> **collisionystm said:**
> Nothing on your network should have the same ip address!

Server should be 192.168.0.200
router 192.168.0.201
your pc 192.168.0.202

get it??? lol

You are giving yourself IP conflicts!

Having changed the ip of the server as i mentioned above,  i don't have conflicting ip's anymore but the problem is still the same.

---

### Post by junovo on 2011-06-08
> **collisionystm said:**
> is your router providing DNS? 

If so, yes your /etc/resolv.conf should have nameserver 192.168.0.200 ( or whatever your router is )

then try to ping google.com first ( this will test the dns ) if it fails try

ping 8.8.8.8 ( this is googles public dns server ) if this passes it means you can get out of your network and onto the web. if it fails... well check your ip's again!

**_server results = _**
administrator@wingu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:d3:23:ba:bf  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:265 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:25560 (25.5 KB)  TX bytes:25560 (25.5 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:00:f3:1d  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:cfff:fe00:f31d/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:483 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:435 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:24007 (24.0 KB)  TX bytes:55263 (55.2 KB) 

administrator@wingu:~$ ping google.com 
ping: unknown host google.com 
administrator@wingu:~$ ping 8.8.8.8 
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.(then just stops)


[B][U]pc on network results 
[/U][/B]
Windows IP Configuration


Ethernet adapter Bluetooth Network:

        Media State . . . . . . . . . . . : Media disconnected

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . : home
        IP Address. . . . . . . . . . . . : 192.168.0.3
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected

---

### Post by collisionystm on 2011-06-08
> **junovo said:**
> **_server results = _**
administrator@wingu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:d3:23:ba:bf  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:265 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:25560 (25.5 KB)  TX bytes:25560 (25.5 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:00:f3:1d  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::216:cfff:fe00:f31d/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:483 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:435 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:24007 (24.0 KB)  TX bytes:55263 (55.2 KB) 

administrator@wingu:~$ ping google.com 
ping: unknown host google.com 
administrator@wingu:~$ ping 8.8.8.8 
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.(then just stops)


[B][U]pc on network results 
[/U][/B]
Windows IP Configuration


Ethernet adapter Bluetooth Network:

        Media State . . . . . . . . . . . : Media disconnected

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . : home
        IP Address. . . . . . . . . . . . : 192.168.0.3
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected


So lets straighten this out.

Correct this if I am wrong
> 
Router = 192.168.0.1
Windows PC = 192.168.0.3
Ubuntu = 192.168.0.200Your Ubuntu /etc/network/interfaces

> # The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.200
        netmask 255.255.255.0
        gateway 192.168.0.1
        broadcast 192.168.255.255Ubuntu /etc/resolv.conf

> nameserver 192.168.0.1Your Windows Machine

open command prompt and do 

```
ipconfig /all
```You should see 

> IP 192.168.0.3
SUB 255.255.255.0
GATE 192.168.0.1
DNS 192.168.0.1yes?

---

### Post by jramshu on 2011-06-08
> **junovo said:**
> 

for the /etc/resolv.conf I have nameserver 192.168.0.200 , is that correct ?



The nameserver should be your routers ip. 192.168.0.1

---

### Post by a2j on 2011-06-09
or you could set your dns to something like 8.8.8.8

now try to ping your server from the workstation. if that works, open a web browser on the workstation and type your servers ip address, did it work?

---

### Post by kimda on 2011-06-09
Try changing your interfaces file into this. Looks like you do not have a route to your gateway.

```

auto lo
iface lo inet loopback

auto eth0

iface eth0 inet static
        address 192.168.0.200
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1
        # dns-search 

```

---

### Post by kb1uab on 2011-06-09
I don't know if this is a stupid reply, but look at the router screenshot. See where you made the rule for the server, the IP address is there, everything looks ok. 

BUT next to that it says 0.0.0.0, that should say ANY (like below it). Your router is never going to let anything in, because there will never be a request from 0.0.0.0, basically making the rule invalid. That is for entering a specific IP to access from the WAN side, same as your only allowing access specific access on your LAN side

---

### Post by junovo on 2011-06-09
> **collisionystm said:**
> So lets straighten this out.

Correct this if I am wrong
Your Ubuntu /etc/network/interfaces

Ubuntu /etc/resolv.conf

Your Windows Machine

open command prompt and do 

```
ipconfig /all
```You should see 

yes?

OK status as follows 

@collisionystm  - all config shown below. on windows machine i get below  (. **** =  personal info) 

Windows IP Configuration

        Host Name . . . . . . . . . . . . : *******
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : ******.COM

Ethernet adapter Bluetooth Network:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Bluetooth LAN Access Server Driver
        Physical Address. . . . . . . . . : 5C-AC-4C-C1-A4-87

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . : home
        Description . . . . . . . . . . . : Intel(R) Centrino(R) Advanced-N 62
 AGN
        Physical Address. . . . . . . . . : 58-94-6B-2E-12-10
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.2 (changed as rebooted router)
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
        Lease Obtained. . . . . . . . . . : 09 June 2011 17:09:25
        Lease Expires . . . . . . . . . . : 10 June 2011 17:09:25

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Intel(R) 82577LM Gigabit Network C
nection
        Physical Address. . . . . . . . . : F0-DE-F1-29-61-B0

Ethernet adapter AGN Virtual Network Adapter:

        Connection-specific DNS Suffix  . : *****.com
        Description . . . . . . . . . . . : AGN Virtual Network Adapter
        Physical Address. . . . . . . . . : 02-50-F2-00-00-05
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 9.79.4.117
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :
        DNS Servers . . . . . . . . . . . : 9.64.162.21
                                            9.64.163.21



@a2j I tried the 8.8.8.8 but still would not ping on the server 192.168.0.200
C:\Documents and Settings\Administrator>ping 192.168.0.200
Pinging 192.168.0.200 with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.
Ping statistics for 192.168.0.200:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),


@kimda I changed the settings as shown below. still no luck 

@kb1uab When checking on how to set up the router it mentions to leave the fields as they are see following 
[http://www.skyuser.co.uk/forum/sky-broadband-tutorial-section/10975-how-set-up-port-forwarding-internal-web-server.html](http://www.skyuser.co.uk/forum/sky-broadband-tutorial-section/10975-how-set-up-port-forwarding-internal-web-server.html)


Thanks to all for the help so far :). Could the problem not able to connect from local workstation be > [http://www.dyndns.com/support/kb/loopback_connections.html](http://www.dyndns.com/support/kb/loopback_connections.html)

but this does not explain the access from internet !!

Current config on server ----
/etc/resolv.conf is :
# Generated by NetworkManager 
domain home 
search home 
nameserver 192.168.0.1 
~                                                                               
~                   

/etc/network/interfaces :
# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5). 

# The loopback network interface 
auto lo 
iface lo inet loopback 

# The primary network interface 
#auto eth0 
#iface eth0 inet dhcp 

auto eth0 
iface eth0 inet static 
address 192.168.0.200 
netmask 255.255.255.0 
network 192.168.0.1 
broadcast 192.168.0.255 
gateway 192.168.0.1 
# dns-* options are implemented by the reslovconf package, if installed 
dns-nameservers 192.168.0.1 
# dns-search 
~                            


message on server when [http://192.168.0.200/](http://192.168.0.200/) on web browser
It works!
This is the default web page for this server.
The web server software is running but no content has been added, yet.

---

### Post by a2j on 2011-06-09
you need to make sure that your server can be accessed internally before you try anything from the "outside", like port forwarding, etc...

---

### Post by OM NOM NOM on 2011-06-09
If your server can't browse the internet then try setting your DNS to an OpenDNS server, like 4.2.2.2. Maybe your router doesn't handle DNS requests for static IPs.

---

### Post by kb1uab on 2011-06-09
Ok, this is bothering me now.


Does the machine have internet access?

I see two adapters, wireless and wired, but I only see one (eth0) being configured, and your reports show ethernet adapter disconnected.

I think it needs to be configured as wlan0 if its on a wireless card.

---

### Post by junovo on 2011-06-09
> **kb1uab said:**
> Ok, this is bothering me now.


Does the machine have internet access?

I see two adapters, wireless and wired, but I only see one (eth0) being configured, and your reports show ethernet adapter disconnected.

I think it needs to be configured as wlan0 if its on a wireless card.

IT WORKS !!!! ..... thank you kb1uab \\:D/ it was the wlan0 that needed to be given not eth0. now I can see the server from my workstation. 

Thank you ALL for your help . Sorry have messed everyone around but am still learning.

---

### Post by kb1uab on 2011-06-09
Hey, you welcome, thats why we're all here. I myself don't have a ton of experience, but I did a setup on a backtrack machine that had a wired and wireless setup and I remember it was not friendly trying to get them to work.

All I did was search for 'ubuntu interfaces wireless' and peeked at others configs, and saw that WLAN0 keep showing up.

Words of advice to all, be a copy-cat and ask questions and questions. More than likely your not the first person to have run into the wall your at. I love that everyone posts shots of there error logs, configuration files and reports. This is what has helped me through most of my Linux trip. Some might argue that it doesn't help you learn, but I disagree. Books are great, but real world experience sticks like glue.

Keep coming back, read others posts, and reply when you can.

---

### Post by junovo on 2011-06-09
spoke too soon ... it was working fine then I rebooted the server and for some reason my static ip is not sticking. It is giving a DHCP address inet addr:192.168.0.7 but I still have the same cofig as before. 

Looking at some posts its advised to sudo apt-get remove dhcp-client but get 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'dhcp-client' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

Any ideas why it would ignore /etc/network/interfaces ?

---

### Post by jramshu on 2011-06-09
Not sure why it's not sticking but I do see "10 not upgraded." From what I remember dhcp-client has had some upgrades recently, so you may want to upgrade those. 

Sorry for not catching the wireless config, I thought you where hard wired.

EDIT: Did you change your /etc/network/interfaces to reflect wlan setup instead of eth0?

---

### Post by junovo on 2011-06-10
> **jramshu said:**
> Not sure why it's not sticking but I do see "10  not upgraded." From what I remember dhcp-client has had some upgrades  recently, so you may want to upgrade those. 

Sorry for not catching the wireless config, I thought you where hard wired.

EDIT: Did you change your /etc/network/interfaces to reflect wlan setup instead of eth0?

Yep ur correct I had not changed the iface part below to wlan0 and  it worked however it gives another problem. When I changed it everything  was connected ok but when i reboot it does not connect to my router ie  no signal. Somewhere during the boot up it needs to login to the router  but does not. If I change the iface wlan0 inet static back to iface eth0  inet static it finds my router when boot up. Are there some further  lines I need to add to the  /etc/network/interfaces to allow login to router . 

auto wlan0
iface wlan0 inet static
address 192.168.0.200
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255
gateway 192.168.0.1
# dns-* options are implemented by the reslovconf package, if installed
dns-nameservers 192.168.0.1
# dns-search

---

### Post by kb1uab on 2011-06-10
Ok, first try setting the unit up as dhcp, see if that works consistently.

Second, you network 192.168.0.1 try changing it to 192.168.0.0. All the examples I see the network ends in 0, gateway ends in 1. I don't understand why it would have worked restarting the service but not the machine. Let me know.

---

### Post by kb1uab on 2011-06-10
Found this here. Make sure wlan0 is the device your concerned with (should be, it worked before)

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)


# Set up the internal wireless network
#
# Don't forget to change wlan0 to the proper name of the internal
# wireless network interface if applicable.
#
# If you would like to use WEP, uncomment the line 'wireless-key'
# and replace '<key goes here>' with a WEP key.
#
# You may also change the network essid and channel.
#
auto wlan0
iface wlan0 inet static

wireless-mode master   <--- I don't think you need this
wireless-essid "UbuntuWireless" <--- Tell it which ssid to connect to
wireless-channel 1
#wireless-key <key goes here>   <--- If required
address 192.168.0.1
network 192.168.0.0   <--- Like I mentioned before, they seem to end in 0
netmask 255.255.255.0
broadcast 192.168.0.255

There seem to be various ways to do this, but I always include the 5th remark "gateway". This example looks like the unit would be stand alone, but then again, its an example.

---

