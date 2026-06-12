---
title: "nvidia-current 285.05.09 lagging out?!?!?"
date: 2011-11-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VinDSL on 2011-11-10
Since doing a massive update, last night, my machine has been lagging out, from time-to-time.

It's most noticeable when I'm using browsers (all three) Opera-Next, Chromium, and Firefox, but...

Sometimes apps lag out too.  Gedit, for instance, lags out when I open a file with syntax highlighting enabled.  The text loads instantly, but the syntax highlighting goes slowly down the window, almost like pulling a shade down.

I suspect that nvidia-current 285.05.09 is causing the problem.  I've had problems with 285.x before.

Anyone else having this problem?

**Edit**

Hrm...  component mismatch.

```
vindsl@Zuul:~$ dpkg-query -l | grep nvidia
ii  nvidia-common                          1:0.2.35                                Find obsolete NVIDIA drivers
ii  nvidia-current                         **[COLOR="Red"]285.05.09-0ubuntu1[/COLOR]**                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        **[COLOR="Red"]280.13-0ubuntu4[/COLOR]**                         Tool of configuring the NVIDIA graphics driver
vindsl@Zuul:~$ 

```

Wonder if this could be causing the problem...

---

### Post by effenberg0x0 on 2011-11-10
> **VinDSL said:**
> Since doing a massive update, last night, my machine has been lagging out, from time-to-time.

It's most noticeable when I'm using browsers (all three) Opera-Next, Chromium, and Firefox, but...

Sometimes apps lag out too.  Gedit, for instance, lags out when I open a file with syntax highlighting enabled.  The text loads instantly, but the syntax highlighting goes slowly down the window, almost like pulling a shade down.

I suspect that nvidia-current 285.05.09 is causing the problem.  I've had problems with 285.x before.

Anyone else having this problem?
@Vin, running unity --replace& and using the PC normally, to have a chance to see the output of the section, I'm seeing many more errors then usual when using any GUI app. I posted 3 that were very frequent here: [http://ubuntuforums.org/showthread.php?t=1877516](http://ubuntuforums.org/showthread.php?t=1877516) Some of them were fixed with the procedure I mentioned in that thread.

I'm also seeing a flood of GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed every time I sense the GUI interface gets kind of laggy. 

I'm using the same driver you are, but this behavior started for me in the previous version. I'm not sure it's nvidia driver or some of the latest updates.

---

### Post by effenberg0x0 on 2011-11-10
> **VinDSL said:**
> 

Hrm...  component mismatch.

```
vindsl@Zuul:~$ dpkg-query -l | grep nvidia
ii  nvidia-common                          1:0.2.35                                Find obsolete NVIDIA drivers
ii  nvidia-current                         **[COLOR=Red]285.05.09-0ubuntu1[/COLOR]**                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        **[COLOR=Red]280.13-0ubuntu4[/COLOR]**                         Tool of configuring the NVIDIA graphics driver
vindsl@Zuul:~$ 

```Wonder if this could be causing the problem...

I installed from NVidia binary, so I can't help there. But when I ls /usr/lib*/*nvidia* /usr/lib*/libGL* -la all my soft links and libs are of the current version.

---

### Post by VinDSL on 2011-11-10
I snagged an Oneiric version in the x-swat PPA.

```
vindsl@Zuul:~$ dpkg-query -l | grep nvidia
ii  nvidia-common                          1:0.2.35                                Find obsolete NVIDIA drivers
ii  nvidia-current                         285.05.09-0ubuntu1                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        285.05.09-0ubuntu1~oneiric~xup1         Tool of configuring the NVIDIA graphics driver
vindsl@Zuul:~$ 
```

I'll see if it makes any difference.  ;)

---

### Post by ventrical on 2011-11-10
> **VinDSL said:**
> Since doing a massive update, last night, my machine has been lagging out, from time-to-time.

It's most noticeable when I'm using browsers (all three) Opera-Next, Chromium, and Firefox, but...

Sometimes apps lag out too.  Gedit, for instance, lags out when I open a file with syntax highlighting enabled.  The text loads instantly, but the syntax highlighting goes slowly down the window, almost like pulling a shade down.

I suspect that nvidia-current 285.05.09 is causing the problem.  I've had problems with 285.x before.

Anyone else having this problem?

**Edit**

Hrm...  component mismatch.

```
vindsl@Zuul:~$ dpkg-query -l | grep nvidia
ii  nvidia-common                          1:0.2.35                                Find obsolete NVIDIA drivers
ii  nvidia-current                         **[COLOR=Red]285.05.09-0ubuntu1[/COLOR]**                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        **[COLOR=Red]280.13-0ubuntu4[/COLOR]**                         Tool of configuring the NVIDIA graphics driver
vindsl@Zuul:~$ 

```Wonder if this could be causing the problem...


I pretty well have the same here but my nvidia GEforce 210 runs like greased lightning! :)

ventrical@ubuntu:~$ dpkg-query -l/grep nvidia
dpkg-query: error: unknown option -/

Use --help for help about querying packages.
```
ventrical@ubuntu:~$ dpkg-query -l | grep nvidia
ii  nvidia-common                          1:0.2.35                                Find obsolete NVIDIA drivers
rc  nvidia-current                         290.03-0ubuntu1~xedgers~oneiric1        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-updates                 285.05.09-0ubuntu1                      NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-settings                        290.03-0ubuntu1~xedgers~oneiric1        Tool of configuring the NVIDIA graphics driver
ii  nvidia-settings-updates                280.13-0ubuntu1                         Tool of configuring the NVIDIA graphics driver
ventrical@ubuntu:~$
```

---

### Post by VinDSL on 2011-11-17
Well... I gave 285.05.09 a (more than) fair trial... a week.

I was hoping that subsequent updates would fix the lagginess, but no joy.

Re-installed 280.13, last night, and life is good again.  ;)

I'll mark this one [SOLVED].

---

### Post by effenberg0x0 on 2011-11-19
@Vin 

Did you experience better performance using 290.06? It seems to perform better than 285.03, 285.09 and 290.03 here. The only relevant issue is an incompatibility with flash (290.03/290.06), to which I posted a working fix here: [http://ubuntuforums.org/showthread.php?t=1881784](http://ubuntuforums.org/showthread.php?t=1881784)

I am also seeing what appears to be a slight decrease in GPU temperature during normal operation (average = 5°C less) with 290.06 64-bit.

**EDIT: **I forgot to say, and this might be relevant: I'm using the latest Compiz, Unity and Nux, compiled from source.

---

### Post by VinDSL on 2011-11-19
> **effenberg0x0 said:**
> Did you experience better performance using 290.06?
I haven't tried it (yet).

I've been busy, building a suitable Conky Weather Script.  LoL!

Not enough hours in a day, you know?!?!?  :D

At this point, I'll probably wait for Alpha-1 before messing around with the nVidia drivers again.  

280.13 is working fine, at the moment...

---

### Post by VinDSL on 2011-11-21
Hrm...

I thought I'd better do an update.  This thread pops up high in Google Search results. ;)

I started playing around with kernel updates, last night, and nVidia 290.06.

Eventually, I succeeded in borking my UbuPP install.  LoL!  :D

After I put Humpty Dumpty back together again, I settled on:

Linux 3.1.0-2-generic, and nVidia-common & nVidia-settings 285.05.09

```
vindsl@Zuul:~$ dpkg-query -l | grep 3.1.0-2
ii  linux-headers-3.1.0-2                  3.1.0-2.3                               Header files related to Linux kernel version 3.1.0
ii  linux-headers-3.1.0-2-generic          3.1.0-2.3                               Linux kernel headers for version 3.1.0 on x86/x86_64
ii  linux-image-3.1.0-2-generic            3.1.0-2.3                               Linux kernel image for version 3.1.0 on x86/x86_64

vindsl@Zuul:~$ dpkg-query -l | grep nvidia
ii  nvidia-common                          1:0.2.36                                Find obsolete NVIDIA drivers
ii  nvidia-current                         285.05.09-0ubuntu1                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        285.05.09-0ubuntu1                      Tool of configuring the NVIDIA graphics driver
vindsl@Zuul:~$ 
```

Everything is working great now!  Go figure...  ;)

---

