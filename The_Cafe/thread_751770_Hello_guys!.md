---
title: "Hello guys!"
date: 2008-04-10
forum: The Cafe
---

### Post by ReZon4ce on 2008-04-10
Hello, im an ABSOLUTE COMPLETE newby to linux, and i decided to go for "ubuntu" because of the really nice compliz and beryl or whatever they are called, anyway, I finally  installed ubuntu after 1 whole day :P Then i managed to follow a tutorial on how to get compliz, which i did, worked fine but then i realized i got one that was like 2 years old..... SO, I do a serch on this forum for compliz and found the new one, but tried to get rid of the old one and failed.. im now back and stuck on no effects mode so im going to to a clean install tomorrow, hopefully the last hey! :lolflag:

But i was just wondering if someone could show me how to install the latest compliz and XGL or something, i have no idea how :P Help would be soooo appreciated! Thanks! And great forum! :) 

PS: Sorry if my spelling is off, but its 2:00 am and im  bloody tired! x)

---

### Post by NightwishFan on 2008-04-10
Welcome to Ubuntu Forums! :KS:popcorn::KS

If you are installing Ubuntu 7.10 the latest stable you have Compiz-Fusion by default. (compiz+beryl merged)

If your card is supported or has the restricted drivers installed run this command.
```
sudo apt-get install compizconfig-settings-manager
```
Under the preferences menu and appearance set effects to normal or extra. If that is successful open the advanced desktop settings above it and  configure as you will.

---

### Post by ReZon4ce on 2008-04-10
thats what i did first, but it does not have beryl and some features i see on youtube videos and such, plus i deleted the default files by accident :S

---

### Post by NightwishFan on 2008-04-10
=O

What features does it lack? It is the latest version of both of those projects. Install it with synaptic.
```
sudo apt-get install compiz
```
Should handle it. Then do:
```
compiz --replace
```

---

### Post by Saint Angeles on 2008-04-10
read up on package managers such as synaptic.

its a totally different way of dealing with programs than windows.

and doing a "sudo apt-get update" then "sudo apt-get dist-upgrade" will update all your software to the newest versions available in the repositories.

---

### Post by retrow on 2008-04-10
Follow the upgrade steps that Saint Angeles has mentioned above. if you see a flashing thing telling you there are restricted drivers available, go ahead and get them first - its automatic so you don't have to do anything except provide the password. If your graphic card drivers are not present, compiz won't let you enable the effects that you are looking for.

---

