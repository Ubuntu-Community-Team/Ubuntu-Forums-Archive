---
title: "Multiple IP addresses"
date: 2009-12-18
forum: Server Platforms
---

### Post by Carson Dyle on 2009-12-18
I need to bind multiple IP addresses to eth0.  I've read some articles and have seen a few sample /etc/network/interfaces files and have set it up and everything seems to be working fine.  But I have a couple of questions that I'd like to resolve.

Here's the beginning of my interfaces file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.9.40
netmask 255.255.255.0
network 192.168.9.0
broadcast 192.168.9.255
gateway 192.168.9.1

auto eth0:1
iface eth0:1 inet static
address 192.168.9.41
netmask 255.255.255.0
network 192.68.9.0
broadcast 192.168.9.255
gateway 192.168.9.1

auto eth0:2
iface eth0:2 inet static
address 192.168.9.42
netmask 255.255.255.0
network 192.68.9.0
broadcast 192.168.9.255
gateway 192.168.9.1

etc.

```Questions:

What exactly do the 'auto ethxxx' lines do?  I've seen some examples with and some without them.

Are the gateway lines necessary for each additional IP address besides the first one? Again, I've seen examples both with and without them.

Are there any shortcut notations that can be used to do this for 20, 30, 40 or however many IP addresses, all of which are on the same interface, same network, etc.?

---

### Post by cdenley on 2009-12-18
```

man interfaces

```
> 
Lines beginning with the word "auto" are used to identify the physical interfaces to be brought up when ifup is run with  the  -a  option.   (This
       option  is  used  by  the  system  boot scripts.)  Physical interface names should follow the word "auto" on the same line.  There can be multiple
       "auto" stanzas.  ifup brings the named interfaces up in the order listed.


You should only need one gateway. I think only the first will be used anyway. I don't believe there are any shortcut notations.

---

### Post by Carson Dyle on 2009-12-18
> **cdenley said:**
> ```

man interfaces

```> Lines beginning with the word "auto" are used to identify the physical interfaces to be brought up when ifup is run with the -a option.

Thanks. I've read it, but a couple things aren't clear.

It mentions "physical interfaces".  Does that include the eth0:1, eth0:2, etc. interfaces?  Are these considered physical or virtual interfaces?  Which is the reason why I ask whether it's necessary to specify for each one.

I suppose I could test it by commenting them all out and rebooting the server to see if the additional IP addresses are enabled, but I'd like to better understand what I'm doing.

---

### Post by cdenley on 2009-12-18
> **Carson Dyle said:**
> Thanks. I've read it, but a couple things aren't clear.

It mentions "physical interfaces".  Does that include the eth0:1, eth0:2, etc. interfaces?  Are these considered physical or virtual interfaces?  Which is the reason why I ask whether it's necessary to specify for each one.

I suppose I could test it by commenting them all out and rebooting the server to see if the additional IP addresses are enabled, but I'd like to better understand what I'm doing.

Well, technically, the only *physical* interface is eth0, but all interfaces should be listed on an "auto" stanza, as in the example in the documentation.
```

zcat /usr/share/doc/ifupdown/examples/network-interfaces.gz|less

```
```

# auto eth0 eth0:1
# iface eth0 inet static
#     address 192.168.0.100
#     network 192.168.0.0
#     netmask 255.255.255.0
#     broadcast 192.168.0.255
#     gateway 192.168.0.1
# iface eth0:1 inet static
#     address 192.168.0.200
#     network 192.168.0.0
#     netmask 255.255.255.0

```

---

### Post by BkkBonanza on 2009-12-18
> **Carson Dyle said:**
> 
I suppose I could test it by commenting them all out and rebooting the server to see if the additional IP addresses are enabled, but I'd like to better understand what I'm doing.

I'm not 100% certain but I think you just need to run,

/etc/init.d/networking restart

after mods in the interfaces file. That would make it a bit less painful to run tests.

---

### Post by Vegan on 2009-12-18
The IP/TCP stack is designed to have 1 IP address per MAC (card) but some servers have dual channel adapters and these have 2 MAC Ids and are intended to increase bandwidth for overloaded servers with slow infrastructure.

Do not use more than one IP per MAC. So restore /etc/network/interfaces back to normal.

---

### Post by cdenley on 2009-12-18
> **Vegan said:**
> The IP/TCP stack is designed to have 1 IP address per MAC (card) but some servers have dual channel adapters and these have 2 MAC Ids and are intended to increase bandwidth for overloaded servers with slow infrastructure.

Do not use more than one IP per MAC. So restore /etc/network/interfaces back to normal.

I believe you could have a separate MAC address for each virtual interface using the "hwaddress" option. This still wouldn't give increased bandwidth or anything, though. I think the most common reason to have multiple IP's would be to have two servers running on the same port or two SSL websites on the same server with only one physical interface. I have no idea why the original poster is talking about 20, 30, 40 IP's, or if that will even work, but I'm not going to comment on what he should do until he says what he hopes to accomplish with so many interfaces.

---

### Post by BkkBonanza on 2009-12-18
It's very common in hosting situations to have many IPs per machine. It's not "abnormal" at all - it is why virtual interfaces were invented. Your typical VPS host runs virtual interfaces coming out their ears - 30 VPS + /machine with multiple IPs per VPS. On mine I get 2 IPs default but if I need more for multiple SSL domains then I can just ask and shall receive. There could be hundreds of virtual interfaces using various methods on a busy server in these cases.

---

### Post by Carson Dyle on 2009-12-18
> **BkkBonaza said:**
> I'm not 100% certain but I think you just need to run,

/etc/init.d/networking restart

after mods in the interfaces file. That would make it a bit less painful to run tests.

Thank you. Yes, I've been running that to apply any changes made to the interfaces file, but wasn't certain if it would be a test of the 'auto ...' lines.  In any case, I only had to run the test one time. Without the auto lines the IP addresses were not automatically brought up, so I restored them.

---

### Post by lisati on 2009-12-18
> **BkkBonaza said:**
> It's very common in hosting situations to have many IPs per machine. It's not "abnormal" at all - it is why virtual interfaces were invented. Your typical VPS host runs virtual interfaces coming out their ears - 30 VPS + /machine with multiple IPs per VPS. On mine I get 2 IPs default but if I need more for multiple SSL domains then I can just ask and shall receive. There could be hundreds of virtual interfaces using various methods on a busy server in these cases.

As I understand it, the usual way of having multiple IP addresses per machine is to have separate adapters. For example, my laptop has an ethernet adapter and a wireless adapter. One IP address gets associated with the ethernet adapter and another with the wireless adapter - one machine, two IP addresses.

---

### Post by BkkBonanza on 2009-12-18
You can't install 100+ network adapters in cases where you need 100+ IP addresses.

While having multiple IPs on a home system would be unusual it is not uncommon at all in servers run by hosting services.

Using /etc/network/interfaces is just an automated way of doing it using the ifconfig command. Usually to add an IP all you need to do is run,

ifconfig eth0:1 192.168.0.2 netmask 255.255.255.0
ifconfig eth0:2 192.168.0.3 netmask 255.255.255.0
... etc
or using "ip add addr ..." is another way (more modern?)

There is no need for another adapter to do this. It's not illegal or wrong or weird at all. It is supported by the system for many useful situations.

However, on many/most hosting uses today it would be handled in a more sophisticated way by the virtualization software which provides virtual venet0 type interfaces (not eth0) automatically for the hosted vps accounts. There could easily be dozens of those per system. And then within each account users can add multiple IPs as well when needed. 

Web server admins often need multiple IPs to run SSL sites because SSL only supports one domain per IP.

---

### Post by DrJohn999 on 2010-02-06
I have a block of 5 IP fixed public IP addresses, let's call them 192.168.99.170 - 192.168.99.174. Eth0 is configured in [FONT="Courier New"]/etc/network/interfaces[/FONT] to have the first address initially:
```
:
auto eth0
iface eth0 inet static
        address 192.168.99.170/29
        netmask 255.255.255.248
        network 192.168.99.0
        broadcast 192.168.99.255
        gateway 192.168.99.1
:

```
Instead of installing four more nics, I can add more IP addresses to the eth0 interface as secondaries by for example
```
ip addr add 192.168.99.172/29 dev eth0 label eth0:0
ip addr add 192.168.99.174/29 dev eth0 label eth0:1
```
and then I see

```
#: ip addr show dev eth0
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:26:18:3b:0b:6e brd ff:ff:ff:ff:ff:ff
    inet 71.245.97.170/29 brd 71.245.97.255 scope global eth0
    inet 71.245.97.174/29 scope global secondary eth0:0
    inet 71.245.97.172/29 scope global secondary eth0:1
    inet6 fe80::226:18ff:fe3b:b6e/64 scope link 
       valid_lft forever preferred_lft forever

```
Then I can accept incoming web traffic on all of these address and redirect them using, eg, Shorewall or iptables, to the desired virtual or real webservers.
In principle I should be able to cause the addition of the secondary address in [FONT="Courier New"]/etc/network/interfaces[/FONT] on boot or network restart thus:
```
:
auto eth0
iface eth0 inet static
        address 192.168.99.170/29
        netmask 255.255.255.248
        network 192.168.99.0
        broadcast 192.168.99.255
        gateway 192.168.99.1
        up ip addr add 192.168.99.172/29 dev eth0 label eth0:0
        up ip addr add 192.168.99.174/29 dev eth0 label eth0:1

```
In Karmic server (don't know about earlier releases, hadn't tried it) this fails with:
```
#: /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
SIOCDELRT: No such process
SIOCADDRT: No such process
Failed to bring up eth0.

```
and eth0 is left running with only the first address.

So, I can get the multiple IPs to work but not on reboot. I know that there are some other ways to add the secondary address outside of [FONT="Courier New"]/etc/network/interfaces[/FONT]: what's the best way to try and then see if it works in one of these other ways?

---

### Post by BkkBonanza on 2010-02-06
You can configure alias interfaces in the interfaces file but the way to do it is add additional sections for each interface,

auto eth0:1
iface eth0:1 inet static
address 192.168.99.172
netmask 255.255.255.248
network x.x.x.x
broadcast x.x.x.x
gateway x.x.x.x

Also, you shouldn't need any redirects for extra IPs in firewalls or iptables. You should be able to just specify which IP to listen on for your web server software. I think apache will even work with * as the listen address, but I know you can write in the new IP as listen address, eg.

<VirtualHost 192.168.99.172:80>
...

---

### Post by DrJohn999 on 2010-02-07
Yes, but the aliased network interfaces aren't supported in Shorewall 4+, and I've gone off in that direction on this one.

After a little experimentation I discovered that using 'post-up' instead of 'up' in [FONT="Courier New"]/etc/network/interfaces[/FONT] to execute the ip addr add commands made no difference. But, setting the CDIR /prefix length to /24 and changing the mask to 255.255.255.0 did fix this. So, here's the working version of [FONT="Courier New"]/etc/network/interfaces[/FONT]:
```
:
auto eth0
iface eth0 inet static
        address 192.168.99.170/24
        netmask 255.255.255.0
        network 192.168.99.0
        broadcast 192.168.99.255
        gateway 192.168.99.1
        up ip addr add 192.168.99.172/24 dev eth0 label eth0:0
        up ip addr add 192.168.99.174/24 dev eth0 label eth0:1
:

```
I originally chose a /29 designation in an attempt to avoid anything beyond minimal masking to process addresses outside the smallest range of 8 that encompasses my five: 192.168.99.168 to 192.168.99.175. Never did that before. But this seems to have confused the system, so I'll stick with having to look at the extra 248 addresses now in range. Probably no noticeable loss anyway.

---

### Post by BkkBonanza on 2010-02-07
I'm not sure why you have the cidr value on that line anyway. The netmask does the same thing and usually it is specified one way or the other but not both ways. In my quick check of the man page it doesn't appear to need the /xx value so I presume it is just ignoring it. 

I'm also not sure what difference there is between using "ip add" and specifiying the eth0: x as another interface but if it seems to work better for Shorewall then I guess it isn't wrong. You can also put the "ip add" lines in the /etc/rc.local file to have them run upon booting. This is where custom boot sripts are often loaded. I don't see any reason why the way your'e doing it is wrong though.

A netmask of 248 should give you IP values in 168-175 range. You may want to try that value without the cidr /29 suffix as maybe that is the part that is confusing it. Also to clarify, the address value is for that interface, and the network value is for the network start address (on a 3 bit boundary here) but the address and gateway must be within the network range. Your values seem to put the network & gateway at .0 but the ip for this interface at .170, which is likely the problem. ie. it's not the software that's confused.

With a mask of 248 (= /29) the network will contain only the last 3 bits. So your network address is the top 5 bits, meaning that you need to sync your network range with your address and gateway values for them to work...

either,

address 192.168.99.170
netmask 255.255.255.248   #means range 168-175
network 192.168.99.168   #because this start addr
gateway 192.168.99.168

or possibly,

address 192.168.99.2
netmask 255.255.255.248   #means range 0-7
network 192.168.99.0    #because this start addr
gateway 192.168.99.1

The gateway has to be in the network or it is unreachable.

---

### Post by DrJohn999 on 2010-02-07
I'm sure it was the gateway address, which is 192.168.99.1. I forgot that it needed to be in range as well. I'm sure that there are mostly DDNS subscribers peppered around my IP addresses, but we all have to use the one gateway.

Works fine without the / designations in interfaces and defaults to /24 as you indicate.

Thanks!

---

