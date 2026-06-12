---
title: "[SOLVED] System sounds silent when jack server is running"
date: 2008-06-24
forum: Ubuntu Studio
---

### Post by ubnewbie2 on 2008-06-24
I have installed ubuntu studio on a laptop to try it out.  I have found that system sounds are silent whenever the jack server is actually running.

Is there a way to fix this?

---

### Post by prismatic7 on 2008-06-24
> **ubnewbie2 said:**
> I have installed ubuntu studio on a laptop to try it out.  I have found that system sounds are silent whenever the jack server is actually running.

Is there a way to fix this?

without multiple soundcards, no. jack takes over the soundcard, dedicating it to jack-aware applications.

There is a method for routing pulseaudio output through jack (which would solve this) but it means you'd have to run jack all the time - probably not suitable if you're just experimenting...

---

### Post by ubnewbie2 on 2008-06-24
Ok thanks, appreciate the quick reply

---

