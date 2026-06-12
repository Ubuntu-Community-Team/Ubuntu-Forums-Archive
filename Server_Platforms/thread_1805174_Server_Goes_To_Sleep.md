---
title: "Server Goes To Sleep?"
date: 2011-07-15
forum: Server Platforms
---

### Post by flyingsuperhigh on 2011-07-15
Hey,

I'm hosting my personal website on a desktop computer running Ubuntu Server. I have my own domain name and everything. When I asked a friend to go to my personal website he was able to do so. When I asked him to do this, I was on one of my other desktop computers which is on the same local network. Later in the day, I tried to go to my personal website from school but was not able to do so. This time all the desktop computers and laptops in my house were turned off (the server was still up and running). I don't really know what is going on here. I don't know why I'm only able to access my site when I am using one of the other computers on the local network. Furthermore, when I'm not using one of the local computers, I am not even able to ssh into my server. Is there some power management issues which I need to address on the Ubuntu server machine or is the problem related to my router? Help would be greatly appreciated.

---

### Post by papibe on 2011-07-15
I would start checking the BIOS power management options, specially if the computer has a [Energy Star Label]("http://ww1.prweb.com/prfiles/2011/07/07/8628308/EnergyStarLogoj.jpg").

Just some thoughts,
Regards.

---

### Post by brighty22 on 2011-07-15
My initial thoughts point to the router - check that your services on ports 22 and 80 can be seen from the internet [here]("http://canyouseeme.org"). If not, the router is the culprit and you have some port forwarding to do :)

EDIT: Does your router have a firewall of some kind? Try turning it off and see if it works from school, or if ssh works. Either your router isn't playing nice, or your school has something getting in the way. The problem doesn't lie on the server, providing you haven't edited the iptables.

---

### Post by flyingsuperhigh on 2011-07-15
The port forwarding is fine. It's just that if I am not using my internet (i.e. I am not using any of the computers on my network) I am not able to access my personal site. If I am using one of the computers and I ask someone to go to my site, they are able to do so. It seems like my server gets disconnected from the internet when I am not using one of the other computers on the network.

---

### Post by papibe on 2011-07-15
Maybe this is too basic, but you never know...

Did you setup an static IP (or reservation) for the server? 

Regards.

---

