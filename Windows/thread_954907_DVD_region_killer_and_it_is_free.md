---
title: "DVD region killer and it is free"
date: 2008-10-21
forum: Windows
---

### Post by sdowney717 on 2008-10-21
[http://www.pcreview.co.uk/articles/Hardware/Make_your_DVD_drive_region_free/](http://www.pcreview.co.uk/articles/Hardware/Make_your_DVD_drive_region_free/)

just sharing this. it allowed my xp WMP to play dvd from region 1, MY REGION! on a player which is region free location 0.
apparently WMP does not let region zero players play discs even if the disc is from the same region as your OS.

---

### Post by jeyaganesh on 2009-02-11
Thanks!:guitar:

---

### Post by Izek on 2009-02-12
I'd rather not flash my CD/DVD Drive and possible take a chance of making it useless.

---

### Post by donkyhotay on 2009-02-12
Just use any open source DVD player (such as those that comes with most linux distro's) since no open source dev is stupid enough to include pointless 'features' like this in their software.

---

### Post by justsomedude on 2009-02-12
> **donkyhotay said:**
> Just use any open source DVD player (such as those that comes with most linux distro's) since no open source dev is stupid enough to include pointless 'features' like this in their software.

These restrictions are built into the drive's firmware and have nothing to do with the player you use it with.

---

### Post by Dr. C on 2009-02-12
> **donkyhotay said:**
> Just use any open source DVD player (such as those that comes with most linux distro's) since no open source dev is stupid enough to include pointless 'features' like this in their software.

Actually "malicious features", as RMS would say, such as region code enforcement can be included in FLOSS, but they can be easily removed so there in no point in including them in FLOSS in the first place. 

> *These restrictions are built into the drive's firmware and have nothing to do with the player you use it with.* 

This is only part of the picture. In order for the DRM to work and enforce the malicious features the player software will check the region on the DVD player against the region on the DVD. If they do not match the software will refuse to decrypt the DVD and refuse to play the movie. FLOSS players such as those commonly used on GNU / Linux work by cracking the DRM using software based on DeCSS and simply ignore the malicious region restrictions, so one can play out of region DVDs without any problem

By the way Microsoft has been back porting also the DRM in Vista to XP (in order to enforce malicious features) through Windows Media Player. So for example a commercial DVD (store purchased) from region 1 will no longer  play in a player from region 1 in a 5 year old computer, using Windows Media player. WMP produced an error saying "there is a problem with the copy protection" The reason Windows Media player no longer trusts the Video Card an Nvidia 7800 GS AGP and Viewsonic Monitor over vga. The solution is simple use the FLOSS VLC media player, crack the DRM and the DVD plays without any problems.

In reality there is really no need to mess around with the DVD player's firmware to deal with malicious DVD region restrictions. Replace the propriety DVD player with a FLOSS player in Windows one (this still works in Windows XP but there is no guarantee of the future) or even better get rid of Windows altogether and use GNU / Linux may turn out to be a much simpler solution.

---

### Post by donkyhotay on 2009-02-13
> **FineE said:**
> Actually "malicious features", as RMS would say, such as region code enforcement can be included in FLOSS, but they can be easily removed so there in no point in including them in FLOSS in the first place.

Exactly, no open source dev would be stupid enough to do it because if they did then someone else would just remove it. Also as mentioned previously you do *not* need to flash your hardware to bypass region encoding. I have a couple foreign films that can't be bought in the USA. They don't work in my regular DVD player but I just toss them in my ubuntu box, fire up VLC or Mplayer and enjoy them whenever I want. I've never flashed anything on my DVD drives. I don't have a windows box to test this but I'm certain doing the same thing with the windows version would work just fine.

---

