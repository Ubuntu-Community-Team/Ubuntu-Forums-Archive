---
title: "Is there a simple way to establish and share a PPTP connection?"
date: 2007-06-29
forum: Server Platforms
---

### Post by PryGuy on 2007-06-29
Good day people! I wonder if it's possible to make a PPTP connection that I could share with the other machines in LAN. I'm a newbie in Linux server aspects so I'd love to know more about it. Ideally, I'd love to get a tool comparable with Kerio Winroute, but I doubt it's possible. What do I want to get:

- a GUI PPTP utility
- a firewall (is Firestarter a good choice for a small LAN server?)
- webmin like statistics

Is it necessary to install the Ubuntu Server edition and why?

Thank you for your suggestions.

---

### Post by Maxtorm on 2007-07-03
I'd be inclined to ignore the GUI.  There are good instructions here for creating a PPTP connection in the command line interface: 

[http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html](http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html)

If you install Apache on an Ubuntu server box with two NICs in it, you can set up Apache to be a forwarding proxy server and then you don't (in my estimation) need a firewall.  Then you can use one of the numerous Apache statistics packages.

All of this could be done on a standard Ubuntu Desktop installation.  The only difference between Ubuntu Desktop and Ubuntu Server is that Server has no GUI and its default package set is geared towards a lean server installation.

---

