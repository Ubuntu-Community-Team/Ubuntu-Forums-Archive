---
title: "Some general server questions"
date: 2010-10-16
forum: Server Platforms
---

### Post by nikclev on 2010-10-16
I've got my home NAS/server up and running with ubuntu server 10.04, but I want to add some functionality to it. Specifically, I want to add a transparent caching proxy, (squid) and replace my router with the ubuntu box. 

from my research, (google is my friend!) squid doesn't look that hard to set up, there are plenty of how-to's and common problem fixes. 

As far as turning my home server into a router in addition to it's current duties, I think need to enable ip masquerading and set up iptables rules to perform the actual NAT. From what I can tell, shorewall has some included configurations that should get me most of the way. 

first question: Does anyone see any problems with running all these services on one box:

these are already set up and running:
- ssh
- webmin
- mt-daapd/firefly (itunes server)
- samba (for filesharing, etc)
- smartd (hard drive health monitoring)
- apcupcd (UPS monitoring)
- postfix (the server emails me if something drastic happens)
- dovecot
- mysql (one of the above needed it, don't remember which...)
- mdadm (it -is- a NAS, among other things.)
- dhcp client
- source dedicated server (yup... gaming, on the LAN only)
I'm sure there are some I'm missing, but none that I can think of off the top of my head.

I want to add:
- squid (for transparent caching proxy)
- procmail (this -is- mail filtering, correct?)
- clamav + freshclam (a layer of security for the windows clients)
- apache2 (for no other reason than because I can, I'll find a valid use for it or leave it off)
- pppoeconf (I have an ADSL connection)
- shorewall (for iptables configuration)
- fail2ban (I think this is or something like it is a good idea if since it the server will be visible on the internet if I replace my current router with my server)
- dhcp3-server (for the rest of the network)

All of these (with the exception of apache2, and possibly an FTP server) I don't want to be accessable or visible from the internet, only from within my home network.

the second questions is basically one I'm sure I'll find the answer to on my own given time, but am I setting myself up for failure in some way? (IE, is there a good reason to not install a service or use a different program to provide the service) are there obvious things I'll need that I'm missing? The server has two working gigabit ethernet ports, and I'll use my existing router as an wireless AP. I particularly want to avoid getting rooted, having my server turned into a mail relay for some spammer, or having my machine be part of some hacker's zombie army.

I know to avoid telnet. (I use ssh and webmin to administer the server, it's headless)  I've no need for any sort of VPN capabilities either.

Basically I'm looking for a sanity check, I can find how-to's for all of this, but getting it all working -together- I think will be the hard part. (and the fun part :))

---

### Post by CharlesA on 2010-10-17
> **nikclev said:**
> 
As far as turning my home server into a router in addition to it's current duties, I think need to enable ip masquerading and set up iptables rules to perform the actual NAT. From what I can tell, shorewall has some included configurations that should get me most of the way. 

first question: Does anyone see any problems with running all these services on one box:

The main problem you would run into with running all those on one box, and using that box as the gateway to the internet is this: If that box is somehow compromised, you are boned.

I've got my NAS set up as a VM host and use a crappy Dlink router flashed with DD-WRT as the gateway.

> these are already set up and running:
- ssh
- webmin
- mt-daapd/firefly (itunes server)
- samba (for filesharing, etc)
- smartd (hard drive health monitoring)
- apcupcd (UPS monitoring)
- postfix (the server emails me if something drastic happens)
- dovecot
- mysql (one of the above needed it, don't remember which...)
- mdadm (it -is- a NAS, among other things.)
- dhcp client
- source dedicated server (yup... gaming, on the LAN only)
I'm sure there are some I'm missing, but none that I can think of off the top of my head.

That looks good, overall.

> I want to add:
- squid (for transparent caching proxy)
- procmail (this -is- mail filtering, correct?)
- clamav + freshclam (a layer of security for the windows clients)
- apache2 (for no other reason than because I can, I'll find a valid use for it or leave it off)
- pppoeconf (I have an ADSL connection)
- shorewall (for iptables configuration)
- fail2ban (I think this is or something like it is a good idea if since it the server will be visible on the internet if I replace my current router with my server)
- dhcp3-server (for the rest of the network)

Setting up squid as a transparent proxy is a bit iffy unless it is running as a gateway. I've done it before using a machine two network cards but not with that machine acting as a gateway device.

I've had too many false positives with clamav, so I've switched to BitDefender, and haven't had any problems with it.

If you are installing shorewall just to configure iptables, check out ufw or just learn iptables, it's not that hard. :)

> All of these (with the exception of apache2, and possibly an FTP server) I don't want to be accessable or visible from the internet, only from within my home network.

You'd have to firewall the services you don't want to be accessible from the internet.

> the second questions is basically one I'm sure I'll find the answer to on my own given time, but am I setting myself up for failure in some way? (IE, is there a good reason to not install a service or use a different program to provide the service) are there obvious things I'll need that I'm missing? The server has two working gigabit ethernet ports, and I'll use my existing router as an wireless AP. I particularly want to avoid getting rooted, having my server turned into a mail relay for some spammer, or having my machine be part of some hacker's zombie army.

Secure SSH properly: use keys instead of passwords and use something like DenyHosts or Fail2ban (even if it's not really needed with key auth only).

> I know to avoid telnet. (I use ssh and webmin to administer the server, it's headless)  I've no need for any sort of VPN capabilities either.

Don't touch telnet. Everything telnet can do, SSH can do better.

I used to use webmin, but found just doing everything over ssh was easier for me.

---

### Post by nikclev on 2010-10-17
> **CharlesA said:**
> The main problem you would run into with running all those on one box, and using that box as the gateway to the internet is this: If that box is somehow compromised, you are boned. 
 

That would be bad. I'll have to weigh the advantages to see if I want the risk. As most of the machines in the LAN are windows, I think there are risks from inside as well. I think the biggest risk is I would get a pretty nasty lesson in what I did wrong in securing it, assuming I did something wrong. I assume that the best approach would be to deny all connections at first, and then open connections up as I need. Even if I screw up and deny -everything- I can still plug a monitor and keyboard into the server and reopen for at least ssh.

That doesn't help in the case of an exploit in a service that I decided I needed open, though. (as opposed to me leaving something open that I didn't mean to) I guess putting all my eggs into one basket is a bit of a risk. 

> 
I've got my NAS set up as a VM host ...
I assume a VM host is a virtual machine host? I understand VM's in theory, never messed with them though.

> 
I've had too many false positives with clamav, so I've switched to BitDefender, and haven't had any problems with it.
Ah! I wasn't aware BitDefender had a linux version. Good to know. All the machines have some form of antivirus on them as well, so AV on the server would just be another layer.

Thanks for the response! I still like the idea of having a caching proxy, the transparent part is just for the ease of the clients. I may rethink having the box as the gateway, but if I do decide I have a reason to have a webserver or ftp server it simplifies things greatly to have it visible to the internet.

---

### Post by BkkBonanza on 2010-10-17
When you run services pay particular attention to what interface they listen on. For example, running cupsd for print sharing make sure it listens on the "LAN" interface not the WAN side. Same with anything else you don't want interacting with the internet. Use **sudo netstat -lntp** command and carefully look at the IP each service is bound to and adjust the config files to set the interface or IP suitable.

Setting up as a router is very easy in iptables directly. Also you need to enable tcp_forwarding. A simple "router" script put in the /etc/network/if-up.d directory that starts when your WAN (eth0 ?) interface if raised is usually enough. I have an example script I use on mine that I can post if you want. It checks the $IFACE and $MODE env vars to know when to insert the rules and enable forwarding and is run during the upstart init sequence after the interface is brought up.

---

### Post by SeijiSensei on 2010-10-17
Running Squid as a transparent proxy isn't hard if the gateway has two NICs, and all traffic goes through the box.  However it only really makes sense if you're supporting a lot of client workstations. It's probably overkill for a small home network since the clients' browsers will cache content locally.

I've set up Squid proxies for a few clients so we can filter out potentially dangerous web objects like executables and to control which sites and mimetypes the user population can access.  Squid's "access control lists" provide a powerful filtering method.

If you do decide to implement transparent proxying, make sure the iptables rule to push traffic through the proxy comes before any masquerading rules in iptables.  Use a rule like this:

```
iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 -s 192.168.1.0/24 --destination-port 80
```

replacing "192.168.1.0/24" with your internal network address. Squid listens by default on port 3128.

---

### Post by CharlesA on 2010-10-17
> **nikclev said:**
> 
I assume a VM host is a virtual machine host? I understand VM's in theory, never messed with them though.

Yep. I've got it running some Virtual Machines as well as Apache, SSH, Samba, etc.

> Thanks for the response! I still like the idea of having a caching proxy, the transparent part is just for the ease of the clients. I may rethink having the box as the gateway, but if I do decide I have a reason to have a webserver or ftp server it simplifies things greatly to have it visible to the internet.

Well if you are only serving pages from one machine, you can always use port forwarding on the router to make those pages accessible from the internet.

---

