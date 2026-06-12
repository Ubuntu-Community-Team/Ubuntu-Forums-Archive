---
title: "Shuting down wine?"
date: 2009-03-29
forum: Wine
---

### Post by rob2nd9th on 2009-03-29
Ok, I have tried trawling through post but no luck, All I need to know it how to kill/stop/shut down wine if wow freezes?

I hate and have had to turn off the laptop.

Thanks for any help.

---

### Post by DirtDawg on 2009-03-29
Open a terminal and enter the command 'killall wine' (w/o quotes, of course). If that fails to work, try 'killall wine-server'.

---

### Post by cogadh on 2009-03-29
"wineserver -k" always works for me.

---

### Post by rob2nd9th on 2009-03-29
All good IF you can open a terminal ?

when wow freezes on me I cant do jack -

---

### Post by hikaricore on 2009-03-29
> **rob2nd9th said:**
> All good IF you can open a terminal ?

when wow freezes on me I cant do jack -

Ctrl+Alt+F[1-6]  example:  Ctrl+Alt+F2

Should bring you to a text terminal.
You can get back to X by hitting Ctrl+Alt+F7 (for some reason on one of my systems it's Ctrl+Alt+F9  *shrug*)

Now what we need to be discussing is why WoW is freezing in the first place.
Do you have decent enough hardware to be running it and/or could your video card be overheating?

---

### Post by rob2nd9th on 2009-03-30
It MASSIVE server lag I'm (at the moment) on dial up speed after Thursday should have broadband.

How ever

"Do you have decent enough hardware to be running it and/or could your video card be overheating?"

Running Acer Aspire 5720

How would I know if the vid card was over heating?

Thanks for the info Its nice to have just in case..

---

### Post by Dejai on 2009-03-30
To kill a program I usually just run: 

ps aux | grep programName

It now prints the programs with that name e.g

70231 programName

Then I just

kill 70231

---

### Post by rob2nd9th on 2009-03-30
Ok tried the "ctrl +alt f2" works fine if the game is not frozen if it is the no text terminal :(

---

