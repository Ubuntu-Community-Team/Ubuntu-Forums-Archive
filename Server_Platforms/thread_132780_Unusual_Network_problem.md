---
title: "Unusual Network problem"
date: 2006-02-18
forum: Server Platforms
---

### Post by kragh on 2006-02-18
I have eth0 connected to the cble modem.
Eth1 has static IP and is connected to a switch with winxp clients.
I am trying to get Eth1 to be the DHCP server nic through which the clients connect to the server and then to the web. However, if eth1 & eth0 are active then I can ping the clients and vice versa but neither the Ubuntu server nor the clients can connect to the internet. In order for the Ubuntu server to connect to the internet eth1 has to be deactivated. Connectivity to the LAN is lost. I saw a post about turning of ACPI which I did but did not solve the problem.

---

### Post by cilynx on 2006-02-18
You're looking at a routing problem.  I don't know of any graphical easy way to do this:

This is my routing table on my laptop.

```

rcw@pyth:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.224.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0_clashed
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0_clashed
rcw@pyth:~$

```

The line with the Destination of 0.0.0.0 is called the "Default Route".

Most likely, your default route is set to your internal interface.

```

route del default

```
That will remove your default route.

```

route add default gw [external IP]

```
That will add a new default route gatewaying through your external interface.

That's the nitty-gritty of it. 

```

man interfaces

```
See what you can find out about the network setup files

---

### Post by kragh on 2006-02-19
I was able to get dhcp server going on the nic with static ip and the other nic connects to the internet. I can browse the internet at the Ubuntu (dhcp) server and I can ping the clients on the LAN. The clients get their IPs and leases. However, the clients are unable to connect to the internet.

---

### Post by cilynx on 2006-02-20
You need to enable forwarding on the router box...  Again, I don't know of a happy, graphical way of doing this.  

[Here]("http://saint.wolfteck.com/~rcw/00forward-iptables") is a simple script that you can put in /etc/ppp/ip-up.d/ that brings up a simple forwarding firewall whenevery your external connection comes up.  If your external connection isn't ppp, put the script in the appropriate if-up.d directory for your external interface.  (most likely /etc/network/if-up.d/)

Also, keep in mind that this script sets up a default forwarding, masquerading firewall.  It should work fine from the "my internal clients have internet access" standpoint.  It is NOT set up to be secure.  If you're looking for secure, read the documentation on iptables and learn to do it right.

Good Luck.

---

### Post by pjstadig on 2006-02-21
This may seem like a stupid comment, but I had to learn the hard way...

ifup uses run-parts to run the scripts in /etc/network/if-up.d/, so your script will not run unless it is marked executable and its name consists of only numbers, lower case letters, upper case letters, hyphens, or dashes. My script was named "enable-nat.sh" and it was never executed. When I renamed it to "enable-nat" it worked fine.

Paul

---

### Post by kragh on 2006-02-21
Do I just cut and paste the script into the etc/network/if-up.d directory?

---

