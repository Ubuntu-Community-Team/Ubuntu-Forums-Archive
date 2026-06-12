---
title: "Anyone installed the latest catalyst?"
date: 2012-08-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Dans564 on 2012-08-12
Not sure what the problem is, it seems to install fine.  On reboot it boots into the screen where you choose "low graphics mode" etc.. but with no mouse or keyboard so I'm forced to just re-install.  

This is the guide I have been following (works fine in 12.04): [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

Of course when building the package I replace 
```
sudo sh ./amd-driver-installer-[12-6]("http://wiki.cchtml.com/index.php/12-6")-x86.x86_64.run --buildpkg Ubuntu/precise
```with 

```
sudo sh ./amd-driver-installer-[12-6]("http://wiki.cchtml.com/index.php/12-6")-x86.x86_64.run --buildpkg Ubuntu/quantal
```other then that im not sure whats going wrong.  Anyone have any better luck?

---

### Post by jfernyhough on 2012-08-12
Yes, but it's a faff.

First, make sure you don't have -proposed enabled so you don't install xorg-xserver 1.13 accidentally (or on purpose!).

You have to patch libpciaccess otherwise X will segfault: [http://ubuntuforums.org/showthread.php?t=2031533](http://ubuntuforums.org/showthread.php?t=2031533)

You have to patch fglrx for kernel 3.5: [http://ubuntuforums.org/showpost.php?p=12090910&postcount=26](http://ubuntuforums.org/showpost.php?p=12090910&postcount=26)

---

### Post by Dans564 on 2012-08-12
thanks for the info!  Im gonna be travelling in the morning and this seems like quite the process, so for now I'm gonna go back to 12.04.  Hopefully amd will have this fixed by the time 12.10 roles out.

Again thanks a ton
the Ubuntu forums rock :guitar:

-Dan

---

### Post by readams on 2012-08-14
Got it working with your instructions.  Thanks much.

---

