---
title: "Linux-Server, Newbie, no boot"
date: 2010-11-03
forum: Server Platforms
---

### Post by KennyDr on 2010-11-03
Heyhey, following Problem:  i startet my first Linux installation! yay Its Ubuntu-Server on an old computer.  Everything went well, i got my first impressions of a Linux-server. (Samba,SSh, nano..) Basic Stuff.  I thought, hey its a server primary connected through SSH and doesnt need a Monitr, Keyboard and stuff. So i pulled out eversthing that i thought, wouldnt be needed. Graphik-Card, unused IDE cables. I started it again and it doesnt work... ****. i put the stuff right back into it, and it still doesnt work...  An Error Message is displayed: grub rescue: Symbol not found: grub_crypto_hmac_init  the symbol changes from reboot to reboot.   What can i do? if I boot Linux Server-CD and press on repair broken System it results into a 2minute blackscreen (i shut it down after 2min because nothing happens(no LED-action))  Some hints? :(  Greets

---

### Post by Peter09 on 2010-11-03
Well of the top of my head the first thing to check is that you have put all the hardware back in correctly. I remember spending a few hours trying to find why a system would not boot - a poorly seated graphics card.

---

### Post by wojox on 2010-11-03
I would take out everything you don't want and reinstall. Linux scans all your hardware and keeps a list. It probably doesn't like the fact it can no longer find half of it. :)

---

### Post by Nerflander on 2010-11-03
What you could do is remove all hardware what you dont like or want or need etc. Then install the server and configure. This way you dont get errors. furthermore you can place new hardware in when needed and just let ubuntu reconize it instead of missing it!


ow well just sugestion :)

---

### Post by arnavk007 on 2010-11-03
i second nerflander
linux tries to configure all devices at boot
so start with the least and add on rather than strip down

---

### Post by KennyDr on 2010-11-03
well i forgot to mention that if i press on "INstall Ubuntu" on the boot-CD, the same thing happens as if i would press repair broken system... just nothing except of black screen :(  i will pull the Graphiccard out and back in, as soon i get my hands on that thing again.  Maybe there is a lil piece of dust on the contact .. i dont know :/

---

