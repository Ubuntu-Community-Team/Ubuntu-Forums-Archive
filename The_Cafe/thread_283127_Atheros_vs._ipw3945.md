---
title: "Atheros vs. ipw3945"
date: 2006-10-23
forum: The Cafe
---

### Post by zachtib on 2006-10-23
I'm about to buy a new laptop.  My options for wireless are a Thinkpad 11a/b/g card (Atheros) or an Intel card (ipw3945)

I plan on going with the atheros card, because of the binary blob issue with the ipw3945 card, but I remembered that the madwifi drivers were in the restricted modules package, and I was wondering why exactly this is.

I'm trying to get a laptop that will run on purely open-source drivers, and I just wanted to make sure there isn't an issue with the atheros card

---

### Post by punkinside on 2006-10-23
atheros cards worked for me since hoary, shows up as ath0 and all... now I have a new laptop with an intel chip and it worked out of the box as well with the ipw3945 driver so... 

The only problem I have is that if I turn off the intel card via hardware the ipw3945 process takes up 100% of the cpu and I have to do remove it with modprobe. AFAIK this didnt happen with the atheros card (if it did I never noticed... I stumbled upon this by playing with top the other day when I noticed that my fans were going crazy)

In any case, I think atheros was waaay better. It had a longer range than the intel, the difference is amazing really. In the same spot I got something like 14 AP's with the atheros card I only get 3 with the intel.

---

### Post by IYY on 2006-10-23
I've never had a problem with the Atheros chipset on Ubuntu (used 2 Atheros cards.)

---

