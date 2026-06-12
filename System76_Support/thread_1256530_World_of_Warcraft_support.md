---
title: "World of Warcraft support"
date: 2009-09-02
forum: System76 Support
---

### Post by jtimbr7546 on 2009-09-02
I am interested in purchasing the Gazelle Ultra Laptop and Leopard Extreme desktop, however I'm concerned because I'm an avid World of Warcraft player and have not had much luck with getting WoW to run decently under Linux. I know it can be done - Ive read the forums, but my assumption is that the Dell xps 400 (with ati 4600HD video card) just "doesnt play nice" with Linux for whatever reason. So brought me to check out System76. They seem friendly enough and the prices are great. Can anyone help me determine if WoW would run nicely on any of the machines listed? 
[LIST]
[*]Gazelle Ultra [Laptop]
[*]Leopard Extreme [Desktop]
[/LIST]Thank you for any assistance yall can offer. Im not a total linux newb - I just need assurance that i'll have a windows like (or better than :) ) experience. I use Ubuntu NBR on my netbook [dell mini 9] and its awesome. I want to replicate this experience to the desktop!

---

### Post by echo314 on 2009-09-02
Please let me know of your general experience with the Leopard if you receive one. I've been waiting to get one, but first I want to hear from other users about what they thought.

---

### Post by jtimbr7546 on 2009-09-02
Yea I will probably get one either way - but I really want to hear accounts from any WoW players here that bought a system from these guys. I havent had much luck with getting wow to "play nice".

---

### Post by falconindy on 2009-09-02
ATI, Intel, and integrated graphics don't get along well with Wine/WoW. Stick to nVidia and you'll be fine. I used to play WoW with a BFG 8600GT, 2gb of RAM and a 3.06ghz Core2Duo. By the time I finished fiddling around with settings and whatnot, it ran better under Linux than it ever did on Windows -- shorter load times, higher FPS, and lower ping.

---

### Post by echo314 on 2009-09-03
With 6GB of the Leopards blazing fast RAM you could run Windows virtually on top of Ubuntu, install any windows drivers the hardware may want and I bet it would run fine then. I'm also sure it will work fine out of the box though.

---

### Post by jtimbr7546 on 2009-09-03
Thanks guys for your help. I have a full retail copy of Vista Ultimate that I can virtualize in a pinch - 6GB should be more than enough :)

---

### Post by reaper308 on 2009-09-03
I have no proplem running wow on my pangolin w/ nvidia card, Best way is to just copy your wow directory from you windows box to your system 76 machine then run wine.its to easy

---

### Post by falconindy on 2009-09-05
> **reaper308 said:**
> I have no proplem running wow on my pangolin w/ nvidia card, Best way is to just copy your wow directory from you windows box to your system 76 machine then run wine.its to easy
You'll need to make sure that you add the flag -opengl to the execution. You'll crash in a hurry trying to use Direct3D as your renderer.

---

