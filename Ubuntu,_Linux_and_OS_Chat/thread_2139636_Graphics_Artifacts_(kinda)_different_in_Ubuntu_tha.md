---
title: "Graphics Artifacts (kinda) different in Ubuntu than in Windows"
date: 2013-04-27
forum: Ubuntu, Linux and OS Chat
---

### Post by agough on 2013-04-27
Apologies for the wacky title, it was the most concise that I could come up with... :)

I've inherited some old but decent hardware and have installed Ubuntu happily alongside Windows. Everything's fine except graphics - there's some weird stuff going on that I have a feeling just means "busted graphics card". I've attached some pics.

The boot screen is rather weird, it varies from boot-to-boot, today's one is rather good comparatively...
[ATTACH=CONFIG]241856[/ATTACH]


The black/white dotty screen capture is actually from OpenTTD running full screen on Windows - for some reason the game didn't appear on the shot, just the artifacts. Windowed it runs fine.
[ATTACH=CONFIG]241855[/ATTACH]

Ubuntu (I also tried Lubuntu) is messed up all the time, to the point of being unusable/unreadable, on both Unity and Unity2d (and LXDE on Lubuntu).
[ATTACH=CONFIG]241858[/ATTACH][ATTACH=CONFIG]241859[/ATTACH]

Windows, however, is fine, unless it does a full screen, as mentioned above, or I make it use 16 bit colour. Then, all sorts of dotty madness occurs. An exception is the cursor - it has funny little lines/dots around it (did that in Linux too). Booting Windows is wrong too:
[ATTACH=CONFIG]241857[/ATTACH]

Using Windows for web-browsing, full-screen flash, GIMP, full-screen DVDs is all fine, yet all Linux stuff is a write off - could something have gone down OpenGL-wise on the card?

Anyway, thanks for your help, I wasn't too sure where to put this thread as it's not specifically a Ubuntu problem.

Edit: I've just thought: I'm yet to try a full-screen app that's DirectX - all the messed up ones have been OGL/SDL games. Back soon...

---

### Post by sudodus on 2013-04-27
It might be hardware, since you have similar problems with Windows too. But it could also be that the graphics driver does not cooperate well with the graphics chip/card.

- What graphics chip/card is it?
 
- What driver are you running in Ubuntu and Lubuntu?

check with the GUI program [I][B]hardinfo

[/B][/I]. look at Kernel modules if you have a built-in driver
. look at Display -- OpenGL if you have a proprietary driver

Do you have any boot option [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by MadmanRB on 2013-04-27
Yeah sometimes older cards are titchy, you may want to do xubuntu on those archaic cards.

---

### Post by deadflowr on 2013-04-27
Could be bad graphics card or if desktop bad wire connection.

It does remind me of when my wire to my monitor is borked, or just too loose.

If it is a desktop, try unplugging the wire and blow out any particles that might be in it.

Maybe try a different wire if possible.

If the problem persists, then you could then narrow it down to card problems.

---

