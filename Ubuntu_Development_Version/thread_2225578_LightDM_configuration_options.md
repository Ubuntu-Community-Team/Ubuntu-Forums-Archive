---
title: "LightDM configuration options"
date: 2014-05-22
forum: Ubuntu Development Version
---

### Post by zika on 2014-05-22
Many times You want to execute some app. while LightDM is getting started. Before we had StartUP cluster but now we have /usr/share/lightdm/lightdm.conf.d/ folder.
In it we have several files and we can create our own files... Nuber at the beginning of names of those files are there for sake of order of being executed...
For example in 50-zika.conf among other things (that I've mentioned in a thread about thta earlier) i have also (given just for sake of an example, I do know that this is default state on NumLock) ```
greeter-setup-script=/usr/bin/numlockx off
```...
So, lot of stuff can be handled here...

---

