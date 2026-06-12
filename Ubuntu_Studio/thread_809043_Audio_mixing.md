---
title: "Audio mixing"
date: 2008-05-27
forum: Ubuntu Studio
---

### Post by TonyFavilla on 2008-05-27
Hello,
I'm trying to make a little mixer/sampler, i'm using aplay to play different samples at the same time, but i'd like to adjust the volumes independently, anyone could help me?

---

### Post by Stochastic on 2008-05-27
I assume you're bash scripting?  if so, try redirecting the output to a multiplier 1=full volume 0=no volume then redirecting that output to /dev/dsp

---

### Post by TonyFavilla on 2008-05-27
Yes, i'm tryng to mix C and bash scripting, thank you for the hint, but i dont know how to do that, could you be a little more detailed?

---

### Post by Stochastic on 2008-05-27
Well you'll need to build the multiplier and I don't code either bash or C so can't really help you there (it will need to do a calculation for every sample).  Then the bash input/output redirection is simple ```
aplay -someParameters > multiplierScript > /dev/dsp
```  This is a really fun technique for accessing the soundcard as any data can be sent there (even graphics, textfiles, etc... though most will produce nasty semi-random noise).

---

