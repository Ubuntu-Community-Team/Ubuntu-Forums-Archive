---
title: "server setup and SSH errors"
date: 2007-03-12
forum: Server Platforms
---

### Post by bandie on 2007-03-12
I have been following a server how to 
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3)

the problem I have is when I type the hostname and hostname -f
I get different results see bold text below.

Also I should be able to use SSH or putty but both are unable to find my host
Any ideas - I'm pulling my hair out - it must be something stupid i'm doing wrong

my router is a 3 com office LAN four port Hub ISDN, this seems to work OK as I can 
apt-get update without problem 
The tutorial begins below


Run

sudo passwd root

and give root a password. Afterwards we become root by running

su


4 Install The SSH Server
Ubuntu does not install OpenSSH by default, therefore we do it now. Run

apt-get install ssh openssh-server

You will be prompted to insert the installation CD again.


5 Configure The Network
Because the Ubuntu installer has configured our system to get its network settings via DHCP, we have to change that now because a server should have a static IP address. Edit /etc/network/interfaces and adjust it to your needs (in this example setup I will use the IP address 192.168.0.100): 

vi /etc/network/interfaces

# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static        
address 192.168.0.100        
netmask 255.255.255.0       
 network 192.168.0.0        
broadcast 192.168.0.255        
gateway 192.168.0.1 

Then restart your network: 

/etc/init.d/networking restart 

Then edit /etc/hosts. Make it look like this:

vi /etc/hosts

127.0.0.1       localhost.localdomain localhost
192.168.0.100   server1.example.com     server1


[B]Now run

hostname
hostname -f

Both should show server1.example.com. If they do not, reboot the system:

shutdown -r now

Afterwards, run

hostname
hostname -f

again. Now they should show server1.example.com. [/B]

From now on you can use an SSH client such as PuTTY and connect from your workstation to your Ubuntu server and follow the remaining steps from this tutorial.

---

### Post by bandie on 2007-03-12
Both should show server1.example.com. If they do not, reboot the system:

shutdown -r now

Afterwards, run

hostname
hostname -f

again. Now they should show server1.example.com. 


they don't even after a reboot

hostname -     gives server1
hostname -f  - gives server1.example.com

---

### Post by Mr. C. on 2007-03-12
The hostname returns an unqualified hostname (eg: buzz).  Hostname -f (of --fqdn) returns the fully qualified name (eg. buzz.lightyear.com).  Your configuration is correct.

A fully qualified hostname only makes sense in the context of DNS.  You are likely using your ISPs DNS servers, and they can never return the FQDN of your host, since it is on a private IP address (and you wouldn't want to create public A records for private address space).

Did you have a problem connecting, or something else?

MrC

---

### Post by bandie on 2007-03-13
OKay that answers one question - thankyou very much
I use a 3Com lan modem ISDN office connect 4 port built in hub
Server has two NICS one connected to the above LAN modem the other to another a Belkin four port hub.

The question is this 
Am I correct in saying the two laptops I have should connect to the belkin hub and use the server for internet access through the LAN modem?

---

### Post by Mr. C. on 2007-03-13
> **bandie said:**
> 
The question is this 
Am I correct in saying the two laptops I have should connect to the belkin hub and use the server for internet access through the LAN modem?

So you want your server to act as a router?  I thought this question was about SSH server setup?  You can configure it as a router if that's what you want, then, yes, all your PCs will connect to your hub(or switch).

MrC

---

### Post by bandie on 2007-03-14
my original problem was the hostname issue which you have thankfully answered, the SSH problem I thought was a result of the first issue, which I guess is not.
Basically I have a PC with two NICS and a ISDN LAN modem, I wanted to build a network server /client so I could use either laptop to connect to my server.
Additional help would be gratefully received.

Server PC eth1 NIC connects to  ISDN Lan modem - all works OK including internet access - guess its using DCHP from modem?

Server eth0 NIC connects to 4 port belkin hub - 

laptop connected to either Belkin hub or ISDN hub will not allow SSH 
I have enabled SSH server

---

### Post by Mr. C. on 2007-03-14
Your laptops connected to your hub (which is connected to eth0) need to be on the same network as eth0.  If you run DHCP on the server, it would provide the proper addresses.  Otherwise, you need to use static IPs for your eth0 interface, and those systems connecting to the hub (your laptops).  All must be on the same IP network (eg. 10.0.0.0/8).  Furthermore, that network must be different from your eth1 network.

If you ssh server is accepting localhost connections from the server itself, and you've not reconfigured sshd, and there is no firewall running (eg. iptables), then your laptops will have access to the ssh server.

For allowing your laptops access to the internet as well...

If your modem does NAT, you can simply connect all your devices to it.  If it does not, then either you need to purchase an inexpensive router to connect your devices to (one that does NAT - it is probably safe to say today that all of them do ), or you need to configure your linux box to act as a router, which passes packets to and from the modem, to and from the second NIC's network.

This requires you to learn a little about routing and how to configure your server as a router.  Review the week 6 "Routing" notes and lab work:  [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

If things aren't working, show me the output of
```

ifconfig -a
netstat -rn
```

and the IP, netmask, and gateway of your laptops.

MrC

---

### Post by bandie on 2007-03-14
Ok thanks once again, I'm away to play and will get back to you:)

---

