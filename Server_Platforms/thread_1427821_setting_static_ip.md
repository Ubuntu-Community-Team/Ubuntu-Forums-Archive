---
title: "setting static ip"
date: 2010-03-12
forum: Server Platforms
---

### Post by zander1013 on 2010-03-12
hi,

i am trying to set [http://alonzofretwell.com:1234](http://alonzofretwell.com:1234) to use a static ip address. at present it is set up with dhcp and is using a dhcp ip address.

i have a port forward setup on my main network server/router/firewall ( [http://alonzofretwell.com](http://alonzofretwell.com) ) with these settings... 
> source ip=all, public port=1234, private port=80, private ip=<dhcp.ip>  

the network diagram is like this..
wan<>network/server/router/firewall<>(new wireless server)

i am following [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic) as an example.

etc/network/interfaces in the new wireless server looks like this...

>  ## To configure a dynamic IP address
auto eth0
iface eth0 inet dhcp


i propose to comment the above out and add this...

> 
auto eth0
iface eth0 inet static
  address <static.ip.address.1>
  gateway <my.gateway.address>
  netmask 255.255.255.224
  network <???>
  broadcast <???>
 i don't know what values to use for <???>.

then do this...
>  sudo /etc/init.d/networking restart 

then add a port forward on the network.server.router.firewall

with...
> source ip=all, public port=1234, private port=80, private ip=<static.ip.address.1>  

the network/server/router/firewall /etc/network/interfaces looks like this...

> 
auto lo
iface lo inet loopback

iface eth1 inet static
	netmask 255.255.255.0
	address 192.168.10.1

iface eth0 inet static
	gateway <my.gateway.address>
	netmask 255.255.255.224
	address <static.ipaddress.0>


is this a sound plan? and if yes what should i use for the <???> that i noted above.

do i need to make any consideration for the wireless aspect if it is already working?

please advise.

thank you for your help.:)

---

### Post by Lucky. on 2010-03-12
It's possible to derive a network address and broadcast address if you know a single IP address in the network and the netmask of the network.  It's a bit tricky, but easy once you get the hang of it.

Also you may not need to write down your network and broadcast addresses in your config file...I've seen a number of installations work just fine without them (possibly because they're deriving the network and broadcast from the netmask and the IP address?)  Try skipping these settings entirely and seeing if it works.

Do you feel comfortable sharing more information, like the IP address of your wireless server?  If you list the IP address and netmask of your wireless server, I can get you the network and broadcast addresses easily.

Wait a minute...if I'm reading you right, your firewall/router/server's internal interface info is:

```

netmask 255.255.255.0
address 192.168.10.1

```

For this guy, the extra information you need is:

```

network 192.168.10.0
broadcast 192.168.10.255

```

If this is the same network that your wireless server is on, then you can use the same network and broadcast settings for the wireless server.  The network address is the lowest possible IP address in a subnet (but you can't use the address for any devices).  Likewise the broadcast address is the highest possible IP address in a subnet (again though, you can't use the address for any devices).

Good luck!

---

### Post by zander1013 on 2010-03-12
i can give you the ip addresses.

network diagram...
(wan)<>((eth0)server/router/firewall(eth1))<>(new wireless server)

this is the contents of /etc/network/interfaces for the server/router/firewall it is the entry point to my wlan shown as (server/router/firewall) in the diagram just above....

iface eth1 inet static
	netmask 255.255.255.0
	address 192.168.10.1

iface eth0 inet static
	gateway 24.234.112.225
	netmask 255.255.255.224
	address 24.234.112.226


as you can see (server/router/firewall) has two ethernet ports eth0 and eth1. my speculation is that eth0 is the external port connected to wan (the internet) and eth1 is the internal port that connects to the wireless lan and the new server.

i had proposed the following for contents of /etc/network/interfaces on (new wireless server) in the diagram just above...

auto eth0
iface eth0 inet static
  address 24.234.112.229 
  gateway 24.234.112.225
  netmask 255.255.255.224
  network <???>
  broadcast <???>

... i think this is all i have to do in order to assign (new wireless server) its own static ip address(24.234.112.229. and like i said i don't know what network or broadcast should be set to. 

at present i have a port forward setup such that the new wireless server at [http://alonzofretwell.com:1234](http://alonzofretwell.com:1234) can be reached through the server/router/firewall ( [http://alonzofretwell.com](http://alonzofretwell.com) ) with 1234 port forward. if you click on those links i think it helps. :)

eventually i want to be able to reach the new wireless server where it is with a domain name that is its own. but first i am just trying to get it set up with its own static ip address.

thank you for helping me through this. this is the first server i have setup from scratch.:popcorn:

---

### Post by Lucky. on 2010-03-12
Ah beautiful!  Indeed, you have a standard class C internal network.  This is real easy.

You're absolutely right, your eth0 on your firewall/router/server is the external interface.  eth1 is the internal one.

For your internal wireless server, I suggest something like the following:

```

auto eth0
iface eth0 inet static
address 192.168.10.2
gateway 192.168.10.1
netmask 255.255.255.0
network 192.168.10.0
broadcast 192.168.10.255

```

An explanation of these:

Gateway:  In order for your internal wireless server to communicate with the outside world, it needs to talk to your router/firewall/server.  Your router/firewall/server is at 192.168.10.1, so that's your gateway for the wireless server.

(My router at my house has an internal IP of 192.168.1.1.  Hence that's the gateway for all of my computers in my network.  Yours is a slight bit different, using 192.168.10.1, instead of 192.168.1.1.  That's perfectly fine though!)

Netmask:  Since your router/firewall/server's internal network card has a netmask of 255.255.255.0, it should be the same for your wireless server since they are on the same "network".  Hence your wireless server's netmask needs to be 255.255.255.0.

The internal IP address of your firewall/router/server is 192.168.1.10, and it's netmask is 255.255.255.0.  In order to find the network address, we convert both to binary and perform a logical AND operation!

192.168.10.1 = 11000000.10101000.00001010.00000001
255.255.255.0 = 11111111.11111111.11111111.00000000

Logical AND:

```

11000000.10101000.00001010.00000001
11111111.11111111.11111111.00000000
-----------------------------------
11000000.10101000.00001010.00000000

```

11000000.10101000.00001010.00000000 translated from binary back into decimal = 192.168.10.0.

Hence the network address is 192.168.10.0.

The broadcast address is the highest IP address allowed in your subnet.

Since you have a subnet mask of 255.255.255.0, this translates into binary:

11111111.11111111.11111111.00000000

This gives us the last 8 bits to use for clients.  8 bits can count from 0 to 255.  So if the network address is the lowest IP address at 192.168.10.0, then the broadcast address is 192.168.10.255.

So your private home network has a range of IP addresses from 192.168.10.0 to 192.168.10.255.  This gives you a 256 addresses to use!  However...you can't use the network address or the broadcast address for any devices.  So 192.168.10.0 and 192.168.10.255 are out.  This leaves you 192.168.10.1 through 192.168.10.254.  However your server/router/firewall is already using up 192.168.10.1, so that leaves you:

192.168.10.2 through 192.168.10.254.

So for the IP address of your wireless server, you can use any address between 192.168.10.2 through 192.168.10.254.  I suggested 192.168.10.2, but you can pick anything from 2 to 254.

(You might want to watch out for the address range your DHCP server dishes out to others on your network.  For example my DHCP server dishes out 192.168.1.50 through 192.168.1.99, so I don't want to use any addresses in that range for my server).

You know what, this is a really bad explanation.  I'm sorry if doesn't help much.  Subnetting is a boring and tedious thing to do.  I really think you're on track though...you're really close!

I have a few write-ups on this, but they're not very detailed.

[An Intro to addressing](http://www.ericforyan.com/index.php?node=40)

[IPv4 Addressing Pt 1](http://www.ericforyan.com/index.php?node=41)
[IPv4 Addressing Pt 2](http://www.ericforyan.com/index.php?node=42)
[IPv4 Addressing Pt 3](http://www.ericforyan.com/index.php?node=43)

Also if you don't already know how to convert binary to decimal:  [woot](http://www.ericforyan.com/index.php?node=57)

The part where I get lost on is how you are performing port forwarding.  I understand the concept, but I've never used Linux to do it before...I always use a router to get the job done.  I'm sorry, I can't help much there.  Maybe somebody else can make sure your settings are good on that?

---

### Post by zander1013 on 2010-03-12
with the info you have given the private ip component of the port forward should be 192.168.10.2.

i do not know that port forward is the best way to access the new server.

i want to give the server a domain name but i am having trouble with aliasing [http://alonzofretwell.com:1234](http://alonzofretwell.com:1234) with <newdomain>.com because the ":" that must be used to address the new wireless servers port forward is not allowed in dns cname records.

dns records in general seem to preclude the aliasing of an ip address with :<portforward> added to the rhs.

subsequently port forwarding may not be the right way to setup the firewall for the purpose i have in mind but i don't know how else to reach new server right now.

thank you so much for this info. it is very helpful and just the sort of tutorial that i need. i am going through every word and number in it to understand it and i will go over your articles too.

you have helped me allot!:)

---

### Post by spynappels on 2010-03-12
Just FYI, in the /etc/network/interfaces you do not need to put in the network and broadcast addresses into this config page, it is automatically calculated from the IP address and subnet mask.

---

### Post by zander1013 on 2010-03-12
hi,

after adding

```
auto eth0
iface eth0 inet static
  address 192.168.10.2
  gateway 192.168.10.1
  netmask 255.255.255.0
```

and commenting out

```
auto eth0
iface eth0 inet dhcp
```

in /etc/network/interfaces, running sudo /etc/init.d/networking restart on my new wireless server and then setting up a new port forward rule for it in the server/router/firewall the new wireless server is unreachable using the expected [http://alonzofretwell.com:1234](http://alonzofretwell.com:1234).<---(its using the dhcp address at present)

192.168.10.2 is in the network range and is not going to conflict  with ip addresses assigned by dhcp.

i have also tried

```
auto eth0
iface eth0 inet static
  address 192.168.10.2
  gateway 192.168.10.1
  netmask 255.255.255.0
  network 192.168.10.0
  broadcast 192.168.10.255
```

with the same results trying to access it "page not found".

please advise.:(

---

