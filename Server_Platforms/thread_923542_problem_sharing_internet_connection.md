---
title: "problem sharing internet connection"
date: 2008-09-18
forum: Server Platforms
---

### Post by belcanm on 2008-09-18
Hello. I'm not an actual newbie to Ubuntu and Linux, but I stumbled upon a problem that I cannot find an answer for.
I installed Ubuntu 8.04 Server to a PC in order to make a small router and torrent box out of it. I use Webmin and PuTTy in order to manage the server. I connect to the internet using PPPoE over eth0, and eth1 connects to a switch where my 2 desktops (mine and my parents') are also plugged in. I have DHCP server enabled for the local network and I've also set up NAT so that I can have internet on the 2 desktops.
The problem is that I cannot make the 2 desktops to access internet simultaneously. Whenever one is used to surf the web (just surfing and Yahoo! Messenger, not heavy downloads or torrents) the other one cannot open anything related to internet (browser, messenger, antivirus updates, etc). So they can only take turns in using the internet, which is very annoying, as you can guess.
My questions are why is this happening and what can I do to make things work as expected.
Thanks in advance for your answers.

---

### Post by jamesrfla on 2008-09-18
I am not sure if this will work but hear it is [http://www.untangle.com/](http://www.untangle.com/)

---

### Post by warchief_ryan on 2008-09-18
I used iptables to make my ubuntu server box NAT/masquerade, to share my connection to my other computers and it works great.

I can't really tell you why you current setup isn't working because I have no idea how you have it setup.

---

### Post by windependence on 2008-09-19
What are the local IPs of the two computers?

Is your machine set up as the gateway?

-Tim

---

### Post by belcanm on 2008-09-19
The 2 computers have addresses given by the dhcp server in the 192.168.1.2 - 192.168.1.6 range, with the netmask 255.255.255.248.
The server acts as a gateway, I have NAT enabled.

---

