---
title: "IP Address not seen on Internet"
date: 2007-06-10
forum: Server Platforms
---

### Post by geakMonkey on 2007-06-10
I had a Security Breach: some hackers logged onto my Ubuntu 6.06 LTS. It has been running mostly non-stop since the beginning of the year. I discovered the hackers logging onto the console. After I turned off the machine, unplugged it from the dsl router, did some research for my router firewall, and am now buildign a BSD Firewall box, I have not been able to get my Web Server IP Address seen from the outside world again. 

I did nothing to the server per se. Since that time, I have been trying to look at every thing using nmap, nestat, apache config files. I cannot see anything wrong. How do I get Ubuntu back on the net as a web server?

TIA

---

### Post by Mr. C. on 2007-06-10
There is not enough information here to help.

Did you install that new firewall?
Does it use NAT, and now provides a different IP?
Did you configure a port tunnel for your web server?

Did you ensure that your compromised machine no longer is compromised ?

I'm not sure I understand "did nothing to the server per se.".  You either did, or you didn't.

Please give more details, networking information, the topology of your network, etc.

MrC

---

### Post by geakMonkey on 2007-06-11
I am building the firewall machine now: it is not installed, up and running. I changed nearly nothing on the WRT54g Linksys Router. I set the firewall to block everything that it blocks. But when I Disable that, the IP Address is still not seen online.

At first, I basically pulled the Ethernet cable out of the machine so that it was not attatched to the Router. I kept the machine on to check logs. That was all - no changes. After I restarted the Router, and DSL Modem, I could not get onto the internet at all. I had to reset the Network IP Addresses several times. 

The only wierd thing that I can recall is that I chose use eth0 as the gateway. In the Network Administration Tools, Default gateway device setting. It was blank before that. I have been thinking that maybe the machine is using the web server machine eth0 as the gateway when at the moment the router is the gateway.

# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

I have been looking all over for help and howto files for setting up a gateway ip address. I have not found any so far.

TIA

---

### Post by PilotJLR on 2007-06-11
Your routing table is fine. Is this machine a dhcp client, or statically addressed?

It sounds to me like the machine got a new address, which broke the port forward.

It would be a good idea to read up on NAT and private IP addresses, cause that's a pretty important element in this setup.

---

### Post by geakMonkey on 2007-06-11
I did not see this in any nmap before I tried this:

 nmap -sF 192.168.1.101

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-11 12:39 PDT
Interesting ports on azedia (192.168.1.101):
Not shown: 1691 closed ports
PORT     STATE         SERVICE
22/tcp   open|filtered ssh
80/tcp   open|filtered http
139/tcp  open|filtered netbios-ssn
445/tcp  open|filtered microsoft-ds
666/tcp  open|filtered doom
5900/tcp open|filtered vnc

Could the issue be caused by the ports being filtered?

When I run it this way, I get:

 nmap -sT 192.168.1.101

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-11 12:45 PDT
Interesting ports on azedia (192.168.1.101):
Not shown: 1691 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
666/tcp  open  doom
5900/tcp open  vnc

Nmap finished: 1 IP address (1 host up) scanned in 0.386 seconds

What is causing those two nmap reports to be different?
TIA

---

### Post by PilotJLR on 2007-06-11
No, this unfortunately has nothing at all to do with port forward. Nmapping local addresses is a waste of your time.

You just need to set the server to a static address, then forward port 80 (if you're doing web only, for example) from the WAN interface to whatever private address you chose for the server (192.168.1.101, if that's the case).

Port mapping from your own LAN is not going to tell you anything relevant to this problem.

---

### Post by geakMonkey on 2007-06-12
This is what I have in Network-Admin:

Static IP 192.168.1.101 
255.255.255.0
Gateway 192.168.1.1

That has been working since I set up the web server. The only change has been that I had unplugged the Router for some days then restarted the machine.

I have no idea what could have changed. I can only think that a file was corrupted or changed somehow before the reboot. Are there config files that I need to look at?

TIA

---

### Post by Nessa on 2007-06-12
I'm assuming that you are online when you bypass the router and hardwire directly to the modem.

If nothing has been changed on your server, maybe a problem with the router? 

What's the version of your router? If it's v5 or v6, you might want to upgrade the firmware if it's not up to date. Have you tried assigning a static IP that's not in the default range of the router? I'm guessing that the starting IP is 192.168.1.100. What about 192.168.1.10 or something like that...

When you access the setup page of your router, do you get a valid internet ip address and dns servers?

---

