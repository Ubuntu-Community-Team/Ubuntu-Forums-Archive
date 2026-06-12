---
title: "simple-quick midi to wav conversion"
date: 2008-12-06
forum: Ubuntu Studio
---

### Post by its_jon on 2008-12-06
Hi.....

I have ardour installed and audacity

I Installed rosegarden but it dosn't work... something about a timer broken.

I had used rosegarden on a 32 bit OK... but not on ubuntu 64 ... broken in U64

So.... any simple way to convert a midi to a wav in the synaptic ?


.... very much a nueb to Linux. and trying my best to keep working at it.

many thanks
John
Scotland

---

### Post by raboofje on 2008-12-07
> **its_jon said:**
> any simple way to convert a midi to a wav in the synaptic ?

timidity?

---

### Post by goodmanbrown on 2008-12-08
Yes, timidity++ does that.  For example:

```
timidity -Ow *.mid
```

will convert all the midi files in your current directory into wav files.

---

