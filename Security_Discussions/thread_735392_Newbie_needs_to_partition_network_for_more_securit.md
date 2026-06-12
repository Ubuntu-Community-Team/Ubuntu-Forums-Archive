---
title: "Newbie needs to partition network for more security"
date: 2008-03-25
forum: Security Discussions
---

### Post by MountainX on 2008-03-25
I have a LAN with several computers, one of which is a file server with some confidential financial data, etc. on it. I have a wireless AP using WPA security. And I would like to add a web server/ftp server to my network. I want to isolate these functions for better security of the LAN.

Is it possible to do the following:
1. put the wireless AP on a different subnet so that anyone who manages to connect to the wireless network, whether invited or not, only has access to the Internet and not to the other computers on the LAN? 

2. If #1 is achieved, if we give certain clients a way to connect to both the wireless AP and the LAN, have we compromised the goals of #1? I'm guessing all the laptops will have to have a wired connection to access the LAN, but could just use their wireless connection if they only want Internet access. Does this make sense?

3. If I set up the web/ftp server so that it is on a separate subnet (if that's the correct term) I assume it is no problem to connect to it via ssh from another computer on my LAN. I would use my Netgear 124G router to point all http and ftp traffic to this web server. To what extent could this web server be isolated using this (simple) approach?

I would appreciate any thoughts on this as well as some basic instructions for setting up a partitioned network like this. Thanks.

---

### Post by Dr Small on 2008-03-25
As for number 3, if you plan to have SSH on the server, then scrap FTP because the FTP protocol sends usernames and passwords as plaintext from the client to the server. You can simply use Sftp with SSH which encrypts everything through the SSH protocol tunnel.

Dr Small

---

### Post by MountainX on 2008-03-25
> **Dr Small said:**
> As for number 3, if you plan to have SSH on the server, then scrap FTP because the FTP protocol sends usernames and passwords as plaintext from the client to the server. You can simply use Sftp with SSH which encrypts everything through the SSH protocol tunnel.

Dr Small

I like that idea. In the past I used IP-based restrictions on FTP access and throw-away passwords. But FTPS or SFTP would be much better I believe. I have never used either, so I'd have to learn how to set up the clients and server.

What about my desire to partition the network? Is that doable?

---

### Post by Dr Small on 2008-03-25
I have no prior knowledge on how to do that, so if someone with more knowledge than the both of us answers, then we both will learn something :)

If you are using SFTP and use gFTP as a client, simply connect to the server as normal, but use SSH2 as the protocol :D

Dr Small

---

### Post by euler_fan on 2008-03-25
If you set up a VPN server with strong passwords and SSH2 encryption you could let people tunnel into the LAN--even over wireless--without sacrificing the isolation of the wireless network from the LAN. Basically people would get on the wireless and set up the tunnel though that out to the internet then to your VPN server and finally into the LAN.

---

### Post by MountainX on 2008-03-26
> **euler_fan said:**
> If you set up a VPN server with strong passwords and SSH2 encryption you could let people tunnel into the LAN--even over wireless--without sacrificing the isolation of the wireless network from the LAN. Basically people would get on the wireless and set up the tunnel though that out to the internet then to your VPN server and finally into the LAN.

Thanks for the reply, but that sounds like a corporate-type solution. I should have specified that this is a home-office and family situation. I will only need outside access into my LAN when I'm traveling, and I could use something like SSH for that as Dr. Small suggested.

The other situations I need to deal with are:
1. uninvited people coming into the wireless network from outside.
2. guests staying in the house who need to connect to the Internet.

For #1, I just want to ensure that these people who might manage to connect to our wireless network get nothing more than free access to the public Internet. I don't want them to have access to our file server, etc.

For #2, the situation is almost the same. I want to give guests access to the Internet when they legitimately connect to our wireless AP, but I don't want them to even see the other computers on the LAN.

---

### Post by euler_fan on 2008-03-26
Okay. A VPN server is simply one way to get relatively secure remote access to a protected network. [Here's a guide to setting up an Ubuntu VPN server.]("https://help.ubuntu.com/community/VPNServer") If you have another way it should still work.

As for segregating the wireless access from the LAN, the most brute force way would be to set up two routers:

1) Router A is a wifi router, sees the internet, and shares it both to Router B and over wireless to whomever you give the SSID to.
2) Router B is a wired router, gets its internet access from Router A, and connects all machines in your trusted LAN.

There's probably a way using clever firewall settings to do all this in one router. Probably the best tool to do this with would be fwbuilder (aka Firewall builder) available in the repos. If you don't want to do that, the two router method will work fine.

The important part is that all wireless-related stuff is *outside* the firewall which protects the LAN and that the firewall which protects the LAN only allows inbound SSH connections. This way from the point of view of a wireless user

---

### Post by MountainX on 2008-03-26
> **euler_fan said:**
> 
As for segregating the wireless access from the LAN, the most brute force way would be to set up two routers:

euler_fan - thanks for the idea. Using two routers may be perfect for me because I already have two.

I have a [Netgear FVS124G]("http://www.netgear.com/Products/VPNandSSL/WiredVPNFirewallRouters/FVS124G.aspx") for the GigE wired network. It has dual WAN ports, and I have it connected to a DSL modem on one port and a cable modem on the other port. It has a decent stateful packet inspection firewall.

I also have[ D-Link WBR-1310 Wireless G route]("http://www.dlink.com/products/?model=WBR-1310")r. It also has a firewall and it has WPA capability. Currently it gets internet access from the Netgear router.

(To make things even more complicated, I have a Vonage VIOP device by Linksys that has to be outside the routers.)

Anyway, can you give me some hints about setting up the networks to use these two routers separately? Is it as simple as just enabling my D-Link to be a DHCP server and to give out IP addresses belonging to a different range from those used on my wired network?

Example:
Wired address range 192.168.100.x subnet mask 255.255.255.0
Wireless address range 192.168.200.x same subnet mask

If I use this method, couldn't someone just assign their wireless client a static IP address in the other range? Obviously, I need some advice! ;)

Thanks

---

### Post by hyper_ch on 2008-03-27
> **MountainX said:**
> I have never used either, so I'd have to learn how to set up the clients and server.

You want all to access different or same folder and they should not have rights to run a shell, right?

If so then I'd

(1) install openssh-server

(2) install mysecureshell (maybe you'll have to compile it) [here's a little howto: [http://www.howtoforge.com/mysecureshell_sftp_debian_etch]](http://www.howtoforge.com/mysecureshell_sftp_debian_etch])

(3) add new users to the system and change their shell to mysecureshell

[(4) if they all have to access the same files then alter their homefolder to a common and and also add them to a common group]

In Windows use then WinSCP ([http://www.winscp.com](http://www.winscp.com)) or in Linux you can use a client that supports sftp (I love konqueror: fish://user@server)

---

### Post by euler_fan on 2008-03-27
What I've seen which works fine is this:

[internet]-->[broadband model]-->[Wireless router]-->[wired router]-->[LAN]

and then make the wireless router do DHCP. On the wired network, it's on a different router anyway, so what you do behind it doesn't matter thanks to Network Address Translation.

It should be as simple as running a patch cable from an outbound port on your wireless router to an/the inbound internet port on your wired router.

---

### Post by MountainX on 2008-03-27
> **euler_fan said:**
> What I've seen which works fine is this:

[internet]-->[broadband model]-->[Wireless router]-->[wired router]-->[LAN]

and then make the wireless router do DHCP. On the wired network, it's on a different router anyway, so what you do behind it doesn't matter thanks to Network Address Translation.

It should be as simple as running a patch cable from an outbound port on your wireless router to an/the inbound internet port on your wired router.

Nice diagram :)

I can't do that because my wired router is the one that has dual-WAN ports with failover and all the fancy stuff. So can I do it like this? If so, how?

```

[internet-DSL]-->[DSL modem]--->[Wired router]-->[LAN 1]
[internet-Cable]-->[cable modem]----^     ^---- [wireless router]-->[LAN 2]

```

Thanks

---

### Post by euler_fan on 2008-03-28
After spending some time looking at the diagram on the page you linked describing the NETGEAR router, you should be able to plug your wired router into one of the LAN ports of your wired router and use your wired router's built-in firewall to manage everything.

Also, the specs say there is a web-based configuration program on the router which the instructions which came with it should tell you how to use.

It looks like dual WAN ports are for multiple broadband routers.

You would tell the wired router to put the web server in the DMZ. The wirelss router you could put on a second DMZ which should isolate it from the rest of your network.

---

### Post by MountainX on 2008-03-28
> **euler_fan said:**
> you should be able to plug your wired router into one of the LAN ports of your wired router and use your wired router's built-in firewall to manage everything.
Typo: you mean plug the wireless router into a lan port on the wired router. Yes, that is what I'm doing.

> **euler_fan said:**
> 
It looks like dual WAN ports are for multiple broadband routers.
.
Typo again - it is for multiple broadband modems. It can either aggregate the bandwidth or let one broadband ISP serve as failover.

> **euler_fan said:**
> 
You would tell the wired router to put the web server in the DMZ. The wirelss router you could put on a second DMZ which should isolate it from the rest of your network.
There is only one DMZ. But using the DMZ feature doesn't create any isolation. I've been using the DMZ feature already.

Hey, I have some friends that live in the same city you live in :)

---

### Post by euler_fan on 2008-03-28
Okay . . . I'm kind of curious how putting your web server and wireless network in the DMZ wouldn't provide protection since the point of a DMZ is to put stuff outside your main network to prevent someone gaining control of (say your web server) from using that to then attack the rest of your network.

Otherwise I'm a bit at my wits end as to further assisting you. Sorry.

---

### Post by MountainX on 2008-03-28
Thanks for your help. I could be wrong about the DMZ, but I exposed a web server once and I was still able to get to it from computers in the LAN and when logged in to the web server I could get to other computers on the LAN. All the DMZ did was allow users outside the firewall to get to the web server (and only on certain ports). Of course, maybe I set this up wrong...

In looking at the help, however, I just saw "Multi Home LAN IPs". This might be what I need to set up two separate LANs - one for wireless and other for more secure computers.

I'll keep researching -- and thanks for your help.

---

