---
title: "Potential Solution for AMD Hybrid Graphics (needs testing!)"
date: 2014-04-04
forum: Ubuntu Development Version
---

### Post by Austin_M on 2014-04-04
So...I'm a big fan of Linux, but I'm an even bigger gamer.  Like a lot of people this has meant spending an inordinate amount of time becoming a WINE Ninja.  However, lately there have been so many advances in graphics cards that WINE is no longer my main stumbling block when attempting to play games on Linux.  This has lead to me dual-booting ever since I got my most recent laptop - an Acer V3-551G - because the AMD Dual Graphics cannot hot-swap under Linux.  And that, in turn, has lead me to spend the vast majority of my time in Windows 7, which while livable, I simply do not like (why they couldn't just provide service packs for XP until the end of time, I will never understand.)

Accordingly I have been racking my brain trying to come up with some zany-yet-functional solution to the problem that many have had with AMD Dual/Hybrid Graphics.  In my case, the cards are a 7600M and a 7660G - and for some insane reason someone at AMD decided the lower power card should end with an G, whilst the gaming card should end with an M.  I'll call them the "battery card" and "gaming card" for simplicity's sake.  Now, I can get both working - but only one at a time - with AMD's binary driver using the standard jocky GUI.  (Running X-Ubuntu 14.04 that was installed as 13.10 then upgraded, but this discussion should be independent of that.)  However, swapping cards requires a reboot.  The problem with this is that it's a laptop.  The sole, lone reason to even have both cards is so that, when not gaming, you save battery on the lower card.  Doing a reboot takes at least 3 minutes (between the actual reboot and all the saving/reopening things) and during that time the CPU is running near 100% as it tries to reload the entire system.  Naturally, if you do this frequently, it's going to fully negate ALL your power savings, and my previous 4 hours of battery life gets cut in half right from the start.  So, a good, reasonable solution MUST include the ability to hot-swap cards, similar to how it works in Windows.  Thus, this post.  Anyhow...here's my insane idea that I wanted some feedback on before I actually attempt it (and probably FUBAR my Linux install in the process.)

The way I understand it, the hot-swap fails because the kernel itself - and the console - has to have a card specified in GRUB, and once GRUB hands off the boot to the Kernel, etc, that cannot be changed.  However, I don't understand WHY this is the case.  Assuming this is a requirement that can be circumvented in some way, solving this becomes trivial.  Here's how.


[LIST=1]
[*]On boot, load X as usual, booting to tty7 on the battery card.
[*]Create a script that is able to load a second instance of X, on tty6, treating the game and/or WINE as the "shell" with the only difference being that it's configure to use the gaming card.  Either X can be passed a different config file, or else simply have the script swap another xorg.conf into place long enough to load the new X session, since X only reads xorg.conf when loading.
[*]Switch the user to tty6, and when the game/wine exits, the X session is set to not automatically relaunch, thus returning the user to tty7.
[/LIST]

Why can't this be done?  Is there some really, really good reason why the kernel is 100% incapable of NOT locking out the other card at boot?  If so, how can people who have 2 normal graphics cards do what they do?

EDIT: I just realized I totally put this in the wrong forum (though relevant to 14.04, it should've been in Hardware.)  If someone wants to move it, feel free.  Sorry!

---

