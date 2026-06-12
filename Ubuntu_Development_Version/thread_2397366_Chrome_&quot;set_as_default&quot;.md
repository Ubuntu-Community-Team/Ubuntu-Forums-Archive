---
title: "Chrome &quot;set as default&quot;"
date: 2018-07-28
forum: Ubuntu Development Version
---

### Post by VMC on 2018-07-28
This only happens with lubuntu LXQT 18.10. And it doesn't always happen. When I install chrome and run it. The first thing it asks, is set as default. Which I usually do.
Then go to settings "Default browser. If it shows "MAKE DEFAULT" on the far right, then it will **always** ask to set as default when chrome is started.
 The attachment shows both with and without "MAKE DEFAULT". 

I've deleted google-chrome from .config. Restarted. Didn't help. Went into advance settings, looking for DEFAULT. Nothing found.

---

### Post by VMC on 2018-07-28
I'll mark this as solved. Reason. I tried all sorts of "tricks". I copied xubuntu "~/.config/google-chrome" to lubuntu. Same result. Searching using "chrome://about" That didn't work. Then I realized that Falken was still installed.
After removing Falken, I also re-installed chrome. This time The above left attached picture appeared without the "DEFAULT BROWSER". I'm thinking that Falken is based on chrome, so the real chrome gets confused (like I am now).

As I stated, it only happens on Lubuntu-LXQT. It didn't happen on any distro that use Firefox.

---

### Post by faure212 on 2019-02-08
I have the same issue with Lubuntu 18.10 with LXQt.  I set Chrome to the default in the Session settings (under Default applications), but when I am not looking (or perhaps during an update?), it changes back to Firefox.  How can I make it stick?

---

### Post by IanW on 2019-02-08
> **faure212 said:**
> I have the same issue with Lubuntu 18.10 with LXQt.  I set Chrome to the default in the Session settings (under Default applications), but when I am not looking (or perhaps during an update?), it changes back to Firefox.  How can I make it stick?

Uninstall Firefox?

---

### Post by slickymaster on 2019-02-08
18.10 is long released.

Thread closed

---

