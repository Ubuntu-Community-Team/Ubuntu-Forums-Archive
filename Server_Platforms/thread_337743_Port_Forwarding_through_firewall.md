---
title: "Port Forwarding through firewall"
date: 2007-01-13
forum: Server Platforms
---

### Post by asforme on 2007-01-13
Hey all, this is my first time posting but I have been reading and getting advice from Ubuntu forums for a while, but now it seems I finally have a problem that no one else has successfully resolved.

My College decided this semester that it would be a good idea to block all outgoing ports except port 80 and port 21 for a few very selective websites (does not include my ftp server).   This means that they have totally shutdown all communications with my home computers,](*,)  I want to try to re-enable access to them by tunneling through port 80.

I have a cable modem with a technically dynamic public IP (though I've only ever seen it change once).  It is connected to a router that is performing NAT and DHCP in the 192.168.15.x range (the router's IP is 192.168.15.1).  I have my Ubuntu server with a static IP of 192.168.15.50.  If I tell my router to forward all incoming traffic on port 80 to my Ubuntu server, I want Ubuntu to sort those packets and send them to their correct internal IP's and ports.

This way I can send an FTP request to my public IP on port 80 and reach my internal FTP server on port 21, or send a Remote Desktop request on port 80 and connect with my WINXP machine on port 3389.

I do not know if Ubuntu would be able to sort the packets based on protocol alone (though that would be cool), or if I would have to make my requests more specific by FTPing into ftp.myipaddress, or myipaddress/ftp.

Also I do not have a public domain so I don't know if ftp.myipaddress is even possible.

Thanks for all your help, I'd hate to think that I might have to use a USB stick to get my data from home to school.

[edit]
Just for clarification, I have tried this using Apache's reverse proxy, but that seems to only want to work with http protocol.  This may be possible using ssh tunneling or iptables, but I haven't found a way to forward to multiple outgoing ports from a single incoming port.

---

### Post by Biggus on 2007-01-14
I'm by no means an expert (as you may soon find out), but is it possible for you to run your FTP server on a different port, ie 80?

---

### Post by asforme on 2007-01-15
Yeah, in fact I can pick any service I want to run on port 80.  My delimma is that port 80 is the only port through which I can access my home computers from school, so I would like to run all of my services on the same port.  I found a program that claims to do Layer 7 Packet filtering, this may accomplish my task, but because of it's reportedly slow speeds I would much prefer a way using subdirectories or virtual servers.

Another option which I am experimenting with right now is trying to run a VPN over port 80.  I think I have the VPN all set up correctly using OpenVPN, but havent gotten a chance to test it outside my network.  The only problem with using a vpn to access all of my home services from school is that I have not yet found a VPN client that I can run on Windows XP without installation or administrative privelages.

---

