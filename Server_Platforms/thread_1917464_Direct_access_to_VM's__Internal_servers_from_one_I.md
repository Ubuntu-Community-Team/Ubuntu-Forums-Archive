---
title: "Direct access to VM's / Internal servers from one IP address"
date: 2012-01-30
forum: Server Platforms
---

### Post by mchaggis on 2012-01-30
Hi,

Firstly I do appologise if this has been ask before, however, I am struggling to find an answer to my problem. I appreciate that the response I get is that it can't be done, however, I seem to be 50% of the way to my end goal.

The reason I mention VM's in the subject, is that I first ran into my wall while playing with Linux KVM, but to avoid specific responses about Linux KVM I will point out that my goal could just as easily be done with physical machines.

Ok, let me begin. My primary goal is to save the amount IP addresses I use by having my servers running within internal IP range and all services available externally.

The problem: Standard port forwarding is perfect if each server exposes unique services, i.e. A webserver (80), smpt (25) and pop3 (11). However, what if you want to run 5 webservers? The solution for webservers is Reverse proxy via Apache or nginx, but this doesn't fullfil other services like FTP/SSH/SFTP etc.

What I have atm, is a box that is configured as a router, with nginx installed and from a website point of view, it works perfectly. However, I have developers that need to get files onto these servers via FTP and SFTP. Now, I know that I could configure each internal server to use unique, but none standard ports, but my idea would be to be able to do the same sort of FQDN translation on these services like nginx allows me to do for my HTTP traffic.

e.g. ssh'ing to server1.domain.com drops me into 192.168.1.101
and ssh'ing to server2.domain.com drops me into 192.168.1.102

Firstly, is what I'm trying to achieve even possible?
Secondly, could someone tell me how to do this, or at least point me in the right direction?

Hope it all makes sense

Al

---

### Post by Wayne_V on 2012-01-30
let's think about this a bit - in order to ssh into server1 and server2 in domain.com they would have to be publicly resolvable address (not in 192.168.x.x).  Even if you entered them into DNS with the same IP address (your router), would the router be able to do an inspection of the packet and determine which server it is intended for (I haven't looked at the packet decode in a while but I don't think it would --- I think only the numeric IP would be in the packet).

I think better would be a VPN, so that any system outside your private subnet could connect via VPN and then it would appear to be on the 192.168.1.x subnet as well.

---

### Post by rubylaser on 2012-01-30
How about a different answer? Just setup a VPN connection for your developers.  That way you can prevent SSH or SFTP from being available on the internet and make them available only to the LAN / VPN clients.

---

### Post by mchaggis on 2012-01-30
Cheers for your help.

Wayne_V - Yes clearly the 2 fqdn's would have an external ip address. This I'm fairly certain I state. I also understand about how packets are sent and how nginx actually functions behind the scenes.

I also understand why you can't do it at the routing/iptables level in that (as you state) connections are made via ip addresses and it is only the application layer that contains the actual fdqn that the "client" requested.

TGH I had not thought about the VPN route and will investigate this further. However, for my clients, this does not work so well as they will just be expecting to connect to their servers just like any other hosting provider. 

I suspect that ssh/sftp may not be possible as the packets are only decrypted after the initial hand shake and even then remains encrypted.

FTP - I would have thought that something would have been possible, even if it's a case of setting the ftp username to be blah@server1 and then do some internal network forwarding based on the username.

Like I said, I am fully aware that my dream is not a valid one and so far the VPN route is looking the most attractive for our developers and contractors

---

