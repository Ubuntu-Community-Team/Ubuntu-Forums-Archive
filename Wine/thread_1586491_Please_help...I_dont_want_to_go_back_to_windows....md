---
title: "Please help...I dont want to go back to windows..."
date: 2010-10-02
forum: Wine
---

### Post by mrchaos101 on 2010-10-02
I have been on this issue for 2 days. I am trying to learn Ubuntu as I go.

I have managed to get VIDEO to work in my browsers and I had sound at one point.

I got Wine installed and working and even manage to get World of Craft up and running very smoothly.  

Some where in my Wine install/config'n and setup etc...and getting WoW to work..I killed the sound.  No matter what I do I can't get the sound to work in my browser....or in game.

It is an Sound Blaster X-fi Fatality sound card.  
Please help.

:confused:

---

### Post by akoskm on 2010-10-02
You killed the sound generally, and there is no playback from any sources (rythmbox, movie player) or just with wine?
Also, is this happening only when you have already started a program with wine? Do you have sound immediately after booting?
What is the selected sound system in wine configuration?
Did you remove any package from the default installation?

---

### Post by Jehdin on 2010-10-06
I don't know if this will help but I had the same issue with the sound. To get it working in  game I had to go into the sound options and change the sound option for high quality to medium, then change it back. It seems to do it whenever I minimize or change screens. It doesnt happen all the time, just once in awhile. Not a big deal...just more of a annoyance.

---

### Post by akoskm on 2010-10-07
In the case if you start them simultaneously, the first program which "grabs" your sound card will block the other. That's a common problem if your are running the same sound system on GNOME and Wine.
I have absolutely no sound in World of Warcraft - I switched off - but, in the case if I wanted to get some sound I would try first to start it through aoss wrapper script, like:
```

aoss wine Wow.exe

```.
If you tested the sound *separately* and still won't work then the problem is somewhere else.

---

