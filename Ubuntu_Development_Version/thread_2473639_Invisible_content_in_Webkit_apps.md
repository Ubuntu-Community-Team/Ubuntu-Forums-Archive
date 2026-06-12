---
title: "Invisible content in Webkit apps"
date: 2022-04-08
forum: Ubuntu Development Version
---

### Post by DuckHook on 2022-04-08
For those of us using Wayland in Jammy, there is a problem with webkit apps in which the app window is entirely blanked out. This will effect apps like Evolution, Epiphany, Yelp, gnome-online-accounts, etc.

A Launchpad bug has been opened: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1966418](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1966418)

In my case, the app where I first noticed it is Yelp. I like using Yelp instead of *man* because I can just click to invoke the next link (and I like the prettier output). However, starting a few weeks ago, every page shows fonts in the same colour as the background. The output is still present because a select&#8209;all&#8594;copy&#8594;paste works, and links are still clickable. Just can't see anything.

The workarounds are to either:

[list=1]
[*]Switch from Wayland back to X11 (which is not an acceptable solution for me), or
[*]Prepend: ```
WEBKIT_DISABLE_COMPOSITING_MODE=1
```…while invoking the app.
[/list]
It took some detective work to chase this one down, so I hope this thread saves someone some time and trouble.

If the bug effects you, please consider tagging it as such on Launchpad. I see that bug priority is already flagged as high, but it never hurts to alert the devs to just how many users are effected.

---

### Post by DuckHook on 2022-04-16
Looks like this bug has now been fixed. At least my yelp pages are presenting properly again. Workaround is no longer needed.

---

