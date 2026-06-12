---
title: "Basic firewall question"
date: 2010-01-26
forum: Security
---

### Post by y_farkash on 2010-01-26
Hi,

This is very basic but I couldn't find the info.

When I install Ubuntu 9.10, is the firewall on?

Are all ports open? Are they all closed? Are some open and some closed? If I port-scan a fresh install what should I expect?

I am trying to set up some software that needs access to port 27350. I have a number of boxes on a local subnet, all with manually configured IPs and manually configured */etc/hosts* file to find each other by hostname. I can remote-desktop and ssh into the new machine from the other ones. When I port-scanned the machine some ports were open, but not the one I needed. So I used UFW to open that port by using:

[FONT="System"]sudo ufw enable
sudo ufw allow 27350[/FONT] 

After this I could not remote-desktop or ssh to it anymore.

Are all the ports closed now that I turned ufw on, which makes the machine inaccessible via remote-access?

For my needs, I don't need a firewall at all, I can have all ports open. How do I make sure all ports are open in Ubuntu?

Thanks!

---

### Post by hhlp on 2010-01-26
when you install ubuntu the firewaal are not set but if you want you have a GUI for that purpouse it call GUFW you cant get in synaptic

---

### Post by Enigmapond on 2010-01-26
```
sudo ufw status
```

```
sudo ufw disable
```

and for any other questions:
```
man ufw
```

---

### Post by y_farkash on 2010-01-26
By saying "the firewall is not set" does that mean that all ports are open? 

If I port-scan this machine should I see all of them open, or does port-scanning only report ports which are listening? 

Are "open" and "listening" the same thing?

I realize how newbie this question is, but it is so basic I couldn't find the answers.

---

### Post by Enigmapond on 2010-01-26
[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

---

### Post by cdenley on 2010-01-26
By default, there are no firewall rules, so no traffic is filtered. This doesn't mean the ports are "open", though, since no services are listening. "Listening" means there is a service binded to a port and waiting for data to be received. This doesn't necessarily mean open, since firewall rules can filter the traffic it is waiting for.

open = unfiltered + listening

On a default install, there are no TCP listening processes, so no "open" ports. There are a couple UDP listening processes (avahi and dhcp), but you don't need to worry about those. There are no firewalls rules by default which would filter traffic an application/server you run is listening for.

A port scan typically checks to see if there is a server listening on commonly used ports which can be reached from the scanning computer (not filtered). If a port scanner can see a service, then someone can interact with that service in some way. If you scan a computer from itself, the results may be misleading since filtering may not apply.

---

### Post by bodhi.zazen on 2010-01-26
A port is open only if you have a server installed and running.

using ssh as an example, if you do not have openssh-server installed,  port 22 is closed.

If  you install opnessh-server and start the server (either automatically when boot or manually) then the port is open.

Firewalls then act as a bouncer and will monitor incoming and outgoing traffic based on rules you specify.

The options for a firewall is 

ACCEPT - allow the network traffic
REJECT - deny the traffic with an error message back to the person attempting to connect.
DROP- deny the traffic without any error message.

Both REJECT and DROP = closed

The default firewall is iptables and you can configure it with any number of tools, including ufw and gufw

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

To allow traffic on ssh, 

sudo ufw allow 22

The links I gave you will give you more specific instructions on how to limit ssh traffic to your LAN.

Now if you have a router you may not need to configure iptables as most routers include firewall traffic as well =)

For more info on iptables see ;

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by y_farkash on 2010-01-26
Thank you so much cdenley and bodhi.zazen!

This is just what I was confused about and you made it crystal clear.

Cheers!

---

### Post by mkvnmtr on 2010-01-26
You can check your system with the app Zenmap a front end for nmap. On a standard unchanged Ubuntu install it shows all ports closed. It sounds like an app that you will like to use after you get set up.

---

### Post by rookcifer on 2010-01-26
There are no ports that cannot be closed.  What I mean is that on Windows there are various ports that cannot ever be closed except by using a firewall (port 135 for example).  Such is not the case with Ubuntu because Ubuntu does not stupidly utilize RPC like Windows does.  The whole personal firewall craze started with Windows because of the way M$ decided to hard code open ports into the OS -- ports that could never be closed (except with a firewall).  Again, such is not the case with Linux.

Bottom line: by default Ubuntu has no open ports at all.  You will only need a firewall if you plan on installing a listening service.

---

