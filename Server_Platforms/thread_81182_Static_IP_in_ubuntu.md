---
title: "Static IP in ubuntu?"
date: 2005-10-23
forum: Server Platforms
---

### Post by OneSeventeen on 2005-10-23
I set up a server, and after installation, I convfigured /etc/network/interfaces to use a static IP.

It works great, I could connect to the server using the IP or the domain name assigned to that IP.

The day after I set it up, it appeared as though nothing worked, then I ran ifconfig and noticed it was using a dhcp IP instead of the static IP it had used previously.

/etc/init.d/network restart

okay, now it reread the network interfaces config file and is using the static IP again.  I changed the "auto eth1" line to show up after all of the static IP specifications, as someone in IRC suggested.

Here I am at the end of the weekend checking up on the server before heading into work tomorrow morning, and it looses all packets during a PING test, and the operation times out when I try to connect to the webserver with my browser.

It looks like it went to the dhcp server and got a new IP  again.

How do I keep it from getting dynamic IPs?  I really need this to stay static 100% of the time, and considering nobody is logging into the machine, it hasn't been rebooted, or anything, I am stumped.

The first time this happend I went back to the server and the screen was the exact same as when I left it before.  (meaning nobody logged in and changed things)

Tips, ideas, suggestions?

---

### Post by dbee on 2005-10-23
Just a thought ... but are you sure that you are assigned a static IP by your ISP ?

I mean if they have you on a dynamic IP, then there's no point in telling your machine to stay on a static one.

Have you thought about using dyndns.org ?

anyway, good luck with it ...

---

### Post by LordHunter317 on 2005-10-24
Post your /etc/network/interfaces.

---

### Post by bjweeks on 2005-10-24
What do you meen? A static ip from a router (LAN IP) (192.168.*.*) or a static ip from you ISP (WAN IP) (68.12.4.79) ?

---

### Post by OneSeventeen on 2005-10-24
When I get to work I'll post my config file.

This is a server at a major university here in New Mexico, and this is a static IP assigned by our central computing office.  I have used this IP for about 3 months while testing things on debian until Ubuntu 5.10 came out.

I am now thinking that I must have at least one variable in the interfaces file wrong.

Is there a plain english description of it?

Man interfaces defines "network" as "network address"... that doesn't really clear things up for me :p

---

### Post by OneSeventeen on 2005-10-24
[Here's my interfaces file](http://bin.woventhorns.com/hrwebserver.txt)

And the only things I know for sure are my address, netmask, and gateway.

I don't know what a broadcast even is (I'm tempted to delete it, since the man page says its optional, but my previous install had that autoconfigured so I left it in.), and I don't know what my "network" is either.

Is there an easy way to find out from other computers on the same network?  (i.e. can I use my windows box that is on the same network to find this out, or run a command to query the network or something?)

**EDIT:**  I just noticed that the IP in the network field is the IP for my DNS server, is that correct?

---

### Post by sanjose on 2005-10-24
iface eth1 inet static
        address 129.24.210.32
        netmask 255.255.248.0
###################################
# try to comment this first see if it will work
# cause i think dhclient will try to acquire this
#        network 129.24.8.1
#        broadcast 129.24.215.255
###################################
        gateway 129.24.208.1
auto eth1

---

### Post by OneSeventeen on 2005-10-24
hmmm.... I commented those out and restarted the network interfaces and it appears to still be working.  (I'm doing this remotely, so the fact that I'm still SSH'ed into the machine says the IP must be right)

So now I just have to wait until tomorrow to see if it will rever to dhcp again.

I have to admit, I didn't think that would work because I thought the new version of the kernel required the network field, but apparently not!

---

### Post by LordHunter317 on 2005-10-24
I'm reasonably certain if you remove the mapping for hotplug, things will work.

---

### Post by OneSeventeen on 2005-10-25
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#       script grep
#       map eth1

# The primary network interface
#iface eth1 inet dhcp
iface eth1 inet static
        address 129.24.210.32
        netmask 255.255.248.0

```

Okay, here's my new interfaces file... does this look right?

It went to DHCP *again* last night, so hopefully this will fix it, otherwise I don't know what I'm going to do.

---

### Post by OneSeventeen on 2005-10-25
My server just assigned itself a dhcp IP again!

I cannot view the website, nor can I connect to it via SSH nor ping it!

Any ideas before I format and install a different distro?  This is a real pain and shouldn't be happening.  I've never had a static-IP based computer change IP addresses, especially linux.  Linux is so cut-and-dry about things like this usually.

Any ideas of reasons my IP would change when I have it set to static IP only?  a /etc/init.d/networking restart *always* makes it reread the config file and properly gets its static IP back, so it doesn't look like a configuration issue to me, it looks like something is triggering it to get an IP from our dhcp server.

---

### Post by heimo on 2005-10-25
Well... If you can't figure out why it's doing that, you could try...
```
sudo apt-get --purge remove dhcp3-client dhcp-client
```
... it's a bit dirty trick and may cause new problems, but at least I would try it. If it still gets a dynamic configuration, you need a shaman (for the server). ;)

---

### Post by wmcbrine on 2005-10-26
How about this: System, Administration, Networking, Ethernet, Properties. What does it say? If it's not static, set it.

I'm an old hand at Linux networking, but when I set up Ubuntu (and when I upgraded to Breezy), I used the GUI like a Windows user. And I haven't had any problems.

Re: network and broadcast: A broadcast address is an address that reaches every machine on your LAN. A network address, in combination with a netmask, tells you which addresses the broadcast will reach. It's also the set of address that you can reach without going through a router. So for instance, on a typical home LAN using non-public IPs, the network address might be 192.168.1.0; the corresponding netmask would be 255.255.255.0, and the broadcast address would be 192.168.1.255. What this means is that machines on the LAN, reachable without routing, could be numbered between 192.168.1.1 and 192.168.1.254. (The network and broadcast addresses are reserved, and should not be assigned to machines.)

I'm just skimming the surface here. But the bottom line is, if you don't know what broadcast and network addresses are, then you probably shouldn't be messing with /etc/network/interfaces. No offense.

---

### Post by heimo on 2005-10-26
Here's nice online subnet calculator. This may make it a bit easier to understand the relations between hosts ip address, network address, subnet masks and broadcast addresses.
[http://www.subnet-calculator.com/](http://www.subnet-calculator.com/)

Personally I don't think it's dangerous for even amateur to edit interfaces file as long as you don't just guess the numbers, use the ones assigned by ISP / it-department and you should be fine. This applies to using the network admin GUI too, of course. Some people have reported having problems getting the network settings to "stick" using GUI and editing interfaces file was the solution. Not to argue with wmcbrine. Nice plain English explanations of ip/network/subnet/broadcast! :)[B]


[/B]

---

### Post by sanjose on 2005-10-26
[quote=OneSeventeen]My server just assigned itself a dhcp IP again!

I cannot view the website, nor can I connect to it via SSH nor ping it!

Any ideas before I format and install a different distro? This is a real pain and shouldn't be happening. I've never had a static-IP based computer change IP addresses, especially linux. Linux is so cut-and-dry about things like this usually.

Any ideas of reasons my IP would change when I have it set to static IP only?  a /etc/init.d/networking restart *always* makes it reread the config file and properly gets its static IP back, so it doesn't look like a configuration issue to me, it looks like something is triggering it to get an IP from our dhcp server.[/quote]


you forgot to add your gateway IP address that's why you can't ping.

can you post the result of ifconfig eth1 when it uses the dhcp not the static one.

and post also your /etc/dhcp3/dhclient.conf

---

### Post by cbkm on 2005-10-26
I had this problem once and it was because even though I'd given it a static IP, dhclient was still running and changing the IP each time the lease time expired.

So you may want to check:
```

$ pgrep dhclient

```

Which should not return a process number. ;)

---

### Post by OneSeventeen on 2005-10-26
Okay, here's the old ifconfig, the new ifconfig, and the result of pgrep dhclient:

[http://pastebin.com/406517](http://pastebin.com/406517)

Long story short, yes, pgrep dhclient returned a number.

How do I disable dhclient?

---

### Post by sanjose on 2005-10-26
do you mind posting your** /etc/dhcp3/dhclient.conf**

---

### Post by sanjose on 2005-10-26
[quote=OneSeventeen]```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#       script grep
#       map eth1

# The primary network interface
#iface eth1 inet dhcp
iface eth1 inet static
        address 129.24.210.32
        netmask 255.255.248.0

``` 
Okay, here's my new interfaces file... does this look right?

It went to DHCP *again* last night, so hopefully this will fix it, otherwise I don't know what I'm going to do.[/quote]


try adding here also your **gateway** which is [I][B]129.24.208.1

[/B][/I]

---

### Post by cbkm on 2005-10-26
[QUOTE=OneSeventeen]Okay, here's the old ifconfig, the new ifconfig, and the result of pgrep dhclient:

[http://pastebin.com/406517](http://pastebin.com/406517)

Long story short, yes, pgrep dhclient returned a number.

How do I disable dhclient?[/QUOTE]

It's already disabled since you change your /etc/network/interfaces file to not use dhcp. 

Personally, I'd just kill the process and be done with it.

---

### Post by OneSeventeen on 2005-10-26
[QUOTE=sanjose]do you mind posting your** /etc/dhcp3/dhclient.conf**[/QUOTE]
[http://pastebin.com/406735](http://pastebin.com/406735)

---

### Post by OneSeventeen on 2005-10-26
[QUOTE=cbkm]It's already disabled since you change your /etc/network/interfaces file to not use dhcp. 

Personally, I'd just kill the process and be done with it.[/QUOTE]
Cool, just ran #kill 5089 and pgrep dhclient no longer shows up.

That's what I was thinking I should do, but I didn't know if there were any reprocussions.

I'm used to working with windows where checking a box somewhere breaks 5 and a half things.

---

### Post by sanjose on 2005-10-26
if i not mistaken here is your old /etc/network/interfaces[INDENT]   iface eth1 inet static
        address 129.24.210.32
        netmask 255.255.248.0
        network 129.24.8.1
        broadcast 129.24.215.255
        gateway 129.24.208.1
auto eth1   
[/INDENT]i've made a little changes try this and restart your /etc/init.d/networking[INDENT]   iface eth1 inet static
        address 129.24.210.32
        netmask 255.255.248.0
        broadcast 129.24.255.255
        gateway 129.24.208.1
auto eth1 [/INDENT]see the difference from broadcast ip 
and also i remove network

the reason why i changed it co'z i thing your giving broadcast wrong ip

---

### Post by heimo on 2005-10-26
[quote=sanjose][INDENT]broadcast 129.24.215.255
*snip*
[/INDENT][INDENT]broadcast 129.24.255.255
[/INDENT] the reason why i changed it co'z i thing your giving broadcast wrong ip[/quote]

Nope. 129.24.215.255 looks good.

---

### Post by sanjose on 2005-10-26
[quote=heimo]Nope. 129.24.215.255 looks good.[/quote] 
why?

well i suggested it for a reason. when his interface reverted to dhcp it gives the broadcast ip i suggested. 
when giving static ip does it require also to hava a static broadcast.


anyway he could at least try my suggestion if it doesn't work well i guess its up to you to help him.
just trying to help here.

---

### Post by heimo on 2005-10-26
[quote=sanjose]why?[/quote]
For host address 129.24.210.32, in network 129.24.208.0/255.255.248.0 (not 129.24.8.1), broadcast address is 129.24.215.255. The network address is wrong and should be left out as suggested (or should be corrected in conf file if it's wrong there too). Sanjose, I'm not trying to argue, I see you're trying to help just like myself. :)

---

