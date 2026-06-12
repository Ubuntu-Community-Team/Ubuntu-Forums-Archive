---
title: "WoW issue"
date: 2010-07-10
forum: Wine
---

### Post by eminembdg on 2010-07-10
So I've been reading and searching the many many pages about WoW and WINE.

I have an issue that I can't seem to find anyone else having.

I can't find the WorldOfWarcraft folder with all of its normal subfolders. YES.. I have selected to unhide folders and still can't find the folders.

I've looked in .playonlinux and the .wine directories. I can find a WoW folder in each, but still there are no Interface folders.

My issue is... since I can't seem to find the Interface and then inside that the AddOns folder, I can not use or install Addons.
I've tried making the folders myself, but still on the sign on screen there isn't a "addons" button.

I've searched the web for last 2 days and I find people who have same problem because they didn't unhide the folders. Again, I've unhidden the folders and they aren't there.

If anyone can help me it would greatly appreciated. Thanks in advance. 

And if this exact issue has been discussed and I just couldn't find it, I apologize. If so , please point me to the right thread.

-Blair

---

### Post by hikaricore on 2010-07-10
/home/username/.wine/drive_c/Program\ Files/World\ of\ Warcraft/

---

### Post by eminembdg on 2010-07-10
That doesn't exist when I type that into the nautilus search bar.

I have a feeling that when I used the installer from wow.com that something got messed up. Everyone, including yourself, keeps saying that's where to find the whole entire WOW folder and all it's normal contents, but it's not there for me. 

I don't know what to do about it. I mean the game works perfectly fine, except for the addons.

Any ideas?   And thanks for your help also

P.S. - What's with the forward and backslashes? Haven't seen that used before.

---

### Post by eminembdg on 2010-07-10
Wait a minute! I found it!

Dummy me! What I did was look at the properties of the shortcut on my desktop to see where it was pointing to. And VOILA!

This is where my WoW got installed to: WINEPREFIX="/home/blair/.wine" wine "C:\users\Public\Games\World of Warcraft\Launcher.exe" 

That is the path that the shortcut uses to get to the launcher.

Well that solves that problem. But still I have a question... Why did it go there and not where everyone said it should of gone?

---

### Post by hikaricore on 2010-07-10
All I can imagine is that Blizzard changed the default installation directory to accommodate win7.

---

### Post by eminembdg on 2010-07-10
ya know what.. that does make sense since that is where win7 installs games and all.

thanks a lot for your time and help

---

