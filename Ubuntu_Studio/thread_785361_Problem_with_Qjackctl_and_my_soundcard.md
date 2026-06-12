---
title: "Problem with Qjackctl and my soundcard"
date: 2008-05-07
forum: Ubuntu Studio
---

### Post by enaoutan on 2008-05-07
faHi!
I was on the Gutsy Gibbons for 4 months and used my soundcard Edirol FA101.
It worked quite good, even if, when using jack and 3 softwares at the same time it crashed (buffer under or overrun). It wasn't really stable but it worked.
I made the update to Hardy Heron and now it works only for a short time (even with hydrogen only) and if I use only 2 softs it crashes.
The message from Qjackctl :
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
LibFreeBoB ERR: SLAVE XMT : Buffer underrun! 512 (0 / 352) (0 / 0 )
LibFreeBoB ERR: Xrun on connection 1
Abandon

For example. And when I use 2 softs this is almost the same but written: buffer overrun

I made the real-time improvement, schedule, priority and co but it's just the same!
I have a laptop with intel core 2 duo and 1024 RAM so I think it's not a hardware problem.
I'm using Linux (before Ubuntu I was on Mandriva) and Qjackctl to make music for 3 years and this problem right now is just weird regarding the abilities of my computer.
I'd really appreciate some help, I really need to make my audio softs work well.
Thanks

---

### Post by enaoutan on 2008-05-08
Ok! Thanks to jwmislan I discovered that there is something interesting in ubuntu studio :
in
System  Administration       then First line (on my french version there is only an icon and no name)
You can set a memlock for audio and that is quite good.
Still...
Today, before I found this, I could only play hydrogen for about 3 or 4mn and then qjackctl crashed.
Now that I found this, it seems like I could play it all night long but when I open Zynaddsubfx + Hydrogen + Rezound = crash
Am I too greedy??? I thougt linux approach of audio was modular : i.e. with many softwares opened at the same time. Am I wrong? Sure not because I made that before with a previous computer and soundcard (it was a PCI, maybe the Firewire is the pbm!?!?)
If anyone had any idea on how to get well with different audio softwares at the same time (how to deal with buffer pbms???), it would be very well welcomed!!!! (Sorry for my english, I hope I make myself clear)

---

### Post by enaoutan on 2008-05-13
Does anyone has any clue???
I'm looking for anything that could make jack work properly.
Pleeeeaaase,

---

### Post by enaoutan on 2008-05-13
I just noticed sthg : my swap partition is active but seems not working (I went to System Monitoring and it was on 0%)
Is it normal when using jack and other audio softs????
I might just be mistaken but answer me please! I'm diving in the mud of my scratching sounds and crashing jack!!!

---

### Post by thorgal on 2008-05-14
salut! do you know the french-speaking website [www.linuxmao.org](www.linuxmao.org) ? you may find some info regarding tweaking your system for optimal performance. In any case, if you have some issues, it is always good to provide your system specs (all hardware specs) and OS settings (partitioning, kernel parameters, boot options, etc). If language is also an issue, you can write to me in french, I am fluent in it, but your posts suggest you're OK with english :)

---

