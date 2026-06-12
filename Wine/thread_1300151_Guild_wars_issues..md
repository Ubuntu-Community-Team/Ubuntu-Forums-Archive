---
title: "Guild wars issues."
date: 2009-10-24
forum: Wine
---

### Post by Dave_57204 on 2009-10-24
Hello, I just downloaded the trial of guild wars today, Install went fine, But when I try to run it in wine all I have is sound, no video whatsoever. Does anyone have any ideas?

---

### Post by Hosmion on 2009-10-24
Considering Wine can only take so much, and since Guild Wars is a massive online MMPORG, it probably can't support sound..  Just guessing though :D

---

### Post by Dave_57204 on 2009-10-24
Any other ideas?

---

### Post by Dave_57204 on 2009-10-25
Still Have not figured it out. >.<

---

### Post by 569874123 on 2009-10-25
Try using the crossover trial.

---

### Post by Toffeeapple on 2009-10-25
Guild Wars works very well in wine, perfectly playable... if you are having problems try [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194").

---

### Post by hikaricore on 2009-10-25
> **Hosmion said:**
> Considering Wine can only take so much, and since Guild Wars is a massive online MMPORG, it probably can't support sound..  Just guessing though :D

Please don't post nonsense.

---

### Post by beastrace91 on 2009-10-26
> **hikaricore said:**
> Please don't post nonsense.

Agreed.

@Dave_57204 What Wine version are you using? Last time I used GuildWars it ran pretty flawlessy under Wine.

Also what sound card do you have?

~Jeff

---

### Post by Annigma on 2010-01-22
Did you fix it?
I would disable any fancy visuals you have running for starters, such as Compiz, etc..
Also try changing one setting at a time in 'Configure Wine', such as 'Windows version', 'Emulate a virtual desktop', etc..
You can also run GW with flags, such as -noshaders, -nosound, -dsound, etc.. such as:

(darn, copy/paste isn't working..)

```
wine "C:\Program Files\Guild Wars\Gw.exe" -dsound
```

Have a good look through the other GW posts here. [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194") and [GW wiki]("http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine") may also be of help.

:)

---

### Post by spongypants23 on 2010-01-22
Try having Wine emulate a virtual desktop. This solved most of my Guild Wars wine problems.

Applications > Wine > Configure > Graphics > Emulate virtual desktop.

(May  not be the exact words as Wine is in Swedish for me.)

Edit: Why the hell revive such an old topic?

---

### Post by recamshak on 2010-06-09
I had the same problem and the solution in my case was as follow :
[LIST]
[*]In the wine config manager, enable "emulate virtual desktop" on the "display" tab
[*]Chose a large enough desktop size for example 1800 X 800
[*]Run GW, you should see an empty desktop
[*]Actually if you move the virtual desktop window, you will see the GW window hide somewhere on the right side of the virtual desktop
[*]Double-click on it to switch it full-screen (inside the virtual desktop)
[/LIST]

That's it! Next time you run GW, it will appear full-screen!

At least that solve the problem in my case, with exacly the same symptoms as you.

Hope it helps

---

