---
title: "Opinions on need for firewall"
date: 2008-04-25
forum: Security
---

### Post by chrisbrat on 2008-04-25
Hi, 

I have a virtual server hosted at my ISP with Gutsy running and I have installed a web server and access the server using ssh.

The only ports that are shown to be active when using nmap are 80 and 22.

At the moment I don't intend to activate any other ports, so my question is would adding a firewall, or activating IPTables, be redundant or not?

Thanks.
Chris

Disclaimer : Yes I am a noob.

---

### Post by Patsoe on 2008-04-25
I guess it would be useful if you want to restrict who can try ssh logins. Plus, having something like shorewall set up your iptables rules makes things dead simple, so why not?
Also, see the forum sticky which has some opinions on this [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by brian_p on 2008-04-25
> **chrisbrat said:**
> Hi, 

I have a virtual server hosted at my ISP with Gutsy running and I have installed a web server and access the server using ssh.

The only ports that are shown to be active when using nmap are 80 and 22.

At the moment I don't intend to activate any other ports, so my question is would adding a firewall, or activating IPTables, be redundant or not?

Thanks.
Chris

Disclaimer : Yes I am a noob.


Using a firewall seems pointless to me. If you feel it necessary to restrict access via ssh it can be done with /etc/hosts.allow. For example, if you only ever login to the server from one location the lines

```
sshd: 158.152.1.59: ALLOW
sshd: ALL: DENY
```

in /etc/hosts.allow are sufficient to deny ssh access from anywhere but 158.152.1.59.

If required, you could do something similar for the web server or use its configuration file.

---

### Post by hyper_ch on 2008-04-25
well, if you want to operate a server then a firewall should not block that, right? So no point for a firewall...

I'd rather use something like hostsdeny that will update the hosts.deny file dynamically if there are too many login attempts from one IP in too short time frame.

With the setup as above you will always require that one IP address to actually ssh into the server. So if the IP addresses changes, you can't ssh in any longer.

---

