---
title: "Ubuntu server running on VMware makes malfunctioning my broadband modem"
date: 2016-04-30
forum: Virtualisation
---

### Post by Manikandan_Ramar on 2016-04-30
After installing **Ubuntu Server on VMware** in my PC, every time when i power on the Ubuntu server, my broadband modem malfunctions and browser will redirect any searches or sites to _*Asianet(ISP) security risk page *_ :( Do I need to configure network in Ubuntu server? or it has any other solutions?

---

### Post by DuckHook on 2016-04-30
As per forum etiquette, please don't post with anything other than the standard font. Strange fonts make for difficult reading.

*Your thread has also been moved to **Virtualisation** as the forum more suited to your issue.*

---

### Post by MAFoElffen on 2016-05-01
VMware is the company... which of their products are you suing? (Player, Fusion, Workstation Pro, VSphere/ESXi...)

On your Guest VM... In the Virtual Manager window, check preferences (general for all) > netwroks > check which virtual switched are confgiured. Probably NAT and Internal.

Highlight your Ubuntu server VM > Settings > Network Card > ... and tells us what you have selected for a switch.

Then start up your VM and post the results of 
```

ifconfig -a
cat /etc/network/interfaces

```
Please post all commands and output witiin code tags.

---

### Post by MAFoElffen on 2016-05-04
It looked like you tried to post images, but I see nothing but the "mssing" graphic icon that happens with an incorrect url is given... Could you edit that last post and try again please/

2 urls you gave were for those png images where the same url, but not accessible. Even if I load that url in a browser. Not a 404 error, so may be that the url is not common public access (not a shared file permission).

---

### Post by Manikandan_Ramar on 2016-05-04
Image 1: [https://app.box.com/s/uczunoq1pkx9krtp3c5wg1a16ji5vq8z](https://app.box.com/s/uczunoq1pkx9krtp3c5wg1a16ji5vq8z)

Image 2: [https://app.box.com/s/5lpdgogubbw1kriqcofwgbjpj7ljd0q8](https://app.box.com/s/5lpdgogubbw1kriqcofwgbjpj7ljd0q8)

---

### Post by MAFoElffen on 2016-05-04
Set to NAT and it would work for you as soon as you made that change. To use "bridge", as a setting, you would first have to create a virtual switch / bridge on your host... I don't see in your output where that is in place yet.

To configure a bridge on your host server, refer to the Ubuntu Server guide. Requires installing at least 2 network cards (1 for the bridge), installing bridge-utils, and configuring the bridge on your host... If you have questions on how to do that... just ask.

---

### Post by Manikandan_Ramar on 2016-05-06
Thanks a lot.
I had only connected my modem before. After I have connected my new the wifi router, everything works fine. I do not know actually what's the problem with modem only.

---

