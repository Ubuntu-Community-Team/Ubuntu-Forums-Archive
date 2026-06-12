---
title: "get steam working in wine?"
date: 2010-05-20
forum: Wine
---

### Post by BrewerFR on 2010-05-20
im sure there are millions of posts on this forum on how to do this, but ive looked and i cant find them.

i wouldn't say im an absolute beginner in ubuntu, but this has taken me a long time and its got to the stage where i actually need to help from someone who can simplify it for me.

Ive followed three separate tutorials about how to get steam working on Ubuntu. 2 for wine, 1 for Play On Linux. the Play On Linux one looked as though it installed ok, but then didn't work at all. the wine ones also looked like they installed ok, however when i ran steam from wine it would show STEAM in my task bar, but the program itself would be invisible.

Im using Ubuntu 9.10, i have no idea what version of wine im using and i have no idea what to do. Can anyone help me? :confused:

---

### Post by LazyLlama on 2010-05-20
Hey there!
It's simple really.

Just pop:

```
wget http://steampowered.com/download/SteamInstall.msi
wine msiexec /i SteamInstall.msi
```

Into the terminal. Then follow the onscreen instructions.
Alternativaly, you can download PlayOnLinux from the Ubuntu Software Center, and use the inbuilt installer on that.

Hope that helps!

---

### Post by jnana on 2010-05-20
one other thing to consider is the new steam client only seems to work  under vista/win08 settings.
also, when you get there, don't forget to turn off steam chat during  play. there's a setting under the client. 
still very boggy for me though, been at it for a day. please let me know  if you find a solid solution! thanks.

---

### Post by benmoran on 2010-05-21
I recommend installing it through PlayOnLinux. Set the windows version to "windows 7" if you have trouble, but mine works when set to XP. 

PlayOnLinux is really awesome because everything you install can be put in it's own wineprefix. This is really beneficial if you start messing around with external DLL files and other wine tweaks. It took me a few days to get the hang of it, and it DOES take a few extra steps sometimes, but i'll probably use it from now on.

---

### Post by BrewerFR on 2010-05-22
Ive tried it in wine, and it didnt work, and ive also tried it in play on linux, which also didnt work. From online tutorials, ive been able to gather that some people find it necessary to download direct X from the POL before steam will work.

---

### Post by BrewerFR on 2010-05-22
> **LazyLlama said:**
> Hey there!
It's simple really.

Just pop:

```
wget http://steampowered.com/download/SteamInstall.msi
wine msiexec /i SteamInstall.msi
```Into the terminal. Then follow the onscreen instructions.
Alternativaly, you can download PlayOnLinux from the Ubuntu Software Center, and use the inbuilt installer on that.

Hope that helps!

The problem im having is that it seems to install ok, but when i start it up it appears for a few moments in my task bar [Saying 'starting steam'] and then just disappears. Do you have compiz fusion working alongside it?

---

### Post by BrewerFR on 2010-05-22
Good news, i have finally got it to work. I installed steam, alongside the gecko and Direct X end user requirements. Works like a charm, if not a little slow

---

### Post by eotakos on 2010-05-25
> **jnana said:**
> one other thing to consider is the new steam client only seems to work  under vista/win08 settings.



thank you very much for that! - without changing this setting, the login window doesn't appear at all, even though the application is running. all you can see is the shadow of the window at the workspace preview...

---

### Post by dardack on 2010-05-25
Can't wait for the linux steam client to be released.

---

