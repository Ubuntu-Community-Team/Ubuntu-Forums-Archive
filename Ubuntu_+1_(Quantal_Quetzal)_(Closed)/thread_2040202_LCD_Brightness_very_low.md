---
title: "LCD Brightness very low"
date: 2012-08-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by skep on 2012-08-10
Hi, 

just tried out a fresh install of Alpha3 (also did an update/upgrade after that). My main problem right now is, that the screen brighness is very low. The brightness buttons seems to "work", as in they show the different brightness levels if I press them, but to no effect.

Acer Aspire One D270
3.5.0.9-generic
Intel D2xxx/N2xxx

Any idea?

---

### Post by johnathansmith on 2012-08-10
Look [Here]("http://askubuntu.com/questions/112050/acer-aspire-one-d270-can-not-set-brightness")
```

Try to configure directly.

sudo setpci -s "00:02.0" F4.B=FF

Where F4.B=FF <-- This FF is rhe intensity of bright in hexa values.

I use:

sudo setpci -s "00:02.0" F4.B=11

For example.
```

If this does help you have to wait, but guys currently working on fixing this [bug.]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1005495")

---

### Post by skep on 2012-08-10
Thank you! THis is what I was looking for (but didn't find). The workaround works fine for me. Again, thanks!

---

