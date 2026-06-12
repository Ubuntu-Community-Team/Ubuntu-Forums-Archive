---
title: "Set server to listen only"
date: 2010-11-02
forum: Security
---

### Post by R33P3R on 2010-11-02
I am trying to figure out how to turn my 10.10 server into a listener only. I  have it set up using snort/acidbase. It is grabbing my network traffic just  fine. I want to now set up a second server to hold all the data it collects. I  need to change the snort server so it only listens. I disabled ping responses,  but I want to go farther than that. I want to diable responses all together. I  want it to only grab the data and store it. 
  
 Can Anyone Help?

---

### Post by Ryan Dwyer on 2010-11-03
If you disable all outgoing data, how is it going to log the data to another server? You'd have to make an exception.

I'd start by looking at iptables.

---

### Post by Kinstonian on 2010-11-03
You're going to need two network cards.  For the sensor interface that snort is listening on you probably want to bring the interface up with the "promisc -arp up" ifconfig options.

---

### Post by R33P3R on 2010-11-03
Yeah, I definitely have 2 Nics. I figured I'd have to use it some time. Can you elaborate on the IPtables?

---

### Post by R33P3R on 2010-11-03
Ok, I've actually done some checking on IPTABLE setup. I found an Input drop command. If i set up an input drop command, will snort still be able to sniff the packets on the network? Will I have to set up different rules to allow snort through? Also, I would like to send the data snort collects to another machine on my network through the second nic card, does anyone know how to forward a file to another ubuntu machine on the network? I appreciate all the help so far!!

---

### Post by s1nch4n on 2010-11-04
> **R33P3R said:**
> Ok, I've actually done some checking on IPTABLE setup. I found an Input drop command. If i set up an input drop command, will snort still be able to sniff the packets on the network? Will I have to set up different rules to allow snort through? Also, I would like to send the data snort collects to another machine on my network through the second nic card, does anyone know how to forward a file to another ubuntu machine on the network? I appreciate all the help so far!!
rather than use complicated command in iptables, i think u can use ufw... [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

it should be more easy to set up...

---

### Post by R33P3R on 2010-11-04
@[s1nch4n]("http://ubuntuforums.org/member.php?u=1179901")  I checked it out. I want this thing to be as responsive as a brick. All I want it to do is sniff packets on the network. I don't want to be able to ping it, see it on the network or anything in that nature. The only way I want to be able to access it is through the console. I want it to be invisible. I dont think ufw is the right tool for this, or I just don't know how to configure it how i want it.

---

### Post by R33P3R on 2010-11-04
I have been using some iptables commands to block incoming connections. But when I do, snort stops working. I can't figure out what command syntax to use. I want snort to be able to sniff all packets on my network, but I don't want anyone to be able to see it, or access it.

---

### Post by Ryan Dwyer on 2010-11-04
You want to block outgoing connections, not incoming.

---

### Post by s1nch4n on 2010-11-04
> **R33P3R said:**
> I have been using some iptables commands to block incoming connections. But when I do, snort stops working. I can't figure out what command syntax to use. I want snort to be able to sniff all packets on my network, but I don't want anyone to be able to see it, or access it.
can i see your current iptables?

> **R33P3R said:**
> @[s1nch4n]("http://ubuntuforums.org/member.php?u=1179901")  I checked it out. I want this thing to be as responsive as a brick. All I want it to do is sniff packets on the network. I don't want to be able to ping it, see it on the network or anything in that nature. The only way I want to be able to access it is through the console. I want it to be invisible. I dont think ufw is the right tool for this, or I just don't know how to configure it how i want it.
so.. do you want to block "ping" responses on your server from another pc?

currently i'm using firehol to build iptables... is more easy for me than using iptables command...

here is my firehol.conf

> [FONT=Courier New]version 5

# Accept all client traffic on any interface[/FONT] [FONT=Courier New]
#interface any world
#       client all accept


lan_ips="192.168.1.10/24"[/FONT]  [FONT=Courier New]

interface eth1 LAN src "${lan_ips}"[/FONT] [FONT=Courier New]
        policy drop

        server "dns ftp samba squid dhcp http ssh icmp ntp webmin mysql"        accept[/FONT] [FONT=Courier New]

        client all      accept[/FONT] [FONT=Courier New]

interface eth0 Internet src not "${lan_ips} ${UNROUTEABLE_IPS}"[/FONT] [FONT=Courier New]
        protection strong 10/sec 10

        server ident reject with tcp-reset[/FONT] [FONT=Courier New]

        client all      accept[/FONT] 
in my firehol.conf configuration, my server respond ping from another pc.. but it doesn't respond ping from internet...

so if you don't want your server respond ping from local network, you can remove "icmp" from server command... 

note :

ping = icmp  services

---

### Post by Brakkez on 2010-11-05
I would suggest trying the following.


On the server where snort is installed:

Instead of blocking incoming traffic, you should block outgoing traffic. This way, your server will accept incoming traffic, and snort will process/log it.
By blocking outgoing traffic, your server won't respond to any of the incoming tcp/udp traffic, so no communication with your server will be possible (ping/ssh/..).

To be able to log to a log-server, you should allow ssh access to that log-server only.


On your log-server:

Block all incoming and outgoing traffic, exepct for ssh access to/from your snort-server.


I mention ssh here, but you can use whatever protocol you like offcourse (sftp/nfs/...)

---

### Post by Kinstonian on 2010-11-05
You don't use iptables, you use ifconfig with the options I said.

---

### Post by R33P3R on 2010-11-10
Thanks for the help everyone!!

I have it pretty secure now. The only thing I seem to have trouble with is nmap. It can still see my MAC Address, along with the hardware running my server. Anyone know how to stop that from happening?

---

### Post by Kinstonian on 2010-11-10
> **R33P3R said:**
> Thanks for the help everyone!!

I have it pretty secure now. The only thing I seem to have trouble with is nmap. It can still see my MAC Address, along with the hardware running my server. Anyone know how to stop that from happening?

Let me guess... you're still using iptables instead of ifconfig.  Nmap finds your MAC address because of [ARP](https://secure.wikimedia.org/wikipedia/en/wiki/Address_Resolution_Protocol).  If you used [ifconfig](http://www.linuxmanpages.com/man8/ifconfig.8.php) with -arp like I said, your interface won't use ARP.  If it doesn't use a layer 2 protocol like ARP, it won't use higher protocols like TCP or IP, etc.

---

### Post by R33P3R on 2010-11-10
Yeah, [Kinstonian]("http://ubuntuforums.org/member.php?u=639587") I am still using the iptables. I will try the ifconfig -arp. I will let you know what I find tomorrow. I can't mess with it right now, it is in production. I will give you my results sometime either Thursday or Friday. Please take a look back at this post then. Thanks, and I hope it works!!

---

