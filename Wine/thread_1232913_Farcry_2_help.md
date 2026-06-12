---
title: "Farcry 2 help?"
date: 2009-08-06
forum: Wine
---

### Post by landy rover on 2009-08-06
hello everyone 

:)
I was just wondering if somebody can help me with farcry2????
I went to add/remove programs and installed wine through when i click on the farcry 2.exe file to play it says starting farcry 2 and then it just hangs and does not enter the game...
I have
2400xt hd Ati graphics card 256mb gddr3 
3.2 ghz intel proseccer
1.5 gig ram 

I have installed it on my windows xp then it reboots my pc
and i tried vista ultimate and it runs but i want to go to ubuntu permanently

---

### Post by Askar450 on 2009-08-06
I tried installing last time but I forgot all about it when I installed 9.04 but anyways it says here you'll need to copy d3dx9_36.dll in to your system32 folder and set ORM=pbuffer plus adding a key in to regedit.

---

### Post by landy rover on 2009-08-06
thank you i will give it a try

---

### Post by BoneSmash on 2009-08-06
> **landy rover said:**
> 
I went to add/remove programs and installed wine

If you installed Wine this way that means you have Wine 1.0.1, which is a very old version (over a year old now I believe).  Try adding the Wine repositories to your system so that you always have the latest version.  I don't know if Farcry 2 will work with the new version, but it is way more likely that it will.

---

### Post by landy rover on 2009-08-06
hello again 

i have copied d3dx9_36.dll into the system 32 folder and now when i enter farcry 2 it says video card drivers are too old please update them then i press ok it opens and just shows a black screen

---

### Post by Askar450 on 2009-08-06
Are you running the latest drivers? What kind of GPU/IGP do you have? Bone is right did you install wine throught Add/Remove or from the site? If you did you need to delete that one and install the latest one or something between 1.1.20-26, I recommend 25 there's apparently something wrong with 26 that doesn't allow you to downgrade. Don't use Add/Remove to uninstall wine go in to your terminal and type "sudo apt-get remove wine" then go to WineHQ > Download > Ubuntu > then " [the WineHQ .deb packages archive]("http://wine.budgetdedicated.com/archive/index.html")." once you do that try it out.

---

### Post by landy rover on 2009-08-14
Hi everyone 
 
I installed wine from the website about three weeks ago...
no luck but thank you everyone who tried to help me i am currently dual booting vista and ubuntu 8.10 intrepid ibex but works on vista perfectly :):)
 
im currently using ubuntu for surfing and just fooling around

---

