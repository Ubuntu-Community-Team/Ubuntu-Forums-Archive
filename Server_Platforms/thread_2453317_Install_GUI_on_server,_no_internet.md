---
title: "Install GUI on server, no internet"
date: 2020-11-07
forum: Server Platforms
---

### Post by hezy2 on 2020-11-07
Hi,
I've just installed Ubuntu server 20.04.1 on SSD but I can't connect to the internet. Is there a way to install GUI from CD/DVD (I have Ubuntu desktop 18.04 on DVD)? Thank you so much,
Hezy

---

### Post by CelticWarrior on 2020-11-07
Installing a desktop won't solve your network issues. Learning how to set up networking in a headless server might.
OTOH, if you want a desktop then install a desktop edition from the start.

---

### Post by hezy2 on 2020-11-09
Not interested in desktop and the network conf. is fine!

---

### Post by mastablasta on 2020-11-09
not from Ubutnu desktop 18.04.

there is a way to install it offline (for example keryx: [https://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline](https://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline)), but the easiest would be to get DVD, USB or Image file of 20.04 desktop and install that.

if you have a way of providing internet connection to the server then you just install ubuntu-desktop (or any other desktop or windows manager of your choice) package on it.

---

### Post by ActionParsnip on 2020-11-09
Are you using a wired or wireless connection?
Can you ping your default gateway (router's internal IP)? 
Can you ping 8.8.8.8?
If you ping BBC.CO.UK do you get an IP back? 
Does BBC.CO.UK ping OK? 
Do you use a proxy for Web access?

---

### Post by CelticWarrior on 2020-11-09
> **mastablasta said:**
> 

if you have a way of providing internet connection to the server then you just install ubuntu-desktop (or any other desktop or windows manager of your choice) package on it.

I strongly suspect the OP doesn't have internet connection, is convinced that the configuration is fine (it isn't) and thinks that by installing some desktop that will enable them to use the GUI tools. We all know how that will end up...

---

### Post by hezy2 on 2020-11-09
I configured the network during the installation but I wasn't applied to connect to my wifi network afterward, also no way to connect through the cli

---

### Post by CelticWarrior on 2020-11-09
> **hezy2 said:**
> also no way to connect through the cli

Yes, way, actually ways...
[https://askubuntu.com/questions/1249160/connecting-to-personal-wifi-on-ubuntu-server-20-04](https://askubuntu.com/questions/1249160/connecting-to-personal-wifi-on-ubuntu-server-20-04)
[https://linuxconfig.org/ubuntu-20-04-connect-to-wifi-from-command-line](https://linuxconfig.org/ubuntu-20-04-connect-to-wifi-from-command-line)

This is to get you started. There are official documents about it that I suggest reading.

---

### Post by slickymaster on 2020-11-09
*Thread moved to **Server Platforms**.*

---

### Post by hezy2 on 2020-11-09
Thank you

---

