---
title: "Suggestion for the Desktop environment"
date: 2017-07-06
forum: Ubuntu Development Version
---

### Post by bask185 on 2017-07-06
When working with Ubuntu (16.04) there are 2 small features I really miss. I miss the go-to-desktop button in the menu bar (the bar with the apps etc). And if I click on chromium, it opens like it should but if I click it again, it does not minimalize like I would like it to.

It are minor thingies ofc. But it would be neat features for a future update.

---

### Post by again? on 2017-07-06
In *system settings > appearance > behaviour*  
you can add a show desktop button to the launcher.
ctrl+Super+d should also show the desktop. (Super is the windows key)

In a terminal run this code to make the launcher icons minimize applications.
```
dconf write /org/compiz/profiles/unity/plugins/unityshell/launcher-minimize-window true
```

---

### Post by Bucky Ball on 2017-07-06
I press control+alt+'d' (at same time) to go to desktop. Not sure if that works with Unity. Give it a try. You can also alt+tab to scroll through whatever you have open.

This is the place to post to discuss and get support for the in-development 17.10 release and beyond. Not the ideal place to suggest future improvements to devs. Ubuntu devs don't visit here. Approach them directly if you are wanting to be heard by them. ;)

---

### Post by bask185 on 2017-07-11
> **guber2 said:**
> In *system settings > appearance > behaviour*  
you can add a show desktop button to the launcher.
ctrl+Super+d should also show the desktop. (Super is the windows key)

In a terminal run this code to make the launcher icons minimize applications.
```
dconf write /org/compiz/profiles/unity/plugins/unityshell/launcher-minimize-window true
```
Thanks, I added the shortcut and tried Ctrl, windows and D. That also seems to work.

I tried Ctrl, alt, D but that adds bookmarks to Chromium :p

---

