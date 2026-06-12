---
title: "machine named &quot;ubuntu&quot; has shown up somewhere on our network"
date: 2007-06-21
forum: Server Platforms
---

### Post by Brazen on 2007-06-21
A machine named "ubuntu" has shown up on our network and I don't know where it came from.  I'm not _too_ worried about it, but I would like to figure out more about the machine, particularly it's location.  Our users are not supposed to make changes to the computers configuration and they are not supposed to bring in outside computers.

So anyway, I'm too worried about an Ubuntu machine being on our network (we have a couple Ubuntu servers, anyway) but I would like to be able to find any information that can help find who is breaking the rules.  Any ideas?

---

### Post by tgalati4 on 2007-06-21
If someone sticks a Live CD into their machine and boots it, then it will probably show up as "ubuntu".

If the client is not actually installing the software onto the computer is that still a violation of your company's policy?

In a windows command line:  ping ubuntu 

See what the IP address is.  This will probably be the same as under Windows assuming your network uses DHCP and the ethernet switch will tend to keep the same address for the same MAC address.

Look for a brown theme on the computer as you walk around.

Most important, send an email with a restatement of the company policy and see if the behavior continues.

Of course if you switched your entire shop to Ubuntu then this wouldn't be a problem.

---

### Post by WinterWeaver on 2007-06-21
Oh crap! .... which company!? .... please dont fire me!

---

### Post by arvevans on 2007-06-21
Your router or managed Ethernet hub will have the MAC address tables of computers that are connected to your network.  If you have a list of the MAC numbers for those computers you have added to the network, then you can cross reference it that way.  Look into using ARP and RARP to view the arp tables.

A good network sniffer on the LAN can also capture and decode packets from your "Ubuntu" based user and thus tell you what he/her is doing, and what computer is doing it.  Linux hosts several network sniffers, including  dsnif, ettercap, ethereal, etc.
_._

---

### Post by Brazen on 2007-06-21
> **tgalati4 said:**
> If someone sticks a Live CD into their machine and boots it, then it will probably show up as "ubuntu".

If the client is not actually installing the software onto the computer is that still a violation of your company's policy?

In a windows command line:  ping ubuntu 

See what the IP address is.  This will probably be the same as under Windows assuming your network uses DHCP and the ethernet switch will tend to keep the same address for the same MAC address.

Look for a brown theme on the computer as you walk around.

Most important, send an email with a restatement of the company policy and see if the behavior continues.

Of course if you switched your entire shop to Ubuntu then this wouldn't be a problem.

You're preaching to the choir or switching the entire shop to Ubuntu :D  I did send out the email.  I'll keep an eye on the MAC address to see if it was a LiveCD and comes back as one of our standard machines.  Then I'll know what computer it is based on it's machine name.  That's a good idea, and I fired up one of my livecds and it does give a hostname of ubuntu.

---

### Post by Brazen on 2007-06-21
> **arvevans@earthlink.net said:**
> Your router or managed Ethernet hub will have the MAC address tables of computers that are connected to your network.  If you have a list of the MAC numbers for those computers you have added to the network, then you can cross reference it that way.  Look into using ARP and RARP to view the arp tables.

A good network sniffer on the LAN can also capture and decode packets from your "Ubuntu" based user and thus tell you what he/her is doing, and what computer is doing it.  Linux hosts several network sniffers, including  dsnif, ettercap, ethereal, etc.
_._

The only problem with looking it up on our switches is, we have about 50 managed switches, which would probably take more time then it's worth unless I was lucky and found it on one of the first couple I checked.

---

### Post by 919Guy on 2007-06-22
Do you have a core router or some central device?  I'd look up the MAC on that first, and work outwards until you reach the switch where the machine is plugged in.

---

