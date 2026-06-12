---
title: "Screensaver menue causes caleidoscope-like display breakdown, unable to revert."
date: 2009-07-17
forum: System76 Support
---

### Post by nanonils on 2009-07-17
I recently chose "Enthusiasm" as my screensaver on my hot new WildDog. My graphics card is a 512 MB ATI Radeon 4830 PCI-Express x16 GDDR3 (2 x DVI, S-Video, DVI to HDMI, DVI to VGA).

I can attest that I'm anything but enthusiastic as a result: immediately when moving to the selection in the Gnome screensaver menu, the screen degraded into an odd caleidoscope-like fragmentation of the entire screen where some windows were displayed way above, to the right or left making it impossible to see what to click and choose. Worse, there is some sort of transparency to all and ghosting. 

There is no way out of that mess other than a hard reset or with "dontzap" (now that I've enabled it).

Problem is, I can't figure out how to choose a different screensaver. As soon as I open the screensaver menu the mess starts again. My screensaver activates after 30 minutes inactivity. 

There are some old ways of deleting a troubling screensaver with system tools, configuration editor but I think as of some recent Ubuntu versions this is fully integrated. 

Thanks for your help!

---

### Post by gila_monster on 2009-07-17
It may not be the screensaver. I am currently conversing (sort of) with Tom Aaron about a similar problem I am having with my Pangolin. I have seen the kaleidoscope problem twice now. (Your description seems better than my "technicolor barf" description.) The first time, it was horrible, and I had to do a hard reset. The second time, I was able to recover without a reboot with ctrl-alt-backspace.

I have also had trouble with gdm resetting at random (I'll try to post a link to that thread here in a moment). I believe the are related. When we first started investigating that problem, the log file indicated that the screensaver had disengaged from from gdm. Tom and I weren't sure whether the screensaver caused gdm to crash, or that the gdm crash just raised the screensaver warning. So I turned off the screensaver (just set it to blank the screen), and I had another crash later. So this might not actually be a screensaver problem, but something a little more complex.

I haven't had this problem with any machine except this one under Jaunty. I am starting to suspect that something happened during a recent upgrade that might be causing problems. Thus far, I've seen it on Jaunty, with and without screensavers, and on Linux Mint (which is based on Jaunty, so that might not be significant). About the only thing I have left to try is to nuke the GNOME configuration directories in case there is some cruft causing a problem. I wouldn't think so, though, since the Pangolin is less than a year old and I started with a fresh desktop then.

I use my box pretty heavily, so I'm very concerned about the uptime. Fortunately, I do regular backups.

One thing I mentioned to Tom by email is that I changed over to IMAP for my email in the past couple of weeks, which is when this has been a serious problem. I doubt that's the cause, though, and I did get one crash about six weeks ago before I switched to IMAP. So don't read much into that.

I'm sure we'll have an "aha" moment soon and get to the bottom of this.

---

### Post by thomasaaron on 2009-07-17
Try turning off your desktop effects...

System > Prefs > Appearance > Visual Effects > None

...and then going to System > Prefs > Screensaver and changing your screensaver.

On that note, I don't see an "Enthusiasm" in my screensaver list. Where did you get that? It could be buggy.

---

### Post by nanonils on 2009-07-17
> **thomasaaron said:**
> Try turning off your desktop effects...

System > Prefs > Appearance > Visual Effects > None

...and then going to System > Prefs > Screensaver and changing your screensaver.

On that note, I don't see an "Enthusiasm" in my screensaver list. Where did you get that? It could be buggy.


Thomas, you've nailed it! I can now browse through all screensavers without problem. And actually, Enthusiasm is "Euphoria". When I posted I simply couldn't read the names anymmore so that's what I recalled. When I run Euphoria now, it's all fine. 

Thanks much!

---

### Post by gila_monster on 2009-07-17
> **nanonils said:**
> Thomas, you've nailed it!

He usually does. :)


> I can now browse through all screensavers without problem. And actually, Enthusiasm is "Euphoria". When I posted I simply couldn't read the names anymmore so that's what I recalled. When I run Euphoria now, it's all fine.

nanonils, I'm glad this worked for you. Didn't work for me, though, so you can disregard the earlier post -- maybe we DON'T have the same problem!

---

### Post by caffeine_robot on 2009-08-22
Genius! Thanks Thomas this fixed it for me aswell.

---

