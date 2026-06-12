---
title: "Any Cisco experts out there?"
date: 2007-02-07
forum: The Cafe
---

### Post by TravisNewman on 2007-02-07
Here's the thing. I have some secondhand Cisco hardware to teach myself the way of the beast. ;)

I have a Cisco 1751 router and a Cisco Catalyst 2924XL switch.

Currently what I'm running is a generic cable modem with a network everywhere router, and a few assorted hubs.

The Cisco 1751 has a T1 card, which is useless for connecting to a cable modem (if I understand correctly, that is). It only has a single ethernet connection (and from what I understand, if it had two this would be way easier).

I know I can't have the router directly link to the cable modem, HOWEVER, a friend told me that I should be able to connect the cable modem to one port (for example, port 24), connect the router to say port 23, and set up a vlan for ports 1-22 (or would it be 23?) and another vlan for port 24 (with the cable modem) and the router can route traffic between the two vlans using trunking. The cable modem must be dhcp, I can't set up a static IP with Charter.

The problem is, I have no clue how to do any of that ;)
I have basic Cisco experience. I've set up a new switch on an existing network, using the config from another router as an example. That took me a while though... I could save my company a lot of money if I could handle all this myself, and I'm hoping this will be a learning experience. Setting up trunking on a router and separate vlans should give me some experience eh?

A guess... I imagine I MAY need to use the network everywhere router on a 10.0.x.x network and the vlan on the first 22 or 23 ports (however that should be arranged) on a 10.1.x.x network, since I may not be able to assign a network to JUST the cable modem. That's definitely a possibility.

Three less important questions:
Both the router and switch already have a config on them, and dhcp is not enabled. I would prefer to have that enabled, with the possibility of also using static IPs. 

Can I configure VPN without a firewall? Our VPN at work is configured on our Cisco PIX firewall. If I can set up a VPN with JUST the router and switch, I would love to, but the fact that I have to use separate vlans for the cable modem and everything else may cause issues with that.

I'd also like to set up a smoothwall server on the network. Where in the network should that be? between the cable modem and the switch? Just on another port on the switch?

That's a lot, I know, hopefully some people can help out, There's a lot to accomplish and I just don't know where to start.

---

### Post by MrHorus on 2007-02-08
My understanding is that for example, you want to put the cable modem on a vlan of one port, put the other ports into another vlan and route between them with the router?

In theory I do think this will work and I would be happy to give you as much advice and assistance as possible.

I set up something similar to this a couple years ago at my old flat but I had a 4000 Series router that had 4 Ethernet ports, so things were a lot simpler ;)

Drop me a PM to remind me and I'll do my best to drop you a reply with as much information as possible on how to set this up but right now i'm utterly rammed with work and things and won't be free to reply really until saturday night.

Depends how urgent you are for this :)

---

### Post by mips on 2007-02-08
What you want to do is possible but depends on whether the router ethernet port supports trunking.

Please draw a diagram (with Dia or Kivio or whatever and save theoutput as .png) of the layout and IP addressing you want. What connects to which switchport number etc. the more detail the better. Also include a diagram of your existing setup and how everything fits together, maybe do this one first then we can discuss your goals.

How many hosts in your company as using 10.1 with a 255.255.0.0 mask might just be overkill.

If you do the above then I will do the router & switch configs for you. Which country/time zone are you in as i can set the router up for ntp.

Edit: I have completed the switch config but just have to fill in some of the blanks i left wrt addressing etc.

---

### Post by mips on 2007-02-08
> **panickedthumb said:**
> 
...since I may not be able to assign a network to JUST the cable modem. That's definitely a possibility.


That would be the idea. Then run inter vlan routing with NAT.

---

### Post by TravisNewman on 2007-02-08
Well this isn't for my company, this is for my home network :) I'm just playing to learn Cisco really.

So all I'm picky about is that I want my comptuers to be 10.0.0.xxx but the router/switch/whatever can be anything really. At any given moment there will be anywhere from 1-10 computers on in my house, so you're right, 255.255.0.0 would be overkill.

I was thinking about using port 24 for the cable modem, port 23 for the router, and ports 1-22 as hosts. Like I said before, I probably want to add a smoothwall firewall in there as well, I don't know what all needs to be done to add a firewall to a network, I know that traffic somehow has to be routed through it, but that's about it.

So here's my basic diagram:

---

### Post by TravisNewman on 2007-02-08
oh and current setup, I don't really need a diagram....

world->Cable modem->network everywhere router-> comptuers
My computers are currently on a 10.0.0.XXX network, DHCP enabled (which I want on the new setup as well).

---

### Post by mips on 2007-02-09
Ok, this is easy to do, the switch config I did matches what you gave me. I just have to do the router config now but I'm on my out so will probably on get a chance tonight.

I'll leave the smoothwall firewall out for now. We can add it later, let's just get the basic networking up and running.

---

### Post by TravisNewman on 2007-02-09
> **mips said:**
> Ok, this is easy to do, the switch config I did matches what you gave me. I just have to do the router config now but I'm on my out so will probably on get a chance tonight.

I'll leave the smoothwall firewall out for now. We can add it later, let's just get the basic networking up and running.

Awesome, you rock :)

---

### Post by mips on 2007-02-11
Sorry, one last request.

Please email the current router config then clear that config and post the now cleared config here. I need a bit of info with regards to interfaces & how it boots flash etc from that. I will PM you my email address.

Also need your cable modems ip address and next hop address (The adress of what the cable modem connects to on the other side). Can you get your ISPs DNS server IP's as well. ntp server would be nice to. If you cannot find the last to just tell me who your ISP is and i'll scratch around a bit.

I think I have finished all the configs now and just need the above to add the finishing touches.

---

### Post by TravisNewman on 2007-02-11
One problem... I can't have a static ip with my cable modem... they'll cut off my access if I set it up static.

---

### Post by mips on 2007-02-11
> **panickedthumb said:**
> One problem... I can't have a static ip with my cable modem... they'll cut off my access if I set it up static.

Not to worry, I set it up so the Cisco router requests an IP address via dhcp from the cable modem. It then does NAT between the isp allocated address and the dhcp server allocated 10.0.0.x addresses on the router between two sub interfaces.

I however require the next hop address to configure the default route and that would be the cable concentrator device on their end which your cable modem connects to.


maybe you can get it by doing a traceroute or checking the cable modems diagnostics which should be available via a web interface.

---

### Post by TravisNewman on 2007-02-11
oh ok, I understand your question now. Sorry, I'd just woken up :)

I'm about to email you everything you asked for.

---

### Post by mips on 2007-02-11
The configs are in the mail.

More believable than saying the checque is in the mail ;)

---

### Post by TravisNewman on 2007-02-11
> **mips said:**
> The configs are in the mail.

More believable than saying the checque is in the mail ;)

Everything seems to work... except the internet :)

vlan2 on the switch (for WAN access) is administratively down, no matter how many "no shutdown"s I throw at it.

Also, the ip address dhcp on interface fastethernet0/0.2 (vlan2 access) doesn't seem to be a valid command.

Put the two together, and that's probably why it's not going out.

Thanks for all your help mips, I really do appreciate it. I've been kinda researching things and learning about them while going through the config, so this has definitely been a learning experience.

if anyone else in mips' absence has a clue as to why that isn't working, I'm all ears :)

---

### Post by mips on 2007-02-11
Almost midnight here, time for bed so i will have a look tomorrow.

ip address dhcp is definately a valid command. Maybe it cannot be used on a sub-interface but that is unlikely. Try it on the main interface Fastethernet0/0 and see if it makes a difference just to see if it works or not or spews out the same invalid command. The only other thing i can think of is that it is a IOS version dependancy. Which IOS version are you running, gimme the IOS image name as save in flash and i will look it up ?

I will look into the VLAN2 issue later. Something just came to mind, if i recall correctly the 2924XL (or was it the 1924 series) had a seperate VLAN menu where you could specify/setup many things with regards to VLANS, bridge groups etc I will have to look this up.

If you want you can have a look at the Cisco site in the meantime which has very good documentation & there forums are also good.

---

### Post by TravisNewman on 2007-02-11
Well, looks like you're right... it doesn't work on the sub-interface, but it would allow me to do it on the main interface. But the vlan is still administratively down.

The image name is: c1700-bnr2y-mz.122-4.T.bin

---

### Post by TravisNewman on 2007-02-11
I found this, but it's a bit over my head :( I think it has everything to do with my issues though...
[http://www.webhostingtalk.com/showthread.php?t=508593](http://www.webhostingtalk.com/showthread.php?t=508593)

---

### Post by mips on 2007-02-12
> **panickedthumb said:**
> I found this, but it's a bit over my head :( I think it has everything to do with my issues though...
[http://www.webhostingtalk.com/showthread.php?t=508593](http://www.webhostingtalk.com/showthread.php?t=508593)

Thanks for jogging my memory. That thread is correct, remove VLAN 2. The vlans get configured in the VLAN database.

To access the VLAN database and configure your vlans see example:

```

enable
vlan database
vlan 2 VLAN-2
vlan 3 VLAN-3
vlan (the number of the ID) (name the vlan ex. technical) --> vlan 2
tecnical
vtp **server** / client / tranparent
vtp domain newman

vtp password xxxxx

exit

```

You cannot modify any of the parameters for VLAN 1.

  (vlan) **vlan** *vlan-id* [**name** *vlan-name*] [**state** {**suspend** | **active**}] [**mtu** *mtu-size*] 


**show vtp 	 status** and the **show vlan** for diagnostics checking.

For the **ip address dhcp** we might have to follow a different path. Instead of creating sub interfaces we just have a main interface and then configure vlans interfaces on on the router to corrospond to those on the switch.

---

### Post by mips on 2007-02-12
Did i add this for the dhcp server ? **service dhcp**

---

### Post by mips on 2007-02-12
Try this, I think it will work. The one very obvious mistake I made was to leave out the encapsulation type and it will NEVER work without that ](*,)
I need to work on my copy and paste skill.


Just add the lines below, don't remove any existing configs you have on these interfaces.
```

interface FastEthernet0/0
mac-address 0007.eb32.c42d

interface FastEthernet0/0.2
 description WAN VLAN 2
 encapsulation dot1q 2
 ip address dhcp client-id FastEthernet0/0 hostname newmanrouter
 ip nat outside 
 no ip route-cache
 no cdp enable
 no shutdown
```The router was providing the wrong MAC address seeing the DHCP request originates from a sub-interface which has it's own MAC address. I'm merely repeating the hardware address in the cofig and telling dhcp to use FastEth0/0 as the identifying device. Hostname part might not be required but from reading a bit I gather that some isps might require it so no harm done.

---

### Post by TravisNewman on 2007-02-12
Writing in from work...

I won't have a chance to test these things out until Friday evening, I'm going to be housesitting this week. I'll definitely try this stuff out then, and I'll keep looking around on the web for stuff as well.

---

### Post by mips on 2007-02-12
> **panickedthumb said:**
> Writing in from work...

I won't have a chance to test these things out until Friday evening, I'm going to be housesitting this week. I'll definitely try this stuff out then, and I'll keep looking around on the web for stuff as well.

The ip address dhcp thing should work on a subinterface as I actually found another example on the net where the guy also connected to a cable modem and also only had 1 physical interface and had to do vlans.

---

### Post by TravisNewman on 2007-02-17
it's really not working... hmm...
```
newmanrouter(config-subif)#$nt-id FastEthernet0/0 hostname newmanrouter
 ip address dhcp client-id FastEthernet0/0 hostname newmanrouter
            ^
% Invalid input detected at '^' marker.
newmanrouter(config-subif)#ip address ?
  A.B.C.D  IP address
```Should I upgrade the IOS you think?

And I'm still totally confused about the vlan config... not sure what I should do... I need to leave vlan1 in the router config, but remove vlan2 and configure it via the vlan databse right? Is the syntax the same for it?

BTW: The first command wrapped in the terminal. I put it in right :)

---

### Post by mips on 2007-02-18
I'll get back to you.

If you have access to a newer IOS then try it.

---

### Post by TravisNewman on 2007-02-18
Well I tried it, misreading the reqirements and now the router won't boot ;)
 
I'm going to see about downgrading. It seems the release I WAS on was the only one that it has ram for (though the flash could have held it), but it was only a couple of revisions back anyway.

---

### Post by gmulak on 2007-04-05
I have an even more basic question.  I am taking a Cisco CCNA class and need a terminal to do that.  I use "Hyperterminal" from Graeves to connect into the routers console port from the serial port on my PIII in Windows, but I don't know how to do that on a Ubuntu Linux machine.  I am assuming I use a terminal window, but how do I use it and send commands out the Com1 port?   

Sorry to borther anyone, but I am such a newbie, I have tried to read the forums but I don't even know what to search on for help.

Thank you.
George

---

### Post by lynxus on 2007-07-31
> **gmulak said:**
> I have an even more basic question.  I am taking a Cisco CCNA class and need a terminal to do that.  I use "Hyperterminal" from Graeves to connect into the routers console port from the serial port on my PIII in Windows, but I don't know how to do that on a Ubuntu Linux machine.  I am assuming I use a terminal window, but how do I use it and send commands out the Com1 port?   

Sorry to borther anyone, but I am such a newbie, I have tried to read the forums but I don't even know what to search on for help.

Thank you.
George



Yes use hyper terminal.
Use the blue/cyan cable that comes with the cisco kit

In Ubuntu install a program called MINICOM.

apt-get install minicom ( if it isnt already installed.

then:
sudo minicom

when inside press i think ctrl+z and set it up from there.

Settings as follows:

Bits per sec    :  9600 
Data bits       :     8 
Parity          :  none 
Stop bits       :     1 
Flow control    :  none

---

