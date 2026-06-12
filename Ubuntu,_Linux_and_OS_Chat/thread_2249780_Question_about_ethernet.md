---
title: "Question about ethernet"
date: 2014-10-24
forum: Ubuntu, Linux and OS Chat
---

### Post by sameer-grover-1 on 2014-10-24
I faced a strange issue about ethernet compatilbility and though not strictly an ubuntu question, I figured I could get get some help here.

I purchased a network hard drive, WD MyCloud (runs on debian) and hooked it up using an ethernet cable to my ISP provided ADSL modem+router (some obscure brand). No link was detected (LED lights didn't glow) and it didn't work. This router works with other wired devices (desktops, printer etc)

I then tried another router I had (linksys wrt120n). Worked flawlessly.

So I was wondering what the issue could possibly be. The network hard drive is advertised as 100/1000 and both routers are 10/100. I was under the impression that backward compatibilty ensures that ethernet ports are plug-and-play, so to speak. Is that really the case or am I missing something?

(This is more of an academic question really. I'm just trying to learn something)

Thanks.

---

### Post by mips on 2014-10-24
Can you force the speed on the mycloud to 100Mb/s by any chance? (never used one of these things)

I have no answer for you as why this happens. I once purchased a Fujitsu Siemens laptop and this simply refused to connect to my adsl router, I could not get the ethernet connection to work. I tried forcing 10mbs half-duplex on the laptop, 100mbs full-duplex and a slew of other things, no go. I returned it the net day and got a HP laptop that worked fine.

My suggestion to you would be to buy a cheap gigabit ethernet switch and connect all your devices to that instead of the router. You will get vastly improved lan speeds and your mycloud would probably work.

---

### Post by tgalati4 on 2014-10-24
Try different cables.  Sometimes you need to plug it in a few times to get the handshaking to work properly.  Otherwise, I would do as mips suggested and get yourself a decent gigabit 8-port router, so you will have room to expand.

---

