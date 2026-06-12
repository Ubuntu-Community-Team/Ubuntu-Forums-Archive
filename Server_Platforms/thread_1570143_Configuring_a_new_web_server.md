---
title: "Configuring a new web server"
date: 2010-09-07
forum: Server Platforms
---

### Post by darms21 on 2010-09-07
Hello all, I very much appreciate your time.
I recently set up an Ubuntu Server on an old comp. I also have recently purchased a Domain Name. I am now wondering how link the two peieces together so that I can serve media from my Ubuntu server through my domain name. Can any1 guide me in detail or point me to a document that can guide me. I understand that there may be easier ways share media like a NAS but I am very much interested @ learning Linux. Thanks in advance. :p

---

### Post by joeaura7 on 2010-09-09
The link between Web server and a domain name is DNS. To run a web server to do everything you will need to install apache2 and bind9. Once you install apache2 you can put files in the folder in /var/www/ and you should be able to see the website at [http://localhost/](http://localhost/). You will have to setup bind9 as a primary zone or root zone. There is documentation how to do this by searching on google. Then you have to make sure your firewall and NAT has the port 80 open to access your website anywhere and use your domain to access it.

---

### Post by jbrown96 on 2010-09-09
joeaura7, he doesn't need bind. He almost certainly has a dynamic IP, so bind won't work.

You will need to pay for DNS hosting with a provider that allows for dynamic updates. The most common provider is dyndns.com. There's a program called ddclient where you just put your user information, and it will update DNS servers for you. Definitely the best way to go.

---

### Post by joeaura7 on 2010-09-09
BIND actually can work with dynamic ip. That is how my website is set up. It depends how your isp dchp servers are configured. If the ip addresses are handed out randomly then you cant really use BIND, however if the dhcp servers is set up to hand out the same ip addresses all of the time then you can. It still might be a risky setup, but it will work. The set up that I mentioned is assuming you want everything in house.

---

### Post by aeiah on 2010-09-10
> **darms21 said:**
> Hello all, I very much appreciate your time.
I recently set up an Ubuntu Server on an old comp. I also have recently purchased a Domain Name. I am now wondering how link the two peieces together so that I can serve media from my Ubuntu server through my domain name. Can any1 guide me in detail or point me to a document that can guide me. I understand that there may be easier ways share media like a NAS but I am very much interested @ learning Linux. Thanks in advance. :p

are you actually wanting to share media over the internet? i just ask because of the NAS think, which is usually local network only. how are you wanting to share it? you may not need a webserver if you really just want to share over FTP/SFTP

---

### Post by darms21 on 2010-09-10
Well I want to share it in 2 manners. I would like to be able to share it over the LAN and also remotely. Would it be possible/more simple to RDP to the server or to run a Web Server to share the media?

---

### Post by aeiah on 2010-09-10
the absolute easiest thing to do for sharing over the internet would be to set up FTP or SFTP rather than a web site.. you just want to be able to transfer files, after all, not present a web site.

for the home, it depends.. if you just want to transfer stuff, again FTP is your best bet, but if you want to stream them it might be worth thinking about what protocols are supported. some things support daap (itunes), some support upnp etc


i dont share with the outside world, but on my network i share things in a number of ways:

- if i want a movie putting on my netbook for a journey away ill use FTP (provided by vsftpd, since its the quickest

- if i want to stream a movie ill use upnp (provided by mediatomb) and play it through xbmc

- if i want to listen to music in exaile ill use daap (provided by firefly

---

### Post by darms21 on 2010-09-10
For your last 2 points what windows side programs do you run to steam/listen to movies/music?

---

