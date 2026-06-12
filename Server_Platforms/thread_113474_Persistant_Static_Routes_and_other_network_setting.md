---
title: "Persistant Static Routes and other network settings"
date: 2006-01-06
forum: Server Platforms
---

### Post by elliot on 2006-01-06
Hello community.
We're trying to replace a bunch of fedora machines that have been acting as routers with shiny new ubuntu machines.  
In the process we've run into some problems relating to rebooting the machines.

First we used to configure static routes and ip addresses in /etc/sysconfig/network-scripts/

ubuntu seems to store static ip addresses in /etc/network/interfaces
Is there a command line program that writes to that file? Or is this done manually.

In addition, we have some static routes that need to be re-installed after a reboot or networking restart.  
Usually we add them manually with a command something like:
route add -net 10.0.0.0 netmask 255.255.255.0 gw 10.0.8.1 dev eth0
but they seem to dissapear when networking restarts.  What file should contain this information?  And what are the best practices for storing the information there?

Finally, we have a iptables firewall that is generated via a bash script.  What is the best way to make this persistant over a reboot?

---

### Post by LordHunter317 on 2006-01-06
You write to /etc/network/interfaces.

The eaisest way to do static scripts and a firewall is have a script, per-interface.  Add 'up', 'down' or whatever lines you need to the relevant interface(s) in /etc/network/interfaces.

See the manpage on interfaces for more details.

---

### Post by elliot on 2006-01-11
Thanks for the help with /etc/network/interfaces
The ip address issue seems to be resolved.

I'm still having problems with the static routes.  
Is there a way to flush the routes?
man route doesn't turn up anything.

My current thought is that I will append a script to /etc/network/interfaces something like:

 post-up /etc/network/if-up.d/route.sh

that will flush the routing table and then add the correct static routes.  Sadly it errors since I can't seem to flush the routes.  

Also, can anyone tell me where the routes are stored?
/proc/net/route seems to be the place, but it isn't human readable.

---

### Post by LordHunter317 on 2006-01-11
You use the route command to mainpulate the routing tables.  Why are you trying to *flush* them though.  That doesn't sound like a good idea to me.  You should only be adding and deleting the specific routes you need.

---

### Post by elliot on 2006-01-12
A semi final solution:
Static ip addresses can be specified in the /etc/network/interfaces file.
See "man interfaces" for how to set that up.  In addition you can specify a post-up command that is run after a specific interface is brought up (and run at startup if the interface is broughtup at boot time.)
Here's a quick example:
```
auto lo eth0 

iface lo inet loopback

iface eth0 inet static
     address 10.0.8.10
     netmask 255.255.248.0
     broadcast 10.0.8.255
     post-up /etc/network/if-up.d/routes.sh
```

In this case we are using the routes.sh file to flush and re-add static routes to the kernel's routing table.  Make sure this file is executable (chmod 755 routes.sh).

Within this file the basic syntax is:
```
ip route flush dev eth0
```
to flush a route and then:
```
ip route add to 10.0.8.0/24 via 10.0.8.1 dev eth0
``` 
to add a route back in.
Here is a quick example routes.sh file:
```
#!/bin/bash

# eth0 is 10.0.8.0 network
# eth3 is 192.168.1.0 network (wan)
# eth4 is Internet

# flush default routes
ip route flush dev eth0
ip route flush dev eth3
# Don't flush eth4 because it should be correct
#ip route flush dev eth4

# Add correct routes
# Send all 10.0.8.0-10.0.15.0 traffic out eth0 directly to switch
ip route add to 10.0.8.0/21 dev eth0

# Send 192 traffic onto the switch
ip route add to 192.168.1.0/24 dev eth3

# send 10.0.3.0 traffic to the correct router 
ip route add to 10.0.3.1/24 via 192.168.1.2 dev eth3

# Send all other 10.0.0.0 traffic to the WAN router 
ip route add to 10.0.0.0/8 via 192.168.1.1 dev eth3

# Send all remaining traffic to the internet
ip route add to 0/0 dev eth4

```

As you can probably see you can do a whole lot with the post-up option in interfaces.  We're also using it to run a script to build an iptables firewall.  Anything you want to do to your network when it comes up can be done using this method.  Just remember two things.  chmod 755 your files, and you can only run one script per interface, so you might have to make a script that calls others if you want to do complex network tasks.

---

### Post by djrakun on 2007-10-23
Can you add the route directly in the /etc/network/interfaces file and it will act as a persistent route, or is it necessary to use a the script?

---

### Post by MJN on 2007-10-23
You can add the commands individually by giving them their own post-up (or whatever) prefix. For example:

```

iface eth0 inet static
      address 10.0.8.10
      netmask 255.255.248.0
      broadcast 10.0.8.255
      post-up ip route flush dev eth0
      post-up ip route add to 10.0.8.0/21 dev eth0
      .
      .

```Mathew

---

### Post by TitanKing on 2007-10-29
Good and simpler guide:

[http://www.pcbuyersguide.co.za/showthread.php?p=62262#post62262](http://www.pcbuyersguide.co.za/showthread.php?p=62262#post62262)

---

### Post by MJN on 2007-10-29
> **TitanKing said:**
> Good and simpler guide:

[http://www.pcbuyersguide.co.za/showthread.php?p=62262#post62262](http://www.pcbuyersguide.co.za/showthread.php?p=62262#post62262)

Nah - too clunky.

Stick with pre-up and post-up directives as then you can specify *per-interface* rulesets. The if-up.d scripts act when *any* interface is enabled hence in the case of multiple adapters you may have to perform additional logic in the script to determine which interface had gone through a state change if the actions depended on it.

Always strive to follow the [KISS principle](http://en.wikipedia.org/wiki/KISS_principle).

Mathew

---

