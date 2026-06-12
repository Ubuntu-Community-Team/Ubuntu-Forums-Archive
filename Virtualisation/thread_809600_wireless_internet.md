---
title: "wireless internet"
date: 2008-05-27
forum: Virtualisation
---

### Post by roflatlife on 2008-05-27
hi everyone
im using ubuntu hardy heron and i installed windows xp on virtualbox
does anyone know how i can get wireless internet on the windows xp? it says something like install ethernet controller and i know nothing about networking
thanks to anyone who can help me 
sorry for being a noob lol

---

### Post by Glucklich on 2008-05-28
It has nothing to do with the XP. What VirtualBox does is create a connection between Ubuntu and XP. The only thing you have to do is on the XP installation say that the PC connects directly to the internet, then check on the VirtualBox configurations for the XP, on the network part if you have the "Network Board" turned on. It should show something like "Adapter Type: PCnet-FAST III (Am79C973) Connected to: NAT" and check the "cable on" option.
One more thing, if you don't have the advanced options installed yet. Install them, and everything should work OK. Sorry if some of the things are not accurate but I'm using the Portuguese version and my translation may suck. :P

---

