---
title: "Start App in Winedbg"
date: 2010-11-22
forum: Wine
---

### Post by doctorzeus on 2010-11-22
I'm trying to get Rainbow 6 Vegas 2 working on wine and apparently it kinda works if you start it through winedbg:

[http://wine.1045685.n5.nabble.com/Bug-12652-New-Rainbow-six-Vegas-2-Fails-to-launch-with-General-Protection-fault-td1469041.html](http://wine.1045685.n5.nabble.com/Bug-12652-New-Rainbow-six-Vegas-2-Fails-to-launch-with-General-Protection-fault-td1469041.html)

(Check third from the bottom post)

I'm a bit of a noob with wine debugging and a bit confused :confused:

Can anyone tell me how to launch the game from winedbg as described in the post on the link pls?

I tried:
```
strace wine /home/dan/.wine/drive_c/Program\ Files/vegas2/Binaries/R6Vegas2_Game.exe
```

It runs but as described it's REAAAAAAALLLLLLYYYYYY SLLLLLOOOOOWWWWW so I can pretty much forget that (not playable at all).

Any help would be great! :D

---

### Post by doctorzeus on 2010-11-22
My Most successfull attempt was this:

```
schedtool -a 0 -e winedbg  /home/(user)/.wine/drive_c/Program\ Files/vegas2/Binaries/R6Vegas2_Game.exe
WineDbg starting on pid 001b
0x7b85960f: movl	%edi,0x4(%esp)
Wine-dbg>

```

What do I do now ???

---

### Post by doctorzeus on 2010-11-23
Come on guys!? No one knows how to start an application using wine debug???

Please help! I really wanna get this game running, it's awesome (also to prove to a friend that Linux is much better that Windows Vista)

---

### Post by dankegel on 2010-11-24
> **doctorzeus said:**
> 
What do I do now ???


Try 'continue' or 'cont'.

---

### Post by doctorzeus on 2010-11-24
> **dankegel said:**
> Try 'continue' or 'cont'.

wow thanks, it worked :)

Can't believe I missed that :p 

Still getting through performance and bug issues though...

---

