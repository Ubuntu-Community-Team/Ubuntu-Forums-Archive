---
title: "Touhou 7"
date: 2011-02-24
forum: Wine
---

### Post by flee0308 on 2011-02-24
Hi, I am trying to run Touhou 7 (Perfect Cherry Blossom) on Linux with wine. But I have this problem where once I reached the first menu, the game keeps scrolling through the choices for the menu. No matter what button I press, I can't stop the menu from scrolling. Enter doesn't work either. The only way to close the game is to use xkill in the terminal. Does anyone know how to solve my problem? Thanks.

---

### Post by HeroKing on 2011-02-24
i have a feeling you'll say no, but do you have a controller plugged into your computer? that was usually the cause of that kind of error with me. especially since i had analog that would always be off center by just a hair

---

### Post by flee0308 on 2011-02-24
Nope. :/

---

### Post by CarpKing on 2011-02-25
In the game folder there should be a file called "custom.exe."  Run it and change the "DirectInput" setting.  I *think* that should fix it.  I had the same problem; if you try it and it doesn't work, take a screenshot of the custom.exe and we'll see if we can figure out what the deal is.  

This is from the [Touhou Wiki](http://en.touhouwiki.net/wiki/Running_in_Linux_and_MacOS_X/Misc_fixes), but I couldn't find exactly what I read before.

---

### Post by flee0308 on 2011-03-20
> **CarpKing said:**
> In the game folder there should be a file called "custom.exe."  Run it and change the "DirectInput" setting.  I *think* that should fix it.  I had the same problem; if you try it and it doesn't work, take a screenshot of the custom.exe and we'll see if we can figure out what the deal is.  

This is from the [Touhou Wiki](http://en.touhouwiki.net/wiki/Running_in_Linux_and_MacOS_X/Misc_fixes), but I couldn't find exactly what I read before.

Umm, all the words are ???. Let me show you a screenshot.

[IMG]http://i74.photobucket.com/albums/i259/flee0308/Screenshot.png[/IMG]

---

### Post by CarpKing on 2011-03-27
Here's the page on the Touhou Wiki with a translation: [http://en.touhouwiki.net/wiki/Config#Perfect_Cherry_Blossom](http://en.touhouwiki.net/wiki/Config#Perfect_Cherry_Blossom)

Try checking the box with "DirectInput" next to it.  I don't remember which of the buttons at the bottom is "OK" and which is "Cancel," so you'll have to try one and run custom.exe again to see if the setting sticks.  If it doesn't, try the other one.  Once you get the setting to stick, try running the game again.  If you still have the same problem we might have to fiddle with the Wine settings.

---

