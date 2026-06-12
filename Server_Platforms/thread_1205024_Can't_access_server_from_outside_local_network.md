---
title: "Can't access server from outside local network"
date: 2009-07-05
forum: Server Platforms
---

### Post by p0732658 on 2009-07-05
Hi!

I had my apache2 server (mysql 5, PHP5, webdav) install and working perfectly with Ubuntu 8.04.  Thru dydndns, I was able to reach my server from anywere on port 8000 (my ISP bloc port 80).  Since I wanted to install OpenOffice.org3 for some headless converting, I upgradeted my install to 8.10, then 9.04.  Now, everything works fine if I use the physical adress (192.168.0.120), but doesn't if I use the domain name from dyndns.  I also can't reach my server from outside my network even if I use the adress detected by dyndns (24.202.1.216).  I haven't change anything on my router.  My ports.conf file is the same with port 8000 open.  I even set Firestarter to allow all incoming and outgoing trafic and even tried to uninstal Apporamor.

After a lot of hairs pulling, I reinstall everything with Ubuntu 8.04.  Everything was again working fine outside my local network.  I then had the stupid idea to upgrade to Ubuntu 8.10 because I could not get php/java bindgin working properly for oodom.  Now the same problem came back!!!

Thank you for your help or suggestion!

Denis

---

### Post by Boondoklife on 2009-07-05
Ok so if you are on another computer in your network you CAN connect to the server if you use the ip correct?

I assume the computers are behind a router correct?

---

### Post by bfdhud on 2009-07-05
I have this problem too. Almost exact.

I had a 8.04 server running OpenSSH server.  I changed the listening port for security reasons.  Then in my router forwarded port 22 to 48000 and sent it to my linux server.

I had dyndns.com assign a hostname to my ip address and ddclient updating dyndns.com

I did some Hardware upgrades and decided to install the newest version of Ubuntu.

Now I cannot connect to my server unless I do it with the router assigned IP address.

ssh -p 48000 username@192.168.0.199

Everything else gives a connection refused error.

---

### Post by ndxtg on 2009-07-06
> **p0732658 said:**
> Hi!
Now, everything works fine if I use the physical adress (192.168.0.120), but doesn't if I use the domain name from dyndns.  

If you want to access from outside (i.e. from the internet):

_you have to set up your router to point to your local machine with specific port. (look for the part "virtual server" on your router setup). I guess your router turned it off by default. 

_after setting that part, remember to set DHCP in your router to make your local IP static.

_and also remember to update your internet IP regularly on dydns

):P

---

