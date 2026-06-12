---
title: "Random lag &amp; sound cuts"
date: 2009-04-30
forum: Wine
---

### Post by Bios Element on 2009-04-30
So I've been running Steam to play Zombie Panic: Source (Same engine as Half Life 2.) for the past few months but recently I've been having some strange bugs.

1). Every 30 seconds or so I have a 1-3 second lag spike where everything just freezes and CPU usage drops off.

2). After maybe 30 minutes of play (Average, It sometimes cuts out earlier/later.) Sound randomly stops being sent to pulseaudio. Banshee works just fine still but I have to re-start the entire application to get sound back.

Anyone have any tips or ideas of what Might be up?

Thanks for your time.

---

### Post by cogadh on 2009-04-30
Try running it without Pulse:
```
pasuspend wine foo.exe
```

---

### Post by u235sentinel on 2009-04-30
> **Bios Element said:**
> So I've been running Steam to play Zombie Panic: Source (Same engine as Half Life 2.) for the past few months but recently I've been having some strange bugs.

1). Every 30 seconds or so I have a 1-3 second lag spike where everything just freezes and CPU usage drops off.

2). After maybe 30 minutes of play (Average, It sometimes cuts out earlier/later.) Sound randomly stops being sent to pulseaudio. Banshee works just fine still but I have to re-start the entire application to get sound back.

Anyone have any tips or ideas of what Might be up?

Thanks for your time.

I would disable pulseaudio.  I've had nothing but headaches with it in 8.04. Not sure if jaunty fixed it up but 8.04 it's a mess.

also what version of wine are you running?  You might want to check out 1.1.20 and see if that helps.  

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14112](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14112)

Looks like it has a gold rating but there was a suggestion of configuring WINE so it runs under windows 98 environment.  Might be something to try

---

### Post by Bios Element on 2009-04-30
> **u235sentinel said:**
> I would disable pulseaudio.  I've had nothing but headaches with it in 8.04. Not sure if jaunty fixed it up but 8.04 it's a mess.

also what version of wine are you running?  You might want to check out 1.1.20 and see if that helps.  

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14112](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14112)

Looks like it has a gold rating but there was a suggestion of configuring WINE so it runs under windows 98 environment.  Might be something to try

Aye, I'll try disabling pulseaudio and see where that gets me. And yes, I forgot to mention I'm using the wine ppa.

---

