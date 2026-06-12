---
title: "Ubuntu Server newb"
date: 2008-02-04
forum: Server Platforms
---

### Post by warrior24 on 2008-02-04
Hello all I have been using Ubuntu for about 6 months and Debian before that for 3. So my knowledge is limited. However I am ready to take it one step further and try my hand at a Ubuntu server. I would like the server to act as a firewall and have it set up to distribute ips to my network. Currently I have one xp laptop and one 7.10 box. I already have a router for firewall but thats to easy. The server would be made up of an 800 MHz AMD Duron and 1gb of ram and two Ethernet cards. Also it would be nice to be able to share files with myselft when I am away. I downloaded the Lts version but I allready have 7.10 installed can I use a server version of that? Or should I just install the Lts and then      sudo apt-get install ubuntu-desktop


USES: Firewall, file server, ip distributor (DHCP I think), Monitor network traffic (as in what websites people visit.)




Or should I just learn more on Ubuntu desktop before I bite more that I can chew. I have been reading the how to set up a server. But its a bit daunting. As I dont know what Mysql is and other names like that.


Ps I hope i posted this in the right spot wasn't sure if it should be somewhere els.

---

### Post by DDuong on 2008-02-04
Hello warrior24,

It's great that you are looking for more challenges.  For myself, the first thing I did to learn linux is building a firewall.  I learned A LOT.  So good for you that you are up for this challenge :)  I suggest you go for it.

The firewall I used is "Shorewall".  Not to be confused with Smoothwall.  Give it a go :)  [http://shorewall.net/]("http://shorewall.net/")

---

### Post by UbuWu on 2008-02-04
[https://help.ubuntu.com/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/ubuntu/serverguide/C/index.html)

---

### Post by jonabyte on 2008-02-05
I have been using ipcop for a few years now and it works great for my needs.
It will log and block websites visited, act as a dhcp server and firewall. Not sure about the file server, but there should be an add-on for it.

[http://ipcop.org/]("http://ipcop.org/")

---

