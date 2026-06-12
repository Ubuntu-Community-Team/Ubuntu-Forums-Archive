---
title: "Server HOWTOs"
date: 2005-07-20
forum: Server Platforms
---

### Post by dpod on 2005-07-20
I must be a real idiot: but after searching for 30 min. I can't find the server installation howtos mentioned in the sticky at the head of this thread. This leads to two questions:

1) Can anybody tell me where it is?
2) Failing that, can anybody point me to basic information on server setup so that I can serve out to an arbitrary domain name (e.g. [http://www.digitalmedievalist.org/](http://www.digitalmedievalist.org/)) using a consumer ADSL line? I'm starting from scratch: I have a working ADSL; working ubuntu, and I can check mail and use a browser using my ISP's domain name. I now want to host my own, piggybacking on their service but am beginning at nul.

---

### Post by relix42 on 2005-07-20
[QUOTE=dpod]I must be a real idiot: [/QUOTE]
I doubt that.

[QUOTE=dpod]
2) Failing that, can anybody point me to basic information on server setup so that I can serve out to an arbitrary domain name (e.g. [http://www.digitalmedievalist.org/](http://www.digitalmedievalist.org/)) using a consumer ADSL line? I'm starting from scratch: I have a working ADSL; working ubuntu, and I can check mail and use a browser using my ISP's domain name. I now want to host my own, piggybacking on their service but am beginning at nul.[/QUOTE]

It sounds like you want to serve web pages from your Ubuntu machine attached to your DSL line.  If so, read on, otherwise, correct me and I'll see what I can do.

Essentially, a few things are going to have to be working before you do what you want to do.  (Would be true if you wanted to do web pages, e-mail, FTP, whatever service).

1) **DNS** - You either need a static IP address (and approprite DNS entries) or you need to use a service (like dyndns.org) that will map your ever changing dynamic IP address to your machine.
2) **Inbound Connectivity** - Once #1 is in place, you need to make sure that traffic is making it into your box.  This is especially true of you have a firewall and router in place between you and the Internet.  You are running a **firewall** aren't you?
3) **Software Applications** You need to make sure that the requisite software is installed and answering requests when sent to your machine. (i.e. Apache2 is answering correctly when you point a web browser at your machine.
4) **Configuration** - Some applications require that you configure them to answer on specific IP addresses or recognize traffic sent to specific IP addresses.

Once all these are in place, you should be happily serving your content.  If you want more specific help, it would be better to post with exactely what you are trying to do, along with IP addresses and Internet connectivity information.

---

### Post by benkong2 on 2005-07-21
[QUOTE=dpod]I must be a real idiot: but after searching for 30 min. I can't find the server installation howtos mentioned in the sticky at the head of this thread. This leads to two questions:

1) Can anybody tell me where it is?
2) Failing that, can anybody point me to basic information on server setup so that I can serve out to an arbitrary domain name (e.g. [http://www.digitalmedievalist.org/](http://www.digitalmedievalist.org/)) using a consumer ADSL line? I'm starting from scratch: I have a working ADSL; working ubuntu, and I can check mail and use a browser using my ISP's domain name. I now want to host my own, piggybacking on their service but am beginning at nul.[/QUOTE]
 I am also seeking the server how-to I am attempting to use my ubuntu box as a router - server. Got cable internet access ubuntu is talking to the web but the second nic, dns and dhcpd aren't working.

Looking for a good source and I don't mind reading. Tried linexhomenetworking and it is good but it is FC based. Need some good ol ubuntu information.

---

### Post by maphew on 2005-07-21
[QUOTE=dpod]I must be a real idiot: but after searching for 30 min. I can't find the server installation howtos mentioned in the sticky at the head of this thread. This leads to two questions:

1) Can anybody tell me where it is?
2) Failing that, can anybody point me to basic information on server setup so that I can serve out to an arbitrary domain name (e.g. [http://www.digitalmedievalist.org/](http://www.digitalmedievalist.org/)) using a consumer ADSL line? I'm starting from scratch: I have a working ADSL; working ubuntu, and I can check mail and use a browser using my ISP's domain name. I now want to host my own, piggybacking on their service but am beginning at nul.[/QUOTE]
 can somebody please answer the first part of his question? where are these mysterious HOWTOs. I can't find them either.

---

### Post by benkong2 on 2005-07-21
[QUOTE=maphew]can somebody please answer the first part of his question? where are these mysterious HOWTOs. I can't find them either.[/QUOTE]

Here is my ifconfig out put:

The eth0 is connected to my cable modem funny part is the Mask:255.255.254.0
My computers on my LAN can connect to the internet by cable working on getting my wireless linksys wrt54g working.

My question is the broadcast and mask are different on eth0 internet dynamic ISP and eth1 i set static ip at 192.168.1.0. Is this correct? Before I move on to DNS...I want my server to also provide dns for my lan I want to make sure this is configured correctly.



eth0      Link encap:Ethernet  HWaddr 00:0F:B5:08:22:35
          inet addr:24.88.250.212  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::20f:b5ff:fe08:2235/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:117097 errors:0 dropped:0 overruns:0 frame:121
          TX packets:3656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9115826 (8.6 MiB)  TX bytes:402133 (392.7 KiB)
          Interrupt:11 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:0F:B5:08:21:C6
          inet addr:192.168.1.0  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe08:21c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:105455 (102.9 KiB)  TX bytes:406021 (396.5 KiB)
          Interrupt:5 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2930224 (2.7 MiB)  TX bytes:2930224 (2.7 MiB)

---

### Post by cheredenine on 2005-07-22
[QUOTE=dpod]I must be a real idiot: but after searching for 30 min. I can't find the server installation howtos mentioned in the sticky at the head of this thread. This leads to two questions:

1) Can anybody tell me where it is?
2) Failing that, can anybody point me to basic information on server setup so that I can serve out to an arbitrary domain name (e.g. [http://www.digitalmedievalist.org/](http://www.digitalmedievalist.org/)) using a consumer ADSL line? I'm starting from scratch: I have a working ADSL; working ubuntu, and I can check mail and use a browser using my ISP's domain name. I now want to host my own, piggybacking on their service but am beginning at nul.[/QUOTE]

I believe I've done what you're attempting to do, ie set things up so that my ubuntu box is serving a website to the internet at large; so here is my contribution:

1) I didn't know about the How-Tos until you mentioned them - can't be that necessary as i've managed to set things up without them, despite being new to Linux in general.

2) I made heavy use of the unofficial guide: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)  to help install and configure samba (so that my windows PC will talk to the ubuntu box), Apache (to server the webpages), PHP (trying to learning this, too) and MySQL.  Everytime I got stuck i ran a few searches through this forum and generally found something to help nudge me along.

My set-up, incase it helps:  I has a router with a nice set of security features - this is set to redirect port 80 (html) traffic to the linux box specifically.  I've not used a DMZ, so only port 80 traffic can reach this machine.  The router has a DynDNS feature where it'll automatically update a DynDNS account so that the free domain i was issued with always points to my dynamic IP.  I have a separate domain that i bought which redirects to the DynDNS domain and so on to my ubuntu box.
I've also spent some time looking at security (probably not enough, but first time after all) - tried to make sure that Apache blocks access to everything thats not specifically intended for web access, also fiddled with ubuntu to set permissions on various folders to deny priviledges to any user or process that shouldn't have them (can't remember all the specifics now)

The bit that confused me most was having it all set up and not being able to access the webpage via my domain name from home...  Doing this effectively asks the Router to poll its own WAN IP address and is automatically blocked as a attempted hack - kept me confused for half an hour or so!

---

### Post by spanishwasabi on 2005-07-22
Hi,

I guess this is what you are looking for:
[http://aboutdebian.com/](http://aboutdebian.com/)

Ok, take care, it's not a production system. Afterwards you'll have to secure a bit your server. The package harden-doc may be of help.

Enjoy,

G

---

