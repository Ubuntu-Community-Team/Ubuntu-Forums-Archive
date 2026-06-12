---
title: "Home Server Suggestions"
date: 2013-09-22
forum: Ubuntu, Linux and OS Chat
---

### Post by arkan01d on 2013-09-22
At work we were throwing away some older laptops: Core 2 Duo 2GHz, 4gb RAM, Gigabit eth0, 160gb SATA, Nvidia 9600M GT, Bluetooth, and Wifi on board. I brought one home and decided to turn it into a Minecraft server for my friends and I to play on. I decided to use CRUX Linux. I was new to Linux and server administration. I learned and studied when I needed to understand or do something. I've always been a hardware guy, but server administration was slowly becoming a hobby. I began having fun tinkering with Linux, however, an active server isn't really the best platform to tinker around on. 

I've got 3 more laptops of the same build now and I'm thinking it may be fun to turn them into servers, but what kind? I don't need NAS I use cloud storage and don't have enough media to warrant setting one up. I was thinking more of a DNS server, DNS cache, Web cache, Router, but I don't know networking enough to make a quality decision. What would you suggest?

---

### Post by mastablasta on 2013-09-23
donate them. they seem like a preety good build.

why were they thrown away?

---

### Post by ssam on 2013-09-23
why not make your own cloud server with owncloud.

---

### Post by arkan01d on 2013-09-24
They're throwing them away because we got newer ones. Nothing really wrong with them. 
The idea of hosting my own cloud sounds fun.

---

### Post by mastablasta on 2013-09-25
> **arkan01d said:**
> They're throwing them away because we got newer ones. Nothing really wrong with them. 
.

ah so consumer oriented society at it's best...

here they would go to lower tier and lower until they are not really useful anymore or until they break down.

---

### Post by arkan01d on 2013-09-25
> **mastablasta said:**
> ah so consumer oriented society at it's best...

here they would go to lower tier and lower until they are not really useful anymore or until they break down.

That's why I'm trying to re-purpose them :D  Some of the laptops they replaced were bad. The one my Minecraft server sits on has a few keys missing, but how often do you use the keyboard on a server? I grabbed the ones that still worked. The rest were sold to recycling. 

However, this isn't helping my OP. If you had 3 PC's and wanted to set up a fun/convoluted home server farm, how would you do it, and what applications do you suggest?

---

### Post by mastablasta on 2013-09-26
notebook usually use less power so they might be good for some bitcoin mining. with 3PC's... i would knwo what to do. if i wanted server route i would probably do one webserver, one storage, one game... i don't know... i mean these are notebooks. they are sometimes not as durable as desktops and are more prone to overheating.

---

### Post by arkan01d on 2013-09-26
Thanks for the suggestions. I had looked into bitcoin mining a while back and it just doesn't seem like it would be worth the trouble. I haven't had any issues, so far, with the one Minecraft server I have going. It's been up and running constantly for 13 months. I keep it in a cabinet with good airflow and elevated. Not to say I have the best solution out there. If I place another server in my cabinet I may install some fans or even place them on laptop coolers. 

I like SSam's idea of a cloud server. These machines have an eSATA plug and I have a few 1TB HDD's just sitting around. Then I may use the other to set up a DNS cache and web cache. Plus I can put a LAMP on the Minecraft server and set up a website. Fun, fun, fun!

---

### Post by tim19 on 2013-09-26
If you can get two network cards on one of them, then I'd use it as a firewall (IP Cop or pfSense). I'd certainly use one as an owncloud server. Lastly, I'd set one up as an SSH server so I could tunnel into the other machines as well as run a LAMP server, since I program in php and use mysql for database management. Personally, having a dedicated DNS server wouldn't do me much good.. also, setting up a quid proxy might be a benefit to you.

---

### Post by sandyd on 2013-09-28
> **arkan01d said:**
> Thanks for the suggestions. I had looked into bitcoin mining a while back and it just doesn't seem like it would be worth the trouble. I haven't had any issues, so far, with the one Minecraft server I have going. It's been up and running constantly for 13 months. I keep it in a cabinet with good airflow and elevated. Not to say I have the best solution out there. If I place another server in my cabinet I may install some fans or even place them on laptop coolers. 

I like SSam's idea of a cloud server. These machines have an eSATA plug and I have a few 1TB HDD's just sitting around. Then I may use the other to set up a DNS cache and web cache. Plus I can put a LAMP on the Minecraft server and set up a website. Fun, fun, fun!

whats the ram
if theirs enough... [https://pve.proxmox.com/wiki/Proxmox_VE_2.0_Cluster](https://pve.proxmox.com/wiki/Proxmox_VE_2.0_Cluster)

---

