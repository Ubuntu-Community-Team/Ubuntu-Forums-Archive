---
title: "wine Half-Life problems; crash after loading 2nd map"
date: 2009-07-28
forum: Wine
---

### Post by Redsandro on 2009-07-28
Hi,

I've got hl.exe working through wine sort of without problems, but when I start a new game and the train from the first level goes around the corner so that the next map is loading (this happens a lot throughout the game), Half-Life clean quits.

The output on a console during this quit is:
```
err:ole:CoGetClassObject class {92fa2c24-253c-11d2-90fb-006008a1f441} not registered
err:ole:CoGetClassObject no class object {92fa2c24-253c-11d2-90fb-006008a1f441} could be created for context 0x1
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

Who knows how to fix this?

I run Xubuntu 8.10 with a GeForce MX440 running good on a proprietary driver. Other games work fine.

Another problem is that in full screen the panels of XFCE show over the game. When I *deselect* to *"Allow the windowmanager take control the windows"* in *wineconfig* this problem is gone, but then the keyboard does not control the game anymore. Alt+F4 works to quit though.

---

### Post by NightMKoder on 2009-07-28
For the toolbars - disable desktop effects (or set some option for "legacy fullscreen"), for the crash, it may be related to pulseaudio, so use

pasuspender wine Steam.exe

---

### Post by Redsandro on 2009-07-29
Thanks for the tips. But it's not applyable.

First, the panels are placed over the screen because the window manager does that by default. I don't have desktop effects enabled anyway. But like I said, if I choose the WM *not* to manage wine windows, my keyboard doesn't work anymore in the game.

Second, the audio works perfectly fine. But just to try it I ran that command (but I use hl.exe because I have an old cd from before steam) and everything was exactly the same.

The crash doesn't seem audio related. It occurs exactly on the millisecond "LOADING" appears on screen to load the next part of the map.

---

### Post by NightMKoder on 2009-07-29
Are you using opengl for graphics? You should be, I hope. Also how does it crash (does wine crash or does the game just quit?)

As for the panels -  not letting the WM control wine windows will mess with focus. Make sure you're using the latest wine (1.1.26) and see if it still happens.

---

### Post by Redsandro on 2009-07-30
Yes I am using OpenGL. And the game doesn't crash, just quits. Although in the old days we would call it a crash. :P

> **Redsandro said:**
> Half-Life clean quits.

The output on a console during this quit is:
```
err:ole:CoGetClassObject class {92fa2c24-253c-11d2-90fb-006008a1f441} not registered
err:ole:CoGetClassObject no class object {92fa2c24-253c-11d2-90fb-006008a1f441} could be created for context 0x1
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

I am using:```
$ wine --version
wine-1.0.1
```

It comes through synaptic packet manager with Xubuntu 8.10 so I guess 'they' labelled that version reliable. I prefer to stick with the defaults because going away from it usually means a lot of work (by experience). But remember, Half-Life is from 1998 and I've read posts from 2004 where people say it runs fine.

But here's a breakthrough: I noticed both my user accounts were not mentioned in owner/group permissions so I **chmod**ded **-R a+w /usr/local/games/halflife**. And now, the game doesn't crash anymore in one of the accounts! But the other (the target account) there it's still the same. :confused:

So far I am sure. I really think it worked for the target account as well but getting back to it the next day it didn't anymore all of the sudden. I am pretty sure but because it seemingly makes no sense, I have to admid that maybe I was tired and confused and Xubuntu was playing tricks on my eyes. :)

Anyway, I understand that the problem might have been that HL wants to write a little file to the game folder everytime a new part of the map is loaded so changing write permissions for *all* would fix this. But I don't get why it doesn't fix this for all accounts..

---

### Post by Redsandro on 2009-07-30
I figured the 'crash' part out.. I wasn't crazy.

When I save a game in one user account, the game crashes in all other accounts because even though the save game files are readable, Half-Life wants it to be writable.

So after quitting, setting write permissions in the all group on all new saved game files makes the game not crash in other user accounts.

Is there a way I can start the game (or wine) so that saved games have write permissions for the all group to begin with?

---

### Post by Redsandro on 2009-07-30
I'd still like to know how to steer **wine** in what permissions files created from that session have. If anyone knows please share.



But for Half-Life (classic, non-steam, if that matters) I have fixed the permission-mess crash in a way that gives every user their own private save games, which is convenient because you cannot name the saves so it will pretty quickly become a mess if two people play the game.

The desktop shortcut to start Half-Life simply points to this file (or you can run it from a terminal or alt+f2):

*/usr/local/bin/hl*```
#!/bin/bash
# Half-Life classic independent saves per account
# Make sure halflife/valve folder has write access for ALL!!
# Redsandro 2009-07-30

savedir=~/.halflife
gamesavedir=/usr/local/games/halflife/valve/SAVE

# Verify SAVE folder
if [ -d $savedir ]; then
        echo okay
else
        mkdir $savedir
fi

# Unlink old symlink if exists
if [ -L $gamesavedir ]; then
        unlink $gamesavedir
fi

# Link SAVE folder to HOME folder
ln -s $savedir $gamesavedir

# Start Half-Life
env WINEPREFIX="/home/`whoami`/.wine" __GL_FSAA_MODE=4 wine "L:\\games\\halflife\\hl.exe"

# Remove symlink
unlink $gamesavedir

```

[SIZE="1"]Exporting *__GL_FSAA_MODE* is for 2x anti-aliasing on nVidia based cards.. you might export some vars specific for your card.[/SIZE]

---

