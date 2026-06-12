---
title: "Adjusting my laptop to play Worldofwarcraft"
date: 2010-07-19
forum: Wine
---

### Post by den1988 on 2010-07-19
Dear Forum!
I am using Fujitsu-Siemens LIFEBOOK a530.
I am new to Linux and installed my Ubuntu 10.4 a week ago.
While trying the Ubuntu various applications I came across the Wine1.2 feature.so I tried it:)
Installing WOW went good and I can really play.
But I see that there are some graphic adjustments that should be made in order to improve the quality of gaming.
There is some kind of delay:I press the button and get the desired action after some moments.
Any ideas for what should I do?what packages to install?
Sincerely yours,
Den

---

### Post by apostra on 2010-07-19
Hello Den,

Could you share some more info please? That you're saying might be just lag, or maybe your card cant handle it that good.

However try this first:

1)Have you enable the graphic card drivers? System->admin->Hardware Drivers.

2)Also go to wow dir, find the WTF folder. Inside there is a config.wtf file. open it and add the line  -> SET gxApi "opengl" <- save and close it. 

3)Lower your Visual effects on your pc. try with none to see how it runs.

Of course i assume you have wine and ubuntu fully updated.If not do it.

Have fun mate.


P.S. I dont know if it makes sense or not, but while ago i saw some1 on forums suggested, before we run anything on wine, first open the wineconfig, to create the folders and settings. Have no idea if its right or not, but its something i always do and have no probs with wine and wow.

---

### Post by den1988 on 2010-07-20
Dear Apostra!
I will be more specific...
I tried to play wow with a Wirless network(97%).
As the game loaded I found myself in Dalaran on Sunday evening(Full on players lol).Graphic looked good and I was moving smoothly in the terrain.
But found a problem clicking on icons because of some kind of delay.
My problem is that my Leptop supported by Intel Graphic..somewhat "unfriendly" for Ubuntu.
I have done what you advice and:
1)I found out that i have no graphical card drivers installed!
2) What's the idea with  SET gxApi "opengl" command?
3)lowering visual effects done.
Could you be more specific about how to configure wineconfig for wow?...what should I do?
If you know, I mean..
Thanks in advance!
Den.

---

### Post by asdfoo on 2010-07-22
The Fujitsu-Siemens LIFEBOOK a530 appears to have an integrated Intel video card.   These are not known for their performance under Linux.

You may need to look into using ubuntu edgers as it has more up to date drivers for intel.  ymmv though.

---

### Post by apostra on 2010-07-22
Hey den,

sorry for my late reply. Just saw your post.

I've got nvidia graphic card personally, so I'm not that experienced with intel. However, i try to help as much as i can.

If you noticed at winwconfig, at application tab, there is a windows version option. As i look around at forums, for some games or application, frequently they suggest to try with different windows version, xp, vista win7 etc. So since it doesnt take long to check it, personally i always try between xp, vista, win7, to see if a prog runs, or run better with one of them. Again, is something i'm doing just for the chances. Also there are some issues with audio drivers and audio cards for  audio performance, which am affraid i cant help here, i always play with no game music, my personal playlist is always loaded and loud, hehe. My settings there are the default always. I never changed the audio option and i have pulseaudio drivers on.

the opengl are drivers, on nvidia cards i can confirm opengl runs smoothly, i could say i got much better performance than i had on my windows. 

For the problems you described, sometime i got the same problem with objects for the first seconds i log on, thats mostly server lag. Also for icons and objects, there is an known issue. Do you have broken icons at action bars, spellbook etc?

Once again all these happens to me with nvidia driver experience and some steps i always do while installing wow. I hope, one more experience guy, good thing there are many here, could help you more with intel cards.

---

### Post by den1988 on 2010-07-24
Dear Apostra!
I appreciate your help and care.
I will undergo all things you advised and try it out.
Doing it yourself is the best experience,hea?
Already trying to play with wineconfig applications,
it feels about the same in wow.
I also will try the OpenGL and ask in forum about Intel Graphical drivers.
I visited the Intel download center and found out that they have drivers for many Linux based OS's like Red Cap,SUSE,Mint..etc.
But not for Ubuntu,Strange:)
Also I read that Blizzard had attempted to release
Linux based wow but closed the project sometime before TBC was released,sad.

About your last questions,
No,I don't have a broken icons or any not working icons.For now,there is nothing wrong in the game experience except the "delay".
Didn't start raiding yet in Ubuntu and I hope it won't ruin raid.
Sincerely yours,
Den.

BTW:
Asdfoo,I will really appreciate if you could get me a hint about where to post questions about Graphics in forum due to my lack of knowledge of forum.:)

---

