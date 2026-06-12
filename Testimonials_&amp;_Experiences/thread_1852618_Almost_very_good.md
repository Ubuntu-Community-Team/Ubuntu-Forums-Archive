---
title: "Almost very good"
date: 2011-09-30
forum: Testimonials &amp; Experiences
---

### Post by kiwibrit on 2011-09-30
I loaded 11.04 into my ex-windows Asus 1000h.  Installation was straight forward, except for loading a driver for the wireless card - though that was quickly resolved on the forum.  Unfortunately, the system freezes from time to time.  It's a graphic driver problem, and it looks as though it may not be soluble.

So, I think I may be converting the computer back to Windows.  That's disappointing, because Ubuntu looks very promising in other respects.  It's quick, and there is lots of free  for personal use.

---

### Post by stalkingwolf on 2011-09-30
i have a 1005HA that is running both 10.10 superos and 11.04 super.  other than a weird experience when i tried to install on an external drive all is well.  might be worth a shot.

---

### Post by Tamlynmac on 2011-09-30
> kiwibrit

Thank you for sharing your experience.

Sorry you had problems, hopefully in the future your hardware will be supported OOTB. Since this section of the forums isn't for support or debate, please know that your feedback is appreciated.

Good Luck

---

### Post by 3rdalbum on 2011-10-02
Ubuntu 11.10 will be out at the end of the month. You can download the beta now, and if you keep it up-to-date you'll eventually have the final release version. It might fix your problem - maybe give it a go?

---

### Post by Swagman on 2011-10-02
I have been suffering weird "lock-up" issues and X resetting for no apparent reason just lately. Must've installed an update that something didn't like.

So I trawled through all the logs until I found a line to do with graphics that read 
> 
Oct  1 03:37:57 Main-Computer gdm-session-worker[1386]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed


Also found 

> 
[  6711.450] Segmentation fault at address 0xb5001000
[  6711.450] 
Caught signal 11 (Segmentation fault). Server aborting
[  6711.450] 


in Xorg.5.log

So.. I fired up Synaptic and re-installed nvidia_current

So Far... bobs my Mothers Brother

This wasn't easy to discover.. I'm not a propellor head. I first did a Memtest check.. Then I ran from a live USB <-- Used that to read the logs too as Desktop session just kept locking up.

---

