---
title: "Nautilus 3.5.90 moving columns"
date: 2012-08-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-24
When using Nautilus 3.5.90 in Ubuntu QQ, the second and third columns (Size, Type) move to the right and back when I press the left mouse button over Nautilus window titlebar and release it. The same happens as I click once anywhere in the desktop and then once in Nautilus Titlebar.

It's hard for me to explain it in English, so I posted a video [here]("http://www.youtube.com/watch?v=MxB5TsqbojM").

I'd like to know if you're also seeing this problem before I post a bug report.

Regards,
Effenberg

---

### Post by dino99 on 2012-08-24
subscribe amigo  ):P

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018718](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018718)

so the newest versions since that report have not made change.

---

### Post by effenberg0x0 on 2012-08-24
> **dino99 said:**
> subscribe amigo  ):P

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018718](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1018718)

so the newest versions since that report have not made change.

Thanks Dino99 :)

I don't know why I didn't find that report when I was browsing for Nautilus stuff today. Anyway, I have added some info there. 

IMO, this is related to the hard-coded "auto-adjustment" of columns' widths, which is refreshed in windows focus events. If I'm right, I think a good test would be to just comment out the calls to whatever function is responsible for this columns width auto-adjustment.

Regards,
Effenberg

---

### Post by mc4man on 2012-08-24
While the effect is greatly reduced in the current master git it still there with focus on/off/on (usually very slight

I wouldn't expect too much out of LP/Ubuntu in 12.10 for naut 3.6 bugs, may be best to file upstream

---

