---
title: "cannot find capture support for my camcorder."
date: 2009-08-24
forum: Ubuntu Studio
---

### Post by FreezWay on 2009-08-24
I have a Sony DCR-TRV310 and cannot find any program that can capture from it. kdenlive, kino, lives, and many others all failed. Can anyone help me here?

---

### Post by bumanie on 2009-08-24
I have a bit of an idea about kino, but it will only capture via firewire. Do you have a firewire port on your computer and a firewire cable for the dv camera? It's a while since I setup kino. I know it works with a sony dv camera as i have one. I managed to capture and burn home movies to dvd via the firewire port.

---

### Post by FreezWay on 2009-08-24
yeah i have firewire... i think its hdv, not sure tho... also, how can i test my firewire? make sure its not a hardware issue?

---

### Post by bumanie on 2009-08-25
To use kino, (from my not so perfect memory) one has to enable dvgrab and 1394 raw. I also found to use kino, one needed to start it with root - not sure if that is technically the correct way to do it, but it is the only way I could get it to work. I am going to try setting up kino again myself. If I manage to get it going, I'll post back with further instructions. There are a few tutorials on the internet that are helpful.

---

### Post by bumanie on 2009-08-25
A quick update. 
A) I don't know whether kino  supports hd or not.
B) To get kino going > sudo apt-get install kino > sudo apt-get install dvgrab> sudo apt-get install libraw1394-8> sudo apt-get install libraw1394-dev
C) Start kino in terminal > sudo kino
D) Plug in firewire cable in to camera (assuming it is already connected to the computer), click on capture and you should be able to capture the video and operate the camera (rewind; Fast forward etc) from the kino GUI.
I tested the above and it works fine on my computer. Hope this works for you.

---

### Post by FreezWay on 2009-08-25
cool, that works, but only as root....

---

### Post by peepingtom on 2009-08-26
System -> Administration -> Users and groups. Unlock. User Properties. Make sure your user is allowed to capture video and use 3d Acceleration, perhaps also access external storage but I don't have a DV cam and this is only an idea :D

---

### Post by bumanie on 2009-08-26
Freezeway: Glad it works. Yes I too have found I can only use kino as root - I did mention that in my second post - I have not found a way around that as yet. I doubt it should be that way.

---

### Post by FreezWay on 2009-08-26
@peepingtom: didn't work =(, whatever, i can get it to work as root.

---

