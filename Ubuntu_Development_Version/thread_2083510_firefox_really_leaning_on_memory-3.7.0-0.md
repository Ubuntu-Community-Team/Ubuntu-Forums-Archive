---
title: "firefox really leaning on memory-3.7.0-0"
date: 2012-11-12
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-11-12
Just noticed that ff is really pulling on memory and I only have 4 tabs open.

---

### Post by raja.genupula on 2012-11-12
> **ventrical said:**
> Just noticed that ff is really pulling on memory and I only have 4 tabs open.

Thats really starving mode .

is that behavior appearing abruptly or from opening on wards ?

---

### Post by ventrical on 2012-11-13
> **raja.genupula said:**
> Thats really starving mode .

is that behavior appearing abruptly or from opening on wards ?

  This is from a fresh install using the daily .iso of raring.  That PC had been running for a few hours. I then just decided to download htop. ff was running for several hours. However, after I reported it, it began to slowly back-off and stabalize.

  If I were not experimenting with htop I would not have noticed.

---

### Post by ventrical on 2012-11-13
From a cold boot with tabs restored:

---

### Post by ventrical on 2012-11-13
system monitor

---

### Post by ventrical on 2012-11-13
So then it jumps to 12.8 without doing any input at all.

---

### Post by ventrical on 2012-11-13
Then I scroll up in htop and have more instances of ff eating away at memory..

---

### Post by ventrical on 2012-11-13
23instances of FF X 16.4MB using 3.5.0-17 kernel.

Definitely appears to be ff problem.

---

### Post by mc4man on 2012-11-13
You're not showing anything out of the ordinary
The "16.4" is % not MB
Each PID is not another instance & doesn't represent any add. mem used or reserved

---

### Post by philinux on 2012-11-13
According to conky FF is using ~12% memory.

Sheesh nvidia temp not worky in raring.

---

### Post by ventrical on 2012-11-13
> **mc4man said:**
> You're not showing anything out of the ordinary
The "16.4" is % not MB
Each PID is not another instance & doesn't represent any add. mem used or reserved

Thanks mc4man.

---

### Post by jerrylamos on 2012-11-15
Raring % memory seems to vary from boot to boot.  It was 30% then I rebooted now it is 20%.  Not doing much except 4 tabs open and making this message.  Seems to keep on at 20% no matter whether it is doing much or not.

---

### Post by ventrical on 2012-11-16
> **jerrylamos said:**
> Raring % memory seems to vary from boot to boot.  It was 30% then I rebooted now it is 20%.  Not doing much except 4 tabs open and making this message.  Seems to keep on at 20% no matter whether it is doing much or not.

 46 - 58 % here now. I have  30 tabs open on this one machine (Intel Dual Core 2.66GHz) but it did not do this  a week ago. Actually , with all these tabs, it would just idle between 0 and 7 %.

 I'm keeping an eye on it.

Linux dale-desktop 3.7.0-030700rc4-generic #201211041435 SMP Sun Nov 4 19:43:27 UTC 2012 i686 i686 i686 GNU/Linux
dale@dale-desktop:~$

---

### Post by dino99 on 2012-11-16
you seems to dream a little :confused:

30 tabs opened with, i suppose a bunch of refreshing ads/video/javascript enabled, ...

you cant get 0% or even 7 % with all that stuff refreshing in a loop  :(

simply unplug or deactivate the network, and you'll see the difference  :P

---

### Post by ventrical on 2012-11-16
On my other machine 151MB with only 3 tabs opened. ff  is really hogging the memory, not usual.

---

### Post by ventrical on 2012-11-16
> **dino99 said:**
> you seems to dream a little :confused:

30 tabs opened with, i suppose a bunch of refreshing ads/video/javascript enabled, ...

you cant get 0% or even 7 % with all that stuff refreshing in a loop  :(

simply unplug or deactivate the network, and you'll see the difference  :P

Not dreaming...  an error on my part.  Tabs were (opened) but not active in those cases.

---

