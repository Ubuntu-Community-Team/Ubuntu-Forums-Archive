---
title: "hotplug backport: problem with ALSA"
date: 2005-01-06
forum: Ubuntu Backports
---

### Post by Bart Van on 2005-01-06
Hi there,

just wanted to report a problem I encountered. I upgraded from hotplug_0.0.20040329-16_all.deb (from debian testing) to the version in the backports repository, and when I rebooted I didn't have any sound anymore.

I have a VIA AC97 soundcard integrated in the motherboard.

Running aplay (with the backported hotplug) gave:```
ALSA lib pcm_hw.c:1155:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: No such file or directory
```, and also xmms complained. I could get xmms play sound by changing the audio-device in the ALSA-plugin-configuration from "default" to "VIA8235: VIA8235 (hw: 1,0)". (This option is absent now by the way, there's only hw: 0,0 and 0,1...)

Also, I had two errors at startup about ppp-generic and -async, or something of the sort (sorry, didn't copy it...)

I could solve the problem with ```
sudo ln -s /dev/snd/pcmC1D0p /dev/snd/pcmC0D0p
``` (pure newbie fantasy, but it worked), but this link disappeared at reboot.

So now I reinstalled hotplug_0.0.20040329-16_all.deb and everything works perfectly. And pcmC0D0p reappeared in /dev/snd.

Apparently these two hotplug-versions result in different "files" in /dev/snd, hence all the problems?

Just wanted to let you know. Great stuff these backports by the way, thanks...

---

### Post by jdong on 2005-01-06
Are lsmod outputs EXACTLY identical with each hotplug?

---

### Post by Bart Van on 2005-01-06
[QUOTE=jdong]Are lsmod outputs EXACTLY identical with each hotplug?[/QUOTE]
Uh, dunno  :confused: Easy on the newbie  :mrgreen: 

If it can really help, I'm willing to investigate more precisely where the error came from, reinstall the backport hotplug (although I'm a bit scared of messing things up and spending hours trying to fix) etc, but you'll have to give me some code please... And some time :-)

---

### Post by jdong on 2005-01-06
well, then don't worry about it for now.

Does anyone else have similar problems?

---

### Post by HiddenWolf on 2005-01-06
[QUOTE=Bart Van]Hi there,

just wanted to report a problem I encountered. I upgraded from hotplug_0.0.20040329-16_all.deb (from debian testing) to the version in the backports repository, and when I rebooted I didn't have any sound anymore.[/QUOTE]
Are you experiencing bug 1293?
If you have a tv-tuner, or a second audio chip, that could be it.
The new hotplug version has things appearing in an unexpected order. In my case, it loads my tv-tuner before it loads the soundcard, and thus tries to use the tv-tuner as a soundcard.

---

### Post by Bart Van on 2005-01-07
[QUOTE=HiddenWolf]Are you experiencing bug 1293?
If you have a tv-tuner, or a second audio chip, that could be it.
The new hotplug version has things appearing in an unexpected order. In my case, it loads my tv-tuner before it loads the soundcard, and thus tries to use the tv-tuner as a soundcard.[/QUOTE]
That's probably it, I have a Hercules TV-card...

---

### Post by gheorghe_pop on 2005-01-08
Hello!
I got the same problem no sound after upgrading to hoary. (PlayTV TV TUNER).
Can this be fixed?
If so how?
Can't I just downgrade the version of hotplug?
Please help!

---

### Post by gheorghe_pop on 2005-01-08
**Solved:**http://ubuntuforums.org/showthread.php?p=45436#post45436

---

### Post by HiddenWolf on 2005-01-10
[QUOTE=Bart Van]That's probably it, I have a Hercules TV-card...[/QUOTE]
The easy way to solve it is switch your cards around physicly in the pci-slots.

---

