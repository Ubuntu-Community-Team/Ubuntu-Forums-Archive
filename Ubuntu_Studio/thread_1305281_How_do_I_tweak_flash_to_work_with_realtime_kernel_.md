---
title: "How do I tweak flash to work with realtime kernel in 8.04."
date: 2009-10-29
forum: Ubuntu Studio
---

### Post by Vigh on 2009-10-29
How do I tweak flash to work with realtime kernel in 8.04. Thanks.

---

### Post by bluesscream on 2009-10-30
> **Vigh said:**
> How do I tweak flash to work with realtime kernel 

same question for 9.10, -rt

---

### Post by Vigh on 2009-11-03
its seems that audio works fine in rt-kernel, just have to turn jack off when u want to watch utube

---

### Post by AutoStatic on 2009-11-03
That's right, Flash Player uses PulseAudio and JACK suspends PulseAudio at startup. You could set up PulseAudio to use JACK too though if you want to.

---

### Post by kayosiii on 2009-11-03
alternatively you can grab the flv file from /tmp and play that which ever jack enabled media player you prefer to use. This tends to result in smoother playback as a bonus.

---

