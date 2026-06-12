---
title: "[SOLVED] Flash video at espn.com stopped working"
date: 2008-10-15
forum: The Cafe
---

### Post by laser_in_your_eye on 2008-10-15
I'm not sure what happened, but I noticed a couple of weeks ago that I can no longer play any flash video at espn.com (using Firefox on Hardy).  Video on youtube, etc. works fine.  Anyone else seen this?  I was able to get espn.com video working by running Firefox in Wine, but that seems like a pretty stupid approach.

Thanks

---

### Post by SunnyRabbiera on 2008-10-15
ESPN works for me, perhaps you need to try flash 10 out, also try user agent switcher

---

### Post by Daisuke_Aramaki on 2008-10-15
works here as well man! as suggested install flash 10 and see if it runs! on a related note, i cannot get the comedy central vdos running, no matter what i try! :(i can play the cc videos when they are embedded on another website, but i couldn't get them to play from their website! :(

---

### Post by SunnyRabbiera on 2008-10-15
I think both check if you have firefox for windows, to trick them use this:
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by laser_in_your_eye on 2008-10-15
Thanks for the suggestions, but I've still got issues.  I actually installed flash 10 this morning to try and circumvent the problem with no luck.  I tried the User Agent Switcher too with no luck.

---

### Post by laser_in_your_eye on 2008-10-15
> **Daisuke_Aramaki said:**
> works here as well man! as suggested install flash 10 and see if it runs! on a related note, i cannot get the comedy central vdos running, no matter what i try! :(i can play the cc videos when they are embedded on another website, but i couldn't get them to play from their website! :(

I just tried comedy central and it works fine for me.  Go figure.  Wish I could switch you...

---

### Post by Daisuke_Aramaki on 2008-10-15
> **laser_in_your_eye said:**
> I just tried comedy central and it works fine for me.  Go figure.  Wish I could switch you...

wud be glad to make the switch! :guitar: i tried useragent switcher long time back after some suggestions to circumvent the problem, but never worked, and still doesn't!

---

### Post by laser_in_your_eye on 2008-10-18
Just in case anyone else ever has this problem, I finally tracked down the issue.  It looks like the Adblock extension in firefox was conflicting with espn.com so that video never started.  Once I reset the filters in the extension, video came back.

---

### Post by laser_in_your_eye on 2008-10-19
> **laser_in_your_eye said:**
> Just in case anyone else ever has this problem, I finally tracked down the issue.  It looks like the Adblock extension in firefox was conflicting with espn.com so that video never started.  Once I reset the filters in the extension, video came back.

Scratch that.  Resetting the filters only worked one time, then the video went away again.  After more digging, though, this does appear to be a problem with adblock.  I added the following exception (*Tools/AdBlock Plus/Add Filter*) and video is back (most of the other ads are still blocked, thankfully):

[COLOR="Blue"]"@@|http://sports.espn.go.com/broadband/video/videopage"[/COLOR]  (without the quotes!)

---

