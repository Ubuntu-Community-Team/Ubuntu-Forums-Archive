---
title: "Starling sleep/standby/suspend oddity[0]: Fn-F1 fails from main login screen"
date: 2010-01-11
forum: System76 Support
---

### Post by tlroche on 2010-01-11
I'm using a nearly-new Starling (model=star1, ubuntu=UNR 9.04), not much customized except that I used gconf-editor to make it show the screenlock GINA (i.e. the screenlocker login "window" with the buttons) on resume: see [this post]("http://ubuntuforums.org/showpost.php?p=8571646&postcount=3") for details.

I mostly use the Fn-F1 keychord to sleep the Starling, but cannot in one case. If I first logout, then hit Fn-F1 while in the "main" GINA (the fullscreen one, with the "Username:" dialog), nothing happens. If I want to sleep the Starling while @ the main GINA, I need to start the "Options" menu (Alt-t, or click on lower left corner of GINA), and choose "Suspend" (which unfortunately lacks a keyboard). Is there a way to enable Fn-F1 from the main GINA?

---

### Post by thomasaaron on 2010-01-11
Hmmm... the Fn-F1 hotkeys may not be activated prior to gdm starting (which happens after you log in). I'll dig into it a bit and see what I can find.

---

### Post by tlroche on 2010-01-23
> **tlroche said:**
> I mostly use the Fn-F1 keychord to sleep the Starling, but cannot in one case. If I first logout, then hit Fn-F1 while in the "main" GINA (the fullscreen one, with the "Username:" dialog), nothing happens.

That's in jaunty. In karmic, Fn-F1 works from the login screen, too.

---

