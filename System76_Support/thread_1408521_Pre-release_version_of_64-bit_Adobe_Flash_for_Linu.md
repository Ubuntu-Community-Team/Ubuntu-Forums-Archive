---
title: "Pre-release version of 64-bit Adobe Flash for Linux is out"
date: 2010-02-16
forum: System76 Support
---

### Post by samalex on 2010-02-16
Hello everyone,

I upgraded Flash on my PanP5 to the latest 64-bit Alpha version a month or so ago, and it's been running pretty good -- better than 32-bit using the wrapper anyway.  Today though I saw Adobe released a Pre-Release version that will hopefully make it more reliable.
[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Also Steven J. Vaughan-Nichols from ComputerWorld gives it [some good praises]("http://blogs.computerworld.com/64_bit_linux_adobe_flash_player_surprisingly_good"), so I'm anxious to check it out.  

I won't be able to do so until this evening, but I'll post back after I've installed it and ran some tests.

See ya --

Sam

---

### Post by llawwehttam on 2010-02-16
Thanks. I probably would never have noticed. I also agree that the alpha was very stable.

EDIT: Just tried it and the alpha2 is more stable than the pre-release.

---

### Post by Objekt on 2010-02-16
Wonder if they fixed the "dies occasionally for no apparent reason" bug?  I have been living with this one for a while.  Restarting Firefox will make Flash vids work again, but it's a pain when Firefox fails to quit properly (which is most of the time!).  Then I have to go into System Monitor to kill Firefox before restarting.

---

### Post by samalex on 2010-02-16
> **llawwehttam said:**
> Thanks. I probably would never have noticed. I also agree that the alpha was very stable.

EDIT: Just tried it and the alpha2 is more stable than the pre-release.

So in your tests the prior version is more stable?  If so what didn't work with this newer version?  I'll install it this evening, so just curious if we run into the same problems.

Sam

---

### Post by revlimiter on 2010-02-16
I grabbed the new one myself, tonight. It's impressive. 10.0 r45 is much more stable for me than 10.0 r42. I had flash vids playing in two tabs while I did a flash game on the third and had no problems. No lock up. No bad behavior. The game was smooth and both vids played and streamed happily. The processor oscillated between 800mhz and 1.6ghz. 

Thumbs up, says I.

---

### Post by samalex on 2010-02-17
I just installed it, and thus far it's working great.  I have Hulu playing Star Trek Generations (great first test!), Firefox has a YouTube video playing, and ustream is working both broadcasting from webcam and playing someone else's stream (Chris Pirillo Live).

No glitches thus far and processors are hanging at around 20% with all this with few spikes.

Thus far I'm impressed since uStream had become very unreliable on the prior version.

Cool! 

Sam

---

### Post by revlimiter on 2010-02-17
How do you get hulu to allow you to play videos? I haven't figured that out yet. I've not looked into it very deeply either. 

I had a crash. Whatever codec that photobucket uses for videos doesn't seem to agree with my system. Not a big deal since I can count on one hand the amount of times I've tried to watch something from photobucket. Still, a crash.

---

### Post by revlimiter on 2010-02-17
Nevermind. I got the hulu desktop .deb and installed it. [http://www.hulu.com/labs/hulu-desktop-linux](http://www.hulu.com/labs/hulu-desktop-linux)

Works great! CPU useage is fairly high at 60-70% of one core, but it plays fine. Even fullscreen hulu plays fine. No jitters or pauses.

---

### Post by samalex on 2010-02-17
> **revlimiter said:**
> How do you get hulu to allow you to play videos? I haven't figured that out yet. I've not looked into it very deeply either. 

I had a crash. Whatever codec that photobucket uses for videos doesn't seem to agree with my system. Not a big deal since I can count on one hand the amount of times I've tried to watch something from photobucket. Still, a crash.

If you're going to hulu.com it should use the Flash .so file you've put into ~/.mozilla/plugins/, but through Hulu Desktop there's a config file you'll need to edit and point it to the .so file (not on laptop now so can't remember config location).  I tried hulu.com through Firefox which worked fine, but I didn't test Hulu Desktop.  

Sam

---

