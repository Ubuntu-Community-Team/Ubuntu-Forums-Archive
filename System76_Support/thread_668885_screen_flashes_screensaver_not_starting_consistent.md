---
title: "screen flashes/ screensaver not starting consistently"
date: 2008-01-15
forum: System76 Support
---

### Post by tuebinger on 2008-01-15
My screen has been flashing black for 1 second off and on.  Sometimes if I reboot the flashing goes away.  It's been an off and on problem for about a week and I don't know where to start to try and fix it. 

Also, my screensaver hasn't been starting consistently.  I have it set to random and to start after 5 minutes of inactivity.  Sometimes it comes on, sometimes it doesn't.  Sometimes the screen goes blank like it's going to start but then nothing..  I've tried playing around with the settings, setting it to different screensavers, and changing the start time, but nothing seems to work.

My model # is:  MS-1221

Thanks!

---

### Post by shae on 2008-01-16
I believe I am experiencing the same problem.  To check if DPMS is working try:
```
xset dpms force standby
```
```
xset dpms force off
```

---

### Post by thomasaaron on 2008-01-16
What level of desktop effects have you configured?
(System > Prefs > Appearnace > Visual Effects)

Try selecting None. Does that stop the problem?

---

### Post by palintheus on 2008-01-16
By default the desktop effects will not work on the daru2 due to the intel GMA graphics.

---

### Post by tuebinger on 2008-01-16
> **thomasaaron said:**
> What level of desktop effects have you configured?
(System > Prefs > Appearnace > Visual Effects)

Try selecting None. Does that stop the problem?

I have visual effects set to 'none'.  I tried to set them to either normal or extra but the notification window said 'Desktop effects could not be enabled'.  Should I be able to enable them? 

 Last night  the screensaver  started working again and it has stopped flashing black.  It's behaving normally today so far -- no black flashes and screensaver is coming on.  EDIT:  Screensaver is no longer coming on and this is occuring after unplugging and moving the computer. Screen goes dark but no screensaver.   Can unplugging the computer have something to do with it?

---

### Post by tuebinger on 2008-01-16
> **shae said:**
> I believe I am experiencing the same problem.  To check if DPMS is working try:
```
xset dpms force standby
```
```
xset dpms force off
```

I tried these commands.  The DPMS seems to be working.

---

### Post by thomasaaron on 2008-01-17
Go to System > Prefs > Screensaver.
There is a BLANK screensaver (which is just a black screen). That may be what you are seeing?

You can enable the desktop effects on your DarU2 by following these instructions:
[http://knowledge76.com/index.php/GutsyCompizIntelX3100](http://knowledge76.com/index.php/GutsyCompizIntelX3100)

---

### Post by tuebinger on 2008-01-17
something unexpected happened last night.  I followed your directions in the Wiki for enabling the desktop effects.  Since I did that the screensaver seemed to be functioning correctly again.  It was coming on consisitently, even when the computer was unplugged.  I thought this had solved the problem. However, this morning the screensaver isn't coming on when the computer is unplugged -- the screen goes blank but no screensaver starts.  Only when it is plugged in does the screensaver operate normally.  There have been no black screen flashes since my first post two days ago.

---

### Post by thomasaaron on 2008-01-18
Go to System > Prefs > Power, click the "On Battery" tab and tell me what your settings are. My guess is that the problem is there.

---

### Post by tuebinger on 2008-01-18
My prefs for 'on battery' are as follows:

ACTIONS:
Put computer to sleep when inactive for:  slider set to 'never'
When laptop lid is closed:  blank screen
When battery power is critically low:  shutdown
DISPLAY
Put display to sleep when inactive for: slider set to 'never'
Dim display brightness by:  slider set to '0%'
'Dim dsplay when idle' box is unchecked.

---

### Post by wheezer on 2008-01-19
Anxiously waiting for comments on this.  My screen save is black too.  But when i move the mouse, the active screen saver flashes for just a split second, and then my desktop returns.  I am using ATI x1600 radeon card, with no desktop effects, and have the same power settings as  the user above.

Very frustrating.

---

### Post by thomasaaron on 2008-01-21
OK. I'll be imaging an ms-1221 today. I'll let you know what I find.

---

### Post by thomasaaron on 2008-01-23
So here's what I found.

When I'm on battery power, regardless of how I configure my screensaver (Random, blank, anything else), the screen always goes black when it is time for the screensaver to come on. Then, when I touch the mousepad or a key, the blank screensaver (that's what it is) goes off, and I'm back to my desktop.

On A/C, whatever screensaver I've set up will run.

Here's the clincher:
It happens on other computers as well. I've got to do some more research on it to see if there is a way around it. But it looks like that is what is supposed to happen. (Either that, or it may be an Ubuntu bug.) I'm guessing the reasoning is: Why use the extra power for graphics when the computer is on battery and not being used.

---

### Post by thomasaaron on 2008-01-23
Also, the screensaver works in battery mode if you disable Gnome Power Manager in System > Prefs > Sessions and reboot.

---

### Post by tuebinger on 2008-01-23
Thanks for researching this for me!  Sounds like I'll just have to live without the screensaver when it's unplugged :(... no biggie, though.  I'm just glad it wasn't anything serious.

---

