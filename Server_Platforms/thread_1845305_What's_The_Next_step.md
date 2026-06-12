---
title: "What's The Next step"
date: 2011-09-16
forum: Server Platforms
---

### Post by pgp_protector on 2011-09-16
I've got a Ubuntu Server running 11.04 up and running now :)
Built on a AMD Phenom 840T Box 6G Ram 2TB HD 

So far I've got 
The MySQL Database being backed up nightly to our WHS shared folder (working)
Apache Web server running serving multiple Intranet sites (working with ISPConfig)
FTP Server running so I can work on the sites (working)
Samba for File Sharing (mostly working, just getting the users worked out)
WebMin for administrating the server from our Intranet (working)
One hole in the firewall so I can use Putty to log into the server from outside (working)

We did the conversion as our old box (running XP & LAMP) was dying due to hardware failures, and ran an internal database / web page for tracking parts.  And I decided to go for more of a real server (yes I know the hardware doesn't truly count as it doesn't have any server redundancy, but that's not in the budget right now)

What I would like to know is one
1) If their are any good tools that run on Windows / Ubuntu for monitoring the system status (load / usage / space / ect)
2) Restrict remote logins to specific domain names ?(Both home & work have dynamic IP Address, but also use dyndns names) so can I have the work server only allow access from ([www.myhomename.dyndns.com](www.myhomename.dyndns.com)) ??
3) How do I fix my Certificate Information? 
> This CA Root certificate is not trusted because it is not in the Trusted Root Certification Authorities store.
4) What's the best way to test the security / improve the security of the system ?  As some of our Intranet pages we would like to eventually want to become intranet pages for employees to access.

---

### Post by pgp_protector on 2011-09-16
One other thing.

Right now the server is operating as the offices DNS Server (working) but not the DHCP Server.

Our Netgear Router is the DHCP server (That the WHS Also uses for access to the outside world)

The problem is the Netgear router sometimes "resets" itself and when it does that it changes the LAN Address of the network from the 192.168 set to the 10.10 set and then a lot of our hardware (cameras, printers, test equipment) that has fixed IP Address, they don't change so the windows boxes can't communicate with them anymore (due to the 192.168.x.x not talking to the 10.10.x.x range) 

So how much trouble am I asking for by making the Ubuntu server also act as the DHCP server?

---

### Post by Habitual on 2011-09-16
> **pgp_protector said:**
> ...
1) If their are any good tools that run on Windows / Ubuntu for monitoring the system status (load / usage / space / ect)


Nagios/Icinga is great for this.
It is a Linux fault tolerance monitoring solution. 

In your REPOs as nagios2. You will also need the nagios-plugins package.

Installing nagios2 should also install this.

The windows client(s) will need the nsclient++ application installed on that/those host(s) to allow/configure nagios/icinga to poll the desired metrics on the Windows boxes.

Get that at [http://nsclient.org/nscp/](http://nsclient.org/nscp/)

HTH.

---

### Post by 2F4U on 2011-09-17
It is not very difficult to setup a dhcp server. Here are some articles about it, so that you can judge yourself:

[http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)
[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html)
[http://www.ghacks.net/2009/09/07/configure-your-ubuntu-server-as-a-dhcp-server/](http://www.ghacks.net/2009/09/07/configure-your-ubuntu-server-as-a-dhcp-server/)

---

### Post by maverickaddicted on 2011-09-17
You can setup DHCP server using this guide very easily, it is also having the screenshots

[http://www.server-world.info/en/note?os=Ubuntu_11.04&p=dhcp](http://www.server-world.info/en/note?os=Ubuntu_11.04&p=dhcp)

---

