---
title: "Jack"
date: 2008-05-30
forum: Ubuntu Studio
---

### Post by dwally89 on 2008-05-30
Hi,

I have downloaded the ubuntustudio-audio package and am trying to do basic home recording.

When I launch JACK Control, and start it, I get loads of xruns.

I think the problem must be to do with my settings.

Can someone please advise me with what settings to use?

I am using a Dell Inspiron 6400, with 2GB of RAM, and the onboard soundcard and ALSA.

Thanks

---

### Post by ventrinal on 2008-05-30
My thoughts don’t collide exactly with what you say….but anyways…..every one has its own way!!!!

---

### Post by dwally89 on 2008-05-30
???

---

### Post by thorgal on 2008-05-30
never mind ventrinal's reply, that guy is most likely fake. All his messages are just generic BS. His signature contains a commercial link. I reported him to the admins.

---

### Post by dwally89 on 2008-05-30
OK thanks.

Any ideas how to solve my problem?

---

### Post by thorgal on 2008-05-30
not with so little info. But I don't have time to guide you in this matter.
May I redirect you to this link ? [http://ubuntuforums.org/showthread.php?t=781105](http://ubuntuforums.org/showthread.php?t=781105)

It's a thread started by a guy who would like to get the best performance out of his laptop to play some virtual piano. I guided him through quite a lot in terms of system tweaking. It will not be visible at the 1st reading but  there are plenty of elements relevant for ubuntu that you may try.

There are other threads and wiki articles more jack / system specific but I never used them so I cannot point you to them. I am a debian user, not ubuntu.

---

### Post by dwally89 on 2008-05-30
> **thorgal said:**
> not with so little info. But I don't have time to guide you in this matter.
May I redirect you to this link ? [http://ubuntuforums.org/showthread.php?t=781105](http://ubuntuforums.org/showthread.php?t=781105)

It's a thread started by a guy who would like to get the best performance out of his laptop to play some virtual piano. I guided him through quite a lot in terms of system tweaking. It will not be visible at the 1st reading but  there are plenty of elements relevant for ubuntu that you may try.

There are other threads and wiki articles more jack / system specific but I never used them so I cannot point you to them. I am a debian user, not ubuntu.


Thanks for the link.

I've searched the forums, and the internet (before posting this thread, and cannot seem to find anything that helps.

I am still relatively knew to Ubuntu.

Does anyone know how to reduce the number of xruns in JACK then?

Thanks

---

### Post by Bungo Pony on 2008-05-30
Put a real sound card in instead of using the onboard. That's what solved all my problems.

....but created some interesting new ones. Some apps will work with one sound card, but will not work with the other. I had to build a switchbox to switch between the two cards.

Ubuntu is going through a sound restructure right now with Pulse Audio, and it really sucks. I had everything working (almost) perfectly in Gutsy, and then they changed everything. :(

---

### Post by Dark Horse on 2008-05-30
This is a screen shot of My current Jack settings:[ATTACH]72260[/ATTACH]
Hope this helps I get few or no xruns although the latency is a little high but has not been an issue for anything I've been doing with it. also I am running Ubuntu Studio with the rt Kernel that might matter.
You will have to fiddle with the settings until you find some that work for you the exact settings will vary depending on your hardware. (Sound card,processor, memory,etc.) There was a tutorial off the Jack website I don't know the URL right now.
Good luck
  Mark  :)

---

### Post by Stochastic on 2008-05-31
Dark Horse, I'd HIGHLY recommend turning on the realtime option in your jack settings (but then again YMMV).

dwally89, you really will just need to go through trial and error to find the best settings for your card.  I would like to mention that onboard soundcards are known to be very low quality, and often more trouble than they're worth, when it comes to pro-audio.

---

### Post by Dark Horse on 2008-05-31
You're Right that should be checked although It did not effect the xrun issue 
and it is now. Some of us ca not afford to go buy a pro sound card and a good stereo input is enough if you're not doing pro work If or when the opportunity presents its self I would certainly take one. :wink:
Mark

---

### Post by Drunky on 2008-06-01
> **dwally89 said:**
> Hi,

I have downloaded the ubuntustudio-audio package and am trying to do basic home recording.

When I launch JACK Control, and start it, I get loads of xruns.

I think the problem must be to do with my settings.

Can someone please advise me with what settings to use?

I am using a Dell Inspiron 6400, with 2GB of RAM, and the onboard soundcard and ALSA.

Thanks

This Ubuntu Help page is, well, helpful :)
[HowToJACKConfiguration]("https://help.ubuntu.com/community/HowToJACKConfiguration")

Make sure your sample rate matches the on-board audio...some are at 48K and some are 44.1K.

To help reduce xruns, I would first increase Frames/Period and then increase Periods per Buffer.

I hope this helps.

Regards.

---

