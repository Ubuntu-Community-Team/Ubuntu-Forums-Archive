---
title: "One click solution Virtualbox"
date: 2010-11-12
forum: Virtualisation
---

### Post by rmcellig on 2010-11-12
Is there a way I can put an icon on my panel so that I can just click once to it and have direct access to my XP virtual machine?

---

### Post by bluelamp999 on 2010-11-12
A quick Google turned up this - [http://www.virtualbox.org/manual/ch08.html#vboxmanage-startvm](http://www.virtualbox.org/manual/ch08.html#vboxmanage-startvm)

I'd imaging creating a launcher which uses the above command along with your VM name could work?

I'm not at my machine right now so can't say for sure...

---

### Post by sanderd17 on 2010-11-12
say the name of your machine is XP, then you must place a link to
```

virtualbox --startvm XP

```
on your desktop. I don't know if it works when the name of the vm has spaces or odd characters.

---

