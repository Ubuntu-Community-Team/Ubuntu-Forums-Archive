---
title: "Apache doesn't work with IPv6 - syntax error"
date: 2008-10-02
forum: Server Platforms
---

### Post by ahaitoute on 2008-10-02
After I've installed Apache2. I've added a line:
Listen [::1]:80

In /etc/apache2/ports.conf, then I've restarted apache and got an error:
[crit] (EAI 9)Address family for hostname not supported: alloc_listener: failed to set up sockaddr for ::1
Syntax error on line 2 of /etc/apache2/ports.conf:
Listen setup failed

I've got IPv6 installed on my server, and I can ping to ::1.

I need help for this problem.

---

### Post by MJN on 2008-10-02
Does it work okay if you leave the directive as **Listen 80** i.e. listen to port 80 on all interfaces (IPv4 and IPv6)?

Mathew

---

### Post by ahaitoute on 2008-10-31
The solution is to configure the ipv6 on your sites and then reboot the computer. It's weird that the ipv6-sites doesn't work after a force-reload.

---

### Post by tomski on 2009-12-10
> **ahaitoute said:**
> The solution is to configure the ipv6 on your sites and then reboot the computer. It's weird that the ipv6-sites doesn't work after a force-reload.

please provide more detailed response

i have a jaunty server and the only 'web based' app i cant access via ipv6 is apache
cacti & ntop all work ok

---

### Post by jrogers360 on 2010-02-23
Ya, that response confused me as well.  What he means is configure your server with an IPv6 address, then reboot the entire server, and apache magically starts listening on IPv6 (using the default configuration, no need to change the Listen statement from anything other than 'Listen 80')

I've tested this, and it does work.  I cannot explain why it is necessary though.

I should have tried an apache reload, before restarting the server.

---

### Post by karimakela on 2011-04-15
Hi, there has been lots of discussion about this and somewhat similar things, and also a bug report 397393.
 
It seems to be a feature, not a bug:
 
- if the system has only "Scope:Link" IPv6 addresses (as seen with 'ifconfig -a'), Apache thinks that there is no IPv6 service, and does not accept Listen with any kind of IPv6 syntax
 
- if one adds just a proper but random IPv6 address and restarts Apache, it starts to work OK and starts to accept also connections to the Link address. No need to add anything in the apache configuration, no need for any "listen [::]:80" entries. Just the plain "Listen 80" is enough, handling both IP protocols.
 
I added an official IP of mine with the following
 
sudo ip addr add 2a00:8a00:4200::209:6bff:fe2d:8d08/64 dev eth0
 
Now I have both the "fe80" address and a proper address, and my system listens to both IPv4 and IPv6.
 
ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:09:6b:2d:8d:08 
inet addr:10.144.154.193 Bcast:10.144.155.255 Mask:255.255.254.0
inet6 addr: 2a00:8a00:4200:0:209:6bff:fe2d:8d08/64 Scope:Global
inet6 addr: fe80::209:6bff:fe2d:8d08/64 Scope:Link

---

### Post by mgiesl2s on 2011-11-29
Hallo I have the Problem, that i can open from the Ubuntu Client where the webservice is running from Firefox at Address: [2a00:8a00:4200:0:209:6bff:fe2d:8d08], but it don't work with the lokal link Address: [fe80::209:6bff:fe2d:8d08]. From an Windows 7 Client it Work to open the Adress: [fe80::209:6bff:fe2d:8d08] with Firefox. Can somebody explain or help me, why it is not possible to open an lokal link ipv6 Adress by an ubuntu client with Firefox?

---

