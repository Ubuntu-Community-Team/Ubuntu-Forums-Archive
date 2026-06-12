---
title: "Set Up Static IP using CLI or Network Settings"
date: 2009-08-26
forum: Server Platforms
---

### Post by snorkytheweasel on 2009-08-26
Kubuntu Server Jaunty (9.04)
I can't set a static IP using network settings -> network management -> add network connection.
[LIST]
[*]I can set "Connect Automatically" to On or Off
[*]I can set the IP method to Manual (or others)
[*]I can set the DNS Server IP and search domain
[/LIST]
But when I click "Add," there's no way to enter an IP. As a sanity check, I tested the same procedure on a Hardy server. While the GUI is a bit different, the concept is the same, and I can set a static IP.

So I did it the old-fashioned way:
[LIST=1]
[*] /* --- Configure /etc/network/interfaces --- */
[FONT="Fixedsys"]auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1[/FONT]
[*] /* --- Configure /etc/resolv.conf --- */
[FONT="Fixedsys"]        name server 192.168.1.1[/FONT]
[*] /* --- remove  the dhcp client --- */
[FONT="Fixedsys"]sudo apt-get remove dhcp-client[/FONT]
[*] /* --- restart networking services --- */
[FONT="Fixedsys"]sudo /etc/init.d/networking restart[/FONT]
or restart entire system
[/LIST]
Restart networking services returns
[FONT="Fixedsys"]SIOCADDRT: no such process
Failed to bring up eth0[/FONT]

Now network services doesn't see eth0, and no other computers can see this computer. Note: I can successfully ping itself (this computer) by IP and by hostname.

If I can get network settings -> network management -> add network connection to work, the problem should go away.

Barring that, I need to figure out what went wrong in the 'old-fashioned' configuration.

---

### Post by jocampo on 2009-08-26
> **snorkytheweasel said:**
> Kubuntu Server Jaunty (9.04)
I can't set a static IP using network settings -> network management -> add network connection.
[LIST]
[*]I can set "Connect Automatically" to On or Off
[*]I can set the IP method to Manual (or others)
[*]I can set the DNS Server IP and search domain
[/LIST]
But when I click "Add," there's no way to enter an IP. As a sanity check, I tested the same procedure on a Hardy server. While the GUI is a bit different, the concept is the same, and I can set a static IP.

So I did it the old-fashioned way:
[LIST=1]
[*] /* --- Configure /etc/network/interfaces --- */
[FONT="Fixedsys"]auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1[/FONT]
[*] /* --- Configure /etc/resolv.conf --- */
[FONT="Fixedsys"]        name server 192.168.1.1[/FONT]
[*] /* --- remove  the dhcp client --- */
[FONT="Fixedsys"]sudo apt-get remove dhcp-client[/FONT]
[*] /* --- restart networking services --- */
[FONT="Fixedsys"]sudo /etc/init.d/networking restart[/FONT]
or restart entire system
[/LIST]
Restart networking services returns
[FONT="Fixedsys"]SIOCADDRT: no such process
Failed to bring up eth0[/FONT]

Now network services doesn't see eth0, and no other computers can see this computer. Note: I can successfully ping itself (this computer) by IP and by hostname.

If I can get network settings -> network management -> add network connection to work, the problem should go away.

Barring that, I need to figure out what went wrong in the 'old-fashioned' configuration.

are you sure that's your gateway IP? usually you get that error when gw or IP configuration is wrong.

BTW, are you running Ubuntu Server with GUI?? OMG! :(

---

### Post by Iowan on 2009-08-26
> **snorkytheweasel said:**
>  Note: I can successfully ping itself (this computer) by IP and by hostname.I presume that means that **ifconfig -a** and **route** show proper information.

---

### Post by terazen on 2009-08-26
Your interfaces file looks good.  Possibly the Network Manager process is still running so when you restart networking it interferes with the /etc/network/interfaces?  Can you kill the network manager process ids and then run the `sudo /etc/init.d/networking/restart`?

Also, when you can ping yourself locally all that means is basically tcp/ip is working and the eth0 interface is turned on.

---

### Post by snorkytheweasel on 2009-08-27
> **jocampo said:**
> are you sure that's your gateway IP? usually you get that error when gw or IP configuration is wrong.

BTW, are you running Ubuntu Server with GUI?? OMG! :(

The gateway is correct. This server's connectivity was great as long as I used DHCP. The entire network (windoze and linux) saw it & shared files, etc.

GUI? Yes. My boss is a self-described 'GUI cripple.'When he says 'put on gui on it,' I put a gui on it. I was hoping to get away with 'apt-get install kde', but that gui was inadequate, so I had to ratchet it up to 'install kubuntu-desktop':-#

---

### Post by shel-hall on 2009-08-27
When I had this problem with the LTSP server, uninstalling Network Manager solved it for me.

-Shel

---

### Post by jocampo on 2009-08-27
> **snorkytheweasel said:**
> The gateway is correct. This server's connectivity was great as long as I used DHCP. The entire network (windoze and linux) saw it & shared files, etc.

GUI? Yes. My boss is a self-described 'GUI cripple.'When he says 'put on gui on it,' I put a gui on it. I was hoping to get away with 'apt-get install kde', but that gui was inadequate, so I had to ratchet it up to 'install kubuntu-desktop':-#

Your boss should not be your boss! He does not know what he's doing. Installing GUI to a Ubuntu server is a stupid idea and you are wasting resources.

Regarding your issue, try to put DHCP again there (btw, servers should NEVER USE DHCP but static IPs) Once your IP is working, do an ifconfig and grab all the info. Change back to static and it should work.

---

### Post by snorkytheweasel on 2009-08-27
> **Iowan said:**
> I presume that means that **ifconfig -a** and **route** show proper information.

ifconfig -a looks the way I expect it to look.

However ...

The actual info (as opposed to the original post):
auto eth0
iface eth0 inet static
address 10.21.1.16
netmask 255.255.0.0
network 10.1.1.10
broadcast 10.1.1.255
gateway 10.1.1.3

route sez:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.21.1.0        *               255.255.255.0     U     0      0        0 eth0

I changed 'network' in 'interfaces to so 'interfaces' reads
auto eth0
iface eth0 inet static
address 10.21.1.16
netmask 255.255.0.0
network 10.1.1.1  [COLOR="Red"][ was 10.1.1.10 ][/COLOR]
broadcast 10.1.1.255
gateway 10.1.1.3

Now route sez:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.21.0.0        *               255.255.0.0     U     0      0        0 eth0

Clearly, my ignorance abounds.... I have no idea what **route** is telling me. Also, for 'gateway' I'm using the IP for http_proxy (without the port#) - since that's waht 'gateway' means to me.

---

### Post by jocampo on 2009-08-27
Ok, let's go to the basics. This is what you provided

```

address 10.21.1.16
netmask 255.255.0.0
network 10.1.1.10

```

If you are not subnetting and I recall well, your 1st two octets should be your network id, because is masked by your netmask value

```

netmask [COLOR="Red"]255.255[/COLOR].0.0
network [COLOR="Red"]10.1[/COLOR].0.0

```

so, your network should be something like 10.1.0.0, again, if you are not doing subnetting. And your gateway should be (this is the normal rule) 10.1.0.1

In your example, your IP and Gateway are in different networks, see..

address [COLOR="Red"]10.21[/COLOR].1.16
gateway [COLOR="Red"]10.1[/COLOR].1.3

they both should read and be the same, like 10.1 or 10.21 .... but no different values for each one ...

---

### Post by snorkytheweasel on 2009-08-27
> **jocampo said:**
> Ok, let's go to the basics. This is what you provided

```

address 10.21.1.16
netmask 255.255.0.0
network 10.1.1.10

```

If you are not subnetting and I recall well, your 1st two octets should be your network id, because is masked by your netmask value

```

netmask [COLOR="Red"]255.255[/COLOR].0.0
network [COLOR="Red"]10.1[/COLOR].0.0

```

so, your network should be something like 10.1.0.0, again, if you are not doing subnetting. And your gateway should be (this is the normal rule) 10.1.0.1

In your example, your IP and Gateway are in different networks, see..

address [COLOR="Red"]10.21[/COLOR].1.16
gateway [COLOR="Red"]10.1[/COLOR].1.3

they both should read and be the same, like 10.1 or 10.21 .... but no different values for each one ...

I can usually plow my way through stuff like this and figure it out from RTFMing and from context, but this time I've hit the wall.

We are using subnetting: 10.1 ... 10.10 ... 10.20 ... 10.30 ... 10.40 
Each of those subnets identifies the type of network resource: one group for servers, one group for workstations, one group for printers, and so on.

So the boss - the genius who hired me 8 years ago - after I passed the TCP/IP exam & got a MCSE cert, but before I forgot it all :) , told me to use 10.21.1.16/24 - which is outside any of the DHCP ranges and the static IPs already assigned. 

I have no doubt that there was a method to this madness. Besides, I never question him about 
[LIST]
[*]whom he hires
[*]why he signs my paycheck
[*]how he divvies up the IP addresses
[/LIST]
I also don't ask him questions that might make him look like he doesn't know something - including anything having to do with CLI (Windows or the CISCO switches and routers or Linux).

Back to harsh reality.

Given the above - the assigned static IP, the design of the network, and the extent of my ignorance - how should that interfaces file really look? 

[FONT="Fixedsys"]address 10.21.1.16  [COLOR="Red"] plus "/24" ???[/COLOR]
netmask 255.255.0.0
network 10.1.1.1        [COLOR="Red"]the root of the network, but not the subnet in question[/COLOR]
broadcast [COLOR="Red"]damphyno [/COLOR]     [COLOR="Red"]10.1 or 10.21 ??[/COLOR]
gateway [COLOR="Red"]likewise[/COLOR]        [COLOR="Red"]10.1 or 10.21 ??[/COLOR][/FONT]

---

### Post by snorkytheweasel on 2009-08-27
UPDATE:      
[LIST=1]
[*]I dusted off the old TCP/IP books and read up on cidr. I calculated the correct values for the 'interfaces' file. Some of the error messages went away. However, 
[LIST]
[*]with **DHCP**, this server and the rest of the network are quite happy with each other. 
[*]With **Static IP**, well, not so good: the server and the rest of the network don't see each other.
[/LIST]
[*]I uninstalled Network Manager and installed wicd.
wicd makes it much easier to get results that don't work.
[/LIST]
With Static IP:

/etc/resolv.conf
[FONT="Fixedsys"]nameserver 10.1.1.10[/FONT]

/etc/network/interfaces (based on my TCP/IP calculations)
[FONT="Fixedsys"]address   10.21.1.16 
netmask   255.255.255.0
network   10.21.1.0  /24
broadcast 10.21.1.255
gateway   10.21.1.1[/FONT]

I'm still stuck, because I have to set a static IP.





.

---

### Post by jocampo on 2009-08-27
Your problem is easier to fix than you think :-) . Just setup your server to use DHCP. Once done and working, please post what your network configuration is; you can use ifconfig and route command for that. The more important vales aree:

-IP
-Netmask
-Gateway IP

Find out what those vales are when you are using DHCP. But bottom line... whatever the IP or Subnet mask you are using, your Gateway MUST ALWAYS BE ON SAME NETWORK, or you will not be able to "talk" to anything outside from your server.

---

### Post by bab1 on 2009-08-27
There is no reason that the gw has to be a specific address.  It can be any address in the range.  Convention usually dictates that it be at the beginning  (or end) of the network IP range.  But it can be any legitimate address in the network.  It is the IP address of the nearside interface of the router it is directly connected to (not including and switches).

---

### Post by TwiceOver on 2009-08-27
Might want to double check your subnet mask.  If you truely are subnetting the mask would not be 255.255.0.0 it would look more like 255.254.0.0 or something similar.  Or the CIDR notation would be /16 (anything other than 24 which = 255)

Easiest way is to grab an IP from the DHCP server and see what it shows for your subnet to make sure you have it right.

---

### Post by snorkytheweasel on 2009-08-27
> **jocampo said:**
> Your problem is easier to fix than you think :-) . Just setup your server to use DHCP. Once done and working, please post what your network configuration is; you can use ifconfig and route command for that. The more important vales aree:

-IP
-Netmask
-Gateway IP

Find out what those vales are when you are using DHCP. But bottom line... whatever the IP or Subnet mask you are using, your Gateway MUST ALWAYS BE ON SAME NETWORK, or you will not be able to "talk" to anything outside from your server.

Using DHCP:
[FONT="Fixedsys"]inet address: 10.1.1.136
netmask:      255.255.0.0
gateway:      10.1.1.1[/FONT]

---

### Post by bab1 on 2009-08-27
> **snorkytheweasel said:**
> Using DHCP:
[FONT="Fixedsys"]inet address: 10.1.1.136
netmask:      255.255.0.0
gateway:      10.1.1.1[/FONT]

So it looks like we have a 16 bit network (/16 or 255.255.0.0).  This could give us IP addresses from 10.1.0.1 to 10.1.255.254.  The gw is not the first number in the range, but it is a good number.

Looking back at your static addressing scheme:```

/etc/resolv.conf
nameserver 10.1.1.10

/etc/network/interfaces (based on my TCP/IP calculations)
address 10.21.1.16      [COLOR="Red"]<--could be 10.1.1.136[/COLOR]
netmask 255.255.255.0   [COLOR="Red"]should be 255.255.0.0[/COLOR]
network 10.21.1.0 /24   [COLOR="Red"]should be 10.1.0.0 /16 [/COLOR]
broadcast 10.21.1.255   [COLOR="Red"]should be 10.1.255.255[/COLOR]
gateway 10.21.1.1       [COLOR="Red"]should be 10.1.1.1[/COLOR]

```

You are not even close.  The network 10.21.1.0/24 is off.  It looks as if you need to be in the range from 10.1.0.1 to 10.1.255.254. I think you will be fine with the addresses noted in red.


Edit:  BTW - Are you in Downey?

---

### Post by jocampo on 2009-08-27
> **snorkytheweasel said:**
> Using DHCP:
[FONT="Fixedsys"]inet address: 10.1.1.136
netmask:      255.255.0.0
gateway:      10.1.1.1[/FONT]

You are all set my friend :-) ... just adjust that so you can assign and IP in the 10.1.0.0 network. Your IP will be in this range: 10.1.0.1 --> 10.1.255.254. DO NOT CHOOSE 10.1.1.1 because is the gateway and DO NOT CHOOSE 10.1.255.255 because is the broadcast address. 

Now, where is or who manage your DHCP server? You should exclude the server IP from the DHCP pool to avoid conflicts.

---

### Post by snorkytheweasel on 2009-08-31
> **jocampo said:**
> You are all set my friend :-) ... just adjust that so you can assign and IP in the 10.1.0.0 network. Your IP will be in this range: 10.1.0.1 --> 10.1.255.254. DO NOT CHOOSE 10.1.1.1 because is the gateway and DO NOT CHOOSE 10.1.255.255 because is the broadcast address. 

Now, where is or who manage your DHCP server? You should exclude the server IP from the DHCP pool to avoid conflicts.

I'm only using DHCP because I can't make the static IP work. I have to assign 10.21.0.16[LIST=1]
[*]all of our servers have static IPs in 10.2x.xxx.xxx  range
[*]the boss sez use 10.21.1.16 /24
[*]all of the other servers inside the firewall run Windows, where this process is much easier
[*] this was never an issue until I upgraded to jaunty
[/LIST]

---

### Post by snorkytheweasel on 2009-08-31
> **bab1 said:**
> So it looks like we have a 16 bit network (/16 or 255.255.0.0).  This could give us IP addresses from 10.1.0.1 to 10.1.255.254.  The gw is not the first number in the range, but it is a good number.

Looking back at your static addressing scheme:```

/etc/resolv.conf
nameserver 10.1.1.10

/etc/network/interfaces (based on my TCP/IP calculations)
address 10.21.1.16      [COLOR="Red"]<--could be 10.1.1.136[/COLOR]
netmask 255.255.255.0   [COLOR="Red"]should be 255.255.0.0[/COLOR]
network 10.21.1.0 /24   [COLOR="Red"]should be 10.1.0.0 /16 [/COLOR]
broadcast 10.21.1.255   [COLOR="Red"]should be 10.1.255.255[/COLOR]
gateway 10.21.1.1       [COLOR="Red"]should be 10.1.1.1[/COLOR]

```

You are not even close.  The network 10.21.1.0/24 is off.  It looks as if you need to be in the range from 10.1.0.1 to 10.1.255.254. I think you will be fine with the addresses noted in red.


Edit:  BTW - Are you in Downey?

As noted elsewhere in this thread, for many reasons, the IP has to be 10.21.1.16 /24.

Downey? Isn't that a brand of butt-wipe?

If you're referring to Downey CA - assuming that it hasn't burned down or been swallowed by an earthquake - I'm just down the street. Turn left and go 1200 miles. Then ask at the gas station.

---

### Post by terazen on 2009-08-31
If your server has 10.21.1.16 with the subnet mask and default gateway like it's supposed to, and you still can't get to the internet you should ask the person who set up the network equipment (switch/router) what's wrong on their end.  Give them the server's mac address and they should be able to find where your server is plugged into their equipment.

---

### Post by snorkytheweasel on 2009-08-31
> **terazen said:**
> If your server has 10.21.1.16 with the subnet mask and default gateway like it's supposed to, and you still can't get to the internet you should ask the person who set up the network equipment (switch/router) what's wrong on their end.  Give them the server's mac address and they should be able to find where your server is plugged into their equipment.

The problem isn't getting to the internet. The problem is seeing the other 2400+ devices and having them see this server. With DHCP it works. With a static IP, I'm missing something.

---

### Post by terazen on 2009-08-31
On my network I only have 1 ip subnet per vlan so I'm just commenting on the way I do things.  But, if you pull dhcp from 10.1.x.x and you want to use 10.21.x.x then the network folks may have you on the wrong vlan.

Say vlan 10 has 10.1.x.x and vlan 20 has 10.21.x.x.  If your server is on vlan 10 then you will never be able to put 10.21.x.x ip on your server and get internet.  It will be able to pull dhcp 10.1.x.x and work.

Of course your network people could have put 2 ip subnets on the same vlan, but that's kinda rare.

---

### Post by Grim76 on 2009-08-31
One question that I do have and I don't see in the rest of the thread.  (Unless I missed it.)  Are you sure that the port on the switch you are using is in the right vlan?

---

### Post by snorkytheweasel on 2009-09-01
> **Grim76 said:**
> One question that I do have and I don't see in the rest of the thread.  (Unless I missed it.)  Are you sure that the port on the switch you are using is in the right vlan?

How can I determine that? Our expert on the switches is not often available.

---

### Post by Grim76 on 2009-09-01
As far as I know you would have to have access to the command line or configuration on the switch to know.

One thing you can try is if you know of another system that is supposed to be on that vlan, and that system is not critical you can swap the connections.  That would be a quick and dirty test to see.

---

### Post by snorkytheweasel on 2009-09-02
What's the smiley for relieved?

I tracked down the Cisco guy and asked him why I couldn't set up the IP on a subnet different from the one where I was working. After all, I do this all the time when setting up other servers, desktops, printers, etc. - remembering that the servers all had static IPs in 10. 0 - and everything else used DHCP in 10.10 or 10.30 or 10.40.

His response: 'you can and you did.'

'Huh?' said I.

'You have to plug the server into the switch for that subnet," he replied.
 
'But set up IPs all the time - from anywhere in the network,' I said.

'Not for 10.20,' he answered.

'Huh?' (that was I who "HUHed")

'10.20 is not trunked out of the "dungeon". The entire subnet is in the dungeon only,' he said. *[ Note: the "dungeon" is our main MDF for the WAN. It's located in the basement of a building a mile or so from my shop. ]*

Armed with that knowledge, I took the server to the Dungeon and connected it to the switch for 10.20. 

*Voilà!* It works!

So I told my boss - the one who told me to use 10.21.1.16 - how I got it working, i.e., connect to a switch in the dungeon.

'Huh?' said he. He didn't know that 10.20 wasn't trunked out with the rest of the WAN.

You've just seen community ignorance in action.

---

### Post by terazen on 2009-09-02
At least it isn't just where I work that does that.

---

### Post by snorkytheweasel on 2009-09-03
> **terazen said:**
> At least it isn't just where I work that does that.

Dilbert rules.

---

