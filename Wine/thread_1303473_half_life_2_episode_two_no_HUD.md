---
title: "half life 2 episode two no HUD"
date: 2009-10-28
forum: Wine
---

### Post by Falc7 on 2009-10-28
I'm playing HL2 episode 2, and i don't have any of the health info or gun changing yellow boxes. I think they are called HUDs. They were all present in the other HL2 games. I am using wine 1.1.29, kubuntu 9.10, and nvidia 9600.

I believe someone else has had the same problem
[http://appdb.winehq.org/commentview.php?iAppId=2095&iVersionId=9421&iThreadId=51585](http://appdb.winehq.org/commentview.php?iAppId=2095&iVersionId=9421&iThreadId=51585)

Does anyone know a fix?

Edit: Apparently, if i set the dxlevel at 81 it works fine, and i have to do this through the command line, how do i do this?

---

### Post by Falc7 on 2009-10-28
aah worked it out, added this
-dxlevel 81
to launch properties within steam, all fixed now

---

### Post by Landoc@verizon.net on 2009-12-03
Thanks for the post saved me alot of time and trouble. Also had to get sound working by selecting Esound Driver under Audio on Wine configuration. Now it plays like a champ.:D

---

### Post by Falc7 on 2009-12-03
glad it helped, enjoy the game! its awesome

---

### Post by The Funkbomb on 2009-12-11
I am having the same issue.  HL2, HL2:E1 played fine.  HL2:E2, no HUD, no cross hairs, can't switch weapons...

I tried the -dxlevel 81 trick, but it didn't work.

Using Ubuntu 9.10, 9600gt, don't know what version of wine.

---

### Post by The Funkbomb on 2009-12-11
fixed it!

---

### Post by pgordon on 2009-12-14
> **The Funkbomb said:**
> fixed it!

I'm having the same problem. I've tried various dxlevel launch properties. How did you finally fix it?

---

### Post by pgordon on 2009-12-14
Ahh. I used the steam launch properties option for episode 2 rather than adding the -dxlevel 81 to the launcher command line. Works great.

---

