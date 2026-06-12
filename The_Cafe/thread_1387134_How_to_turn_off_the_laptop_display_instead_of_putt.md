---
title: "How to turn off the laptop display instead of putting it to sleep"
date: 2010-01-21
forum: The Cafe
---

### Post by legolas_w on 2010-01-21
Hi

I have a thinkpad t400 and I am looking for a way to turn off the display sometimes like when I want to go to bed and let it play some music or download some torrent files.


I know that somehow the display turn off after some time, but I can not do it manually which is what I am looking to do.

Thanks.

---

### Post by deadalus.globalnode on 2010-01-21
What kind of graphics card do you have?

---

### Post by whiskeylover on 2010-01-21
Close the lid, and change the settings so that closing the lid does not put the laptop to sleep.

---

### Post by deadalus.globalnode on 2010-01-21
The reason I asked about the graphics card is because many have a command to turn of the display but Whiskylover's solution is much simpler and probably better. As usual I thought of the hard way first :lolflag:

---

### Post by tgalati4 on 2010-01-21
Or just set the screensaver to a blank screen.  The backlight will normally turn off by itself after 10 minutes or so.  You can adjust it in the BIOS under power management settings.  

Hitting FN-F3 (on my T43P) activates the "lock-screen" which blanks the screen then activates the screensaver (which could also be a blank screen) until you hit a key.

man xset

You could also write a script to use xset and force a dpms setting, then play your music for an hour, then put the machine to sleep.  Set wake on BIOS time and automatically play an internet radio station or an mp3 playlist.

---

### Post by whiskeylover on 2010-01-21
> **whiskeylover said:**
> Close the lid, and change the settings so that closing the lid does not put the laptop to sleep.

Make sure you do that in reverse order.

---

### Post by juancarlospaco on 2010-01-21
**[COLOR="Blue"]xset dpms force off[/COLOR]**

---

### Post by humphreybc on 2010-01-21
> **whiskeylover said:**
> Make sure you do that in reverse order.

Nice.

---

