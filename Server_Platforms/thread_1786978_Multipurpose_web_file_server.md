---
title: "Multipurpose web file server"
date: 2011-06-20
forum: Server Platforms
---

### Post by chives84 on 2011-06-20
After endless hours of inconclusive searching, I still haven't found the answer I am looking for. Me and a friend are trying to set up a file server, accessible over the internet to computers, as well as game consoles. I found countless articles explaining web servers, but that's not what I want.

I plan to get an old desktop, load it with hard drives, running the ubuntu server edition. that part seems pretty solid. what I haven't been able to find, is a straight forward way to do it. I'll be honest, completely new in the whole actually setting it up part, except for oodles of terminology from a computer science class (i know LAN/WAN, differences of a switch/hub/bus, topologies, concepts, etc).

I know so far that when you boot into the server, it asks you for name, ip, etc, but what i don't know is if there are guidelines (well, of course there are, but,) on how to name, what you can or cant do, etc. 

Next, I was wondering what pieces of hardware I would need besides the server, a switch, cables, wireless router (already have, comes with my internet connection). trying to minimize cost, already buying the server myself. Also, what's impossible to find is a physical layout of it to make it this way (attached to the router, etc). 

Any help and further suggestions are welcome. Thanks in advance,

---

### Post by ian dobson on 2011-06-20
Hi,

A server is nothing more than a normal computer that provides services to other computers. So from the hardware side of things you just need to connect the server to the router, just like a normal pc.

On the software side you need to tell to router that connections to a specific port should be passed on to the server. If you get a web server up and running you could use webdav (File system over http) to share files.

This may not be the most secure/fastest solution but it's not too hard to setup.

Regards
Ian Dobson

---

### Post by chives84 on 2011-06-20
To make sure I understand this right and that I've expressed what I was trying to right, the following is how i envision my setup:

Cable connection from outside>router where server and switch connected>switch to other computers

What I need to do is (the way i would say it) have a port that goes from computer to server? Logistics on how it would be actually configured to come later, when i get the base of it down. lol.

---

### Post by Lars Noodén on 2011-06-21
For file sharing you'll want either Samba or SSHFS.  The latter is easier to set up.

---

### Post by chives84 on 2011-06-25
I looked up both of them, and while SSHFS is indeed easier to configure, I'm worried about access through other non-computer devices, like my ps3 or iPod/phone.

Also, still wondering about IP addressing.

---

### Post by doas777 on 2011-06-25
> **chives84 said:**
> I looked up both of them, and while SSHFS is indeed easier to configure, I'm worried about access through other non-computer devices, like my ps3 or iPod/phone.

Also, still wondering about IP addressing.

well I would recommend you do use a webserver, running FTP, as it is the web-freindly protocol for file sharing, and there are clients for almost any platform out there. SMB is not a web protocol, and while you can extend it to the wan using netbios-over-tcpip, that is not what it is for, and it will not perform well at all. many ISPs block SMB protocols over the web to protect unsavvy users that have hooked their PC to the web without a firewall. also most non-pc platforms do not implement netbios at all. 

as for IP addressing, you will have to get a dynamic ip registrar like DynDns.com and register a dns name with them.

---

### Post by Lars Noodén on 2011-06-26
> **chives84 said:**
> I looked up both of them, and while SSHFS is indeed easier to configure, I'm worried about access through other non-computer devices, like my ps3 or iPod/phone.


From those you could access via SFTP, if they lack a SSHFS client, without needing any changes to your SSHFS setup.

---

### Post by chives84 on 2011-06-26
Do you know if the PS3/360 specifically have the capabilities to? I'm not worried about the i-devices, there's most likely a cydia app for them.

---

### Post by TechSupportx86 on 2011-06-27
Well to answer one of your questions (well i think it's a question):

~ ----[ISP Supply]--COAX--[Cable Modem]--Cat5--[Router]--Cat5--[Switch]--Cat5--[Server]

Make sure the switch doesn't act as a DHCP server (99.9% of them don't) And you need to forward ports 8080, 20, 21, 22, And the port for whatever else you may need. The ports listed are for HTTP, FTP Data, FTP Control, and SSH (Disable SSH later or use a strong password). Also you need to direct the WAN address to the server's internal IP, usually called "DMZ Server" in the router settings, As well as set a designated static IP address for the server in /etc/network/interfaces so the router can always find it.

---

