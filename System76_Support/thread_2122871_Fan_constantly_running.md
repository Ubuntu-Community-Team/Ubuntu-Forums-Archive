---
title: "Fan constantly running"
date: 2013-03-06
forum: System76 Support
---

### Post by b3d on 2013-03-06
I have a Gazelle Pro running 12.10. I have been noticing that the cooling fan runs all the time. Even when the CPU has been idle for hours. Does anyone know if this is a problem? Could there be some config parameter that has gotten messed up that is causing the fan to run continuously? It seems that this will burn out my fan sooner.

Any thoughts on this matter would be appreciated.

---

### Post by krishna.988 on 2013-03-07
I would redirect you to this thread  [http://ubuntuforums.org/showthread.php?t=1907622](http://ubuntuforums.org/showthread.php?t=1907622)

---

### Post by isantop on 2013-03-07
> **b3d said:**
> I have a Gazelle Pro running 12.10. I have been noticing that the cooling fan runs all the time. Even when the CPU has been idle for hours. Does anyone know if this is a problem? Could there be some config parameter that has gotten messed up that is causing the fan to run continuously? It seems that this will burn out my fan sooner.

Any thoughts on this matter would be appreciated.

> **krishna.988 said:**
> I would redirect you to this thread  [http://ubuntuforums.org/showthread.php?t=1907622](http://ubuntuforums.org/showthread.php?t=1907622)

Acutally, the Gazlle doesn't use any proprietary graphics, so there are no other drivers required.

It's normal for the fan to spin all the time in any computer. This helps prevent dust from settling in the cooling system and keeps it running efficiently. 

If the fans are always loud, then that might indicate a problem. See if you can make the fan speed increase by loading the system with a heavy task.

---

### Post by b3d on 2013-03-07
It does not seem to matter what the load is. It seems to be on full speed all the time. This does have nVidia graphics. 
GeForce GTX 460M/PCIe/SSE2 
Intel® Core™ i7-2630QM CPU @ 2.00GHz × 8 
I will try making sure everything is up to date.

---

### Post by krishna.988 on 2013-03-08
Then without doubt It definitely seems to be the driver which is the culprit..opensource drivers are buggy due to lack of specifications by nvidia..your fan is vulnerable to blow off soon..try using the proprietary driver or install windows and check to see if the same happens...

---

### Post by b3d on 2013-03-09
I believe that I am running the proprietary drivers. I have the nvidia-settings program and it indicates that the vendor is NVIDIA Corporation in the OpenGl/GLX section.

And I am NOT going to install Windoze on this System76 machine which has never been sullied by such filth.  ;-)

---

### Post by ManamiVixen on 2013-03-09
[http://ubuntuforums.org/showthread.php?t=1967867](http://ubuntuforums.org/showthread.php?t=1967867)

---

### Post by b3d on 2013-03-12
> **ManamiVixen said:**
> [http://ubuntuforums.org/showthread.php?t=1967867](http://ubuntuforums.org/showthread.php?t=1967867)

This is about it running at high speed. It is a useful tip, but it's not my issue. When I do this, fn-1, then I do get the high speed fan. I'm just wondering why my fan runs all the time, even when it's fairly cool. Perhaps it's just that the fan has always run all the time, but was quiet before?

---

### Post by krishna.988 on 2013-03-12
[COLOR=#222222][FONT=Verdana]See this site:It is a known problem for AMD and Nvidia**:**[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][[COLOR=#0000ff]http://linuxfonts.narod.ru/why.linux.is.not.ready.for.the.desktop.current.html[/COLOR]]("http://linuxfonts.narod.ru/why.linux.is.not.ready.for.the.desktop.current.html")[/FONT][/COLOR]


[COLOR=red][FONT=Verdana]![/FONT][/COLOR][COLOR=#222222][FONT=Verdana] No high quality open source Intel, [[COLOR=#0000ff]NVIDIA[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau")and [[COLOR=#0000ff]AMD[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati")drivers: [/FONT][/COLOR]
[COLOR=#222222][FONT=Symbol]·        [/FONT][/COLOR][COLOR=red][FONT=Verdana]![/FONT][/COLOR][COLOR=#222222][FONT=Verdana] Open Source AMDand NVIDIA drivers do not properly and fully support power management featuresand fan speed management.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]So you can try this to control fan speed:[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana][[COLOR=#0000ff]http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/[/COLOR]]("http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/")
[/FONT][/COLOR]
[http://www.emreciftci.net/2011/07/ubuntu-and-high-cpu-temperature.html](http://www.emreciftci.net/2011/07/ubuntu-and-high-cpu-temperature.html)


[COLOR=#222222][FONT=Verdana]Hope this helps!! Good luck!![/FONT][/COLOR]

---

### Post by garcianc2003 on 2013-05-19
The Gazelle Pro has poor air flow circulation under the laptop. Try elevating it and see if the fan stops running at high speed. In my case, I set my laptop on a couple of books (leaving the vents unobstructed) and that confirmed my suspicion of what my problem was.

I ordered [one of these]("http://www.amazon.com/gp/product/B004ARHYZS/ref=oh_details_o04_s00_i00?ie=UTF8&psc=1"), and that did the trick.

---

### Post by pqwoerituytrueiwoq on 2013-05-19
that is over priced garcianC2003
[http://www.amazon.com/dp/B008TO35G0](http://www.amazon.com/dp/B008TO35G0) - perfect fit for a 15.6" notebook
the fans are detachable you don't have to use them and it even fits in a notebook case

---

### Post by garcianc2003 on 2013-05-20
> **pqwoerituytrueiwoq said:**
> that is over priced garcianC2003
[http://www.amazon.com/dp/B008TO35G0](http://www.amazon.com/dp/B008TO35G0) - perfect fit for a 15.6" notebook
the fans are detachable you don't have to use them and it even fits in a notebook case

Thanks. I am glad I was on the right track.

---

