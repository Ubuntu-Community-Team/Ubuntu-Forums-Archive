---
title: "Help needed for iptables setup"
date: 2008-02-22
forum: Server Platforms
---

### Post by evert_ on 2008-02-22
Hi all,

I've just installed ubuntu server on my home server. It's a x2 4800+ with 1gb of ram and 4*500gb disk for my mdadm raid5 set. Ubunut itself is installed on a 4gb usb stick. The server is used as a ftp server, trackmania nations server and a (local) webserver. I'm using it with some friends who live in the same building as me to share data and to make backups. Also downloads are (mostly) done on this server. 

The current setup looks like this:
[IMG]http://omploader.org/vZDhs/old.JPG[/IMG]
This is working all right, but i'm wanting to go to the following setup:
[IMG]http://omploader.org/vZDht/new.JPG[/IMG]

I'm having a few reasons why i want this new setup: now when somebody is downloading something from the internet, the internet is going slow for all the others and my trackmania server is getting lagg. I'm having two network cards in this server and i've used it before (with freebsd 7 beta) as a NAT. But this time i don't only want to do NAT'ing but also some more advanced iptables rules:

- I need to give my trackmania server the highest priority of all.
- The downloading on my server (hellanzb for usenet and torrents) need to be capped at a certain speed and need to have lower prioraty then the rest.
- I've to give the desktop users a fairly high amount of bandwith towards the internet, but i need to make sure they don't make my trackmania server lagg. I certainly need to cap the amount of upload and the torrent port(s) and the amount of connections. 

I've been searching with google after iptables howto's and stuff, but i'm unable to understand how i can do it. There is quite some information about iptables, but even after reading a lot i haven't got a clue how to start making my rules :(.

A little help is appreciated, thanks in advance :).

---

### Post by tehet on 2008-02-22
Hi,
The following script works for me. Put it in /etc/init.d/ and call it "iptables", "firewall" or whatever.
```
#!/bin/bash

# Flush old rules
iptables -F

# Route net packages
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

# Drop incoming traffic you didn't ask for, i.e. close all ports for incoming traffic
iptables -A INPUT   -i eth0 -m state --state NEW,INVALID -j DROP
iptables -A FORWARD -i eth0 -m state --state NEW,INVALID -j DROP

# Optional rules
# Open incoming http request, if you've got a web sever
iptables -I INPUT -p tcp --destination-port 80  -j ACCEPT

# More optional rules, for ssh, ftp and https
iptables -I INPUT -p tcp --destination-port 21  -j ACCEPT
iptables -I INPUT -p tcp --destination-port 22  -j ACCEPT
iptables -I INPUT -p tcp --destination-port 443 -j ACCEPT

echo 1 > /proc/sys/net/ipv4/ip_forward
```
[edit]
eth0 will be looking at the web, eth1 will be looking at your back-end
[/edit]

As for capping up and downloads, I think that'll be a real pain to do with iptables/netfilter. It's probably better to use iproute2
[http://www.linux-foundation.org/en/Net:Iproute2_examples](http://www.linux-foundation.org/en/Net:Iproute2_examples)
or MasterShaper
[http://www.mastershaper.org/index.php/Main_Page](http://www.mastershaper.org/index.php/Main_Page)
or something like that for capping, though I have no experience with either.[edit] if you get shaping to work, I'd be interested in a recipe :)[/edit]

---

