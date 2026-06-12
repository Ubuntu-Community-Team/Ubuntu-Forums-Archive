---
title: "Compiz not behaving with QT apps?"
date: 2013-03-03
forum: Ubuntu Development Version
---

### Post by screaminj3sus on 2013-03-03
Is anyone else seeing this? When I use any QT apps such as VLC or Smplayer compiz acts extremely buggy. Whenever I right click in a qt app for a context menu it shows up in the unity launcher as another window (and when I was in xfce with compiz it showed up in the taskbar as "untitled window"). In addition the floating fullscreen controls in both apps are totally borked and don't even work half the time under compiz (and sometimes you see flashes of the unity desktop when you try to bring them up.) The other issue I saw is in QT apps sometimes menus come up as invisible until you restart the application (doesn't happen if using unity with global menu, but does happen with global menu disabled and in xfce).

I put in bug report here, please up the heat if you are seeing this! Apps like vlc and smplayer are unusable under compiz right now! I was also able to replicate the issue with a fresh install.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1141079](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1141079)

This only started happening somewhat recently (not sure exactly when, but it used to be fine in raring)

---

### Post by mc4man on 2013-03-03
try installing libgnome2-common & see if they behave any better
(no issue here with ^ & qt apps on an Ubuntu install, ubuntu session

If better then 
[https://bugs.launchpad.net/bugs/1094360](https://bugs.launchpad.net/bugs/1094360)

---

### Post by screaminj3sus on 2013-03-03
> **mc4man said:**
> try installing libgnome2-common & see if they behave any better
(no issue here with ^ & qt apps on an Ubuntu install, ubuntu session

If better then 
[https://bugs.launchpad.net/bugs/1094360](https://bugs.launchpad.net/bugs/1094360)

Tried installing that and rebooting, that didn't change anything. At first I thought it was just something with my install or something to do with running xfce with compiz, so I downloaded a fresh ubuntu/unity raring iso and clean installed and saw the same issues (when you right click on vlc or smplayer you see that the unity launcher now shows two windows are open for that application, and if you go fullscreen and try to use the controls it glitched out)

This is a pretty bad regression this late in the cycle!

---

### Post by mc4man on 2013-03-03
Only once had an issue with vlc fullscreen not exposing controls, generally works fine.
While i use plank don't see any issue in a vlc unity launcher quicklist, if the playlist is docked only 1, if undocked then 2 which is expected.
(I only allow 1 instance of vlc - so no chance of a 2nd instance running, with or without visible window

As far as menu dropdowns - can occasionally cause some of the menus not to drop, though here I don't use the global menu with media players, keep them in the player window

---

### Post by screaminj3sus on 2013-03-03
> **mc4man said:**
> Only once had an issue with vlc fullscreen not exposing controls, generally works fine.
While i use plank don't see any issue in a vlc unity launcher quicklist, if the playlist is docked only 1, if undocked then 2 which is expected.
(I only allow 1 instance of vlc - so no chance of a 2nd instance running, with or without visible window

As far as menu dropdowns - can occasionally cause some of the menus not to drop, though here I don't use the global menu with media players, keep them in the player window

The disappearing menus only happens to me *without* the global menu, when I have global menu disabled so they are in the player window like you have them thats when I get the annoying invisible menus

---

### Post by screaminj3sus on 2013-03-03
Here's a video: I wasn't able to replicate the vlc fullscreen screwing up with xfce + compiz, that seemed to only happen in unity for some reason, but you can definitely see the other issues clearly: [http://www.youtube.com/watch?v=eTOAHeOwdko&feature=youtu.be](http://www.youtube.com/watch?v=eTOAHeOwdko&feature=youtu.be)

---

### Post by mc4man on 2013-03-03
The 'tools' one does seem to be one that's likely to become non-functional at times, also 'help'
don't see any errors/warnings anywhere

By-passing the global may be considered a 'non-supported' action...

---

### Post by screaminj3sus on 2013-03-03
> **mc4man said:**
> 
By-passing the global may be considered a 'non-supported' action...

Even if ubuntu uses global menus by default, rendering menus in all major toolkits correctly is a pretty basic function of a window manager and is something that really shouldn't be broken!

---

### Post by mc4man on 2013-03-03
Now I see what you mean by '2' windows in launcher icon (wasn't as obvious in plank

Here only see on context menu sub-menus & it sorta stops after a once-over per submenu
As far as this & the in window menus not working - 

When it started not sure, there are a lot of daily's in the last several weeks

Edit: caused by something in r3606 (rather large commit

---

