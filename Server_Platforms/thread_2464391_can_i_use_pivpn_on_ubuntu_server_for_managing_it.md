---
title: "can i use pivpn on ubuntu server for managing it"
date: 2021-07-01
forum: Server Platforms
---

### Post by moowii on 2021-07-01
[COLOR=#1A1A1B][FONT=&amp]hi

my windows home server 2016 just went up in smoke (metaphorically at least) and i want to replace it by a new system running on ubuntu server with docker and stuff installed. this server will be located in a remote place (meaning in another LAN than my client) and i want to access it via a windows computer.

[/FONT][/COLOR][COLOR=#1A1A1B][FONT=&amp]my idea is to install pivpn and [enable SSH]("https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-20-04/"), and then connect via VPN and putty to the console so i can install and manage stuff. this idea stems from using pivpn on my raspberry pi in combination with pihole.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]will this work out? or do i miss anything?

also, what things should i install using docker and what should i install standalone?
[/FONT][/COLOR]

---

### Post by Frogs Hair on 2021-07-01
Moved to ***Server Platforms***.

---

### Post by ActionParsnip on 2021-07-01
Could just SSH directly to the server from the outside. Use Fail2ban and use SSH keys only as authentication. You don't *really *need a VPN to connect to a server if you are using SSH. SSH is secure. It's what the first 's' in it's name means

---

### Post by LHammonds on 2021-07-02
Why use pivpn over openvpn?  Just curious.  I use neither since I have an enterprise firewall with VPN built-in.

As for Docker vs standalone, I still tend to install standalone apps.  If the repositories have a sufficient enough version, I will use the repo first.  If not, I will manually install the app.  Sometimes I have to install standalone simply because of the server farm design I use.  I like presenting a single database server (even if in a cluster + proxy) which means I cannot use ANY of the pre-packaged applications like Wordpress or NextCloud which will install its own database on the application server.  I want my app servers to be JUST app servers and have them all point to my robust database server/cluster.   If I have a bunch of silo systems, that just means I have to create that many more database-specific backup jobs all over the place.

To me, Docker and the like seem ok for very complicated / dependent installs where you want to mimic the exact environment that it was developed for (e.g. testing) but I have not really found a use case for my environment yet.  But I'm not like most other environments so to each their own.

@ActionParsnip, it is always more secure to NOT expose a server to the Internet unless you absolutely have to...and even then, try to stick a proxy between it. ;)

LHammonds

---

