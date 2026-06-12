---
title: "Can pulseaudio and jack play nice?"
date: 2010-02-01
forum: Ubuntu Studio
---

### Post by white95 on 2010-02-01
I'll try to keep it short.

I had some issues with Ubuntu-studio; I couldn't seem to get jack to work.  Reading through posts it seemed that pulseaudio was the problem.

So I installed Ubuntu 9.10 and upgraded to Ubuntu-studio without pulseaudio and the studio desktop.  Jack is working now, but I'm not sure if it's because of pulseaudio or if I just didn't setup jack correctly the first time.  

When I had pulseaudio (the first install), playing videos and music seemed to be better; so I would like to have both if possible.  When I look at posted guides and how-to's they are from 2008 and followed by posts saying "this didn't work" or "pulseaudio sucks".

So, do pulseaudio and jack currently co-exist properly?

---

### Post by trulan on 2010-02-01
It depends who you ask.

I had no issues with pulse audio as it came by default in Ubuntu Studio (which is to say that it gets suspended every time Jack Control is started, effectively separating the pulse and jack sound servers.)  When I actually tried to mix pulse and jack (using packages from ppa's) things got messy.

Technically, Pulse Audio shouldn't cause any probems with Jack in Ubuntu or Ubuntu Studio. YMMV.

---

### Post by dawiba on 2010-02-02
I'll second what Trulan says. I have UbuntuStudio 9.10 standard install with Jack and PulseAudio and they both work as they should. I also ran into problems previously using PPA's, so I've just left this install untouched and it's been fine for ages.

---

### Post by white95 on 2010-02-02
Thanks guys.

---

