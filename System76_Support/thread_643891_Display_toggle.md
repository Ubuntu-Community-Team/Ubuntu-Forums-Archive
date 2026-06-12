---
title: "Display toggle?"
date: 2007-12-18
forum: System76 Support
---

### Post by cheuschober on 2007-12-18
Hi. Proud new owner of a darter with only one real 'worry'

I'm looking for some kind of button that can toggle my display output and I'm not finding one. Every laptop I've had for the last 7 or 8 years (most of which had linux on them) has had a fn key or similar that toggles through output to the local flat panel, the vga-out, and clone -- and I use it pretty often because when at home I need a larger monitor for my cad work and outright closing every gui app I have so that I can switch X configurations to or from might as well be the same thing as a full-restart -- it's not particularly grab & go.

Please tell me, I'm missing something here! Does this button exist?

Regards and thanks,
~C

---

### Post by thomasaaron on 2007-12-18
It is the Fn-F2 keys. It only works prior to booting (while you're still on the manufacturer's screen). So, you have to set it the way you want it there and then let it boot.

---

### Post by cheuschober on 2007-12-18
thomasaaron,

thank you for the swift reply. is the reason it only works on the mfg screen because of ubuntu gutsy's specific implementation of '(un)breakable X' or just X in general?

I have a fair amount of experience with other distros (gentoo, rh, and debian proper) and I could issue the change display command without issue. I even recall doing it on a hoary machine I once tested out.

If it's just ubuntu's X implementation I might dig around and try to find a means to wrest control back to standard X handling as restarting is just as bad as writing a little script to change serverlayouts (which, in gutsy, I can't seem to change anyway without a restart).

regards,
~C

---

### Post by thomasaaron on 2007-12-18
I don't think it has to do with X. It definitely doesn't have to do with unbreakable x (as we had the same problem under Feisty).

It may be a bios issue, although available upgrades have not fixed the problem.

---

### Post by palintheus on 2007-12-19
I use this command when plugging in my LCD monitor to my darter

```
xrandr --output VGA --auto
```

---

