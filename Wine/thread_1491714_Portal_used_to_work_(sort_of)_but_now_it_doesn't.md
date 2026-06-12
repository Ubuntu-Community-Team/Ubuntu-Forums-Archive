---
title: "Portal used to work (sort of) but now it doesn't"
date: 2010-05-23
forum: Wine
---

### Post by LizLove on 2010-05-23
When I downloaded Steam and Portal a little over a week ago, it kinda worked (I don't know if ways it didn't work so well are relevant to this or not, if you think they might be, just ask), and then it just quit working. The Valve and Source logos play, and then the screen goes black. The cursor still moves, but everything else freezes completely. I can't switch windows or workspaces, even the clock stops, so I can't get a look at the terminal output.  I'm running Wine 1.1.44 on Ubuntu 10.4 and have a Nvidia graphics card.

---

### Post by Soulcage on 2010-05-24
Try upgrading to wine 1.2 rc1. I actually couldn't get half-life2 working in 1.1.44 but it now works in 1.2 rc1.

---

### Post by LizLove on 2010-05-24
Upgraded and am unfortunately still having the same issue.

---

### Post by Soulcage on 2010-05-25
Have you ran steam from a terminal and portal in windowed mode?
You can add to the launch options for portal: ```
-windowed -novid
```

---

### Post by LizLove on 2010-05-25
Yep, I try to run it windowed and with -novid, and I've tried playing with -dxlevel (80,81,90), too. I've looked at other forums and found people running it on Windows/Mac having a similar problem, but they seemed to be to get it to work, so I tried the stuff people suggested to them and have not had any luck with it.

---

### Post by jakejw93 on 2010-05-26
I just tested the game then on ubuntu 10.04 with wine 1.2rc1 and the game runs how it should do, It may be something with the free version ( if thats the on you got ), I have the one that came in the orange box.. but for me it runs how it should do?

---

### Post by beastrace91 on 2010-05-26
> **jakejw93 said:**
>  I have the one that came in the orange box

That doesn't matter.

@OP What video card/driver version?

Regards,
~Jeff

---

### Post by LizLove on 2010-05-26
I've got an nVidia GeForce 7150 with the nvidia accelerated graphics driver (version 173)

---

### Post by beastrace91 on 2010-05-27
> **LizLove said:**
> nvidia accelerated graphics driver (version 173)

WOW that driver is old! Upgrade to the newest driver and see if that resolves the issue.

Regards,
~Jeff

---

### Post by LizLove on 2010-05-27
I knew it was old, but I never updated because for a while there, Compiz refused to work with a newer driver. Apparently that got fixed at some point (I'm a fairly recent convert from Windows, I'm still not quite used to updates actually fixing things yet).

So I updated and it runs! It isn't really playable anymore like the last time I had it running, but I can start it up and it doesn't kill my computer.

Why it randomly quit working I may never know, but thanks for the help.

---

