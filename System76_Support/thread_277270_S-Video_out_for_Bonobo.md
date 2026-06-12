---
title: "S-Video out for Bonobo?"
date: 2006-10-14
forum: System76 Support
---

### Post by rapha on 2006-10-14
Hi all,

I've bought an S-Video-to-SCART cable for use with my Bonobo, but somehow can't seem to get anything out of it. The TV's SCART plug is working, as verified with an old VCR.

Is there some kind of tutorial somewhere? Couldn't find anything using Google :-/

Thanks and regards,
Raphael

**Edit:** found out about *fglrxconfig* (which seems to be named *aticonfig* for me) and got it to enable the TV Out. It now says: ```
rapha@bonobo:~$ aticonfig --query-monitor
  Connected monitors: lvds, tv
  Enabled monitors: lvds, tv

``` Unfortunately, there is still nothing appearing on the TV screen. Anything that I'm missing?

---

### Post by crichell on 2006-10-14
You may want to try to give YANC a try:

[http://www.ygriega.de/index.php?id=2&detail=1](http://www.ygriega.de/index.php?id=2&detail=1)

It was originally designed for nVidia cards but now also controls ATI cards.  We've been impressed with it.

---

### Post by rapha on 2006-10-14
HAH! The laptop was fine all the time! Turns out our TV has a slack joint and you have to hit it just the right way for SCART to work :-] ... YANC seems to be a nice tool still; another need for the terminal bites the dust.

---

### Post by sgtron on 2007-01-28
I tried using YANC with my Serval to get the S-video to work. 

First I had to install Java, then I downloaded the gzip file, gunzipped it and tar -xvf'd it.  Then I ran ./yanc via sudo in the terminal.

But then once YANC ran all I saw was a blank screen.  Then I replaced the .jar file with another from the website and it showed up.  This got me a bunch of settings that I will investigate with various output devices in the days ahead.

***UPDATE***

Ok, I don't own a projector, so I borrowed one.  I ran Yanc and now I can connect via VGA cable to the projector but no twin view.  I connect via S-video and get plenty twin-view.  

Is there some setting I'm missing to get this working right?

---

