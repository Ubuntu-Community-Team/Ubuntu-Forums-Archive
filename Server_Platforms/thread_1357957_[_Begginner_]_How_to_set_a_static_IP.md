---
title: "[ Begginner ] How to set a static IP"
date: 2009-12-17
forum: Server Platforms
---

### Post by Skidbladniir on 2009-12-17
I am a very beginner, in fact, I'm 12 :P, and I want to know how to set a static IP.  What should I use for address, netmask, gateway, nameserver, etc.  Please be as specific as possible.

---

### Post by jerrrys on 2009-12-17
maybe all you need is a search engine

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=static+IP+setup&as_qdr=all&sa=Google+Search&lang=en#1002](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=static+IP+setup&as_qdr=all&sa=Google+Search&lang=en#1002)

---

### Post by Iowan on 2009-12-17
As usual... it depends. Your static address will need to be in the same subnet as other machines on your network and will need to be outside the range of your DHCP server. Does your machine currently get a DHCP address? Do you have access to the (DHCP) server (which will probably be your router)?

Once you find the address/netmask (192.168.?.x/255/255/255/0), you might be able to use Network Manager to set up a Manual address (static by another name...)

---

### Post by Skidbladniir on 2009-12-17
Yes, I do.

So, if this computer's (PC - connected to wireless router via ethernet, then to Time Warner Cable router) address is 70.114.165.50, could you give me some hints?

---

### Post by R.Bucky on 2009-12-17
It should be fairly easy to edit your /etc/network/interfaces file with gedit or vi.
```
# The secondary network interface
auto eth1
iface eth1 inet static
	address 10.1.10.30
	netmask 255.255.255.0
	network 10.1.10.0
	broadcast 10.1.10.255
        gateway 10.1.10.1

```
The gateway is your router, address is your desired static address...

---

### Post by Skidbladniir on 2009-12-17
So, I just copy my gateway from my router login, use the same class IP address (I read somewhere that I have to use the same netmask) and get a public DNS to use?

Also, what is "network"?

---

### Post by theozzlives on 2009-12-17
It depends on what you want to do with it. Like my setup, I have a static IP from my ISP setup in the router. Then I have port 80 forwarded to the computer that's running Apache Server. Thus my website was born, granted I had to pay a registrar for the name, but it's all good.

---

### Post by Skidbladniir on 2009-12-17
> **theozzlives said:**
> It depends on what you want to do with it. Like my setup, I have a static IP from my ISP setup in the router. Then I have port 80 forwarded to the computer that's running Apache Server. Thus my website was born, granted I had to pay a registrar for the name, but it's all good.
I'm setting up my own website.

Anyway, what is the "network" property?

---

### Post by Skidbladniir on 2009-12-17
address 53.167.22.4
netmask (What would this be?)
gateway 70.114.160.0
broadcast (What is this?)
network (What is this?)

---

### Post by Skidbladniir on 2009-12-17
Please - need help ASAP.  X_X

---

### Post by Iowan on 2009-12-17
Network and broadcast are not actually required. Ordinarily, a router has it's LAN port in one of the private address ranges - usually 192.169.x.x. If you have access to the DHCP server, it's probably possible to set up a static lease based on MAC address... then the server could be left on DHCP (it'd still have the same address every time).

---

### Post by Skidbladniir on 2009-12-17
> **Iowan said:**
> Network and broadcast are not actually required. Ordinarily, a router has it's LAN port in one of the private address ranges - usually 192.169.x.x. If you have access to the DHCP server, it's probably possible to set up a static lease based on MAC address... then the server could be left on DHCP (it'd still have the same address every time).
I'm sorry, what?  DX

---

### Post by HighCommander540 on 2009-12-17
> **Skidbladniir said:**
> address 53.167.22.4
netmask (What would this be?)
gateway 70.114.160.0
broadcast (What is this?)
network (What is this?)

If you are using a router. Your address is going to be something like this 192.168.x.x. Not 53.167.22.4, that is your external IP address.

Also your gateway is going to be something like this 192.168.x.1.

Your netmask is usually "255.255.255.0" check what it currently is on your computer or another one on your network by doing this:

```
ifconfig
```

Broadcast isn't needed, unless you really what that feature of networking. Otherwise your computer will just auto-assign it.

Network isn't needed, unless you really what that feature of networking. Otherwise your computer will just auto-assign it.

Also, you don't need a public DNS. The DNS your ISP gives you will work. You can look it up in your router. or if you arlready did a DHCP on your Ubuntu machine the DNS server's will be stored in.

```
/etc/resolv.conf
```

> **Iowan said:**
> Network and broadcast are not actually required. Ordinarily, a router has it's LAN port in one of the private address ranges - usually 192.169.x.x. If you have access to the DHCP server, it's probably possible to set up a static lease based on MAC address... then the server could be left on DHCP (it'd still have the same address every time).

Not all router's offer static lease for MAC addresses..

---

### Post by Skidbladniir on 2009-12-17
Done:
```

iface eth0 inet static
address 53.167.22.4
netmask 225.225.224.0
gateway 70.114.160.0
network 70.114.160.0

```

So, this will work, right, so now I reboot the network thingy?  Lol... How do I do that?

---

### Post by Skidbladniir on 2009-12-17
Fail'd...

---

### Post by fibercode on 2009-12-17
Here is what it most likely should be:

iface eth0 inet static
address 192.168.1.25
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.0

Also edit your /etc/resolv.conf file. 

It should look like this:

```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 8.8.8.8
```

I am giving you the IP of Google's public DNS here to be sure that it will work for you.


I am assuming several things:

1. Your router's IP address is 192.168.1.1
2. The 192.168.1.25 is not taken by another machine on your LAN
3. You have only one subnet on the 192.168.1.* network

I will be absolutely certain what to put there if you post the results of this command:
```

ifconfig
```
Execute the above command before you attempt to switch to static IP from DHCP.

---

### Post by Skidbladniir on 2009-12-17
```
-bash: ipconfig: command not found
```

---

### Post by HighCommander540 on 2009-12-17
> **Skidbladniir said:**
> ```
-bash: ipconfig: command not found
```

That is because you are literally not reading what we told you to run. It is:

```
ifconfig
```

The "f" is not a typo.

---

### Post by Skidbladniir on 2009-12-17
X.X

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inter6 addr: ::1/28 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets: all 0
TX packets - same
collisions: 0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

---

### Post by Skidbladniir on 2009-12-17
... DOH.  One second...

---

### Post by fibercode on 2009-12-17
This is just the local loopback virtual interface.

You are not posting the whole output of the ifconfig command.

Please, scroll up on your terminal window and post absolutely everything after the ifconfig command.

---

### Post by Skidbladniir on 2009-12-17
Actually, I forgot to turn DHCP back on.  :S

eth0

Link encap:Ethernet HWaddr 00:13:20:83:9c:fa
inet addr:192.168.1.2
inet6 addr: fe80::213:20ff:fe86:9cfa/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:35 errors:0 dropped:0 overruns:0 frame:0
TX packets: Same - carrier:0
collisions:0 txqueuelen:100
RX bytes:11233 (11.2 KB) TX bytes:7407 (7.4 KB)

---

### Post by fibercode on 2009-12-17
You should have something like:  

Bcast:192.168.1.255  Mask:255.255.255.0

after

inet addr:192.168.1.2



Anyway... Use the settings I gave you earlier. They should work for you.

If that does not work for you. Go back to DHCP. Then run:

```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
ifconfig
route

```
And then post the results of the ifconfig and route commands.

---

### Post by jamieleshaw on 2009-12-17
If you want your own dns.
I wrote a howto just for that.
[http://jamieleshaw.co.cc/?p=26](http://jamieleshaw.co.cc/?p=26)
Goodluck

---

### Post by fibercode on 2009-12-17
> **jamieleshaw said:**
> If you want your own dns.
I wrote a howto just for that.
[http://jamieleshaw.co.cc/?p=26](http://jamieleshaw.co.cc/?p=26)
Goodluck

Not to diminish your article... it has its purpose... but this is completely unnecessary for him.

He does not know what a gateway or a network is and you want him to run his own DNS server :D

Completely unnecessary in this case.

If he edits the /etc/resolv.conf file like I told him this would be all that is needed when it comes to DNS.

---

### Post by jamieleshaw on 2009-12-17
Well, if he wants to run his website on his own server he'll need to learn at some point
;)
He'll work it out ;)

---

