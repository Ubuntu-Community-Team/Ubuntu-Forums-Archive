---
title: "Warcraft III no CD error"
date: 2009-01-23
forum: Wine
---

### Post by Carltonlinux on 2009-01-23
I have ubuntu 8.10 and the newest version of Wine installed.

I installed under the C: directory and have gone into winecfg to set it up.

every time I go into a terminal and run wine Warcraft\ III.exe -opengl

I just get an no CD error, I am fully aware how to crack and run games in xp, i normally go to gamecopyworld.com and get a .exe file but this doesnt seem to work because i still get the same error. I am a Computer Science student and decided to immerse myself in linux, but would really like to have a few of my fav windows games to play when i take a break from doing C++ work in Eclipse.

Thanks in advance
Carlton

---

### Post by hotweiss on 2009-01-23
You have to download and install this:

[http://www.microsoft.com/downloads/details.aspx?familyid=200B2FD9-AE1A-4A14-984D-389C36F85647&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=200B2FD9-AE1A-4A14-984D-389C36F85647&displaylang=en)

Now you you will not have the CD error anymore.

---

### Post by k@e on 2009-01-24
I can run Warcraft III without having installed any runtimes.

Don't use a crack. Get and apply the latest patch (1.22a), it removes the need for having a CD inserted.

---

### Post by hotweiss on 2009-01-24
> **k@e said:**
> I can run Warcraft III without having installed any runtimes.

Don't use a crack. Get and apply the latest patch (1.22a), it removes the need for having a CD inserted.

I got this error without using the crack also. I just backed up my Warcraft 3 onto a DVD so that I would not have to install each time, and that's what I think the OP did also.

---

### Post by ucal on 2009-12-03
Maybe I'm beating a dead horse here, but I have the same error.  Frozen Throne worked until I patched it to 1.24 (right after installing it), and now it gives me a No CD error.  

[QUOTE=WineHQ]How to play without CD?

Connect to battle.net to upgrade to the latest version of Warcraft 3 which doesn't need a CD.

If you ever get "Please insert disc", this is NOT a problem with detecting the CD. The protection system is probably still built into the game even though the CD check itself is disabled. Make sure you use version 1.21b or later. If you get this problem after having this version installed, you are likely suffering from a buggy video driver as this is the only known (and proven possible) cause at this point.

DO NOT USE NOCD PATCHES - They are pointless, and won't fix the real problem.[/QUOTE]

My question is, will a NoCD patch actually let me play the game?  Because as far as I'm concerned, that is the real problem.  I've updated to the latest video driver for my card, with no luck.

---

### Post by PariahVayne on 2009-12-03
x

---

### Post by ucal on 2009-12-03
It is updated. According to wineHQ this is a video driver error.  I was wondering if the nocd patch will help me get past it.  Sadly, I haven't been able to find a nocd patch because of the fact that it isn't needed because of the damn patches.  Why oh why does blizzard have to be so understanding and nice with their warcraft 3 customers?

---

### Post by PariahVayne on 2009-12-04
x

---

### Post by ucal on 2009-12-04
> **PariahVayne said:**
> Oh ok, I haven't played W3 in a while. Strange that a graphics driver would cause that issue. Could you please post a link to where it states that?

My first post in the thread.  Apparently my buggy driver and wine don't get along.  >_<

---

### Post by Azuu on 2009-12-04
Go to their main website and register your warcraft 3 cdkey. at any time after you do you can download a no cd install that installs the latest version of the game to any computer with access to your account, this will save you time in the future.

---

### Post by ucal on 2009-12-04
> **Azuu said:**
> Go to their main website and register your warcraft 3 cdkey. at any time after you do you can download a no cd install that installs the latest version of the game to any computer with access to your account, this will save you time in the future.

I already have done that.  In fact that's how I got the game installed on Ubuntu.  The problem is that it's still requiring me to have a CD to play it.  I was able to play it once (right after using that installer), at which point it updated to 1.24, then when I restarted, it started asking me for a cd.

---

### Post by ucal on 2009-12-05
Okay, reinstalling it worked to get rid of the error.  Now I just have to boost performance.  Switching into opengl mode boosted performance but now it's back to the same old levels.

EDIT:  Nevermind.  Turns out I was running it with an -opengpl command.  /facepalm.

---

