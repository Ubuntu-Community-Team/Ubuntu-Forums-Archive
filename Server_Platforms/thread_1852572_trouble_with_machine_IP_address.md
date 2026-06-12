---
title: "trouble with machine IP address"
date: 2011-09-30
forum: Server Platforms
---

### Post by xplayman on 2011-09-30
Hi there
I'm having a trouble with 11.04 server (with desktop installed)
I've installed zoneminder on it and wanted to use it as gateway/router/DHCP
I've spent countless hours on this machine with no luck creating gateway/router/DCHP (or what ever it's called)
I have a clearOs server here that I wanted to replace with ubuntu server, all the pc's here are connected to the switch and from there to the clearOs and from clearOs to the router.

I tried using webmin to setup DHCP, webmin didint want to install it, then I was told to install ebox/zentyal.
that's when I had enough, now I cant acces the internet on the server.
the machine should have 192.168.111.199 as IP address, but after restart it say's it's 10.42.43.1, but interfaces say it's 192.168.111.199.
__________________________________________________________
I have 2 ethernet cards installed.

my /etc/network/interfaces looks like this
#the loopback network interface
auto lo
iface lo inet loopback

#the primary network interface
auto eth0
iface eth0 inet static
address 192.168.111.199
network 192.168.111.2
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.111.1

iface eth1 inet dhcp
_____________________________________________________________

when in desktop and I click on (the connection symbol nexto to the clock)
and select connection information some times I get "no information available" (or sumthing like that)
then I restart and do it again I get information about "Auto eth1-eth0"

So... can some one please tell me what to do, how can I get this to work?
all I want is ubuntu server with zoneminder, be able to use it as gateway/router/DHCP with graphical interface administration like webmin or ebox/zentyal to be able to control the net traffic going trough the router, close pages at certain times and stuff like that.

I'm pretty new to the whole server/linux thing, i'm still learning and eager to learn,
but atm I just really need this to work, so making this as simple and quick as possible is requested, later on 
when I have enough time I will start learning it with out all the graphical interfaces

if this all sounds like mumbo jumbo I apoligise for that, and just ask me if you need better clarification, english is not my native language, so please stick with simple words lol :)

---

### Post by CharlesA on 2011-09-30
Network manager doesn't really display network info from what I remember.

You'd have to use the terminal to do that.

```
ifconfig
```

---

### Post by jonobr on 2011-10-02
Hello


I would like to add that your config on your primary ethernet interface appears incorrect

```
#the primary network interface
auto eth0
iface eth0 inet static
address 192.168.111.199
network 192.168.111.2
netmask 255.255.255.0
broadcast 192.168.0.255 <-- incorrect should be 192.168.111.255
gateway 192.168.111.1

```

---

### Post by xplayman on 2011-10-03
Thanks for the replys guys.

jonobr
> I would like to add that your config on your primary ethernet interface appears incorrectI changed what you mentioned, and now it starts up with the right IP address.

CharlesA
> Network manager doesn't really display network info from what I remember.
You'd have to use the terminal to do that.I just threw it out there for "reference" porpose.
________________________________________
I decided to throw out this info as well.

Network manager:
Error displaying connection information:
No valid active connections found!
________________________________________

Paste from ifconfig

eth0      Link encap:Ethernet  HWaddr 00:00:00:30:3b:c8  
          inet addr:192.168.111.199  Bcast:192.168.111.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe30:3bc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3709 (3.7 KB)  TX bytes:15915 (15.9 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:211425 (211.4 KB)  TX bytes:211425 (211.4 KB)

I dont get it why I dont get the second Ethernet card now.
__________________________________________________________

ATM I can access it trough local network, but it does not want to acces the internet.
if I do ping google.com I get "ping: unknown host google.com"

So any more suggestions on how to make this work for me?

---

### Post by saphil on 2011-10-03
try 
```
ifconfig -a
```shows all hardware attached to the system
if your other eth card is off, it will not show anything for that.

How is it you have a network address of? 
network 192.168.111.2

I would just skip the fancy subnetting, as long as the first 3 octets are at least one different from the dhcp address on the outside network, you should be fine with 
192.168.111.0 as your network address** -- oops I just noticed that the outside network is identical -- make that 192.168.112.0 with a gateway (this machine) of 192.168.112.0**
the gateway (which is a host and not the same as the network address)
could be 192.168.111.2 if you want, but it is pretty standard to use the 1st address in the network past the network address as the gateway.  On this internal network - if your machine is the gateway for the internal network, then your machine address should be identical with the gateway address, I think.
If you were using a cisco device, that would be true.

---

### Post by xplayman on 2011-10-03
Thanks saphil
after I did ifconfig -a I got
______________________________________________
eth0      Link encap:Ethernet  HWaddr 00:00:00:30:3b:c8  
          inet addr:192.168.111.199  Bcast:192.168.111.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe30:3bc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11939 (11.9 KB)  TX bytes:18440 (18.4 KB)
          Interrupt:22 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:50:fc:f7:5f:38  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3830 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3830 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:922622 (922.6 KB)  TX bytes:922622 (922.6 KB)
________________________________________________________________

yes this machine (192.168.111.199) connects trough a gateway (192.168.111.1)
wich has ClearOs on it, I wanted to get rid of that machine and replace it with the ubuntu server, acting as gateway.
so IP's will be different, as I would make the ubuntu have 192.168.1.1 instead of 192.168.111.199(or *.*.*.1)
my router is cisco linksys.

---

### Post by CharlesA on 2011-10-03
Add this to the interfaces file:

```

auto eth1
iface eth1 inet dhcp
```

Think you were missing the auto eth1 part.

---

### Post by xplayman on 2011-10-05
> **CharlesA said:**
> Add this to the interfaces file:

```

auto eth1
iface eth1 inet dhcp
```Think you were missing the auto eth1 part.

Allright I changed to what you said.
I restarted the server and no internet connection yet.
**After first restart I got **
_____________________________________
Network manager:
worked as it's suposed to.
________________________________________
```
ifconfig got me

eth1      Link encap:Ethernet  HWaddr 00:50:fc:f7:5f:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xe000 

eth1-eth0 Link encap:Ethernet  HWaddr 00:00:00:30:3b:c8  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe30:3bc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:519 (519.0 B)  TX bytes:14022 (14.0 KB)
          Interrupt:22 Base address:0x4000 

eth1:avahi Link encap:Ethernet  HWaddr 00:50:fc:f7:5f:38  
          inet addr:169.254.8.194  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:209120 (209.1 KB)  TX bytes:209120 (209.1 KB)
```
_____________________________________________________________
Since I had the wrong IP I decided to restart again.
this is what I got then.

_____________________________________
Network manager:
 Error displaying connection information:
 No valid active connections found!
 ________________________________________
```
ifconfig got me

eth0      Link encap:Ethernet  HWaddr 00:00:00:30:3b:c8  
          inet addr:192.168.111.199  Bcast:192.168.111.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe30:3bc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:316 (316.0 B)  TX bytes:10494 (10.4 KB)
          Interrupt:22 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:50:fc:f7:5f:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xe000 

eth1:avahi Link encap:Ethernet  HWaddr 00:50:fc:f7:5f:38  
          inet addr:169.254.8.194  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:215609 (215.6 KB)  TX bytes:215609 (215.6 KB)

______________________________________________________________
and still no internet connection. :(

here is my current /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.111.199
network 192.168.111.2
netmask 255.255.255.0
broadcast 192.168.111.255
gateway 192.168.111.1

auto eth1
iface eth1 inet dhcp
```

---

### Post by CharlesA on 2011-10-05
Network should be:
192.68.111.0

ifconfig looks ok - is dhclient running?

More info on the interfaces file can be found [here]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/").

---

### Post by xplayman on 2011-10-11
> **CharlesA said:**
> Network should be:
192.68.111.0

ifconfig looks ok - is dhclient running?

I changed the network like you said, then restarted and I got the 10.42.43.1 IP address.
So I restarted again and got the 169.254.8.194 IP address.

And still no luck on getting to the internet.
why do the IP addresses change each time I restart?
what is the conflict?

btw how can I see if the dhclient is running? :/

Sorry for the long response I just had an car accident, and I just returned to work.

---

### Post by CharlesA on 2011-10-11
The first time, it sounds like it grabbed an IP from DHCP for some reason.

Second time it wasn't able to get an ip from DHCP.

Do you have another dhcp server on the network?

---

### Post by jazzon on 2011-10-11
also what are the contents of ```
/etc/resolv.conf
```

---

### Post by xplayman on 2011-10-12
> **CharlesA said:**
> The first time, it sounds like it grabbed an IP from DHCP for some reason.

Second time it wasn't able to get an ip from DHCP.

Do you have another dhcp server on the network?
Yes, I have a Clearos Gateway that I'm trying to replace with the ubuntu machine.
I havent had any trouble regarding it, that I know of atleast.

> **jazzon said:**
> also what are the contents of ```
/etc/resolv.conf
```
all it say's is
```
#Generated by NetworkManager
```

---

### Post by xplayman on 2011-10-14
any one?

---

### Post by CharlesA on 2011-10-14
Not really sure what they are supposed to look like, to be honest.

You could add your router's ip address or public dns [noparse](I use 8.8.8.8)[/noparse] to the resolv.conf file and see what happens.

---

### Post by saphil on 2011-10-14
Without a nameserver, you will not resolve web pages.  If your private network computers are using you (the gateway) as their dns nameserver, they will not have WWW pages either.
Here is a simple example of /etc/resolv.conf

```
# Generated by NetworkManager
domain TLC
search TLC
nameserver 192.168.23.1 
nameserver 64.94.1.33

```Note: you can safely edit this page with vi or nano.

The domain and search lines are there because I am in a peer network (MS-term 'Workgroup'). My network name 'TLC' makes it easier for the windows boxes CIFS shares to work.  If my network had a domain name, then the search and domain lines would be the FQDN for instance example.com, and my machine would be 'telcontar2.example.com'

The first nameserver is my gateway router.
The second nameserver is (one of) my ISP's nameservers - that is what is listed as the nameserver in my gateway router, without which my gateway couldn't resolve dns and my own laptop here couldn't resolve dns.  

If you are making this the gateway router for your network, you have to find a valid nameserver other than itself. 
Your ISP nameservers are good choices

---

### Post by xplayman on 2011-10-14
> **CharlesA said:**
> Not really sure what they are supposed to look like, to be honest.

You could add your router's ip address or public dns (I use 8.8.8.8) to the resolv.conf file and see what happens.

I did that and no change.
but what I did to was.
remove  "network 192.168.111.0" and broadcast "192.168.111.255"from Interfaces.
uninstalled ebox

then I did 3 commands
sudo ifconfig eth0 up
sudo ifconfig eth1 up
sudo dhclient

and I was able to access the internet.

now, I dont have any webconfigurations ebox or webmin.
and I still want to make it as a gateway/router/dhcp client and replace the clearos gateway, where do I move from here?

---

### Post by xplayman on 2011-10-14
> **saphil said:**
> Without a nameserver, you will not resolve web pages.  If your private network computers are using you (the gateway) as their dns nameserver, they will not have WWW pages either.
Here is a simple example of /etc/resolv.conf

```
# Generated by NetworkManager
domain TLC
search TLC
nameserver 192.168.23.1 
nameserver 64.94.1.33

```Note: you can safely edit this page with vi or nano.

The domain and search lines are there because I am in a peer network (MS-term 'Workgroup'). My network name 'TLC' makes it easier for the windows boxes CIFS shares to work.  If my network had a domain name, then the search and domain lines would be the FQDN for instance example.com, and my machine would be 'telcontar2.example.com'

The first nameserver is my gateway router.
The second nameserver is (one of) my ISP's nameservers - that is what is listed as the nameserver in my gateway router, without which my gateway couldn't resolve dns and my own laptop here couldn't resolve dns.  

If you are making this the gateway router for your network, you have to find a valid nameserver other than itself. 
Your ISP nameservers are good choices

awesome thanks for that.
so, how would I find out what my ISP nameserver is?
(yes i'm new to all this)

EDIT:
I just checked resolv.conf
and I noticed that it has changed since last reboot.
```
domain fjolsmidjan.com
search fjolsmidjan.com
nameserver 192.168.111.1
```the nameserver is obviusly my gateway
and the domain fjolsmidjan.com is our webpage.
is it ok for me to have the current domain and search, or should I change it to TLC?
the only linux machine on the local network will be the server, the rest will be XP and win7 machines.

---

### Post by saphil on 2011-10-14
Ask your ISP about what their nameserver IPs are?
or, if you can look at the control panel web page (probably) of your ClearOS box...

---

### Post by xplayman on 2011-10-19
I just installed ubuntu 11.10 and everything got ******* So I just formatted, hopefully that will play better for me to make the gateway, fresh start and no more clutter of uneded programs.

But I learned alot from this thread and I want to thank everyone for their inputs.

---

