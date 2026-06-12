---
title: "Woo hoo, my last linux issue is resolved (sound!)"
date: 2006-04-04
forum: The Cafe
---

### Post by BoyOfDestiny on 2006-04-04
Well sound has always been great on my desktop (sb audigy2 has hardware mixing). [dapper amd64]

My laptop [dapper 32] has been another story (intel ich6 card). Open more than one app often would block sound and give an error. ESD was crap...
However, dmix rocks. 

Then, boom, I could load beep-media-player, zsnes, dosbox, videolan and get sound from every app. No lag. No esd!

Go dapper and alsa with dmix!

P.S. I know maybe this should be under testimonials... It's here since I know other people have sound issues, and are just putting up with it. I hope this helps!

EDIT: Turns out dmix is automatic if your card needs it, just make sure the apps are using ALSA. If firefox and flash lag, try launching 
aoss firefox 
that solved it for me, and works with multiple sounds (you must have alsa-oss installed for that to work btw...)

---

### Post by Iandefor on 2006-04-04
Don't be sad, I'm sure some other problem will pop up :).

---

### Post by K.Mandla on 2006-04-04
Congratulations!

---

