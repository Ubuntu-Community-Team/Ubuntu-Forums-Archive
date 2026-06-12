---
title: "Non-existent nVidia Legacy Driver Support for Linux 3.12"
date: 2013-10-26
forum: Ubuntu Development Version
---

### Post by VinDSL on 2013-10-26
Surprisingly, Linux 3.12 works on ancient nVidia 173.14.37 legacy drivers...  :KS  :KS


[INDENT]**[COLOR="#800080"]Ubu 'Trusty' 14.04 / Gnome-Shell 3.10.1 Staging / Custom Linux 3.12-rc6 Kernel /  Plank / Conky / ConkyWX [/COLOR]**
[URL="http://vindsl.com/images/vindsl-desktop-26-oct-2013-1.png"]
[IMG]http://vindsl.com/images/vindsl-desktop-26-oct-2013-1(650x520).png[/IMG][/URL][/INDENT]


Heh!  It's a kludge, but it's a start...  LoL!  :D

---

### Post by VinDSL on 2013-10-26
Getting closer!  Here's nVidia 304.88  :)

[INDENT][URL="http://vindsl.com/images/vindsl-desktop-26-oct-2013-2.png"]
[IMG]http://vindsl.com/images/vindsl-desktop-26-oct-2013-2(650x520).png[/IMG][/URL][/INDENT]


Continuing...

---

### Post by VinDSL on 2013-10-26
I dunno.  I *think* I'll quit while I'm ahead.  304.88 has been working nicely.

I've been messing with this for hours.  Too bad we have to roll_our_own.  Where's the upstream support?!?!?

304.108 looks like a piece of work.  Only benefit I can see are the Flash fixes -- not worth the effort, really.

Gotta say, it's a relief getting away from the increasingly frequent Nouveau lockups...

---

### Post by ventrical on 2013-10-27
Nice work as always Vin! :)

---

### Post by VinDSL on 2013-10-27
Thanks, Vent!

I'm starting to wonder if nVidia will ever come out with modern 'legacy drivers' for Linux >= 3.12

Linux 3.12-rc1 was released six weeks ago.  I just got tired of waiting.

I've never seen it take this long before -- and nothing is in the pipe, AFAIK.

Oh, well.  This too shall pass... hopefully.  ;)

---

### Post by QDR06VV9 on 2013-10-28
```
I dunno.  I *think* I'll quit while I'm ahead.  304.88 has been working nicely.

I've been messing with this for hours.  Too bad we have to roll_our_own.  Where's the upstream support?!?!?

304.108 looks like a piece of work.  Only benefit I can see are the Flash fixes -- not worth the effort, really.

Gotta say, it's a relief getting away from the [COLOR=#ff0000]_increasingly frequent Nouveau lockups._[/COLOR]..
```

Yes Sir!!([COLOR=#ff0000]_increasingly frequent Nouveau lockups._[/COLOR].)
Im pretty sure there is something coming as far as legacy drivers when ?????
I happened to get Lucky and had an _**off the record conversation**_ with one of there devs..(No dates or even promises.)

---

### Post by VMC on 2013-10-28
I also get those lockups using *nouveau* on all Ubuntu distros, except Kubuntu.

---

### Post by NM5TF on 2013-10-29
> **VMC said:**
> I also get those lockups using *nouveau* on all Ubuntu distros, except Kubuntu.

I was getting those also, especially on Mint 14.....getting to be almost unusable...

then installed nvidia-current.....has been working perfectly since....

---

### Post by paul_in_london on 2013-11-08
> **VinDSL said:**
> Thanks, Vent!

I'm starting to wonder if nVidia will ever come out with modern 'legacy drivers' for Linux >= 3.12

Linux 3.12-rc1 was released six weeks ago.  I just got tired of waiting.

I've never seen it take this long before -- and nothing is in the pipe, AFAIK.

Oh, well.  This too shall pass... hopefully.  ;)

Nouveau hasn't actually been causing me any problems, but I've been wondering about this too.

I see from this page that 304.116 was released the other day (6th November):

[http://www.nvidia.com/Download/driverResults.aspx/69366/en-us](http://www.nvidia.com/Download/driverResults.aspx/69366/en-us)

No sign of it in xorg-edgers yet. Soon presumably though?! I prefer to use packaged versions instead of running the nvidia installer.

---

### Post by VinDSL on 2013-11-08
> **paul_in_london said:**
> I prefer to use packaged versions instead of running the nvidia installer.
Agreed.

I installed 304.116, last night, via the nVidia installer.  Gawd!  That thing is sooooo last century...

After three slightly varied attempts, it still couldn't find my display on reboot.  :p

I'll wait patiently for 304.116 to show up in edgers, or the official PPAs...

---

