---
title: "Domain"
date: 2006-08-02
forum: Server Platforms
---

### Post by dgcarter on 2006-08-02
Ok, I kinda know whats causing this but I don't have a clue hoe to fix it...

My donain name softnet-server.dyndns.org only works on the internet side (eg: works on a friends computer @ another house)

BUT if I try to use the domain on my internal network (LAN) it takes me to my routers config panel.

The domain only works if I go to it from my Ubuntu Server desktop but not on any of the other computers on my network. So I have to use my servers local IP to connect fron the other computers on my network. (10.0.0.5)

How can I fix this?

---

### Post by Glut on 2006-08-03
The simple way is to add the entry to your /etc/hosts file, the hard way is to configure your router to redirect that port from incoming internal connections to the appropriate server.

---

### Post by dgcarter on 2006-08-03
What would I put in that file?

My domain is soft-net.co.za
and my servers LAN IP is 10.0.0.5

---

### Post by Glut on 2006-08-03
According to [color=seagreen] man hosts [/color] the synax is:
IP_Address    Host_name    Alias    Alias   ...
so in your case:
10.0.0.5 softnet-server.dyndns.org [www.soft-net.co.za](www.soft-net.co.za) 
or whatever aliases you require

---

### Post by dgcarter on 2006-08-04
Ok, cool, but that only seems to work for my server, but if I try to browse to the site from any of the other computers on my LAN it dosen't work, so how do I configure my router to do the redirect thing.

This is that the routing config looks like:
[Click here]("http://i49.photobucket.com/albums/f285/tsaec/router.jpg")

---

### Post by Sam on 2006-08-05
You need to edit the /etc/hosts on EVERY computer of your local network, if you don't have a common DNS server.

If you have any Windows box, the file to edit is C:\WINDOWS\system32\drivers\etc\hosts

---

