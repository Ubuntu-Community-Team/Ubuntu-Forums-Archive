---
title: "Card reader errors in 12.10 and 13.04"
date: 2013-05-31
forum: System76 Support
---

### Post by kinglear333 on 2013-05-31
Hello everyone,

I have a System76 Gazelle (p7) not the latest, the ge laptop. Since upgrading from 12.04 to 12.10 and recently to 13.04, I have been having problems with Ubuntu recognizing card reader. It seems to be closely related to this bug: [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876)

Every apt-get upgrade I do, this bug pops up and ruins the day.

I tried the fix from planet76.com but no luck.

System76 -- is there a fix coming up or is this related to the kernel?

Thanks!

---

### Post by isantop on 2013-05-31
Try it from a live disk. If you still have problems there, it's likely a hardware failure.

---

### Post by kinglear333 on 2013-07-31
Just wanted to report back.

I had to re-install Ubuntu because full version upgrade is still not a smooth process in Ubuntu :(

After I re-installed 13.04, it still wouldn't work until I upgraded the Kernel to 3.9. But kernel 3.9 caused my headphone jack to not work, so I upgraded yet again to 3.10 and now everything is working perfectly. I guess it's not a Ubuntu-only issue if the kernel caused all this. It's just a reminder that you really can't have a laptop completely compatible with Ubuntu out-of-the-box without tinkering with stuff.

All happy now, though. Love my System76 beast!

---

