---
title: "Virtual desktop in wine tearing thru game"
date: 2009-05-05
forum: Wine
---

### Post by johnhdsi on 2009-05-05
Hi all I'm having a weird issue in Wine. I installed World of warcraft and it runs fine, a little laggy but fine nontheless. My major issue is the virtual desktop. I had to enable the virtual desktop to keep the game from crashing on me but every time I click the screen with the mouse I get a screen flicker of the virtual desktop showing through (IE: the screen flashes blue on mouse cick). I am running Ubuntu 8.1, a P4 3 gig, 1 gig of RAM, ATI 9600 se video card, and out of the box wine 1.1.20, any ideas?


john

---

### Post by del_diablo on 2009-05-05
sudo Aptitude uninstall compiz

I think that should do the trick.

---

### Post by abeisgreat on 2009-05-06
> **del_diablo said:**
> sudo Aptitude uninstall compiz

I think that should do the trick.

I think the command you want is
```

sudo apt-get remove compiz

```

I dont know how well that would work, not my command, I'm just fixing his syntax.

---

### Post by johnhdsi on 2009-05-06
ok...so removing compiz might fix it? Can I ask if there is a reason/thoery behind this as I would like to have Compiz for all the neat little bells and whistles. I don't mind removing it, I'm a newb and I was just wondering about the why of removing it to solve the issue. I appreciate the replies and the help with it.

John

---

### Post by u235sentinel on 2009-05-06
> **johnhdsi said:**
> ok...so removing compiz might fix it? Can I ask if there is a reason/thoery behind this as I would like to have Compiz for all the neat little bells and whistles. I don't mind removing it, I'm a newb and I was just wondering about the why of removing it to solve the issue. I appreciate the replies and the help with it.

John

I wish I could answer why but I had similar problems with it myself.  After removing it I was able to game just fine with Linux.  It was a nightmare with WINE and native linux gaming.

---

### Post by NightMKoder on 2009-05-06
Wine and compiz use the same graphics calls, and compiz sometimes messes up wine's rendering (it tries too hard, shall we say). You don't have to uninstall compiz, just disable desktop effects before you start the game (I remember seeing scripts that do this for you).

---

### Post by johnhdsi on 2009-05-06
When u say disable desktop effects are you talking about the settings where you set "none" "normal" and "extra"? I did the sudo apt-get remove compiz and I tried launching the game, it launched fine but I still had screen tearing and there were alot of either messed up or missing graphics in game, about 2 min. into the game it crashed. I have tried running opengl mode but for some reason it makes things worse. I checked the Wine site and it says that WoW runs perfect out of the box with no tweaks but I keep having the graphics issues. I can't run WoW without the virtual desktop either or I crash immediatly upon launch. I'm going to try reinstalling compiz I guess and maybe set the desktop effects to none? Any other ideas are appreciated, thanks for all the info.

John

---

### Post by johnhdsi on 2009-05-07
Hi all,
I got the issue worked out here's what I did. I did remove compiz as suggested and I disabled desktop effects (I set it to none), I also removed the OpenGL line in my WoW Config.wtf file as this seems to crash the game no matter what I do. I booted up WoW and it runs great!!! No tearing, no bleed throughs none of it. I did not make any of the reg edits or config.wtf edits from the other posts, so I am basically running WoW out of the box with the same for Wine. Thank you so very much for all your help in figuring this out I really appreciate it!!!


John:guitar:

---

