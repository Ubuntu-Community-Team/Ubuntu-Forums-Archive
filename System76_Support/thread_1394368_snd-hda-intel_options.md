---
title: "snd-hda-intel options"
date: 2010-01-30
forum: System76 Support
---

### Post by dabrowsa on 2010-01-30
What are the correct options for the snd-hda-intel module in /etc/modprobe.d/alsa-base.conf?

I ordered a wild dog  last Oct, arrived early Nov, Order #8945.  

64 bit, quad core, Ubuntu 9.10.

audio card:
Card: HDA Intel
Chip: IDT 92HD73E1X5

alsa device id: STAC92xx

From many other posts I've read, it seems that the default options

  options snd-hda-intel power_save=10 power_save_controller=N

don't work well.  In particular I can't get sound-in to work.  The mic doesn't work and line-in doesn't even show up in pavucontrol unless I change the line above to

  options snd-hda-intel model=ref

and I'm not even sure what "ref" means.  

What's the correct setting for the card that System76 shipped?

For the record, I've tried...

...loading module-loopback (that worked last month but not now)
...adjusting every possible setting in alsamixer
...ditto for pavucontrol
...purging pulseaudio and alsa and then re-installing
...removing pulseaudio and trying alsa alone
...and probably some other stuff I can no longer remember.

:mad:

I'm disgusted with Ubuntu.  I've spent hours trying to get one simple feature, that had been operational for years in my other linux boxes, working in my brand spanking new computer, and it's like 1998 all over again.  It seems like ease of configuration has not improved in 12 years.  

I'm this close <holds up hand as if pressing one thin dime between forefinger and thumb> to installing Vista.  Sure, it's got plenty of its own problems, but at least its audio jacks work.

Please save me before I do anything drastic.

---

### Post by Odd-rationale on 2010-01-31
This forum post has a list of many sound card model options. I was able to fix my problem by finding the correct model to use with my card:

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Good luck!

---

### Post by dabrowsa on 2010-01-31
Thanks for the link O-r, but did you notice that System76 isn't mentioned anywhere on that page?  I guess I could try, one at a time, all 200 options lines posted there and other similar pages that google turned up...

But I thought, perhaps naively, that a System76 techie could tell me exactly how to configure the machine they sold me a few months ago.

---

### Post by dabrowsa on 2010-01-31
OK, I've got line-in working.  Audio is now broken in firefox and google-chrome, though.

I updated alsa using the script at [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137).

In alsa-base.conf I used the simple "options snd-hda-intel index=0 model=ref".

---

### Post by Eldera on 2010-01-31
[quote=dabrowsa]But I thought, perhaps naively, that a System76 techie could tell me exactly how to configure the machine they sold me a few months ago.[/quote]

Wait at least until Monday morning (Denver time) and see if S76 has some more specific information. This forum is pretty quiet on the weekends.

Have a great day. Eldera

Edit: Sorry to get the posts out of sequence. dabrowsa must have been posting at the same time I was and he/she typed faster.

---

### Post by thomasaaron on 2010-02-01
Are you still using xfce, as you were here...
[http://ubuntuforums.org/showthread.php?t=1360514&highlight=wild+dog+mic&page=2](http://ubuntuforums.org/showthread.php?t=1360514&highlight=wild+dog+mic&page=2)

---

### Post by dabrowsa on 2010-02-01
Hi Tom,

I'm willing to try anything.  I'd been using Gnome to troubleshoot this problem, but now I'm using KDE.

To fix the audio problem in firefox and chrome I eventually resorted to removing pulseaudio from my system.  That breaks Gnome, so now KDE is my desktop of choice.

Incidentally, removing pulse fixed the browser problem, but without pulse I could no longer use the pulse loopback to redirect the line-in to line-out.  So it took another 2 hours of googling to come up with similar solutions using alsa alone.  I finally settled on

arecord -f cd -D hw:0 | aplay -f cd

but I can't believe this is optimal.

---

### Post by thomasaaron on 2010-02-02
Honestly, I'm not set up at all to troubleshoot via anything but gnome. We just don't have the bandwidth and time to explore KDE and xfce.

It looked in that other thread like you got your problem solved, but at this point, I'm not really sure what the problem is anymore! These threads get pretty ungainly to track once they get a few pages long.

The way the computer arrives, it should support pretty much all of the audio functionality. (Although I'm sure there are some desired usages that we either do not think of, or are unable to test.)

To answer the question of this thread, we don't add anything to the alsa-base.conf file. The Wild Dog uses the alsa-base.conf file that comes stock with a standard Ubuntu install.

If you like, I can image a wild dog with a fresh 9.10 64-bit Ubuntu installation and post the alsa-base file here.

---

### Post by dabrowsa on 2010-02-02
Gnome is fine with me.

My problem is that I can't get line-in to work with pulseaudio.  In the earlier thread I mentioned I had found a work-around, using the mic jack instead, but the line-in problem was never resolved.

I hope you don't mean that that plugging an audio cable into the line-in jack is one of those "desired usages that we either do not think of, or are unable to test".

Is it possible that System76 made a poor choice of the audio card to use?

---

### Post by thomasaaron on 2010-02-02
> I hope you don't mean that that plugging an audio cable into the line-in jack is one of those "desired usages that we either do not think of, or are unable to test".

That's definitely not something we test with. I will, however, pass it to R&D for their consideration. It definitely seems like a usage that would be common and useful. Although, it's interesting that there are precious few mentions of it with our systems.

> Is it possible that System76 made a poor choice of the audio card to use? 

I don't know if I'd characterize it that way. We don't choose a sound card per se. Sound is integrated into all of our mobos, and the mobos have to pass certain basic tests under Ubuntu for them to be accepted. But, like I said, you're particular issue definitely isn't part of our testing. And even if it were, I'm not sure a lack of that particular functionality would be a deal-breaker for us. But information on whether or not it works should indeed be available to customers.

Right now, my gut feeling is that the problem is more likely a configuration issue or a pulseaudio/ALSA deficiency that will eventually be worked out by those projects.

In the meantime, though, I'll get a Wild Dog built (mine is in pieces all over the bench) and imaged and post the alsa-base.conf file. Then, I'll play around with it and see if I can get it working.

Right now, we are in a crunch-phase for squashing a few different bugs, so this may take a few days. But I'm adding this issue to the list. I hope that is helpful.

---

### Post by dabrowsa on 2010-02-02
Thanks for your response.  

The standard options line in /etc/modprobe.d/alsa-base.conf for this card seems to be:

options snd-hda-intel power_save=10 power_save_controller=N

which seems very environmentally conscientious but doesn't manage the card properly.



I would think this sound card jacks issue would be a deal breaker for any users like me who are interested in music creation.  I was certainly very disappointed to discover I was going to have to spend hours and hours fiddling with system config issues just to record audio.  I was used to those horrors with converted windows machines, but I thought buying a System76 box would mean smooth sailing.  I'm a bit dismayed to learn that System76 apparently doesn't consider it very important that all hardware work out of the box.

It's nothing personal, Tom, I appreciate your attempts to help.  But this episode has made it less likely that I'll but a System76 machine in the future.

---

### Post by thomasaaron on 2010-02-02
> I would think this sound card jacks issue would be a deal breaker for any users like me who are interested in music creation.

I can certainly see that.

> ...but I thought buying a System76 box would mean smooth sailing. 

Unfortunately, that's kind of the nature of ALSA and Pulseaudio. I remember when both of them absolutely stunk. They've come a long way in the past few years. They seem to have most of the basics down, but considering how much hardware there is out there to build in support for, it's still not unusual to run into issues like this from time to time. In fact, it is running into issues like this (and filing bug reports in the appropriate places) that betters open source software for the next user. (But I realize that's not what you signed up for. You just wanted something that worked.)

> I'm a bit dismayed to learn that System76 apparently doesn't consider it very important that all hardware work out of the box.

We actually care a lot about providing customers with working hardware, and we put a HUGE amount of time into getting things to work and solving the problems (like this one) that inevitably come up. And we will do the best we can for you as well.

> It's nothing personal, Tom, I appreciate your attempts to help. But this episode has made it less likely that I'll but a System76 machine in the future.

I am sorry to hear that. But, I promise, I'll do all I can to help you get it sorted out.

---

### Post by thomasaaron on 2010-02-03
OK, I just spoke called up Intel and asked them about this. Here's what they said...

1. speaker out to mic jack -- this will definitely NOT work.
2. speaker output to line in jack -- in theory, this should work, but (and this surprised me) they do not test it and could not guarantee it would work.

So, as we move forward with this, please realize that it may or may not even be possible on the Wild Dog's motherboard.

(I saw another post where you are looking for a sound card. Do you want me to continue?)

---

### Post by dabrowsa on 2010-02-03
[INDENT]> OK, I just spoke called up Intel and asked them about this. Here's what they said...

1. speaker out to mic jack -- this will definitely NOT work.
2. speaker output to line in jack -- in theory, this should work, but (and this surprised me) they do not test it and could not guarantee it would work.
[/INDENT]



I'm confused.  Do you mean: 

(1) line-in jack to speaker-out, i.e. internal playthrough allowing e.g. audio daisychaining or simultaneous recording and audition; or

(2) speaker-out to line-in, i.e. running a cable from the audio output back to the line-in, allowing e.g. recording the product of sound generation software?

I want (1), and it was not a problem with the last two Dell machines I owned (running Ubuntu).

---

### Post by thomasaaron on 2010-02-03
I'm sorry, I just don't know a lot about audio recording.

My conversation with the Intel tech was more along the lines of number 2. But I see what you're getting at now with number 1.

I shall do more research on it.

---

