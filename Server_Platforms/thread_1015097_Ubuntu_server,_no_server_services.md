---
title: "Ubuntu server, no server services"
date: 2008-12-18
forum: Server Platforms
---

### Post by sorrow777 on 2008-12-18
My question is how would I make sure my Ubuntu server isn't trying to be a server on our network. 

In the past when working with solaris I would ensure to touch /etc/notrouter  

What sort of things like that exist for Ubuntu server.

Also i would imagine i could ensure that dns is not enabled.  I guess i'm looking for a list i could use to ensure i don't run into any problems on our network.  i would hate to put my incoming box on the network and forget something like it acting as a primary dhcp server!  (:

thanks in advance

---

### Post by Titan8990 on 2008-12-18
Unlike many other distros, Ubuntu does not have server apps installed by default.

I would nmap scan the machine from another computer on the network to ensure Ubuntu is not listening on any ports.

---

### Post by capscrew on 2008-12-18
You can scan your local host from the CLI with:```
netstat -plntu
```

---

### Post by sorrow777 on 2008-12-18
yeah and |grep LISTENING  or open depending on whats what.

Ok so the system76 box i get with 8.10 shouldn't have any server apps running.  I'll check before i get it on the network but its good to know.

thanks guys/gals

---

### Post by albinootje on 2008-12-18
> **sorrow777 said:**
> yeah and |grep LISTENING  or open depending on whats what.

Ok so the system76 box i get with 8.10 shouldn't have any server apps running.  I'll check before i get it on the network but its good to know.


If you use the ubuntu-server install cdrom, then you get a choice of which services you would like to install.

And concerning DHCP, by default you can install a dhcp-server in Ubuntu, but i always needed to edit the /etc/dhcpd.conf file because a subnet declaration was needed for one of the interfaces. 
It's pretty unlikely that the default example dhcpd.conf is gonna start right away and cause trouble.

---

### Post by cdenley on 2008-12-18
> **sorrow777 said:**
> yeah and |grep LISTENING  or open depending on whats what.

The "l" switch will only show listening processes.

p = process name/id (must be run as root)
l = listening processes
n = don't resolve hostnames
t = tcp ports
u = udp ports
```

man netstat

```

---

### Post by Iowan on 2008-12-18
I suppose **ps aux** would yield TOO much information...

---

### Post by cdenley on 2008-12-19
> **Iowan said:**
> I suppose **ps aux** would yield TOO much information...

It doesn't really help to determine what TCP or UDP ports you're listening on. Once you run "netstat -plntu", that can help determine more about a listening process.

---

### Post by sorrow777 on 2008-12-19
I will try all of these things once i get my system76 box.  I'm gettin an eland pedestal quad xeon 4gb ram and 4 250g drives  (:  sexy right?

I'm going to use the virutalization kernel to do testing of solaris 10 builds and so forth.

---

