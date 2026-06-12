---
title: "Where to start?"
date: 2006-06-10
forum: Server Platforms
---

### Post by tymanthius on 2006-06-10
I have a 333Mhz machine that I want to have as file server/ftp server/print server.

Also, I use dhcp from my router (linksys running dd-wrt firmware) right now, but I may change that to the server, so that I can use name resolution to make things easier via ssh, vnc, etc.

But . . . where do I start?  The Server guide on help.ubuntu.com really isn't that informative.

---

### Post by ChakRa on 2006-06-11
[QUOTE=tymanthius]I have a 333Mhz machine that I want to have as file server/ftp server/print server.

Also, I use dhcp from my router (linksys running dd-wrt firmware) right now, but I may change that to the server, so that I can use name resolution to make things easier via ssh, vnc, etc.

But . . . where do I start?  The Server guide on help.ubuntu.com really isn't that informative.[/QUOTE]

For this you have to install Samba on your linux machine. The best way is to read some documentation on it. Here are a few that will be helpful. 
[http://gentoo-wiki.com/HOWTO_Setup_Samba#installation]("http://gentoo-wiki.com/HOWTO_Setup_Samba#installation")
[http://www.howtoforge.com/samba_setup_ubuntu_5.10]("http://www.howtoforge.com/samba_setup_ubuntu_5.10")

---

### Post by fireshell on 2006-06-11
Thanks for the links, just what I've been looking for

---

### Post by tymanthius on 2006-06-15
Samba, at this point, is a side issue. 

My main concerns are making my server the router, setting up inet access (my linksys currently turns off inet to my kids puters at 930pm), and moving all my linux machines to centralized authentication.  I really have no idea how to do this, as I've never tried it before.

So where do I start with that?

The one advantage Windows has is that if you don't know how to do something, it's usually easier to figure it out in Windows.  Linux has a steep learning curve, but it's well worth it b/c it works better.  :)

(edited to add 2 concerns - I should learn not to post when I'm tired.)

---

### Post by tymanthius on 2006-06-16
shameless bumb

---

### Post by tymanthius on 2006-06-16
Ok, I installed dnsmasq, but none of my machines will pull an IP from my server.  dnsmasq says that the default port is 53, but when my other ubuntu machines go to pull an IP they search port 67.  

When I set port=67, dnsmasq complains that the port is in use.  What am I missing???

---

### Post by Ixzat on 2006-06-16
What does a "sudo netstat -tap" show you?

---

### Post by tymanthius on 2006-06-16
[QUOTE=Ixzat]What does a "sudo netstat -tap" show you?[/QUOTE]


Hand typing this as the server isn't on the 'real' network right now:

Prot rcvQ SndQ Local Add  Foreign Add State Name
tcp  0      0      *:domain   *:*           Listen dnsmasq
tcp6 0      0      *:domain   *:*           Listen dnsmasq

There are others, but they are python, hpiod, vsftpd & cubsd.  None of them appear to be using a port I need, but I don't really know how to read this output.

---

### Post by tymanthius on 2006-06-17
Some slight additional info:

Here's my setup:

Cable mdm
   |
   |
-------------------------------
|eth0           UbuntuServer      |
|                                         |
|eth1                                   |
-------------------------------
   |
   |
Linksys Router
  |    |    |    |
Xb XP Xbox  DumbSwitch
                 |   |   |   |
               EdB Xb  

XP=Windows XP, EdB=Edubuntu, Xb=Xubuntu

eth0 gets it's IP from the cable modem via DHCP
eth1 is staticlly set to 192.168.1.1

I took the dumb switch out of the 'main' network and put the server on it just to test things.  Even if I manually set the ip on a PC connected to the dumb switch, it still won't ping eth1 on the server.

I don't THINK my hardware is bad, but it is a possibilty.

---

### Post by Ixzat on 2006-06-17
[QUOTE=tymanthius]Hand typing this as the server isn't on the 'real' network right now:

Prot rcvQ SndQ Local Add  Foreign Add State Name
tcp  0      0      *:domain   *:*           Listen dnsmasq
tcp6 0      0      *:domain   *:*           Listen dnsmasq

There are others, but they are python, hpiod, vsftpd & cubsd.  None of them appear to be using a port I need, but I don't really know how to read this output.[/QUOTE]

If you do a "cat /etc/services | grep domain" you will see that the service named domain will use port 53. 

The output you got will therefore tell you that dnsmasq is running and listening on local port 53, on both ipv4 and ipv6.

---

### Post by Ixzat on 2006-06-17
[QUOTE=tymanthius]
Cable mdm
   |
   |
-------------------------------
|eth0           UbuntuServer      |
|                                         |
|eth1                                   |
-------------------------------
   |
   |
Linksys Router
  |    |    |    |
Xb XP Xbox  DumbSwitch
                 |   |   |   |
               EdB Xb  

XP=Windows XP, EdB=Edubuntu, Xb=Xubuntu
[/QUOTE]

Why bother with your linksys router? Wouldnt it be better to only use a switch connected to eth1 and let linux do all the routing?

---

### Post by tymanthius on 2006-06-17
[QUOTE=Ixzat]Why bother with your linksys router? Wouldnt it be better to only use a switch connected to eth1 and let linux do all the routing?[/QUOTE]


The linksys is being used as a wireless AP (forgot to include that part), and as a switch.  It has 4 ports, and the switch has 4 ports, and I have 6 devices in need of IP's.  :)

---

### Post by tymanthius on 2006-06-17
[QUOTE=Ixzat]If you do a "cat /etc/services | grep domain" you will see that the service named domain will use port 53. 

The output you got will therefore tell you that dnsmasq is running and listening on local port 53, on both ipv4 and ipv6.[/QUOTE]


Ok, you're absolutely right.  But why do all my other systems look for a dhcp server on port 67?  

And when I do the same thing, but 'grep 67' it tells me I have a bootp server running there.  I don't think I need bootp (it's for systems that boot from the network yes?)  So perhaps if I kill bootp, then set dnsmasq.conf to set the port to 67, I'll be ok?

It appears that dnsmasq is running the bootp server, and I can't see how to turn it off.  I'm confused!

---

### Post by tymanthius on 2006-06-17
When I run ifup eth0 on any linux machine, it gives this:

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

Several times, with varying intervals, then quits.  With my linksys providing dhcp, it work straight off, giving:

DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 40677 seconds.

So I guess the idea is 'Why does dnsmasq provide it on 53, when all my linux machines look on 67?'  I assume Windows looks on 67 too.

---

### Post by juicybananahead on 2006-06-18
[QUOTE=tymanthius]I have a 333Mhz machine that I want to have as file server/ftp server/print server.

Also, I use dhcp from my router (linksys running dd-wrt firmware) right now, but I may change that to the server, so that I can use name resolution to make things easier via ssh, vnc, etc.

But . . . where do I start?  The Server guide on help.ubuntu.com really isn't that informative.[/QUOTE]
Hi tymanthius,

I don't know if this will interest you, but you can run DNSMasq on your Linksys router under dd-wrt. I use this for local dns.

// juicy

---

### Post by tymanthius on 2006-06-18
[QUOTE=juicybananahead]Hi tymanthius,

I don't know if this will interest you, but you can run DNSMasq on your Linksys router under dd-wrt. I use this for local dns.

// juicy[/QUOTE]


I am doing that, and dd-wrt is great, but I want to move my network control functions to a full computer.  It's going to end up fileservering, printserving, ftp serving, etc, etc, etc.  :)

---

### Post by tymanthius on 2006-06-19
I'm thinking of starting a new thread w/ a better title, as I now know that dhcp ports are my problem.  But I'd rather not if I can keep it all here, how can I change the title that shows on the forum list?

---

