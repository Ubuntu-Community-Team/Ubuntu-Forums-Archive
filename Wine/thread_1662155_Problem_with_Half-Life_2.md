---
title: "Problem with Half-Life 2"
date: 2011-01-07
forum: Wine
---

### Post by Cant on 2011-01-07
I installed this game three days ago, played it and beat it without any kind of technical problem. Now, all of the sudden, starting it up is hit and miss at best. It either gets stuck at the loading screen or starts up normally. Then, on top of that, the sound has a tendency to cut off and not coming back on until I restart my computer(wtf)!

Error:
```
err:seh:setup_exception_record stack overflow 1888 bytes in thread 0021 eip 7bc3dc8e esp 00240bd0 stack 0x240000-0x241000-0x340000
```

---

### Post by Hippytaff on 2011-01-07
games in wine can be a bit hit and miss...I haven't tried it myself, but playonlinux (a wine derivative tweaked for games as far as I know) might be more successful - [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by Cant on 2011-01-07
> **Hippytaff said:**
> games in wine can be a bit hit and miss...I haven't tried it myself, but playonlinux (a wine derivative tweaked for games as far as I know) might be more successful - [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

But it worked perfectly before :(

---

### Post by Hippytaff on 2011-01-07
Computers have a way of messing about with our minds...maybe try uninstalling an reinstalling it

---

### Post by Cant on 2011-01-07
I reinstalled it and I can start it up normally again but the sound still cuts out.

---

### Post by Hippytaff on 2011-01-10
Do you have sound probelms with any other software or just Half-life?

---

### Post by Cant on 2011-01-10
> **Hippytaff said:**
> Do you have sound probelms with any other software or just Half-life?

This happens with Garrys Mod, too, which uses the same engine.

---

### Post by Cant on 2011-01-10
> **Hippytaff said:**
> Do you have sound probelms with any other software or just Half-life?

This happens with Garrys Mod, too, which uses the same engine.

---

### Post by Hippytaff on 2011-01-10
This might be a problem with this engine then. Might be worth googling for a fix or see if the wine site has a bug report for it.

---

### Post by M1ttenz11 on 2011-06-28
Hello, im very new to linux, but however i do believe im picking it up quite fast,  ive just in stalled my steam account and went to try and play HL2 after I downloaded it. (I installed all my steam games from disc) using wine auto run. however when i started up HL2, just after the Valve screen, (Guy with tap in back of head) just as it loading to menu for play or load game etc, it cuts off, (lag free) and doesnt explain a problem, so i just think its closing for no reason, I then went to try CSS and that did pretty much the same thing, just after the loading bar (preparing to play CSS) gets to the end, it cuts off, once again, with out any lag, or explaining  a problem, i've un-installed and re-installed, same situation...
So now im trying to install it again with playonlinux. (still installed with wine too).
However the reason for making this post is I still get the feeling that when I wake up and its all downloaded, im still going to have the same problem,(un-explained closing of the game) im just curious if anyone has any ideas, or knows the solution to my problem, it would be greatly appreciated.
I will post a again when I wake up which is after playonlinux has installed.

Thank you. M1ttenz11

---

### Post by brian70809 on 2011-06-28
There are a few things you need to do..

Make sure you have the latest version of wine.. 

Go to wineHQ and check..

Second part, go to WineHQ and look up your game and see if there are any must have .dll files to make that game run..  

Did you use winetricks and install the d3d drivers? etc.etc..

Very little in Linux is plug-n-play...  Ubuntu is trying to fix this problem.

---

### Post by M1ttenz11 on 2011-06-28
Had to edit this, did not notice replies. Im getting right on that and double checking over everything, I did have the latest version of wine, but Im'a give it a go, and get back to you.
Thanks.

---

### Post by M1ttenz11 on 2011-06-29
Alright, I uninstalled everything, and re-installed it starting from the older models of counter strike :). I got the new version of wine [version 1.3.21] and it worked straight away to be honest and i wasnt expecting it..
I did have all the correct drivers first time round, but I didnt have winetricks [thanks for the tip :b] and I had to get the new wine version maybe? But also I couldnt find any NEEDED tool/app to run the game.
So im just installing Halflife 2, Counterstrike Source to see if the same open and close problem happens..
fingers crossed it doesn't... but I'll get back to you's either way..

---

### Post by M1ttenz11 on 2011-06-29
Alright, just tried halflife 2. Works, loads and offers me to  play a game, so i believe it will run probably run without a problem [could be very wrong.]
however, Counterstrike source is just preparing to launch and does not, I have to go out right now, but when i get back i will edit this with some screen shots. :) thanks. I feel like we gettnig there now!

Right, ya, just like i thought, HL2 runs fine. Except minimize,and the maximize again is weird.. but never mind, not a real issue. odd small amount of lag but i think i can fix that myself, dont think its a real issue.
However, CSS on the other hand, still wont load up... at all..
strange eh? :o thanks.

---

### Post by brian70809 on 2011-06-29
Counter Strike has a lot of issues it looks like..

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

There are sound driver issues, etc.. go down and read up on it.. This database is awesome for fixing wine problems.

Good luck!

---

### Post by M1ttenz11 on 2011-06-29
Yes, it does seem that way doesn't it?
However, I will work my way around this and post the solution.
Thank you for the link, I'll go through it right now :p
(Y)
[5/5 for your support :b]

---

