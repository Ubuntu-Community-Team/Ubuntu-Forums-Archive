---
title: "Trying to install diablo 2 on latest ubuntu version using wine"
date: 2011-02-02
forum: Wine
---

### Post by jlisec01 on 2011-02-02
Hi, I'm sure you heard this plenty of times before but I really need to talk to someone on installing diablo 2 on wine.  I used ubuntu in the past before but I'm still a beginner at it as well as using wine.  I installed wine for the most part and inserted my disc.  The menu pops up then asks me to insert the next disc but when I insert the disc nothing else happens, the pop up box saying please insert play disc still remains, anyone have any ideals?  Thanks for any help most appreciated.

---

### Post by Largaroth on 2011-02-03
I had the very same problem when I was installing Diablo 2 a few weeks ago, I overcame it my adding drives in my wine configuration.

Start my locating where you disks get mounted when you put them in.
In my case it was in /media/

so what I did was add the following drives to my drives list :

/media/PLAYDISC
/media/Cinematique
...
and so on.

(I have the french version of the game so your cd titles will probably be different, just replace where necessary)

Also, if you have no sound InGame (I had sound in the menus but not InGame) just switch your DirectSound hardware acceleration to Emulated and that might work for you.
keep me posted ;)

Oh and while I'm here, I might aswell post one of my problems ^^.

I have no scrolling InGame, it works fine in the menus, but InGame I can't scroll anything, including my skills, which makes it rather tiresome to play a character that uses more than 4-5 skills in combat.

Any suggestions are welcome of course =)

---

### Post by ronnielsen1 on 2011-02-03
> so what I did was add the following drives to my drives list :

/media/PLAYDISC
/media/Cinematique

I didn't think of that. I manually unmounted and mounted. I like it.

Here's the winehq guide if you get stuck on something:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=74](http://appdb.winehq.org/objectManager.php?sClass=application&iId=74)

---

### Post by jlisec01 on 2011-02-03
thanks for all your help, configuring the drive under wine tab drives really helped, most appreciated.

I'm actually playing diablo 2 right now, its fantastic.  However its kind of laggy, has anyone else experience lag?

---

### Post by Largaroth on 2011-02-07
Sometimes, yes, but some of it is actually due to the blizzard servers.
Any slowing down of the actual game due to wine I have found is quite negligible (and I think my level 77 druid would support me on that =D)

---

