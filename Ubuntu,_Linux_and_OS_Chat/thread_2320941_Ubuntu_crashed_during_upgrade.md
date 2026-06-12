---
title: "Ubuntu crashed during upgrade"
date: 2016-04-19
forum: Ubuntu, Linux and OS Chat
---

### Post by cash1981 on 2016-04-19
So I just wanted to vent a little frustration.

I upgraded from 14.10 LTS to 15.10 and during the upgrade, I had to go out for an errand. When I came back, my computer had gone into power save mode or hibernation. I am not sure.
I couldn't revive Ubuntu, so I had to hard restart the computer.

After the restart, Unity didn't start, and Ubuntu only goes to shell. I am not sure where in the process it crashed, but I don't even have Networking, so I can't even connect to me wifi. :(

I guess I have to boot up with USB, and copy my files before I reinstall everything again :(

---

### Post by Bucky Ball on 2016-04-19
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Please vent frustrations in non-support areas. :)

Do you mean 14.04 LTS? 14.10 wasn't an LTS.

Yes, I'd boot from live media, backup your files, and personally, I'd install 16.04 LTS which is officially released in three days and is supported until 2021. 

If you go the 16.04 LTS route, once installed, do this regularly (at least once a day):

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

After the 21st doesn't need to be as regular.

---

### Post by cash1981 on 2016-04-19
Yes I meant 14.04
It was LTS.

---

### Post by Bucky Ball on 2016-04-19
Pity, because LTS can upgrade to LTS and although this normally isn't possible until the first point release of the next LTS, it can be done using the terminal.

In other words, 14.04 LTS> 16.04 LTS directly is possible, leapfrogging the interim releases in between.

---

### Post by cash1981 on 2016-04-21
Thanks.

At least I know until next time

---

