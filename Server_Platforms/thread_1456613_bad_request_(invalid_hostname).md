---
title: "bad request (invalid hostname)"
date: 2010-04-17
forum: Server Platforms
---

### Post by bernd brechbart on 2010-04-17
hello,

i have a nasty little problem with our webserver that i can't seem to fix. it is a fresh install of ubuntu server 9.10 (x64). the webserver seems to run fine after i issue "aptitude update" and "aptitude install apache2". sadly this only works for about ten minutes, after that a http error 400 greets me instead of the default apache page. the error disappears after a server restart, restarting apache alone doesn't help. after ten minutes it's http 400 again. whats strange is that "aptitude update" also fixes the problem temporarily. same behaviour with a debian minimal installation. one more thing, the server runs as a virtual machine in a vmware environment. any suggestions or hints would be greatly appreciated.

bb

---

### Post by gombadi on 2010-04-17
What do the apache access and error logs show?

---

### Post by bernd brechbart on 2010-04-18
i've just cleared all log files and restarted the machine. it worked as expected and after a short time it stopped again.
apache's error and access logs look normal until they just stop like there is no access at all. "wget localhost" from the server's shell works and generates correct log lines.
i've rewritten the page for the error 400 but the displayed message stays the same. it seems that the server itself cannot be accessed anymore, not even from another machine in the same network. i wonder where the error comes from, if not from apache. ssl stops working, too ("access denied"). 
the server is behind a firewall, but port 80 is open and the firewall logs show no denied connections.

---

### Post by Ryan Dwyer on 2010-04-18
I'd probably try packet sniffing next, though I don't know what software you could use in a CLI environment. Sniff packets on the server to see what it's receiving. Then sniff on the firewall and client to see which one is at fault.

---

### Post by bernd brechbart on 2010-04-19
thank you for your answers.
the issue seems to be somehow related to the manual network configuration.
i moved the server to another network with a dhcp server and apache worked like a charm. 

the settings in the production environment look like this (etc/network/interfaces):
```
auto eth0
iface eth0 inet static
address x.x.x.213
gateway x.x.x.194
netmask 255.255.255.224
network x.x.x.192
broadcast x.x.x.223
```

and etc/resolv.conf points to the nameserver's ip addresses.
could subnetting be the problem?

---

### Post by koenn on 2010-04-19
> **bernd brechbart said:**
> the issue seems to be somehow related to the manual network configuration.
i moved the server to another network with a dhcp server and apache worked like a charm. 

Does this mean you have dhclient or network-manager on that server ?
If so, and it's still  running, it'll override your static config, causing your server to get a random address assigned by dhcp - that would explain you suddenly can't reach it by its static address (directly or through DNS)

---

### Post by bernd brechbart on 2010-04-20
> Does this mean you have dhclient or network-manager on that server ?
ps -A should show this, right? i didn't install either. it's a plain server installation with lamp. ifconfig displays the correct static ip, and i am able to reach the default page from the server via ip or hostname.

---

### Post by koenn on 2010-04-20
dhclient shows upin ps, I'm not sure about network manager, but I'd be surprised it gets installed by default on a server. I wouldn't rule out dhcp-related issues just yet.

otoh, a bad request should show up in your apache logs, so maybe you can set logging more verbose (~debug?).

you can also run tcpdump to see what's happening on the server's network interface


Also, what else is involved ? proxies ? 

You might also want to check what hostnames you're using in the apache conf, and wheither they have accurate address records in DNS or in /etc/hosts on the server (so that the server knows what names it should answer to). 

It's not that any of that would cause a real problem, but with intermittent problems like the ones you have, you're probably dealing with a combination of factors, so you want to rule out as much as possible.

Also, consider it could be your browser causing this. Can you reproduce the problem from a different PC ? With different browsers ? ...

---

### Post by bernd brechbart on 2010-05-04
thanks for all your help.

i couldn't find a solution, so i installed a virtual appliance called [turnkey linux]("http://www.turnkeylinux.org/"). it's based on ubuntu 8.04 and i haven't encountered the error so far. everything seems to work fine out of the box.

i'm just not sure if i can use it as a production server for our clients. should i?

bb

---

### Post by bernd brechbart on 2010-05-04
i can't believe it. the error has returned after it worked for nearly 12 hours. aargh!

---

### Post by bernd brechbart on 2010-05-12
got it.
ubuntu was completely innocent.
turns out the ip was still in some other servers alternative configuration.. *facepalm*

thanks for your help!

---

