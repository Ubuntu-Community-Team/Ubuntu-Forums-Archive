---
title: "Wake on lan/WAN"
date: 2011-10-06
forum: Server Platforms
---

### Post by 6sl7g12xW4 on 2011-10-06
So I configured my ubuntu server to wake on lan using ethtool (with magicpacket)
Internal it isn't a problem, I just give the command wakeonlan (macaddres) and it turns on.
But when I try to do it over the internet, it will not turn on.

I set open port 7 & 9 on my router and it indicates a package is being send to the server. But it still doesn't wake-up. So I tried to see what the wakeonlan command sends, but unfortunately the packet sniffers don't recognise my network card (pc, not server). 

I already tried to google it and went through a lot of pages/fixes but it still doesn't work and I really don't have a clue where to search anymore.

Hope someone can help!

---

### Post by drdos2006 on 2011-10-06
I copied this from one of the forum requests. Hope it helps.

> 
Can't get Wake on LAN to work
I'm trying to get WOL to work on my web server built on an ASUS P4A800D-X motherboard (which supports wol).

I have it enabled in my BIOS and I've tried several different tools with no results, including my dd-wrt based router which has this functionality built into the firmware.

All the guides I've read say it has to be enabled in the driver settings in the Windows Control panel before it will work, but I'm running Ubuntu Server 10.04.

Is there any special steps that must be taken in the OS to enable my web server to power on from the LAN? I've never used this feature before and would like to just shove my web server in a corner some where and have 100% remote control from my main PC.

Found the solution to my own problem while searching for info on server hibernation.

Code:

sudo apt-get install pm-utils ethtool

Run
Code:

sudo ethtool -s eth0 wol g

and add it to /etc/rc.local to run at boot.

After running this command my server wakes properly from a powered off state when sending a magic packet.


regards

---

### Post by tgalati4 on 2011-10-06
It's possible that your router has additional security such as Stateful Packet Inspection (SPI) and it simply rejects packets that it doesn't recognize as a valid TCP/IP protocol.

You could try to install open source firmware on your router such as dd-wrt, I believe it has WOL capability.

I have set up WOL scripts to wake other machines internally on my network, but that requires me to log into my machine remotely and run the script or set up a script within Drupal if you are running a website for instance.

---

### Post by volkswagner on 2011-10-06
Here is a nice tool for testing.

[http://www.dslreports.com/wakeup](http://www.dslreports.com/wakeup)

I once setup WOL on a Linksys WRT54G, I had to change my subnet form 255.255.255.0 to 255.255.255.128.  There was something about the broadcast address that would not work otherwise.  This may or may not be an issue for you.

Also on you router port forward you can't forward port 9 to the machine ip you are trying to wake since there is no IP for a sleeping machine.  You need to set it to a broadcast address and the machine with matching mac address shall respond.

---

### Post by 6sl7g12xW4 on 2011-10-07
Thanks for the tips.
It ultimately took me here: [http://www.dslreports.com/forum/remark,3806194~root=wakeonlan~mode=flat](http://www.dslreports.com/forum/remark,3806194~root=wakeonlan~mode=flat)

So I want to wake up internal ip 192.168.2.178. My router is connected at 192.168.2.1, so I send a broadcast at 192.168.2.255. 
Then in theory, it sends a magic packet to all the devices connected to 192.168.2.*

But commenting on Volkswagner: my subnet from my router is 255.255.248.0 and I can't find a way to change it in my router, so it may be a problem there?

I tried looking at installing the other firmware, but my router isn't supported, so this is not an option.

Any other ideas I can try?

---

### Post by volkswagner on 2011-10-07
I will not even pretend to be an expert on subnetting.

Perhaps you can run an ipconfig on the machine you are waking to verify the broadcast address.

```
ipconfig
```

What model router are you using?   I find it strange if you can't change the subnet.

---

### Post by Jonathan L on 2011-10-07
> **lordfreak3012 said:**
> Thanks for the tips.
It ultimately took me here: [http://www.dslreports.com/forum/remark,3806194~root=wakeonlan~mode=flat]("http://www.dslreports.com/forum/remark,3806194%7Eroot=wakeonlan%7Emode=flat")

So I want to wake up internal ip 192.168.2.178. My router is connected at 192.168.2.1, so I send a broadcast at 192.168.2.255. 
Then in theory, it sends a magic packet to all the devices connected to 192.168.2.*

But commenting on Volkswagner: my subnet from my router is 255.255.248.0 and I can't find a way to change it in my router, so it may be a problem there?

I tried looking at installing the other firmware, but my router isn't supported, so this is not an option.

Any other ideas I can try?

Hi ..

I am as surprised as the others that you can't change your subnet.  Nonetheless if you really can't, or choose not to, if your router has a mask 255.255.248.0, then the broadcast address is 192.168.7.255.

Calculation: 255.255.248.0 is a /21: it's 21 '1's followed by 11 '0's, giving 32 bits.
The broadcast address is therefore the first 21 bits of the router address 192.168.2.1, followed by 11 '1's, which gives 192.168.0.0 + 0.0.7.255 = 192.168.7.255.

Be aware that many routers block this kind of directed broadcast.  It might be possible to add permanent arp table entries though, where you tell the router that 192.168.2.178 = 12:34:56:78:ab:cd ether address.  If that doesn't work on the router, perhaps there's another computer that you can do it from.

Hope that helps.  Let us know if it works.

Regards,
Jonathan.

---

### Post by 6sl7g12xW4 on 2011-10-07
Hey guys,

So after some more searching I was able to change the subnet. 
It was named subnet on my router, thus the confusion.
The subnet is now set to 255.255.255.128 .
An ifconfig on the server now tells me it's broadcast address is 192.168.2.127.
So I portforwarded port 9 to that address, unfortunately with little success.
I did however find something else on my router called routing.
So essentialy it says create fixed routes to fixed destinations.

I can set the IP (I assume this will be the broadcast IP), netmask, gateway and metric (some number) and interface (wan/lan). Maybe  I need to set this instead? although I have no idea what the settings should be.

Thanks for you help so far!

edit: I also tried turning off SPI with no succes

---

### Post by Vegan on 2011-10-07
WoL needs a machine that has support in the BIOS and is in standby.

My old dead IBM used to support it

---

### Post by Jonathan L on 2011-10-08
> **lordfreak3012 said:**
> Hey guys,

So after some more searching I was able to change the subnet. 
It was named subnet on my router, thus the confusion.
The subnet is now set to 255.255.255.128 .
An ifconfig on the server now tells me it's broadcast address is 192.168.2.127.
So I portforwarded port 9 to that address, unfortunately with little success.
I did however find something else on my router called routing.
So essentialy it says create fixed routes to fixed destinations.

I can set the IP (I assume this will be the broadcast IP), netmask, gateway and metric (some number) and interface (wan/lan). Maybe  I need to set this instead? although I have no idea what the settings should be.

Thanks for you help so far!

edit: I also tried turning off SPI with no succes

Hi

Wake on LAN requires you to be able to send a packet to a sleeping machine, either by broadcast (normal method) or a packet to the correct ethernet address, if you can somehow specify that (depends entirely on your router, but it's rare for domestic routers).

The normal routing table won't help at all because that requires IP addresses, which don't form part of the wake-on-LAN packet.  (So I'd ignore the routing table of your router.)  Typically the wakeup packet is wrapped in a UDP packet, but but you can't use send it to the victim's IP address as there's no ARP to find the ether addres.

To test what you've got, may I suggest the following:

[LIST=1]
[*]Have the server on (the one you want to wake up)
[*]Run tcpdump or wireshark to look at the incoming packets for its own ether address and broadcasts ```
 sudo tcpdump -i eth0 -n -e ether host 11:22:33:44:55:66 or ether broadcast
```
[*]send it a wakeup packet from a local machine
[*]send it a wakeup packet from a remote machine
[/LIST]

Obviously, as it's already awake, the wake-on-LAN packets won't have any effect, but you will be able tos if it is correctly receiving them.  My guess is that your router isn't forwarding them as a broadcast, and step 4 will be silent.

If there's a suitable function on your router try ping 192.168.2.127 (ie, the broadcast address) and see if that is allowed and shows on your server.

Hope that's of some use

Kind regards
Jonathan.

---

### Post by 6sl7g12xW4 on 2011-10-08
Thanks for the tip with the command, was searching for something like that!

So, you are right the external packet does not reach the server, while the internal does.
Unfortunately I can not set up ARP tables in my router, and I can not leave another computer on with the tables on it, so I guess this is not an option.

I could ping from the router, so I pinged the broadcast address with no response. Directly pinging my server does work, so the problem lies with the broadcast address I guess.

But I can't just set another broadcast address? (with changing subnet but both 255.255.255.0 /.128 didn't have any effect). 

For info, my router is a SMCWBR14-N2

---

### Post by Jonathan L on 2011-10-08
> **lordfreak3012 said:**
> Thanks for the tip with the command, was searching for something like that!

So, you are right the external packet does not reach the server, while the internal does.
Unfortunately I can not set up ARP tables in my router, and I can not leave another computer on with the tables on it, so I guess this is not an option.

I could ping from the router, so I pinged the broadcast address with no response. Directly pinging my server does work, so the problem lies with the broadcast address I guess.

But I can't just set another broadcast address? (with changing subnet but both 255.255.255.0 /.128 didn't have any effect). 

For info, my router is a SMCWBR14-N2

Hi LF

Manual is at [http://www.smc.com/files/AN/MN_SMCWBR14-N2.pdf](http://www.smc.com/files/AN/MN_SMCWBR14-N2.pdf)

I took a look at the manual for your router and it specifically says it supports Wake On LAN, in the advanced firewall section of the manual. I'm pretty sure it can be made to work.   I see it also has a place to put the ethernet address of your server,  as a "DHCP reservation", which may also preload the ARP cache, which would be the second thing I'd try.

I'd go back to 192.168.2.0/24 for your network, with netmask 255.255.255.0 and broadcast address 192.168.2.255.   On the virtual server page, forward ports7 and 9 or whatever you're using for UDP (not TCP) to the broadcast address 192.168.2.255,  Switch on WOL per manual.  Test as before with tcpdump.

My belief is that the "Wake On Lan" box must be ticked on in the the  "Application Level Gateway configuration" (diagram on p42) to make the  broadcast work.  And I'm just wondering whether you've got port forwarding for UDP correct, not TCP.

If for some reason that doesn't work, I'd try putting the ethernet  address in the DHCP reservation for your server at 192.168.2.178, put the same address for ports 7 and 9 on the virtual server page, for UDP not TCP.   Test as before.

Notes from Manual
[INDENT]**Wake-On-LAN (p46, diagram on p42)**
[/INDENT][INDENT]This feature enables forwarding of "magic packets" (that is, specially formatted wake-up
packets) from the WAN to a LAN computer or other device that is "Wake on LAN" (WOL) capable. The WOL device must be defined as such on the Advanced &#8594; Virtual Server page. The LAN IP address for the virtual server is typically set to the broadcast address 192.168.2.255. The computer on the LAN whose MAC address is contained in the magic packet will be awakened.
[/INDENT][INDENT]**Add/Edit DHCP Reservation (p22)**
[/INDENT][INDENT]This option lets you reserve IP addresses, and assign the same IP address to the network device with the specified MAC address any time it requests an IP address. This is almost the same as when a device has a static IP address except that the device must still request an IP address from the router. The router will provide the device the same IP address every time. DHCP Reservations are helpful for server computers on the local network that are hosting applications such as Web and FTP. Servers on your network should either use a static IP address or use this option.
[/INDENT]Let us know how you get on.

Regards,
Jonathan.

---

### Post by 6sl7g12xW4 on 2011-10-09
Hi Jonathan,

The wake on lan option was already on and the port was open.
Also, the server already had a DHCP reservation.

So I decided to see if the port really was open. I configured the router to directly send port 9 to the server, put the server on, to see if it worked.
But no success. So I just a site to see if my port really was open and it said it was closed. Other ports which I set open in the router under the same circumstance (although really high numbers) did get a response. So could it be my ISP is blocking port 9? 
Is there any way that I can change the port for wake on lan to another port? (although from what I understand it depends on your hardware which port it uses).

---

### Post by Jonathan L on 2011-10-09
> **lordfreak3012 said:**
> Hi Jonathan,

The wake on lan option was already on and the port was open.
Also, the server already had a DHCP reservation.

So I decided to see if the port really was open. I configured the router to directly send port 9 to the server, put the server on, to see if it worked.
But no success. So I just a site to see if my port really was open and it said it was closed. Other ports which I set open in the router under the same circumstance (although really high numbers) did get a response. So could it be my ISP is blocking port 9? 
Is there any way that I can change the port for wake on lan to another port? (although from what I understand it depends on your hardware which port it uses).

Hi Again LF

You can use any port you like: the ports are just faked for the purposes of getting the packet to the server.

To explain that better: wake-on-LAN works at the ethernet level.  The server is in a standby mode where it is waiting for an ethernet frame with certain contents.  That frame can by any kind of frame whatseover, just so long as a) it is sent to the right computer (normally by broadcast, so everybody gets it), and b) somewhere inside it are the right 'magic bits' which will cause the computer to wake up.  Part of those bits are the ethernet address of the machine which is suppose to wake up.  The rest of the frame is ignored, by the wake-on-LAN system, including any IP header or details.  If we put these magic bits inside IP packets everything will work fine, and, if your packets are to traverse the internet, then they must be inside IP packets, with suitable addresses to route them to your computer.

You can put them inside any kind of packet, though the easiest is UDP, to any port number you like.  Wake-on-LAN is usually used with ports 7 or 9, whose normal purposes are echo and discard (see /etc/services for list).

If you want to use a different port, go right ahead.  Ideas for UDP port numbers which your ISP is unlikely to block would be 13 (daytime), 37 (time), 49 (tacacs). 53 (domain), 69 (tftp), 123 (ntp), 161 (snmp), 162 (snmp-trap), 179 (bgp), 512 (biff), 513 (who), 514 (syslog), 1812 (radius), 1823 (radius-acct).  They are quite likely to have blocked almost everything < 1024, but even an ISP which is just selling you "plain web surfing" access can't really block DNS or NTP; or try a high number one first.  You can also use a number such as 8000 or 10000.  

If you think that your ISP is blocking certain ports, you can test this by sending yourself various packets on different port numbers and monitoring on your server:
```
sudo tcpdump -i eth0 -eXn ip proto \\udp or ether broadcast
```note -e show ether header, -X show hex, -n show numbers, and you want to see all ether broadcasts too

Hope that helps.  Let us know how you get on.

Jonathan

---

### Post by 6sl7g12xW4 on 2011-10-12
Hi Jonathan,

First of all I want to say thanks for also posting a lot of side information. This way I can understand (a little) what's happening instead of just fixing a problem without knowing what I did.

But unfortunately, it still doesn't work. I tried checking other computers if they received packages. From lan no problem but not from the internet. Tried to change some settings, still no success.
So I googled about it in combination with my provider and the main conclusion is that it can't be done. 
A lot more people tried it, but just ended up not solving it. 
So thanks for your help, and I'm going to try to contact my ISP and see if they can help me.

---

### Post by 6sl7g12xW4 on 2011-10-12
So my ISP says, nope we can not help you.
Also they don't allow access to the modem so I can't see if that is blocking my packets.

So, unfortunately it is not going to work :(

thanks for all you help guys!

---

### Post by Jonathan L on 2011-10-12
> **lordfreak3012 said:**
> So my ISP says, nope we can not help you.
Also they don't allow access to the modem so I can't see if that is blocking my packets.

So, unfortunately it is not going to work :(

thanks for all you help guys!

Hi 

It's almost certainly still possible, despite what the ISP says, just sometimes takes a bit of ingenuity.

I'd definitely try sending yourself DNS and NTP packets from a distant computer and using tcpdump on your server to see if they arrive.

Kind regards,
Jonathan

---

### Post by Jonathan L on 2011-10-12
> **lordfreak3012 said:**
> So my ISP says, nope we can not help you.
Also they don't allow access to the modem so I can't see if that is blocking my packets.

So, unfortunately it is not going to work :(

thanks for all you help guys!

Well ... LF and I gave it a really good thrash for a couple of hours and we found out that:

[LIST]
[*]Syslog packets get through the ISP perfectly on port 514, and if you have port forwarding for UDP 514 forwarded to a real IP address of the server, 192.168.2.7, they arrive perfectly.
[*]Port forwarding on this router is extremely peculiar and doesn't do what the manual says
[*]We changed it to a usual 255.255.255.0 mask and forwarded port 514 UDP packets to 192.168.2.255 but without success.  Indeed, the router seemed to send things to very strange addresses.  Even with the Wake-On-LAN feature of the router enabled, we would sometimes get nothing, sometimes get the previous settings, and so on.  We tried lots of different settings, and did copious reboots.
[*]The only thing which still sounds possible is a factory-reset of the router, followed by minimal config to see if the advertised Wake-On-LAN features work then.
[/LIST]
Conclusion: ISP perfectly usable, router very peculiar indeed 

Jonathan

---

