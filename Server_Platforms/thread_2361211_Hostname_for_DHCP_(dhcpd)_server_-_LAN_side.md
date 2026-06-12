---
title: "Hostname for DHCP (dhcpd) server - LAN side"
date: 2017-05-13
forum: Server Platforms
---

### Post by milkness on 2017-05-13
This may seem like a stupid question to some but I am struggling to find out how to set a hostname for my dhcp server,  LAN side.

I am managing the server (dhcpd) from webmin with all of it's packages up to date.

My network configuration looks like this:

[FONT=times new roman]

[FONT=courier new][SIZE=4][SIZE=3]Internet  -----to------- Router (Only 100MB for it's LAN) (192.168.0.1) ------to------ Ubuntu server (1 GB a second LAN)(192.168.1.1[/SIZE])[/SIZE][/FONT][/FONT]



I am relatively new to networking but I have managed to tech myself just enough to allow me to configure my own network, but when I try all the default ways of setting my hostname of the machine, it just sets it for the first router (192.168.0.1)'s LAN side not my server's dhcp LAN. I have fiddled around with the hostname settings in webmin but I feel like I am missing something.

The server's current hostname is "gateway", which I cant find a reference to anywhere.


Please help! - Thanks in advance.

I will post a solution if I manage to find a way to do it myself, i just want to use it to quickly connect to my server via ssh without having to type out the ip.

:) - Milkness

---

### Post by wildmanne39 on 2017-05-13
*Thread moved to **Server Platforms**.*

---

### Post by milkness on 2017-05-14
Thanks :)

---

### Post by darkod on 2017-05-14
Name to IP resolution is done by DNS servers, doesn't really matter which hostname you set on a machine/server.

1. Are the machines on the LAN using 192.168.0.1 or 192.168.1.1 as their primary dns server? Or something else?

2. If you want to connect by name only from specific small number of machines it is probably best and easier to use the local hosts file on the client machine that you want to connect from. The only thin you need to do is make a manual entry in its hosts file, something like:
192.168.1.1   myserver

Then when typing myserver the machine knows it stands for 192.168.1.1.

3. Webmin is not really supported and recommended, alhtough many people seem to be interested in use it as GUI frontend. For setting up the hostname on your server I recommend connecting by ssh session and put the hostname you want to use in /etc/hostname and /etc/hosts. Those are the files used to set the hostname on the server.

---

### Post by milkness on 2017-05-14
Thank you darkrod, I did the client side /etc/hosts files and it worked a treat! Thanks!

The network was using 192.168.0.1 as primary because using 192.168.1.1 (which makes more sense to use) did not allow me to connect the the internet. Yet 192.168.0.1 does not dispense DNS leases but 192.168.1.1 does even thought it is not primary.

---

### Post by darkod on 2017-05-15
If it is solved please mark it as solved. You can do that in Thread Tools above the first post.

---

