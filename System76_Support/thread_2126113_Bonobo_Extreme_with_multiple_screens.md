---
title: "Bonobo Extreme with multiple screens"
date: 2013-03-16
forum: System76 Support
---

### Post by hsarvell on 2013-03-16
Hi guys, I'm thinking about buying the Bonobo Extreme (bonx6).

I would then like to connect two Apple LED 27" screens to it for a total of 3 if you include the laptop's own screen. Each Apple screen has a resolution of 2560x1440.

Would that work without any issues or does hardware and/or Ubuntu drivers or software limit it? Note that I want Compiz to work on this setup too, also note that I would have to find some kind of HDMI -> DP adapter for the HDMI out port, this adapter needs to be able to handle 2560x1440.

This stuff is not my forte and I haven't been able to find any definitive answers by googling either so sorry if it's a stupid question.

---

### Post by 3Miro on 2013-03-16
The video card and the Nvidia drivers under Linux have more then enough power to let you work on two 1440 monitors.

Having said that, Apple monitors are a bad choice. I am not sure if the Thunderbolt monitors can even work with non-Apple systems and the older Cinema monitors work only on **Mini**-Display port. Bonobo comes with regular display port and adapters for regular to mini DP are at best rare (I couldn't find any on newegg). Furthermore, there are DP to HDMI adapters, but HDMI to DP adapters do not exist. On top of that, unless you already have two Apple monitors, you should consider something cheaper and at least as good (i.e. Asus PB278Q). At work, I am one Linux guys surrounded by Apple people and my Asus is at least as good as the Apple monitors.

If you get the Asus monitors (or something of that type), you need to use both the DP and HDMI ports on the laptop. DP should run without any issues, I am using my Asus monitor with a desktop and DP, no problems at all. I just use the Nvidia utility and everything works great. However, getting HDMI to run 2560x1440 is tricky. Here is a thread of mine where I had to work on the issue:

[http://ubuntuforums.org/showthread.php?t=2120497](http://ubuntuforums.org/showthread.php?t=2120497)

Note that the Nvidia driver may not play well with xrandr and you may have to use something from the Nvidia-settings tool, I am not sure what or how.

---

### Post by hsarvell on 2013-03-17
Hi 3Miro, thanks for the Asus tip and the help, no need for the Apple screens, will avoid them if it's going to be like that. Just to confirm, you're actually running two extra screens with 2560x1440 yourself or are 100% sure it's doable?

---

### Post by 3Miro on 2013-03-17
I do not have a Bonobo laptop, I only have a Pangolin one. Pangolin can run one monitor at 1440 (see my thread). I have run two 1440 monitors on a desktops like Leopard extreme.

The only reason why Bonobo may fail to run the two monitors is the HDMI port.

---

### Post by isantop on 2013-03-18
> **3Miro said:**
> Note that the Nvidia driver may not play well with xrandr and you may have to use something from the Nvidia-settings tool, I am not sure what or how.

Note that as of the 304 driver, Nvidia has built-in XRandR support, so you can use the built-in Ubuntu utility for this.

---

### Post by 3Miro on 2013-03-18
I didn't know that, I've had issues with the Nvidia drivers not agreeing with the rest of the settings and system tools, but it is good to know that they have fixed at least this one.

Thanks for the info, isantop.

---

