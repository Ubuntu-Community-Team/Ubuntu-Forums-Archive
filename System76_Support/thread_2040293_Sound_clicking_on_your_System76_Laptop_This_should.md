---
title: "Sound clicking on your System76 Laptop? This should fix it."
date: 2012-08-10
forum: System76 Support
---

### Post by TheOnlyEnglishRose on 2012-08-10
If your System76 machine makes a clicking noise while sound is not playing, don't worry. It turns out it's an issue with power save in the Intel High Definition Audio drivers. What's worse, is that it's an issue that has affected some portable Intel HDA users for years.

Anyway, according to [this post from three years ago]("http://ubuntuforums.org/showpost.php?p=8239757&postcount=4"), the easiest way to fix it is to simply turn off the power save function.

It's pretty simple to do:

To disable it immediately,
```

echo 0 | sudo tee /sys/module/snd_hda_intel/parameters/power_save

```

To disable it on every boot, add this above "exit 0" in /etc/rc.local
```

echo 0 > /sys/module/snd_hda_intel/parameters/power_save

```

---

### Post by isantop on 2012-08-10
> **TheOnlyEnglishRose said:**
> If your System76 machine makes a clicking noise while sound is not playing, don't worry. It turns out it's an issue with power save in the Intel High Definition Audio drivers. What's worse, is that it's an issue that has affected some portable Intel HDA users for years.

Anyway, according to [this post from three years ago]("http://ubuntuforums.org/showpost.php?p=8239757&postcount=4"), the easiest way to fix it is to simply turn off the power save function.

It's pretty simple to do:

To disable it immediately,
```

sudo su
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
exit              # to exit your dangerous root session

```

To disable it on every boot, add this above "exit 0" in /etc/rc.local
```

echo 0 > /sys/module/snd_hda_intel/parameters/power_save

```

As a note, it's much better to run that like this:

```
 echo 0 | sudo tee /sys/module/snd_hda_intel/parameters/power_save
```

This uses sudo rather than su, which means you don't have a root shell open. This is much less dangerous.

---

### Post by TheOnlyEnglishRose on 2012-08-11
Thanks! OP has been updated.

---

### Post by bjornd on 2012-08-30
> **TheOnlyEnglishRose said:**
> If your System76 machine makes a clicking noise while sound is not playing, don't worry. It turns out it's an issue with power save in the Intel High Definition Audio drivers. What's worse, is that it's an issue that has affected some portable Intel HDA users for years.


Thanks this solved the problem on my Dell Inspiron 17R with the following audio device:
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
``` - the clicking was only there when running on battery for obvious reasons.

---

### Post by chronos00 on 2012-10-02
> **TheOnlyEnglishRose said:**
> 
It's pretty simple to do:

To disable it immediately,
```

echo 0 | sudo tee /sys/module/snd_hda_intel/parameters/power_save

```

To disable it on every boot, add this above "exit 0" in /etc/rc.local
```

echo 0 > /sys/module/snd_hda_intel/parameters/power_save

```

Thank you so much!!!

This solved the problem for my Samsung NP300!
I have the following audio device:

```
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)

```


Anyway, how I am affecting my system by disabling this power-saving feature?

Thank you!

---

### Post by bjornd on 2012-10-07
Turns out that it was actually Google Chrome causing this problem on my laptop. After a lot of searching I found out that disabling the "Pepperflash" plugin solved the issue, leaving the power-saving feature intact.
To do this, go to chrome://plugins and disable the plugin with the path /opt/google/chrome/PepperFlash/libpepflashplayer.so. Flash content is not affected as far as I can tell.as content reverts to the Adobe flash player.

FYI, on my laptop the problem only occured when running on battery after waking up from a sleep state.

---

### Post by mgolden on 2012-10-07
Wow, Bjornd!  This solves a long-term problem I have been having.  I run Kubuntu 12.04, and I have noticed that using Chrome to play videos causes the system sound to stammer.  Generally it is about one second of audio that repeats 3 times, then goes on.

Disabling pepperflash seems to have fixed it!

---

