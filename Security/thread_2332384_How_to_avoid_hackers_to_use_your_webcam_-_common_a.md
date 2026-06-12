---
title: "How to avoid hackers to use your webcam - common and easy hack!"
date: 2016-07-31
forum: Security
---

### Post by patrikmellq on 2016-07-31
In Sweden we could read on MSN that is so easy to hack a webcam and see other pepoles home and what they do, so what is the solution?
Put something infront of camera so you get not see or can you passwordprotect your webcam with some kind of Ubuntu software?

Cheers

---

### Post by TheFu on 2016-07-31
Good reminder ... this has been known for a long time.  [https://www.wired.com/2014/03/webcams-mics/](https://www.wired.com/2014/03/webcams-mics/) and security people have covered cameras since first introduced.

I use black electrical tape as a tab (folded half over itself to keep the goo off the lens.

But ... the microphone is just as easy to hack, so how do you block those sounds from being picked up?  Most laptops have a combined mic/headphone jack which disables the built-in microphone. By just plugging any earphones into the jack, that might switch the microphone to the jack.  It doesn't always work.

Everyone should understand that the camera working and the light being on are 2 separate things. They aren't tied together, it is just convention that nice programmers use to provide visual feedback.

Don't forget that smart TVs are listening too.  Advertisers have been using sonic feedback from TV with their websites to track when we watch TV and browse to their websites. [http://www.consumerreports.org/cro/news/2015/03/how-to-turn-off-smart-tv-features-that-invade-privacy/index.htm](http://www.consumerreports.org/cro/news/2015/03/how-to-turn-off-smart-tv-features-that-invade-privacy/index.htm)

And don't forget that bluetooth is very weak. Basically, there isn't any real security in bluetooth.

Be aware that everything we do is being tracked unless we take steps to prevent this.

---

### Post by patrikmellq on 2016-07-31
Question - what happens i use hide ip with crypted tunnel - is it still easy to hack the webcam?

Cheers

---

### Post by TheFu on 2016-07-31
> **patrikmellq said:**
> Question - what happens i use hide ip with crypted tunnel - is it still easy to hack the webcam?

Cheers

Depends on the type of tunnel. Some are 2-way.  The system may be self-reporting back to a C&C setup using all sorts of methods (image-bug, IRC, or just visiting any URL you or I can imaging with some tiny script (it is 2 lines in perl) or wget or lynx or curl, or ..... infinite ways.  These scripts could as easily provide a reverse ssh proxy.

My VPN, which I run out of my home for **my** convenience, is 2-way.  A VPN provider I use, has 1-way, but I or someone else with 5 sec access to my PC could break that.  If you work in public spaces, like a coffee shop, could someone plug in a USB drive for 5 seconds?  If so, they could own the computer enough to setup a reverse proxy.

Should be common knowledge by now, but stick with L2TP and IPSec VPNs.  These are NOT the default for most services I've seen.

If you are a high-valid target, then your OPSEC needs to match the attacker.  Even people which a strong need for OPSEC don't always get it right. There are a few stories about the CIA getting caught doing things they shouldn't outside the USA due to poor OPSEC. Read about a child-porn group that was monitored by 3+ countries and 1/3rd of them were caught due to poor OPSEC. This group KNEW they needed to be perfect, yet not all of them were.  There's an FBI podcast about it and what they did.  TOR was prominent in the solution, but TOR alone isn't sufficient. They used some tricks to get the group's PCs to report their real IP back to law enforcement.  Good OPSEC is hard.  I'm not 100% positive I could do it correctly and 1 tiny mistake is all it requires. Some mistakes wouldn't really be within most people's control. After all, would you only use a minimal web browser all the time - something like Lynx?

Ok ... so now that everyone is paranoid, we need to understand that running Linux and not using flash or javascript or java will stop almost all the sorts of people we would run into ... unless we do something stupid like join a WebRTC conference and forget to shut it down when done or use any video conferencing software and don't verify the process is off when we are done.

IMHO.  OTOH, what do I know?  I've never tried to spy on someone's webcam and it honestly isn't much of a concern to me - put the electrical tape over mine years ago. ;) If I want a webcam, I'll plug in a Logitech C920 with is very nice for audio and video. Didn't always work well with Linux, but 16.04 seems to have made it stable in my testing. With prior versions, it didn't work at all or would only work 20 min at a time. I think google's chromeOS is to thank for this. Lots of vloggers use both Chromebooks and a C920 webcam, so Logitech was forced to help/allow Linux devs to make it work well.

Sorry for going off topic.

---

