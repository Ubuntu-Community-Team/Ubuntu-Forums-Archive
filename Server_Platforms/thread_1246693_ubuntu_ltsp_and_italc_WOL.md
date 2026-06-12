---
title: "ubuntu ltsp and italc WOL"
date: 2009-08-22
forum: Server Platforms
---

### Post by noorez on 2009-08-22
I'm currently experimenting with the latest Ubuntu ltsp server on virtual box 2.2 but I'm having a bit of trouble with a couple of things. I have set things up so that

- my wireless card will receive internet and my wired card will serve as the 'server' connection. 
- My wireless router has been set as the default gateway to allow for the internet to work. 
- Within the virtual box Ubuntu ltsp installation, I set the wireless card as the primary one during the installation process.

The thin clients connected to the switch (to the wired port) are able to boot with the network and login correctly.

However, the 'wakeonlan' program will not work unless I have specify the -i switch. This wouldn't be a problem but I am also experimenting with the iTalc tool and I cannot power-on computers with it. I think this has to do with the default gateway being set to the wireless router to which the thin clients are not connected. Is there a way to fix this?

---

