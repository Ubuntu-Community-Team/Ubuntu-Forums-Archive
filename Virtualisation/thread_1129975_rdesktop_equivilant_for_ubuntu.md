---
title: "rdesktop equivilant for ubuntu?"
date: 2009-04-19
forum: Virtualisation
---

### Post by mattmac24 on 2009-04-19
Hey guys, basically what im looking for is a way of doing exactly what rdesktop does but for a linux server instead of windows.

here is my setup/problem:

i have GTKPod running on my ubuntu server. i use it to wireless update my iphone by VNC'ing into my ubuntu comp from my XP lappy and it all works fine. what im looking for is a way to seamlessly integrate gtkpod on my ubuntu box into my XP laptop. also it would be ideal if i could use like a resumable session so i can tell it to update and then close the app on my xp box but gtkpod stays open on my ubuntu box doing what i told it too.

Is this possible? its just abit annoying having to use vnc(well at least as it is currently setup) as it shows the entire gnome instead of just the window i want it too. also it has abit of lag.

Thanks for you help,

Matt:)

---

### Post by bodhi.zazen on 2009-04-19
You can forward single apps with ssh -X

Secure, fast, easy ;)

---

### Post by mattmac24 on 2009-04-20
Hey,

That solution is a huge improvement over my current setup!

the only slightly annoying issue is that when i close GTKPod on my xp laptop GTKPod on my ubuntu computer also closes. for example i tell gtkpod to update my iphone(which takes quite a while) via X11 forwarding on my xp laptop with a whole new set of songs and then turn my laptop off(closing gtkpod on my windows laptop) and the update does not happen. it works fine until i close the program on my xp comp. 

Can i configure my setup so that by closing the session on my xp laptop the session is still running on my server and i can relogin to the session later on? is this possible or should i just settle for what i have now(which as i said is a much better setup then b4 using vnc-apart from the above mentioned issue).


Thanks,

Matt:)

---

