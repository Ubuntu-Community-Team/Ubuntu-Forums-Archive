---
title: "Finally an upgrade which worked!"
date: 2010-10-10
forum: The Cafe
---

### Post by arnab_das on 2010-10-10
In my 3 yrs of ubuntu usage this was the first time when an ubuntu upgrade actually worked! It wasnt as simple as hitting "update" since I was asked for replace xyz with abc quite a few times.

But finally, for the first time an upgrade worked! Every single time, be it from 8.10 to 9.04, 9.04 to 9.10 etc. something or the other used to break. This time, everything went ahead smoothly. Perfectly!

Anyone else had a "first time" proper upgrade experience like mine?

(BTW the ubuntu font is beautiful, and I believe ubuntu is now so beautiful, its freakin feminine! :D)

---

### Post by Legendary_Bibo on 2010-10-10
I've never had an issue with Ubuntu 9.10 or 10.04. I'll probably update next weekend when all my ppas have a 10.10 version.

---

### Post by arnab_das on 2010-10-10
> **Legendary_Bibo said:**
> I've never had an issue with Ubuntu 9.10 or 10.04. I'll probably update next weekend when all my ppas have a 10.10 version.

yea cant seem to find a medibuntu rep for 10.10 :(

---

### Post by RainPhantom on 2010-10-10
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
``` 

This worked for me. Had to run it twice though.

---

