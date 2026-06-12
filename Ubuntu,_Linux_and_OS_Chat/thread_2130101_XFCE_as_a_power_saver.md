---
title: "XFCE as a power saver"
date: 2013-03-28
forum: Ubuntu, Linux and OS Chat
---

### Post by mreq on 2013-03-28
Have some of you noticed difference in power usage on a laptop? I am amazed at how light XFCE runs.

My laptop battery lifetime went to 4h from ~2.75h of full usage (wifi & work) on either Unity or Gnome shell. Also the temperature is ~5°C lower. Though I miss some things I liked on Gnome (mainly alt+tab switcher, the XFCE's one sucks :icon_frown:) I can say that I now officialy dig XFCE.

---

### Post by neu5eeCh on 2013-03-28
I use XFCE and have read rumors confirming what you say. Would be interesting to see some actual stats. Phoronix maybe?

---

### Post by mreq on 2013-03-28
never tried Phoronix, but:

The reason I switched from Gnome was gnome-shell constantly consuming ~15% CPU visible with `top`. Unity (compiz) was a bit better, but still ~12% CPU. With XFCE I rarely see any :) Also the wakeup stats in powertop tend to show there's a major difference.

---

### Post by montag dp on 2013-03-28
> **mreq said:**
> never tried Phoronix, but:

The reason I switched from Gnome was gnome-shell constantly consuming ~15% CPU visible with `top`. Unity (compiz) was a bit better, but still ~12% CPU. With XFCE I rarely see any :) Also the wakeup stats in powertop tend to show there's a major difference.That's weird, you're saying the other desktops used that much cpu at idle?  Doesn't seem right.

I've been using TLP for power management on my laptop, which has proven to work very well.  It saves probably a couple watts most of the time, including at idle.  I use KDE and get better battery life on Linux than on Windows 7.

[http://linrunner.de/en/tlp/tlp.html](http://linrunner.de/en/tlp/tlp.html)

---

### Post by kyalami321 on 2013-03-28
montag, the CPU usage might've gone up so drastically on the OP's machine when using Unity due to the increased graphics requirmeent. since we're talking about battery, the OP's machine is likely a laptop, likely with integrated graphics; hence the CPU usage, HDD activity likely increased as well, though this depends on available/installed RAM more so than video.

---

### Post by montag dp on 2013-03-28
> **kyalami321 said:**
> montag, the CPU usage might've gone up so drastically on the OP's machine when using Unity due to the increased graphics requirmeent. since we're talking about battery, the OP's machine is likely a laptop, likely with integrated graphics; hence the CPU usage, HDD activity likely increased as well, though this depends on available/installed RAM more so than video.But if he's talking about idle performance (which I'm not sure based on his post), I don't think it should matter, right?  If you're not changing anything on the screen there shouldn't be much graphics requirement.  I'm not totally sure if that's true, but on my laptop with integrated graphics running KDE, the CPU usage gets near 0 at idle.

---

### Post by mreq on 2013-03-28
Yes I've got an integrated Intel graphics. The CPU usage was ~15% when idle, which seemed like WAY too much. I've got 8gb ram. With XFCE it's fine ~0%.

---

### Post by TOMBSTONEV2 on 2013-03-28
From my experience unity causes there to be a higher idle processor usage. I have intel integrated graphics as well and I have tried ubuntu 12.04, 12.10, and lubuntu 12.10. The processor was the same on ubuntu 0-2% on idle, lubuntu was 0-1% idle. Now I have debian, my processor stays mostly at 0% occaisional 1% on idle. 12 - 15% is really too high for any os on a computer. I would look at what is utilizing the processor.

---

### Post by mreq on 2013-03-28
I don't know what could be wrong. I observed, that when completely idle it's about ~3%, but when I do alt+tab to chrome and immediately alt+tab back, I see above 20%. On XFCE, it's 0% to 3% after alt-tab.

Could something with my Intel card be wrong?

```
petr@sova:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
    GL_NV_conditional_render, GL_ARB_ES2_compatibility,
```

---

### Post by andrew.46 on 2013-03-28
Have a look at a decent installation of Fluxbox and you will start considering xfce a resource hog :).

---

### Post by mreq on 2013-03-28
> **andrew.46 said:**
> Have a look at a decent installation of Fluxbox and you will start considering xfce a resource hog :).

I'd love to use Awesome WM but there are so many things I'd miss, like network managers, brightness adjust etc. Also couldn't get even the simpliest widgets to work. I might give gnome 3.8 a shot and see how goes. Till then I'll stick with XFCE.

---

### Post by slickymaster on 2013-03-28
> **VTPoet said:**
> I use XFCE and have read rumors confirming what you say. Would be interesting to see some actual stats. Phoronix maybe?

There's an article at Phoronix comparing power and memory usage between XFCE, LXDE, KDE and Gnome, but's quite dated now, since it's from March 08, 2010.

Anyway, for those interested, here's the [link]("http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1").

---

### Post by montag dp on 2013-03-28
> **slickymaster said:**
> There's an article at Phoronix comparing power and memory usage between XFCE, LXDE, KDE and Gnome, but's quite dated now, since it's from March 08, 2010.

Anyway, for those interested, here's the [link]("http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1").I saw that too at one point.  I don't think it's very relevant anymore because all of those desktop environments have undergone major changes since then (at least, I know KDE and Gnome have).

---

### Post by vasa1 on 2013-03-28
> **andrew.46 said:**
> Have a look at a decent installation of Fluxbox and you will start considering xfce a resource hog :).

Isn't Fluxbox a window manager only whereas Xfce is both WM and DE?

---

### Post by andrew.46 on 2013-03-28
With fluxbox you assemble as much of a desktop environment as you want from 3rd party offerings. I use Thunar for file manager, libreoffice for docs, sakura for terminal, xscreensaver for screensaver, leafpad for text editing etc etc...

---

### Post by sffvba[e0rt on 2013-03-29
> **andrew.46 said:**
> Have a look at a decent installation of Fluxbox and you will start considering xfce a resource hog :).

Pfft, once you realize all you need is a terminal you will never go back :)

(Not that I will ever do that myself :p)


404

---

### Post by mips on 2013-03-29
> **not found said:**
> Pfft, once you realize all you need is a terminal you will never go back :)

(Not that I will ever do that myself :p)


404

Pfft, once you realise you don't need a computer you will never go back :)

---

### Post by andrew.46 on 2013-03-30
Are you guys all using a computer!!? I'm using a pocket calculator running on solar power.....

---

### Post by mreq on 2013-03-30
> **andrew.46 said:**
> Are you guys all using a computer!!? I'm using a pocket calculator running on solar power.....

Calculator? Not needed anymore: [Installing Linux on a Dead Badger: User's Notes]("http://www.strangehorizons.com/2004/20040405/badger.shtml")

---

### Post by Irihapeti on 2013-03-30
Pocket calculator??

Pass me my marble tablet and chisel...

---

### Post by mreq on 2013-03-30
okay, back to XFCE experience ;)

---

