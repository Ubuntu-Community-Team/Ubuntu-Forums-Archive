---
title: "lubuntu Job swap.target failed with result 'dependency'"
date: 2018-08-06
forum: Ubuntu Development Version
---

### Post by VMC on 2018-08-06
[B]Lubuntu 18.10 Cosmic
[/B]
Here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/swapspace/+bug/1785450").

Maybe someone can install HDD, not VB. To see if you get the same result.
After install from terminal ```
journalctl|egrep "swap|timed"
```

Need to have swap partition not swapfile.

edit: Lubuntu 18.10

---

### Post by Claus7 on 2018-08-09
Hello,

I posted the output of the command for 18.04, yet, you wanted for 18.10. So I removed it.
[edit]
I downloaded the latest iso of lubuntu 18.10 and installed it using virtualbox.
I issued the above command and the result was:
Aug 10 19:11:15 lub12 kernel: zswap: loaded using pool lzo/zbud

The memory consumption thus far is 270MB.
I think that is looking more KDE-ish to me as it is up to now.
[edit] 

Regards!

---

### Post by VMC on 2018-08-11
Using today's ISO, it didn't fail using lubuntu's grub menu. There's a lot of maintenance that I did in the past before I checked for swap error. I will check for swap error after each step to try and narrow down exactly when the swap error starts.

---

