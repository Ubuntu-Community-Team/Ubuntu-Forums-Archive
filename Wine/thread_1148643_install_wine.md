---
title: "install wine"
date: 2009-05-04
forum: Wine
---

### Post by volter on 2009-05-04
I'm new with wine(and linux) and I installed the  "stable release: Wine 1.0.1" (from Add/Remove ) and I couldn't play some of my games (like dawn of war) and I read that in the new version "development release: Wine 1.1.20" I can play this game. So I deleted the 1.0.1 and I don't know how to install  1.1.20? :confused:

---

### Post by smudi on 2009-05-04
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Agent.Logic_ on 2009-05-04
Hi volter,

Have you tried the method described in [this page](http://www.winehq.org/download/deb) over at WineHQ?

---

### Post by volter on 2009-05-04
ok, for not doing more stupid things can I play this game on 1.0.1

---

### Post by Agent.Logic_ on 2009-05-04
Have you tried running the game? Does it launch, or does it give you any error messages? Also, please mention the full title(s) of the game(s) you are trying to launch.

---

### Post by volter on 2009-05-04
the game called dawn of war soulstorm and after I install it the game looks like mess of colors.

---

### Post by Agent.Logic_ on 2009-05-04
Well, according to [this thread](http://ubuntuforums.org/showthread.php?t=777884) (post #4), it should work under wine 1.0.1. Have you the latest drivers for your graphics card? We'll need some info about your system specs. This is unfortunately the problem when trying to run something built for another platform (Windows, in this case), it doesn't usually work out-of-the-box. But don't worry, there is always someone or the other in the community to lend a helping hand and make it work for you.

---

### Post by volter on 2009-05-04
I have intell G31/G33 chipset - worked at full graphic effects in 'Windows'

and I didn't get any updates to the drivers.

---

### Post by Agent.Logic_ on 2009-05-06
> **volter said:**
> I have intell G31/G33 chipset - worked at full graphic effects in 'Windows'

and I didn't get any updates to the drivers.
Hmm, intel and linux aren't known to be good buddies from my experience. It worked in Windows because Windows automatically installs the correct drivers for your hardware. In linux, that isn't *always* the case. Anyway, could you please run the following command in the terminal and paste the output here?
```

cat /etc/X11/xorg.conf | grep Driver

```

---

### Post by volter on 2009-05-08
it's writing exactly nothing.  :confused:

---

