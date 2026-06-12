---
title: "how to get games to boot from disk"
date: 2009-01-10
forum: Wine
---

### Post by bobbyallan on 2009-01-10
i have several games that require the disk to run. how do i configure wine to detect the disk. and yes i have already installed the game from the same disk.

---

### Post by hikaricore on 2009-01-10
Depending on the titles you may need to look into nocd patches.
If this is the case we will not be able to assist you on this forum due to the legal grey area this touches on.

However don't take this is the final word, I just don't have time to get into detail on cd mounting and such, hopefully someone will be able to provide better answers.

---

### Post by soluphobe on 2009-01-10
I assume just sticking the CD in the drive doesn't work?  ;)

One thing I've been able to do is to (specifically with multi-cd installs) is to go into winecfg>>drives, then define a new drive (usually as a folder in my home folder.  Under 'Advanced' you can force it to register as a CD drive.  Then, if you can, copy the files of the cd into that folder (and delete unneeded ones).  You don't have to take an iso of the CD, and I'm fairly sure it's not illegal (it wasn't on the game I used) - many EULAs allow you to make one backup copy for personal use (at least, they used to...).

---

### Post by cogadh on 2009-01-10
> **bobbyallan said:**
> i have several games that require the disk to run. how do i configure wine to detect the disk. and yes i have already installed the game from the same disk.
If you are referring to the autoplay functionality that you normally see when running a game in Windows, you don't need that with Wine (or with Windows, for that matter). Just insert the CD, let it mount, then launch the game using the menu shortcut that Wine created when you installed the game. It should automatically detect the presence of the CD and just run. Of course this is assuming that you already have your CD/DVD drive properly configured in winecfg, which it should do automatically anyway. Occasionally, you may need to create a symbolic link to your CD drive's /dev entry in addition to the mount link that Wine creates by default, which you can do like this:
```
ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
```
You will need to adjust that line to match the /dev entry for your actual CD drive (it probably isn't /dev/hdc) and if you defined the drive as something other than "D:" in Wine, change the "d" in "~/.wine/dosdevices/**d**\:\:" to match it.

However, as hikaricore mentioned, there are some games where it will never properly detect the CD, mainly because the game uses a copy protection/CD check scheme that is not supported in Wine. In these cases, you will need to use a cracked executable that removes the CD check in order to run the game. You will need to find out on your own how to do that.

Depending on the game, you may be able to find specific information on what is required to run it from Wine's [Application Database](http://appdb.winehq.org/), so you might want to check there first to see if there are any specific instructions on how to get the CD detection to work properly on your game.

---

