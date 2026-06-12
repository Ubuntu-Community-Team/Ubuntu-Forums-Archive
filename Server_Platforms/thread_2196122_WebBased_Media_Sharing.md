---
title: "WebBased Media Sharing"
date: 2013-12-28
forum: Server Platforms
---

### Post by farazhamza on 2013-12-28
HIz Everybody.. i m new Bee Here. with little Knowledge about Ubuntu and poor English, :p

I need Help from Seniors and Experts, about webbased media sharing.

right know i m running Ubuntu Desktop Server Edition on my Quad core Cpu with 3 Lan Cards, using SAMBA for File Sharing i have more then 400 CPUz in my LAB, so i need 2 IP Series for 2 LAN cards.

1 LAN ip = WAN (Internet)
2 LAN ip = 192.168.0.1
3 LAN ip = 192.168.1.1

using Samba every thing is working Fine. but now i want to also install any free Webbased Media sharing for Videos and Audios,

So is there any Software which can help me in this Case? and how can it will be working for both ip series clients like if a client pc have 192.168.1.122 ip and other have 192.168.0.17 ip.

Cuz i search and each shows me that type localhost or ip of server. and my server have 3 IPS, 2 from lan and 1 from WAN

so guide me which software is best for me for this purpose. i m Using this for only LAN network

your Help realy apriciated for me.

---

### Post by volkswagner on 2013-12-28
You need to find your preferred service such as [Subsonic]("http://www.subsonic.org/pages/index.jsp"), [Ampache]("http://en.wikipedia.org/wiki/Ampache") or [Jinzora]("https://github.com/jinzora") or similar.  

Any of the above should be able to listing on all interfaces or multiple specified interfaces.

There's a fairly [long list of streaming media servers]("http://en.wikipedia.org/wiki/List_of_streaming_media_systems").

---

### Post by rubylaser on 2013-12-28
Another great option is [plexmediaserver]("https://www.plex.tv/downloads").

---

### Post by farazhamza on 2013-12-29
1st Thanks to [ 						 							 						 					]("http://ubuntuforums.org/member.php?u=288711") 				 				 					 						 	[**[COLOR=#000000]volkswagne[/COLOR]**]("http://ubuntuforums.org/member.php?u=288711") and Rubylaser for your quick reply.

2ndly

I have attached 5 Hard drive and created almost 15 Partations. and all partations have differ categories of data like English songs, Hindi Songs, Movies,Etc.

So which software you suguested which can easily handle a lot of data and can bear a hug load of trafic

i want to categories as i created the folder. and want to show each movie with a poster

and New added will display serprately

also is there any possiblity to control trafice with any of these software like ip based bandwidth managment etc?//

---

### Post by farazhamza on 2014-01-02
No reply................... 
Bump

---

### Post by volkswagner on 2014-01-02
I think several suggestions were offered.

It is really up to you to decide which software best suits your needs.

Handling traffic is more dependent on hardware/disk throughput and network bandwidth as compared to which software service you choose.

---

### Post by nerdtron on 2014-01-03
If you want something like a per account file sharing (more like dropbox, but with better photo and video capability) I recommend OwnCloud.
Very easy installation [https://www.digitalocean.com/community/articles/how-to-install-owncloud-and-configure-owncloud-apps-on-an-ubuntu-12-04-vps](https://www.digitalocean.com/community/articles/how-to-install-owncloud-and-configure-owncloud-apps-on-an-ubuntu-12-04-vps)

---

### Post by CharlesA on 2014-01-03
> **nerdtron said:**
> If you want something like a per account file sharing (more like dropbox, but with better photo and video capability) I recommend OwnCloud.
Very easy installation [https://www.digitalocean.com/community/articles/how-to-install-owncloud-and-configure-owncloud-apps-on-an-ubuntu-12-04-vps](https://www.digitalocean.com/community/articles/how-to-install-owncloud-and-configure-owncloud-apps-on-an-ubuntu-12-04-vps)

+1. I use it on my VPS, so handy.

---

