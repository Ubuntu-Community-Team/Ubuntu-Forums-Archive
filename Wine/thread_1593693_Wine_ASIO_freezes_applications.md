---
title: "Wine ASIO freezes applications"
date: 2010-10-11
forum: Wine
---

### Post by proxess on 2010-10-11
I just compiled the latest Wine ASIO (0.8.0) on my 64 bit machine and all went pretty well if I have to add. regsvr32 wineasio.dll went fine too. The problem is when I start up the applications that use it. When I choose the Wine ASIO driver, the applications completely freeze up. No output error anywhere tho, which makes things much more difficult. I run jackd with qjackctl and it starts up fine. Something weird tho is that when I choose the WineASIO driver, jackd trys to start again, but I doubt that's the problem.

Wine version is 1.3 and ASIO SDK is 2.2.

---

### Post by yanni.ilousis on 2010-10-19
I had the same problem when using wineasio 0.7.5 (but with Reaper).

I bypassed the freezing by installing wineasio 0.8.1 which is on [http://sourceforge.net/projects/kxstudio/files/](http://sourceforge.net/projects/kxstudio/files/) . But, at this time I have no inputs and no outputs, despite of setting 4 inputs and 4 outputs, and test it by writing down (and after of every time by doing restart of gnome session), one time exclusively and one time both in files *.profile* and *.wineasiocfg*, the following two lines:

```
export ASIO_INPUTS=4
export ASIO_OUTPUTS=4
```

Ubuntu 10.10 64 bit, Wine 1.3.5

---

### Post by proxess on 2010-10-19
Thanks! I'll give it a try later!

---

