---
title: "Where is browsing history located?"
date: 2018-12-15
forum: Security
---

### Post by newlinux2 on 2018-12-15
I am using Ubuntu 16.04 with several browsers. Recently Chromium browser, version [COLOR=#5F6368][FONT=Roboto]71.0.3578.80,[/FONT][/COLOR] crashed and my browsing history from the last session disappeared. Restore session does not work, because even after I restarted Chromium, only the session before the last one was restored. I am thinking about using forensic software to recover browsing history, but I do not know where to look for the relevant files.

My chromium files are stored in ~/snap/chromium/538/.config/chromium/

---

### Post by TheFu on 2018-12-15
I don't use snaps.  They break some things and provide added security for others.
Normally, all data for any userid has been stored in the HOME.  Looking for chromium ... lead me to ~/.config/chromium/

~/.config/chromium/Default/Session Storage/ would be my best guess. Looking a little closer and it appears some of the data in PGP encrypted.

But when anything gets written from RAM to disk is completely up to the program, so any active information may not be flushed to disk during a crash situation.

---

