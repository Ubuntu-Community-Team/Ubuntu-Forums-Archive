---
title: "Is this related to the recent Nvidia problems?"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by BigSilly on 2012-04-21
I'm noticing a bit of flaky Unity performance since installing a daily build of 12.04. I am running the 64 bit edition kept up to date, with the 295.40 driver. There was no difference for me with this driver or the 295.33 one.

[Dash glitch picture.]("http://img854.imageshack.us/img854/8371/screenshotfrom201204211.jpg")

You can see in the picture that the background behind the Unity dash turns black. This happens when switching between maximising and minimising the dash. It corrects itself quick enough, but I don't think it should be happening. I also get a black screen when going from boot to log in, then log in to the desktop, which never used to happen with Oneiric. I imagine they are related.

Generally speaking it's all running fine apart from these things, but they do take away from the polish of the OS. Are they just Nvidia problems as recently reported, or wider Unity/Ubuntu issues? Thanks all.

---

### Post by dino99 on 2012-04-21
the actual nvidia issue performance with 295.40 should not concern your card, as its limited to 6, 7 & 8800 gtx/gts geforce cards.

---

### Post by BigSilly on 2012-04-21
> **dino99 said:**
> the actual nvidia issue performance with 295.40 should not concern your card, as its limited to 6, 7 & 8800 gtx/gts geforce cards.

Ah right. But isn't the 9800 just a rebranded 8800? 

Is this something you have seen, and should I report it?

---

### Post by dino99 on 2012-04-21
> **BigSilly said:**
> Ah right. But isn't the 9800 just a rebranded 8800?  [COLOR="RoyalBlue"](hm, i know the nvidia bad game)[/COLOR]

Is this something you have seen, and should I report it? [COLOR="SandyBrown"]nvidia is already aware since a few days & should push a fix soon[/COLOR]

but it seems that issue has been quite hidden till now with the older graphic cards, but some users said that the only good driver is the 280.10

---

### Post by BigSilly on 2012-04-21
If Nvidia are releasing an improved driver shortly, I'll hang on and see if it improves things. I think if I still see the issue after the new driver has landed, I'll put a bug report in. Many thanks. :)

---

### Post by MonkeyPaw on 2012-04-21
> **BigSilly said:**
> Ah right. But isn't the 9800 just a rebranded 8800? 

Is this something you have seen, and should I report it?

You are correct in that the 9800 is quite similar to the 8800 series.

Could it be that the bug hits the G80-based nVidia cards and not the G92? I'm running 295.40 with an 8800GTS 512, which is another G92 card, and I have had zero issues since install of Beta 2.

---

### Post by xyzzyman on 2012-04-22
My 9600M GS 512MB was having issues with .40 and I had to roll back to .33 also. The forums on nvnews.net have a # of people with 9 series cards having issues.

---

### Post by BigSilly on 2012-04-22
> **xyzzyman said:**
> My 9600M GS 512MB was having issues with .40 and I had to roll back to .33 also. The forums on nvnews.net have a # of people with 9 series cards having issues.

It was the same for me on .33. It was the reason I decided to try the .40 release.

---

### Post by xyzzyman on 2012-04-22
> **BigSilly said:**
> It was the same for me on .33. It was the reason I decided to try the .40 release.

Oh sorry, you were clear in that. Been reading so much about people rolling back to .33 I must have been presumptuous while reading your post.

Have you purged nvidia-current and rebooted to see if it occurs with the kernels noveau driver.

---

