---
title: "Update server down?"
date: 2009-08-30
forum: Wine
---

### Post by Jimleko211 on 2009-08-30
Whenever I try to update my system, it always tells me that it can't connect to the Wine servers.  What's going on?

---

### Post by hikaricore on 2009-08-30
Happens sometimes, give it time and try again.

---

### Post by Torgas Prim on 2009-08-30
I have been trying all day due to a fresh ubuntu install and cannot get to any download area for Wine. Hope it comes back up soon I am missing my D2 and Guild Wars!!

---

### Post by beastrace91 on 2009-08-30
I actually havn't been able to connect to it for the last two days or so... :/ I ended up just downloading the source code and then compiling it myself instead of adding the repos.

Just download the source [here](http://prdownloads.sourceforge.net/wine/wine-1.1.28.tar.bz2) from source forge, un-tar the package. Get the dependencies needed by running ```
sudo apt-get build-dep wine
``` in terminal, then build wine by running ```
./configure
make
sudo make install
```

Let me know if it gives you any issues :)

~Jeff

---

### Post by LinuxTAd on 2009-08-30
Thank you Jeff,

 Ran into this upon the end of  ```
./configure
```

> configure: libgsm development files not found, gsm 06.10 codec won't be supported.

As I am not familiar with that particular codec, perhaps someone could shed some light?

Thank you,
TAd

---

### Post by Dinchamion on 2009-08-31
> **LinuxTAd said:**
> Thank you Jeff,

 Ran into this upon the end of  ```
./configure
```



As I am not familiar with that particular codec, perhaps someone could shed some light?

Thank you,
TAd

I also have no idea what it does or what it is for... Installing the libgsm1-dev package doesn't fix it, but it seems wine will compile just fine without it.

And, as almost all kernel help comment states: if you don't know what it is, you don't need it :P)

---

### Post by LinuxTAd on 2009-08-31
> **Dinchamion said:**
> I also have no idea what it does or what it is for... Installing the libgsm1-dev package doesn't fix it, but it seems wine will compile just fine without it.

And, as almost all kernel help comment states: if you don't know what it is, you don't need it :P)

Had no compile errors as well, seemed to go fine,  and I believe your comment on kernel help is so very true :lolflag:

---

### Post by Torgas Prim on 2009-09-02
It's back up and I am playing GW again! :D

---

