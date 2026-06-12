---
title: "cannot install using amd radeon hd7700 graphics card"
date: 2014-02-27
forum: Ubuntu Development Version
---

### Post by chris_dummer on 2014-02-27
i am trying to install 14.04 64bit on my main system with duel boot.
my graphics card is amd radeon hd7700 series with vga and hdmi o/p.
when  i boot from dvd instalation disk my monitors display the loading screen with checking for network etc.when it comes to the install/try screen the graphics go hay wire /unreadable.does this version of ubunu suport this card?.
best regards.

---

### Post by Eric_Atwood on 2014-02-27
I haven't tried this in 14.04 yet, but usually starting your install with the --nomodeset option will get you into the system.  From there downoading the proper drivers should take care of your problem.

---

### Post by chris_dummer on 2014-02-27
how do you select no mode set?

---

### Post by ventrical on 2014-02-27
While the .iso is booting , just hold down or tap any key. You will see Function key Options on the bottom. explore.

---

### Post by ventrical on 2014-02-27
Just did a full install. Works beautifully.

```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]

```

```

Linux ventrical-P5QL-PRO 3.13.0-11-generic #31-Ubuntu SMP Wed Feb 19 19:57:21 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

```

ventrical@ventrical-P5QL-PRO:~$ uname -a
Linux ventrical-P5QL-PRO 3.13.0-11-generic #31-Ubuntu SMP Wed Feb 19 19:57:21 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by chris_dummer on 2014-02-27
thanks ventricle i`m finally geting there my first download  iso had a corrupt file:: then it took a while to master accses to the loading menu:: then i realized on instalation my gpu was setting hdmi as my monitor my desktop screen was blank. now all installed and building up my apps.
this instalation looks diffrent  to the 32bit ver i have on an old think centre its more like 13.10 how do i place my app icons onto the desktop?
will keep posted thanks again.

---

### Post by ventrical on 2014-02-27
> **chris_dummer said:**
> thanks ventricle i`m finally geting there my first download  iso had a corrupt file:: then it took a while to master accses to the loading menu:: then i realized on instalation my gpu was setting hdmi as my monitor my desktop screen was blank. now all installed and building up my apps.
this instalation looks diffrent  to the 32bit ver i have on an old think centre its more like 13.10 how do i place my app icons onto the desktop?
will keep posted thanks again.


If you are using Unity, you can't. You have the Unity Panel and the Unity Dash (the dash takes place of desktop app icons. You can fix them to the Unity Panel if you like.

---

### Post by chris_dummer on 2014-02-27
i prefer the the desktop version of 14.04 like my 32bit machine how can i install that instead?

---

### Post by ventrical on 2014-02-27
> **chris_dummer said:**
> i prefer the the desktop version of 14.04 like my 32bit machine how can i install that instead?



 You can use the gnome flashback classic sessions. However, you will still not be able to pin app shortcuts to the desktop. If you want your apps on the desktop then I suggest kubuntu as (last I recall) you can put your apps as icons on the desktop. That program needs a lot of resources however.

```


sudo apt-get install gnome-session-flashback


```

if you want the simpler version of olde gnome spin.

---

### Post by chris_dummer on 2014-02-28
thanks for all your help my main problem is now resolved.

---

