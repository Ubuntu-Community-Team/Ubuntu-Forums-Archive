---
title: "Kernel 3.3 mainline available"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jfernyhough on 2012-03-18
3.3 mainline build is available here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/)

For me at time of posting (YMMV) fglrx 8.950 builds OK, nvidia 295.? doesn't.

AMD64, i386 and i386-PAE are all there. Have fun.

---

### Post by VinDSL on 2012-03-18
Bwahahaha!  You're fast!  :D

I swear - I checked less than 15 minutes ago, and it wasn't there.  LoL!

Okay, off I go, to install it.  ;)

---

### Post by VinDSL on 2012-03-18
Okay... built & booted just fine!

Here it is with nVidia 295.20 running (still requires the 'cp' trick):


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-18-mar-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-18-mar-2012-1.png")[/INDENT]


Thanks, again!

---

### Post by cottfcfan on 2012-03-19
VinDSL..
What icon set are you using there, looks good?

---

### Post by rajeev1204 on 2012-03-19
> **VinDSL said:**
> Okay... built & booted just fine!

Here it is with nVidia 295.20 running (still requires the 'cp' trick):

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-18-mar-2012-1%28650x520%29.png[/IMG]]("http://vindsl.com/images/vindsl-desktop-18-mar-2012-1.png")[/INDENT]
Thanks, again!

Awesome looking desktop.

---

### Post by VinDSL on 2012-03-19
> **cottfcfan said:**
> VinDSL..
What icon set are you using there, looks good?
> **rajeev1204 said:**
> Awesome looking desktop.
Thanks!

I made those icons, using ACYL 0.9.4  ;)

---

### Post by kaldor on 2012-03-19
So does anyone know which graphics features from 3.3 will be backported to Precise?

---

### Post by dino99 on 2012-03-19
> **kaldor said:**
> So does anyone know which graphics features from 3.3 will be backported to Precise?

will know with the next kernel changelog (can have an idea following kernel-ppa/pre-proposed)

---

### Post by Starks on 2012-03-19
It should be illegal to post the mainline kernels as legit or usable.

They don't work with out-of-tree modules or binary drivers. Period.

Then again, what is the CP trick?

---

### Post by dino99 on 2012-03-19
> **Starks said:**
> 
Then again, what is the CP trick?

illegal question :) only available for subscribers :)

---

### Post by VinDSL on 2012-03-19
> **Starks said:**
> [W]hat is the CP trick?

LINKAGE:  [http://ubuntuforums.org/showthread.php?p=11738908#post11738908](http://ubuntuforums.org/showthread.php?p=11738908#post11738908)

Just delete the "rc6" from the path (on line-3)...  ;)

---

