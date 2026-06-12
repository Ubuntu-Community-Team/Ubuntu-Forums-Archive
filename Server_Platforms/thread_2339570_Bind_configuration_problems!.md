---
title: "Bind configuration problems!"
date: 2016-10-10
forum: Server Platforms
---

### Post by flaviustech on 2016-10-10
Hey there, i have some difficulties with configuring bind and create websites.
I have an gb connection but is dynamic, however my isp give for free ddns so i made it [COLOR=#ff0000]pcmod.go.ro[/COLOR] for my connection. I have a asus router with [COLOR=#ff0000]192.168.1.1 ip[/COLOR], i made a ubuntu server with intel mb s3000ah, 2gb ram ddr2, dual core proc.
The ubuntu server got [COLOR=#ff0000]192.168.1.164[/COLOR] ip and i set it to static ip in network/interfaces
I setup master zone for pcmod.go.ro wich is my ddns from my isp and forwarded from router to acces over the internet and working fine. The problems i have with nameservers, when i add virtual host with new website in local networking is working fine, but when i try to access that website from outside local network i get errors.
I created for a test a virtual host "[COLOR=#ff0000]ciomolugma.ro[/COLOR]" when i access from personal computer is working. Here are the errors that bind throw.
**The following errors were found in the BIND configuration file /etc/bind/named.conf or referenced zone files ..**
 

[LIST]
[*]/etc/bind/named.conf.options:35: option 'topology' is not implemented 
[*]/var/lib/bind/ciomolugma.ro.hosts:18: ignoring out-of-zone data (www) 
[*]zone ciomolugma.ro/IN: has no NS records 
[*]zone ciomolugma.ro/IN: not loaded due to errors. 
[*]_default/ciomolugma.ro/IN: bad zone 
[*]/var/lib/bind/pcmod.go.ro.hosts:10: ignoring out-of-zone data (www) 
[*]zone pcmod.go.ro/IN: NS 'ns1.pcmod.go.ro' has no address records (A or AAAA) 
[*]zone pcmod.go.ro/IN: NS 'ns2.pcmod.go.ro' has no address records (A or AAAA) 
[*]zone pcmod.go.ro/IN: not loaded due to errors. 
[/LIST]
Also i have few websites registered on my country TLD with *.RO terminal for my country, and i want to host website files myself. How can i get nameservers to add to my registrar?

And like this is my config network 
# The primary network interface
iface eth0 inet static
        address 192.168.1.164
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1
Btw i installed webmin/virtualmin on server.

---

### Post by Vegan on 2016-10-12
bind is designed for programmatic configuration, use zpanel which can help setup a dot.com

---

### Post by flaviustech on 2016-11-09
Thanks, i figured out that dns server is in fact a tunnel communication route, i allways made confusion between dns and fqdn. I missconfigured server ip. Now i have set like 5 websites and more to come. I installed webmin. 
But i have noticed a time response high when i check .com website from google pageinsight on a blank site i get 500ms time response. I've modified apache2.conf  Timeout from 300 to 45 only and mpm_prefork.conf for maxworkers is set to 150. 
I know 2gb ram isnt ideal, but websites will be blog type with low traffic. I expect that low traffic to have a quick opening website.
It's true that i host sites from europe, and when a client from u.s try to connect to my server, it will take a lil' longer to resolve querry from Europe.
My isp however have 24 ms response in us servers. Why from 24 ms till my website appear with 500ms time response as google page insights shows me?

---

