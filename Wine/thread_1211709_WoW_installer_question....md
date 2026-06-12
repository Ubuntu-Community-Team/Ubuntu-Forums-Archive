---
title: "WoW installer question..."
date: 2009-07-12
forum: Wine
---

### Post by Darkoblivion2 on 2009-07-12
Ok so, i have wine, and i was able to dl the wow installer, and im pretty sure it downloaded the files, but when i go to install, and i get to the first EULA, and it says u must scroll to the end of page to hit "agree", i do that, but my agree button isnt highlight, only disagree...

anyone have a clue?

---

### Post by brinamaree on 2009-07-12
Wow... sorry dont know an answer to your question but curious how you got it to run on yours? I have Ubuntu 8.10 and put the cd in the drive with no luck, not sure if it has anything to do with being the burning crusade cd but yea it doesnt even dl :(

---

### Post by Darkoblivion2 on 2009-07-12
i just downloaded the client thingy from blizz's website...

maybe i should try to dl it again

---

### Post by josephpiche on 2009-07-13
What versions of wine and Ubuntu do you have?

---

### Post by Darkoblivion2 on 2009-07-13
grrr... i still cant hit agree... anyone help me?

please?

---

### Post by Darkoblivion2 on 2009-07-13
> **josephpiche said:**
> What versions of wine and Ubuntu do you have?

wine: 1.0.1
and 9.04 ubuntu

---

### Post by josephpiche on 2009-07-13
I would try the latest version of wine 1.1.25. You can get the Ubuntu repository for it on winehq.org.

---

### Post by Darkoblivion2 on 2009-07-13
<-ubuntu noob here...

what do u mean by repository... can i just run a terminal command to update wine?

---

### Post by Freezing on 2009-07-13
try to locate the folder and just run the wow.exe file for wine.
there are some twinks on winehq.com how to make it run smoth etc.
btw to update to the latest version of wine its prety simple just remove it .
once you remove it go to you home folder and you will see an folder called .wine if you can see it do ctrl + H (which will allow you to the hidden files and folders) well delete that. and than just do the latest version download and install from winehq.com its very simple. (i just installed ubuntu 4-5 days ago never used it before, just takes some reading an patiece) :P

---

### Post by ChaiTan on 2009-07-14
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by omightyzero on 2009-08-08
having the same problem with hitting the agree button, i have installed wow before but recently got the newest version of ubuntu.

---

### Post by omightyzero on 2009-08-08
got it to work type

    sudo aptitude update
    
sudo aptitude install wine

it should prompt you to install mozilla (gecko) when you go on the installer
after that the agree sign should work. worked for me

---

