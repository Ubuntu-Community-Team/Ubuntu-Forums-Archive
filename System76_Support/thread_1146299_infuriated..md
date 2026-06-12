---
title: "infuriated."
date: 2009-05-02
forum: System76 Support
---

### Post by xakh on 2009-05-02
Okay. First.
As I was browsing the web, my laptop turned off, with no warning. I thought it may be due to it running out of battery and power manager not working, so I turned it back on.
It started beeping.
As soon as I turned it on, it looked like it was having a kernel panic, with num lock and caps lock blinking, and then shut down. This bothered me. Then, after that happened, I turned it on again, went to the BIOS, where it stated it thought I was running Vista. Thinking this must be the problem, I switched it to "other", which fixed the beeping upon reboot. I thought I was in the clear. I was so terribly wrong. Now I can't start firefox outside of safe mode, I installed Midori a while ago, so that has to be my default browser. Every time I start firefox, it either segfaults, or throws an illegal instruction. Neither are things I like.

Edit:Well. Now we're getting somewhere. I've found I can run with the addons Ad Block Plus, and the Ubuntu extensions. My other addons, Ghostery, which has worked for about four months, which detects what is watching you, adwise, Socialite, Which has been working for a similar amount of time, which is an addon that helps with Reddit, and AmIonmyspace, which is just a thing that allows me to make sure I avoid myspace

Edit:I'm on a panp4n.

Another Edit: I can't save images. Jaunty sucks.


AND A FINAL EDIT!
I needed a Fsck. Everything's cool now.

---

### Post by thomasaaron on 2009-05-02
Fsck may have fixed some other things caused by the shutdown, but I don't think a hokey filesystem is the primary cause of the problem.

You should set the BIOS back to Vista for better SATA support.

The blinking LEDs were a kernel panic. Let's figure out what caused it. If it happens again, please restart and *immediately* go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

---

### Post by xakh on 2009-05-02
Well, the reason I said it looked like it was a kernel panic was that it happened before the actual boot. It also shut off during the boot, when I tried to just plug my ears and ignore the beeping. You guys put strong buzzers in the machine, so it was hard.
Edit: Changed my BIOS back to Vista, no beeping.
Also. Firefox stopped going on its little rampage afterwards, but it still does occasionally silently crash when watching flash stuff, but that's just because Flash Sucks. All in all, nothing new. Oh, Pidgin crashes when I connect and disconnect to too many networks, any idea why that happens?

---

### Post by thomasaaron on 2009-05-04
Honestly, it sounds like you had a hosed Jaunty upgrade/install. You might want to consider a re-do. None of that is typical behavior for a panp4 on Jaunty.

If you go that route, I'd also recommend using...
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)
...to get flash and your other restricted codecs installed.

---

