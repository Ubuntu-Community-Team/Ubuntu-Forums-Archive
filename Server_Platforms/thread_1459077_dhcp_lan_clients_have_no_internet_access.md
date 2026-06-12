---
title: "dhcp lan clients have no internet access"
date: 2010-04-20
forum: Server Platforms
---

### Post by pavel989 on 2010-04-20
alright so i set up dhcp server and my clients are getting ip's, can ping each other, and can ping/ssh the server. but nowhere beyond that.

however if i ping an externel site, i get its IP addr, but no pings (100% loss)

im ripping my hair out over this. i know that iptables is right, but i dont know about dns

idk if this helps:

```
pavel@ubuntu-server:~$ cat /etc/network/interfaces
auto lo br0 eth0 eth1
iface lo inet loopback

#mapping hotplug
#        script grep
#        map eth0
 
iface br0 inet dhcp
	bridge_ports eth0

iface eth0 inet manual
	up ifconfig $IFACE 0.0.0.0 up
	up ip link set $IFACE promisc on
	down ip link set $IFACE promisc off
	down ifconfig $IFACE down 
	post-up iptables-restore < /etc/iptables.up.rules

iface eth1 inet static
	address 192.168.5.1
	netmask 255.255.255.0
	broadcast 192.168.5.255
	network 192.168.5.0
pavel@ubuntu-server:~$ cat /etc/resolv.conf 
domain Alla
search Alla
nameserver 192.168.2.1
nameserver 192.168.0.1
pavel@ubuntu-server:~$ 

```

FOR THE RECORD THOUGH:
i plan on this being my internet gateway but my isp does dynamic ip's.

is there a way to make this update on its own?

---

### Post by Ryan Dwyer on 2010-04-21
You need to set the gateway on the server to your modem's IP address (or the IP address of whatever device it should send to in order to get out).

You also need to enable net.ipv4.ip_forward in /etc/sysctl.conf so that server will forward packets. And make sure your DHCP config on the server is sending its own IP address as a gateway address.

Having a dynamic IP shouldn't affect it.

---

### Post by pavel989 on 2010-04-21
> **Ryan Dwyer said:**
> You need to set the gateway on the server to your modem's IP address (or the IP address of whatever device it should send to in order to get out).

You also need to enable net.ipv4.ip_forward in /etc/sysctl.conf so that server will forward packets. And make sure your DHCP config on the server is sending its own IP address as a gateway address.

Having a dynamic IP shouldn't affect it.

well the thing is that my modem doesnt really have an addr. i have FIOS. so when i connect a router, it gets an IP from the DNS, so i dont know if i can find out the ip of my modem.

but either way, right now, the gateway is behind a router who's ip address i do know. i did edit sysctl.conf and im not sure about my dhcp and if its sending its ip as a gateway, but im almost positive i did tell it to somewhere.

for the record i have webmin installed

---

### Post by mockingbird on 2010-04-21
I know in windows you can get the gateway by typing "ipconfig /all".  In Linux you must be able to do it with ifconfig.

---

### Post by pavel989 on 2010-04-21
i tried ifconfig -a

didnt get much. ima keep lookin for it

---

### Post by tumandro on 2010-04-21
To get the gateway in linux you just use the command: route. Did you put the default gateway in your dhcp configuration?

---

### Post by Iowan on 2010-04-21
I won't merge the threads (yet), but for reference to those assisting, [here]("http://ubuntuforums.org/showthread.php?t=1452648") is a previous thread leading up to this one... :)
Toward the end, there's a question about whether or not **br0** is working (or necessary?). Which version is this server (8.04, 9.10, etc)?

---

### Post by pavel989 on 2010-04-21
br0 is for openvpn. 

am i supposed to bridge my to eth cards?

9.10

---

### Post by capscrew on 2010-04-21
> **pavel989 said:**
> br0 is for openvpn. 

am i supposed to bridge my to eth cards?

Pavel,

If you have 2 (or more) NIC's in a host you have the physical parts to create a router.  I believe this is what you are trying to do.  Is the physical topology is like this:  ```
FIOS-->eth0<Ubuntu Gateway>eth1<-- network
```

If this is so then you need to setup the router with forwarding from the inside network (eth1) to the outside (eth0).

The proper method is available [**_here_**]("https://help.ubuntu.com/community/Router").  As you are creating the router you need to add DHCP services for the inside network.  I would use DNSMasq for this as you can also set up DNS for the inside network at the same time.

As you say bridging is not for this it is for OpenVPN if you are going to use that later.

Edit: The term gatway refers to the *nearside*interface to the network.  In this case that is eth1.  For the other hosts on the network, the IP address or this interface is the gateway address.  Please note that the router it self has not gateway address as it is handing the data (packets) off to the FIOS network.  You will have a public address on the eth0.  You can get this by using this website:[http://www.whatsmyip.org/]("http://www.whatsmyip.org/")

---

### Post by pavel989 on 2010-04-21
> **capscrew said:**
> Pavel,

If you have 2 (or more) NIC's in a host you have the physical parts to create a router.  I believe this is what you are trying to do.  Is the physical topology is like this:  ```
FIOS-->eth0<Ubuntu Gateway>eth1<-- network
```

If this is so then you need to setup the router with forwarding from the inside network (eth1) to the outside (eth0).

The proper method is available [**_here_**]("https://help.ubuntu.com/community/Router").  As you are creating the router you need to add DHCP services for the inside network.  I would use DNSMasq for this as you can also set up DNS for the inside network at the same time.

As you say bridging is not for this it is for OpenVPN if you are going to use that later.

yep correct.

well for the most part i have done all this through other guides.
i have dhcp3 server and bind9 installed with webmin for dns and dhcp

---

### Post by capscrew on 2010-04-21
> **pavel989 said:**
> yep correct.

well for the most part i have done all this through other guides.
i have dhcp3 server and bind9 installed with webmin for dns and dhcp

So you are saying that the router is now setup correctly and you are providing DHCP and DNS services to you LAN.  Can you provide us with the configuration of one of the hosts on the LAN?

You do NOT need to provide DHCP to the WAN side interface.  FIOS will do that part.

---

### Post by pavel989 on 2010-04-21
> **capscrew said:**
> So you are saying that the router is now setup correctly and you are providing DHCP and DNS services to you LAN.  Can you provide us with the configuration of one of the hosts on the LAN?

You do NOT need to provide DHCP to the WAN side interface.  FIOS will do that part.

yeah its getting dhcp and dns

which config?

---

### Post by capscrew on 2010-04-21
> **pavel989 said:**
> yeah its getting dhcp and dns
???  What's getting dhcp and dns.  Can you be more specific.> 

which config?

I am looking to see the end results of your configuration of the router/dns/dhcp.  How many hosts are on the LAN (not the router)?  Show me results of one of the interface configurations such as ```
ifconfig -a
```.

---

### Post by pavel989 on 2010-04-22
> **capscrew said:**
> ???  What's getting dhcp and dns.  Can you be more specific.

I am looking to see the end results of your configuration of the router/dns/dhcp.  How many hosts are on the LAN (not the router)?  Show me results of one of the interface configurations such as ```
ifconfig -a
```.

it being computers on my LAN. right now there is just one computer:
```
pavel@pavel-netbook:/etc/network$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:5a:4c:69:fc  
          inet addr:192.168.5.108  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:fe4c:69fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10467 errors:0 dropped:0 overruns:0 carrier:23
          collisions:0 txqueuelen:1000 
          RX bytes:208031 (208.0 KB)  TX bytes:989943 (989.9 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75769 (75.7 KB)  TX bytes:75769 (75.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:4d:65:46  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:19198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14859 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19645772 (19.6 MB)  TX bytes:1880163 (1.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-4D-65-46-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pavel@pavel-netbook:/etc/network$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.5.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.5.1     0.0.0.0         UG    0      0        0 eth0
pavel@pavel-netbook:/etc/network$ 

```

---

### Post by capscrew on 2010-04-22
> **pavel989 said:**
> it being computers on my LAN. right now there is just one computer...


The router seems to be setup correctly for everything but the external interface (eth0).  Your configuration of eth0 looks strange:```
[I][COLOR="blue"]iface eth0 inet manual
	up ifconfig $IFACE 0.0.0.0 up
	up ip link set $IFACE promisc on
	down ip link set $IFACE promisc off
	down ifconfig $IFACE down 
	post-up iptables-restore < /etc/iptables.up.rules
[/COLOR][/I]
```

In all FIOS installs that I have seen an [**_ActionTec _**]("http://www.actiontec.com/products/product.php?pid=189")router is connected to the ONT (Optical Network Termination).  The ONT is the media converter and should provide your router an Ethernet connection with a FIOS supplied (via their DHCP) IP address for eth0.  Just as it would for the ActionTec.

Why do you have the eth0 interface configured as you do?  Are you using the ActionTec router or are you attempting to replace it?  Could you use this topology?```
FIOS<--->ActionTec<-->Ubuntu Gateway<-->Netbook
```

---

### Post by pavel989 on 2010-04-22
> **capscrew said:**
> The router seems to be setup correctly for everything but the external interface (eth0).  Your configuration of eth0 looks strange:```
[I][COLOR="blue"]iface eth0 inet manual
	up ifconfig $IFACE 0.0.0.0 up
	up ip link set $IFACE promisc on
	down ip link set $IFACE promisc off
	down ifconfig $IFACE down 
	post-up iptables-restore < /etc/iptables.up.rules
[/COLOR][/I]
```

In all FIOS installs that I have seen an [**_ActionTec _**]("http://www.actiontec.com/products/product.php?pid=189")router is connected to the ONT (Optical Network Termination).  The ONT is the media converter and should provide your router an Ethernet connection with a FIOS supplied (via their DHCP) IP address for eth0.  Just as it would for the ActionTec.

Why do you have the eth0 interface configured as you do?  Are you using the ActionTec router or are you attempting to replace it?  Could you use this topology?```
FIOS<--->ActionTec<-->Ubuntu Gateway<-->Netbook
```


```
FIOS<--->2 routers<-->Ubuntu Gateway<-->Netbook
```

im trying to make it
```
FIOS<-->Ubuntu Gateway<-->switch<--->Netbook
```

---

### Post by capscrew on 2010-04-22
> **pavel989 said:**
> ```
FIOS<--->2 routers<-->Ubuntu Gateway<-->Netbook
```

Explain it. What do you mean by *2 routers*?> 

im trying to make it
```
FIOS<-->Ubuntu Gateway<-->switch<--->Netbook
```
No comments on your incorrectly configured WAN connection (by my interpretation)?

---

### Post by pavel989 on 2010-04-22
btw...
im also making this a wireless router.
is there a way to have the wireless and wired on the same subnet?

---

### Post by capscrew on 2010-04-22
> **pavel989 said:**
> btw...
im also making this a wireless router.
is there a way to have the wireless and wired on the same subnet?

Wireless is possible on the same subnet as wired. 

How about you get the router (Ubuntu Gateway) to work first?

---

### Post by pavel989 on 2010-04-22
> **capscrew said:**
> Explain it. What do you mean by *2 routers*?
No comments on your incorrectly configured WAN connection (by my interpretation)?

the fios modem connects toa router, which connects to another, and finally my gateway.

and i am going to get wired working first. just wanted to throw in a quick q.

and to explain my goal, i want the gateway to connect to a switch to serve as the gatway for my LAN

---

### Post by capscrew on 2010-04-22
> **pavel989 said:**
> the fios modem connects to a router, which connects to another, and finally my gateway.


Not very clear.  Do we have this?
```
FIOS--router1--router2--gateway--switch--netbook
```
How about some Brand/model# on each device (e.g. FIOS modem, router1, router2)
> 

and i am going to get wired working first. just wanted to throw in a quick q.

and to explain my goal, i want the gateway to connect to a switch to serve as the gatway for my LAN

Why do you want the gateway? Are you just experimenting or do you have a specific need to isolate your LAN?  What is the purpose of  router1 and router2?

---

### Post by pavel989 on 2010-04-22
> **capscrew said:**
> Not very clear.  Do we have this?
```
FIOS--router1--router2--gateway--switch--netbook
```
How about some Brand/model# on each device (e.g. FIOS modem, router1, router2)


Why do you want the gateway? Are you just experimenting or do you have a specific need to isolate your LAN?  What is the purpose of  router1 and router2?

correct that is how my network is set up.  i know theres nothing wrong with the routers cuz my internet works thru the routers. but its some version of wrt54g on the first, so im guessing its a linksys (its somewhere in the garage) and a belkin N1.

and yeah this is experimenting and i wanted to make my lan more effecient since i have a buncha computers connected and multiple routing tables.

plus ima bridge a dd-wrt(which i have done be4) to this gateway so i can get live on my 360

---

### Post by capscrew on 2010-04-22
> **pavel989 said:**
> correct that is how my network is set up.  i know theres nothing wrong with the routers cuz my internet works thru the routers. but its some version of wrt54g on the first, so im guessing its a linksys (its somewhere in the garage) and a belkin N1.

I'm almost afraid to ask...but what the hell.  Is the router that is "*somewhere in the garage*" up and running in the network?

I'm gunna guess yes.
> 

and yeah this is experimenting and i wanted to make my lan more effecient since i have a buncha computers connected and multiple routing tables.

Not sure what you mean, but okay...if you say so.
> 


plus ima bridge a dd-wrt(which i have done be4) to this gateway so i can get live on my 360
Yeah!

So now how do we do this?

I keep asking for specifics, computers like that sorta s**t, and all I get is generalities.  I guess the best we can do is:  you ask a specific question (stay focused now) on the subject at hand  (configuring ur gateway) and I'll answer it.  On the other hand I could ask you to explain (I did ask this b4, didn't I?) why u config'd your eth0 port the way you did.  I mean WTF is this?  ](*,)```
[COLOR="Blue"]iface eth0 inet manual
	up ifconfig $IFACE 0.0.0.0 up
	up ip link set $IFACE promisc on
	down ip link set $IFACE promisc off
	down ifconfig $IFACE down 
	post-up iptables-restore < /etc/iptables.up.rules[/COLOR]
```

---

### Post by pavel989 on 2010-04-23
> **capscrew said:**
> I'm almost afraid to ask...but what the hell.  Is the router that is "*somewhere in the garage*" up and running in the network?

I'm gunna guess yes.

Not sure what you mean, but okay...if you say so.

Yeah!

So now how do we do this?

I keep asking for specifics, computers like that sorta s**t, and all I get is generalities.  I guess the best we can do is:  you ask a specific question (stay focused now) on the subject at hand  (configuring ur gateway) and I'll answer it.  On the other hand I could ask you to explain (I did ask this b4, didn't I?) why u config'd your eth0 port the way you did.  I mean WTF is this?  ](*,)```
[COLOR="Blue"]iface eth0 inet manual
	up ifconfig $IFACE 0.0.0.0 up
	up ip link set $IFACE promisc on
	down ip link set $IFACE promisc off
	down ifconfig $IFACE down 
	post-up iptables-restore < /etc/iptables.up.rules[/COLOR]
```

well yeah the router in the garage is working. and what i meant is that my network is ugly. to each router there are computers connected and each router port forwards. so basically i wanna make 1 single router and have the port forward for my entitre network.

to explain the eth0 config. be4 i decided to make this computer a gateway, i had it set up as an openvpn and squid server.

and i followed some guides to set up the bridge. i get everything in the interfaces document, except for the eth0 config tbh. i dont get what that crap meant, but it worked. so i left it

---

### Post by capscrew on 2010-04-23
> **pavel989 said:**
> well yeah the router in the garage is working. and what i meant is that my network is ugly. to each router there are computers connected and each router port forwards. so basically i wanna make 1 single router and have the port forward for my entitre network.

That make sense.  If I get yer drift u wanna hook all the 'puters up to only 1 router. One side (wan) connects to FIOS and the 'puters connect on the other ports.

One BIG prob.  **The first device (yr modem) is probably a router (gateway/whatever u want to call it).**  **[SIZE="3"]Is it an ActionTec?[/SIZE]**

I ask because **there has to be a way to convert the media from the FIOS ONT to  Ethernet **(along with providing the IP addr.)
> 

to explain the eth0 config. be4 i decided to make this computer a gateway, i had it set up as an openvpn and squid server.

and i followed some guides to set up the bridge. i get everything in the interfaces document, except for the eth0 config tbh. i dont get what that crap meant, but it worked. so i left it
Well that won't work!  There's no magic here.  You need to connect 2 nets together with ur gateway.  

So lets think here for a minute...  The Inside net (eht1 (192.168.5.0/24)) needs to forward packets to the eth0 interface and on to the next router.  To do this the eth0 interface needs to be in the ip network of the next router.  [COLOR="Red"]**_What is the network of the next router upstream?_**[/COLOR].  Look at this diagram:```

netbook<-[COLOR="Blue"]192.168.15.5[/COLOR]->switch<-[COLOR="Blue"]192.168.5.1[/COLOR]->[COLOR="Blue"]<eth1>[/COLOR]ur gateway[COLOR="Red"]<eth0>[/COLOR]<- [COLOR="Red"]**What network is this?**[/COLOR]->router2

```
**Is there a DHCP server in the *next *network upstream of your LAN that eth0 can get an IP addr from?**

---

### Post by pavel989 on 2010-04-24
well yeah the top level router connects to some modem setup and recieves an ip from externel dhcp servers. our actiontec got screwedup.

---

### Post by capscrew on 2010-04-24
> **pavel989 said:**
> well yeah the top level router connects to some modem setup and recieves an ip from externel dhcp servers. our actiontec got screwedup.

We seem to be slowly going in big circles.  We are getting nowhere. The thread needs to move to a logical end.  Please answer my other 2 questions.

---

### Post by pavel989 on 2010-04-25
> **capscrew said:**
> That make sense.  If I get yer drift u wanna hook all the 'puters up to only 1 router. One side (wan) connects to FIOS and the 'puters connect on the other ports.

One BIG prob.  **The first device (yr modem) is probably a router (gateway/whatever u want to call it).**  **[SIZE="3"]Is it an ActionTec?[/SIZE]**

I ask because **there has to be a way to convert the media from the FIOS ONT to  Ethernet **(along with providing the IP addr.)

Well that won't work!  There's no magic here.  You need to connect 2 nets together with ur gateway.  

So lets think here for a minute...  The Inside net (eht1 (192.168.5.0/24)) needs to forward packets to the eth0 interface and on to the next router.  To do this the eth0 interface needs to be in the ip network of the next router.  [COLOR="Red"]**_What is the network of the next router upstream?_**[/COLOR].  Look at this diagram:```

netbook<-[COLOR="Blue"]192.168.15.5[/COLOR]->switch<-[COLOR="Blue"]192.168.5.1[/COLOR]->[COLOR="Blue"]<eth1>[/COLOR]ur gateway[COLOR="Red"]<eth0>[/COLOR]<- [COLOR="Red"]**What network is this?**[/COLOR]->router2

```
**Is there a DHCP server in the *next *network upstream of your LAN that eth0 can get an IP addr from?**


sorry i havent had time to really sit down and answer, ive been mostly responding from my phone.

anyways... there is NO actiontec router in the picture.
to simplify this, ima write out as best i can, the entire network. here goes

---

### Post by capscrew on 2010-04-25
> **pavel989 said:**
> sorry i havent had time to really sit down and answer, ive been mostly responding from my phone.

anyways... there is NO actiontec router in the picture.
to simplify this, ima write out as best i can, the entire network. here goes

When you have time to get serious we can finish this.  You still haven't answered my last 2 questions.

I have modified your drawing (see my drawing).  This may help you visualize what I need to know.  The colors are the same in the drawing as what I used for eth0 and eth1.

---

### Post by pavel989 on 2010-04-25
the gateway's eth0 is on the subnet which the belkin n1 servers to. meaning my desktop, vonage, laptop, and the gateway are on the same subnet. the wrt54g serves to the media center and the belkin n1 on a different subnet. the wrt54g receives an ip from or through the modem

---

### Post by capscrew on 2010-04-25
> **pavel989 said:**
> the gateway's eth0 is on the subnet which the belkin n1 servers to. meaning my desktop, vonage, laptop, and the gateway are on the same subnet. the wrt54g serves to the media center and the belkin n1 on a different subnet. the wrt54g receives an ip from or through the modem

That's obvious.  What I need is the IP number of the Red (eth0) network.  And the answer to the other question (DHCP server) is...

---

### Post by pavel989 on 2010-04-25
> **capscrew said:**
> That's obvious.  What I need is the IP number of the Red (eth0) network.  And the answer to the other question (DHCP server) is...

my understanding is ur asking about the gateway, its eth0/br0 is 192.168.2.7

and its eth1 is 192.168.5.1

and im not sure what ur other qustion is. i scrolled back thru the posts and im not sure. i tihnk what your asking is if there are any dhcp servers above the gateway, and well yes there are. each router is serving ip address on different subnets, so i guess they count as dhcp servers

---

### Post by capscrew on 2010-04-25
> **pavel989 said:**
> my understanding is ur asking about the gateway, its eth0/br0 is 192.168.2.7 and its eth1 is 192.168.5.1

Yes we are talking about ur gateway.

Did you change the IP address on eth0 to 192.168.2.7?  The last I heard it was this:```
[COLOR="Red"]iface eth0[/COLOR] inet manual
	up ifconfig $IFACE 0.0.0.0 up
	up ip link set $IFACE promisc on
	down ip link set $IFACE promisc off
	down ifconfig $IFACE down 
	post-up iptables-restore < /etc/iptables.up.rules
```

> 

... im not sure what ur other qustion is. i scrolled back thru the posts and im not sure. i tihnk what your asking is if there are any dhcp servers above the gateway, and well yes there are. each router is serving ip address on different subnets, so i guess they count as dhcp servers
Look carefully at my diagram.  I asked about a DHCP server (yes, it is in the router) in the red network (192.168.2.0/24  **???**) because your can configure eth0 to receive its address via DHCP if you want.

It is important that you understand that each router is the gateway to the network upstream of it.  The **Ubuntu gateway** is the gateway for the [COLOR="Blue"]blue network[/COLOR] to the [COLOR="Red"]red network[/COLOR].  The Belkin is the gateway for the red network to the green.  The gateway interface in any network is always the interface that has a IP address *_in _* the LAN that it services.

In your case, the Ubuntu services the blue network and the Belkin services the red network.

Anther way to look at it is that the Ubuntu has an interface that is connected to the red network as well as servicing the blue network.  All gateways (routers) manage IP traffic between 2 networks.

[COLOR="Red"][SIZE="3"]We need to configure eth0 to have an IP address in the range of the RED NETWORK.[/SIZE][/COLOR]

[SIZE="3"][B]Is the red network 192.168.2.0?  

What is the IP address of your desktop (My Desktop in the diagram)?[/B][/SIZE]

---

### Post by pavel989 on 2010-04-25
> **capscrew said:**
> Yes we are talking about ur gateway.

Did you change the IP address on eth0 to 192.168.2.7?  The last I heard it was this:```
[COLOR="Red"]iface eth0[/COLOR] inet manual
	up ifconfig $IFACE 0.0.0.0 up
	up ip link set $IFACE promisc on
	down ip link set $IFACE promisc off
	down ifconfig $IFACE down 
	post-up iptables-restore < /etc/iptables.up.rules
```


Look carefully at my diagram.  I asked about a DHCP server (yes, it is in the router) in the red network (192.168.2.0/24  **???**) because your can configure eth0 to receive its address via DHCP if you want.

It is important that you understand that each router is the gateway to the network upstream of it.  The **Ubuntu gateway** is the gateway for the [COLOR="Blue"]blue network[/COLOR] to the [COLOR="Red"]red network[/COLOR].  The Belkin is the gateway for the red network to the green.  The gateway interface in any network is always the interface that has a IP address *_in _* the LAN that it services.

In your case, the Ubuntu services the blue network and the Belkin services the red network.

Anther way to look at it is that the Ubuntu has an interface that is connected to the red network as well as servicing the blue network.  All gateways (routers) manage IP traffic between 2 networks.

[COLOR="Red"][SIZE="3"]We need to configure eth0 to have an IP address in the range of the RED NETWORK.[/SIZE][/COLOR]

[SIZE="3"][B]Is the red network 192.168.2.0?  

What is the IP address of your desktop (My Desktop in the diagram)?[/B][/SIZE]


well the thing is, br0 is set to get its IP via dhcp from the belkin n1, and br0 is bridge to eth0. so i  guess i really dunno what eth0 does, but id assume that i have to treat eth0 as br0, and thus id say that eth0 is in the 192.168.2.0 subnet

so yes, eth0 is by that rule, in the red network

in case you wanna look at it, heres the guide i used to set up my bridge for openvpn: [https://help.ubuntu.com/community/OpenVPN]("https://help.ubuntu.com/community/OpenVPN")

---

### Post by capscrew on 2010-04-25
> **pavel989 said:**
> well the thing is, br0 is set to get its IP via dhcp from the belkin n1, and br0 is bridge to eth0. so i  guess i really dunno what eth0 does, but id assume that i have to treat eth0 as br0, and thus id say that eth0 is in the 192.168.2.0 subnet

so yes, eth0 is by that rule, in the red network

in case you wanna look at it, heres the guide i used to set up my bridge for openvpn: [https://help.ubuntu.com/community/OpenVPN]("https://help.ubuntu.com/community/OpenVPN")

Provide me with info from your gateway using:```
ifconfig -a
```

Is the bridge the way u connect to the DD-WRT?

---

### Post by pavel989 on 2010-04-26
```
pavel@ubuntu-server:~$ ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:0d:88:44:04:ab  
          inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fe44:4ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48175 (48.1 KB)  TX bytes:7853 (7.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:0d:88:44:04:ab  
          inet6 addr: fe80::20d:88ff:fe44:4ab/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51607 (51.6 KB)  TX bytes:7965 (7.9 KB)
          Interrupt:10 Base address:0xf400 

eth1      Link encap:Ethernet  HWaddr 00:20:78:11:44:ec  
          inet addr:192.168.5.1  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::220:78ff:fe11:44ec/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xf800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3017 (3.0 KB)  TX bytes:3017 (3.0 KB)

tap0      Link encap:Ethernet  HWaddr ea:9a:47:d4:fa:7a  
          inet6 addr: fe80::e89a:47ff:fed4:fa7a/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:44262 (44.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:08:54:96:e4:26  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Memory:d0820400-d0820500 

pavel@ubuntu-server:~$ 

```

yeah, via br0/eth0 i connect to the dd-wrt switch

---

### Post by capscrew on 2010-04-26
> **pavel989 said:**
> ...

yeah, via br0/eth0 i connect to the dd-wrt switch

The config is completely wrong. If only for the time being, you need to connect directly to the Belkin router.  The only interfaces should be lo (for the loopback) and eth0 for connectivity with the Belkin and eth1 for connectivity with the netbook.

Later, once you have this working you can ADD the bridging.  It is never instead of an IP address.

The loopback is okay as you have it.

The eh1 is incorrect it should not be link local. It should look like this:```

eth1      Link encap:Ethernet  HWaddr 00:20:78:11:44:ec
          [COLOR="Blue"]inet addr:192.168.5.1  Bcast:192.168.5.255  Mask:255.255.255.0[/COLOR]
          inet6 addr: fe80::220:78ff:fe11:44ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12908 (12.6 KB)  TX bytes:22314 (21.7 KB)
          Interrupt:11 Base address:0xc800
```

The eth0 is also wrong for what we need.  The interface shuld be setup with an IP address in the range of the 192.168.2.0/24 network.  This can be an IP address set statically (not with DHCP).  If we do this way then we need to use an address that is **_[COLOR="DarkRed"]NOT [/COLOR]_**in the range of the DHCP pool of addresses.  It should look like the one above, except the [COLOR="Red"]HWaddr [/COLOR]address will be different and the           [COLOR="Red"]inet addr: and  Bcast:[/COLOR] will be different.

No LINK LOCAL, no Bridge, no tun, no tap, and no wan0.

Do you know how to set this up using **/etc/network/interfaces** and **/etc/resolve**?  You will also need **route** to set the default gateway for the eth0 interface (The GW for eth0 is the Belkin addr).

To sum it up you need to [LIST]
[*]Connect the Ubuntu gateway to the one of the Belkin ports
[*]Reconfigure the eth0 and eth1 interfaces 
[*]Set the nameservers for both interfaces 
[*]Set the default gateway for the **_eth0_** interface
[/LIST]

I am not sure if you have the gateway setup to forward packets or NAT correctly so you have to check that out too.

---

### Post by pavel989 on 2010-04-26
> **capscrew said:**
> The config is completely wrong. If only for the time being, you need to connect directly to the Belkin router.  The only interfaces should be lo (for the loopback) and eth0 for connectivity with the Belkin and eth1 for connectivity with the netbook.

Later, once you have this working you can ADD the bridging.  It is never instead of an IP address.

The loopback is okay as you have it.

The eh1 is incorrect it should not be link local. It should look like this:```

eth1      Link encap:Ethernet  HWaddr 00:20:78:11:44:ec
          [COLOR="Blue"]inet addr:192.168.5.1  Bcast:192.168.5.255  Mask:255.255.255.0[/COLOR]
          inet6 addr: fe80::220:78ff:fe11:44ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12908 (12.6 KB)  TX bytes:22314 (21.7 KB)
          Interrupt:11 Base address:0xc800
```

The eth0 is also wrong for what we need.  The interface shuld be setup with an IP address in the range of the 192.168.2.0/24 network.  This can be an IP address set statically (not with DHCP).  If we do this way then we need to use an address that is **_[COLOR="DarkRed"]NOT [/COLOR]_**in the range of the DHCP pool of addresses.  It should look like the one above, except the [COLOR="Red"]HWaddr [/COLOR]address will be different and the           [COLOR="Red"]inet addr: and  Bcast:[/COLOR] will be different.

No LINK LOCAL, no Bridge, no tun, no tap, and no wan0.

Do you know how to set this up using **/etc/network/interfaces** and **/etc/resolve**?  You will also need **route** to set the default gateway for the eth0 interface (The GW for eth0 is the Belkin addr).

To sum it up you need to [LIST]
[*]Connect the Ubuntu gateway to the one of the Belkin ports
[*]Reconfigure the eth0 and eth1 interfaces 
[*]Set the nameservers for both interfaces 
[*]Set the default gateway for the **_eth0_** interface
[/LIST]

I am not sure if you have the gateway setup to forward packets or NAT correctly so you have to check that out too.


im confused, i dont see what you changed for eth1.

but yeah i know i shouldve configd it with no bridging or wireless, but i did everything out of order to begin with.

i know how to edit /etc/network/interfaces but idk much about /etc/resolve

i did  a route and setup packet forwarding in /etc/sysctl.conf

---

### Post by capscrew on 2010-04-26
> **pavel989 said:**
> im confused, i dont see what you changed 
for eth1.


Ur right.  I thought I saw a link local on the the in interface.  It's good just the way it is. 

> 

but yeah i know i shouldve configd it with no bridging or wireless, but i did everything out of order to begin with.


Everyone is entitled to mess with there own system, but there should be a kind of path to getting every thing working.  I go from simple to more complex.  That way if something f**ks up I know what to fix.
> 

i know how to edit /etc/network/interfaces but idk much about /etc/resolve

It's just the file to tell the OS where the nameservers are.> 

i did  a route and setup packet forwarding in /etc/sysctl.conf

I assume that you are NOT using any GUI on this host.  Am I correct?

How about the NATing?  I wonder?  We are going from on private net (192.168.2.0) to another (192.168.5.0).  Maybe we don't need to NAT at this point.  Only when packets have public (internet) destination do they need NATing.  That would be at the last upstream router (Linksys).

Did you configure the Belkin and the Linksys (WRT54G)?  Did you configure NAT at the Belkin?

The way I see it; you should try and reconfigure the eth0 interface and connect a cable between the Ubuntu Gateway (UG from now on) and the Belkin.  Then see what you have.

I think you should install Wireshark on the UG too.  This way you can see the packet flow on eht0.

---

### Post by pavel989 on 2010-04-26
> **capscrew said:**
> How about the NATing?  I wonder?  We are going from on private net (192.168.2.0) to another (192.168.5.0).  Maybe we don't need to NAT at this point.  Only when packets have public (internet) destination do they need NATing.  That would be at the last upstream router (Linksys).
well i configured packet forwarding using webmin (idk if u know what that is) and i made it that like basically everything is forwarded.
> **capscrew said:**
> 
Did you configure the Belkin and the Linksys (WRT54G)?  Did you configure NAT at the Belkin?
i didnt configure anything at all on either except the IP addr and thus dhcp settings. and the belkin's wireless i configd.
> **capscrew said:**
> 
The way I see it; you should try and reconfigure the eth0 interface and connect a cable between the Ubuntu Gateway (UG from now on) and the Belkin.  Then see what you have.
but how is that different than what i have?
> **capscrew said:**
> 
I think you should install Wireshark on the UG too.  This way you can see the packet flow on eht0.

ill install it asap, see whats going on.

and finally...

nope, no gui. all console. and i know what systcl does, i just dunno how to properly configure it.

---

### Post by capscrew on 2010-04-26
> **pavel989 said:**
> well i configured packet forwarding using webmin (idk if u know what that is) and i made it that like basically everything is forwarded.

Yes I know what Webmin is.> 

i didnt configure anything at all on either except the IP addr and thus dhcp settings. and the belkin's wireless i configd.

Good deal.  Then you also know the range of the dhcp pool.

> 


[QUOTE]Originally Posted by capscrew  
The way I see it; you should try and reconfigure the eth0 interface and connect a cable between the Ubuntu Gateway (UG from now on) and the Belkin. Then see what you have.

but how is that different than what i have?

[/QUOTE]I thought we went over all that.  You need to clear out all that bridging stuff and set up the interface correctly.  The cable is just to eliminate the DD-WRT from the equation.

Do you know how to setup the interface correctly?  Do you know which files to edit?  It's no biggie if you don't. I can show you.  i have several non-gui servers that are configured without anything but the CLI and the VIM editor.

---

### Post by pavel989 on 2010-04-27
well i reconfigure the interfaces to only include eth0, eth1, and lo

(btw what does lo do?)


and i havent been able to move the gateway up the chain to be right at the belkin yet. i plan on doing so later tonight

---

### Post by capscrew on 2010-04-27
> **pavel989 said:**
> well i reconfigure the interfaces to only include eth0, eth1, and lo

Great!> 

(btw what does lo do?)

The ***lo*** interface is the loopback interface and by convention it should be configured with a 127.0.0.1 address.  It it is a virtual interface (no physical hardware (NIC)) needed.  It is for testing the IP stack and communications internally with the OS and services. > 


and i havent been able to move the gateway up the chain to be right at the belkin yet. i plan on doing so later tonight

Why do you need to move it?  The cable can be up to 300ft long.  I'm guessing here; but if you have the dd-wrt set up to be just a switch then it is transparent (no ip address) as a switch.  If this is true then you can leave it in place.  Either way the connection has to be via cable or through a switch between the Belkin and the UG.

---

### Post by pavel989 on 2010-04-27
> **capscrew said:**
> Great!The ***lo*** interface is the loopback interface and by convention it should be configured with a 127.0.0.1 address.  It it is a virtual interface (no physical hardware (NIC)) needed.  It is for testing the IP stack and communications internally with the OS and services. 

Why do you need to move it?  The cable can be up to 300ft long.  I'm guessing here; but if you have the dd-wrt set up to be just a switch then it is transparent (no ip address) as a switch.  If this is true then you can leave it in place.  Either way the connection has to be via cable or through a switch between the Belkin and the UG.

well right now the dd-wrt is infact a switch, and is not giving and ip addresses. so i guess i can leave the ug in place? and i wanted to move the UG so that id still have internet on my desktop

---

### Post by capscrew on 2010-04-27
> **pavel989 said:**
> well right now the dd-wrt is infact a switch, and is not giving and ip addresses. so i guess i can leave the ug in place? and i wanted to move the UG so that id still have internet on my desktop

What do you mean.  If the dd-wrt is a switch it (by definition) has no IP address itself and has no services to provide IP addresses to others.

Try and be specific.  Tell me what the physical arrangements are for the equipment (i.e. The UG is in my bedroom, the dd-wrt is in the kitchen, the Belkin is in the garage, etc., etc.).  We need this for ALL of the equipment from FIOS all the way to your netbook.

Edit:  It would help if you participated in this a little more.  I shouldn't feel like I'm more interested in this than you are. It appears that you are only casually interested in this.  If this is not interesting enough for you to be pro-active, I'm not interested in continuing this opus.  We are at reply #42 (with +500 views) and we are no closer to resolution than we were at the very beginning.

---

### Post by pavel989 on 2010-04-28
> **capscrew said:**
> What do you mean.  If the dd-wrt is a switch it (by definition) has no IP address itself and has no services to provide IP addresses to others.

Try and be specific.  Tell me what the physical arrangements are for the equipment (i.e. The UG is in my bedroom, the dd-wrt is in the kitchen, the Belkin is in the garage, etc., etc.).  We need this for ALL of the equipment from FIOS all the way to your netbook.

Edit:  It would help if you participated in this a little more.  I shouldn't feel like I'm more interested in this than you are. It appears that you are only casually interested in this.  If this is not interesting enough for you to be pro-active, I'm not interested in continuing this opus.  We are at reply #42 (with +500 views) and we are no closer to resolution than we were at the very beginning.

sorry, im trying to answer as best i can. And no im definetly interested, im just not too educated in networking so i can only give as much as im asked.

well here goes.

in my garage, i have the Fios Modem which is connect to the wrt54g. the wrt54g serves the media center, and the belkin N1, which is in an office. the N1 serves wireless, a laptop, vonage, and via the dd-wrt switch in my room, the UG and my desktop. 

the dd-wrt IS a switch. it does NOT have an IP address and does not have any services.

im guessing the wireless clients dont matter

---

### Post by capscrew on 2010-04-28
****> **pavel989 said:**
> sorry, im trying to answer as best i can. And no im definetly interested, im just not too educated in networking so i can only give as much as im asked.

well here goes.

in my garage, i have the Fios Modem which is connect to the wrt54g. the wrt54g serves the media center, and the belkin N1, which is in an office. the N1 serves wireless, a laptop, vonage, and via the dd-wrt switch in my room, the UG and my desktop. 

the dd-wrt IS a switch. it does NOT have an IP address and does not have any services.

im guessing the wireless clients dont matter

As long as the UG is connected via Ethernet cable to the dd-wrt and the dd-wrt is connected via Ethernet cable to the Belkin then it is transparent to what we are doing.  If you set up the UG eth0 interface correctly, you should be able ping the desktop and the Belkin for the command line of the UG.

So I would leave the UG, dd-wrt devices where they are and concentrate on configuring eth0 on the UG.  Remember to give the interface an IP address that is not in the DHCP pool range BUT IN the network (red).

**Edit:**This is to update the final result.  As soon as the bridge (br0) was removed from the eth0 interface and an IP address in the 192.168.2.xxx range was configured, the OP had connectivity from behind the UG to the internet.  The incorrectly configured bridge was causing the interface to not function correctly.

---

### Post by Iowan on 2010-04-29
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") - or should we expect an epilogue? 

**capscrew**:
You certainly are tenacious - are you a collection agent? ;)
Thanks for sticking with it!

---

### Post by capscrew on 2010-04-29
> **Iowan said:**
> [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") - or should we expect an epilogue? 

**capscrew**:
You certainly are tenacious - are you a collection agent? ;)
Thanks for sticking with it!

Hi Iowan,

Long story short:  Pavel and I have been using IM to talk. He configured it and it worked and then broke it.  So we fixed it again with an explanation.  I thought it best with an audience that we at least let everyone in on what was the final result.

I like to teach.

---

