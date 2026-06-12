---
title: "Problems with Radeon HD 4890 on VB on Win XP"
date: 2011-05-31
forum: Virtualisation
---

### Post by Extol11 on 2011-05-31
First of all I'm new to anything regarding virtualization. I thought I'd use virtual box to run windows xp inside Ubuntu so when I wanted to play some games I wouldn't have to switch to Windows. So installed Virtual Box on my Ubuntu 10.04 installation and configured it this way. 
1 cpu
2GB of ram
128MB ram for video ( I don't like this)
Fixed VHD of 64GBs.
The installation went smooth and the system is updated and all with Service Pack 3, antivirus and firefox. But when I tried to install the graphics card driver it didn't install. It said something about a package not wanting to install. I haven't tried it again because I don't want to mess anything up. Now the thing is this... should I installe the windows drivers of the real card or does VB treats it as something generic? It's a Radeon HD 4890 with 1GB of ram. The whole intention of the windows installation is just to play videogames on it. This is my computer's specs.:
Core i7 (920)
8Gbs of Ram
Asus p6X58D Premium motherboard.
250GB of total HD space. 

Also, will the ram asignated to video for the virtualmachine make it not be able to run games or is that like general ram (from the main 8GB) but just asignated to video? Any help will be greatly appreciated. Thanks.

---

### Post by Joe of loath on 2011-05-31
You need to install the virtualbox guest additions, the guest doesn't have direct access to the video card.

Also, don't expect to play any games in virtualbox, the graphics subsystem is shocking.

---

### Post by Extol11 on 2011-06-01
Really, playing games is the only reason I'm trying this out. I want to play Aion and Rift without having to install them on Windows. Aion likes to mess with Direct X and creates other bothersome problems. Rift I'd just like to have on Linux. Is there a way that I can play these games on linux without wine? Rift plays fine I hear, though. And thanks for your time.

---

