---
title: "External Monitor for laptop"
date: 2011-07-02
forum: System76 Support
---

### Post by bakelitedoorbell on 2011-07-02
Hello, I own a Serval Pro (Serp5) with the optional 1920x1200 matte screen, and am considering getting an external monitor for it.  I have never used a monitor with a laptop, so not sure how it works.  

What do I need to know in terms of compatibility, ports and cables?  Would I have to change something in preferences to use it?

---

### Post by gamerchick02 on 2011-07-03
Not sure what ports your Serval came with, but take a look; you probably have VGA or HDMI ports.

You just hook your external up to your VGA or HDMI port, and ta-da, you have extra screen real estate (after you configure your graphics card to deal with it).

You can probably buy any monitor you want. I'm using a Westinghouse LCD panel that outputs 1280x1024.

I'm not sure if a store will allow you to bring your laptop in and hook it to the monitor you're interested in trying, but it's worth a shot.

Amy

---

### Post by bakelitedoorbell on 2011-07-03
Thanks for the reply Amy

It has a DVI and HDMI port, and a NVIDIA GeForge GTX 260M.  So I can just get any monitor?  That's cool, with Linux I usually have to check if there is a driver, so I wasn't sure.

---

### Post by gamerchick02 on 2011-07-05
You're welcome.

Generally any monitor will work, but if you're going to buy one in a store, it can't hurt to wander into the shop and hook your computer up to it and make sure it works.

Amy

---

### Post by fancy_ninja on 2011-07-13
Hiya bakelitedoorbell-I see that this thread is a week old but I thought I'd put in my 2 cents! Hope you got a monitor you liked and things are working out-but just in case you're still looking around, I have a suggestion. I'm on a Gazelle Professional and whenever I hook up to my TV at home or the projector at my school I use an HDMI cable. Please check out my friend's post here: [http://ubuntuforums.org/showthread.php?t=1781792](http://ubuntuforums.org/showthread.php?t=1781792) for info on how to configure the additional screen in Nvidia X Server Settings; it's pretty easy-when you're in the preferences dialog open that link and follow the steps--works like a charm! I agree with Amy--see if you can take your laptop in the store and hook up there to test it out! Make sure to give the audio a run too while you're there. Hope that helps!

---

### Post by HotShotDJ on 2011-07-13
I'll also add my "2 cents" here since I often use an external monitor with my Pangolin (PanP5, Nvidia GeForce G105M).  This laptop has the options of standard VGA or HDMI... I've only used the VGA port.  On my set up, I typically use TwinView to extend the desktop to the external monitor.  It should also be possible to turn off the laptop monitor and use the external monitor by itself, although I've haven't done this myself.

[LIST=1]
[*]**NVidia "Feature" with Dual-Monitor Set Up**: Be warned -- GPU Scaling does not work with NVidia chip-sets with an external monitor attached and both monitors turned on.  The GPU remains at its highest setting at all times.  This can be an issue with laptops, since it will create a lot of heat.  At best, it creates a noisy laptop with the fans running on high all the time.  At worse, it can over-heat your laptop causing system instability and even system failure. (see: [http://www.nvnews.net/vbulletin/showthread.php?p=2027196#post2027196](http://www.nvnews.net/vbulletin/showthread.php?p=2027196#post2027196)).  NOTE:  If you turn off the internal monitor and use only the external monitor, this should not be an issue.
[*]**Ubuntu 11.04 & Dual Monitor Set-Up**: Ubuntu 11.04 doesn't play well with a dual monitor setup.  I was able to get things configured so that 11.04 w/ Unity would display properly with TwinView (using standard NVidia settings tool)... BUT, when I booted with the external monitor disconnected, the screen was all wonky with no way to correct the problem other than booting up to the CLI and removing the offending /etc/X11/xorg.conf.  In classic mode, it worked a bit better, but with the external monitor disconnected, the desktop was still extended onto the non-existent external monitor.  Not good.  (This is also a problem in OpenSuSE 11.4, but it is correctable using SCPM + SUMF).
[/LIST]

SUMMARY:  If you will be using the external monitor with the internal monitor turned off, I don't foresee any major problems for you.  Go ahead and purchase whatever monitor you fancy and you should be good to go after a bit of configuring using "nvidia-settings."

If you will be using the external monitor to extend your desktop, you will probably have some problems.

Best of Luck, and most importantly... HAVE FUN!

---

### Post by gamerchick02 on 2011-07-15
Sorry to hijack the thread, but HotShotDJ, have you had problems with the binary driver?

I'll use the binary driver and xorg will chomp all of my available CPU and my computer will slow to a crawl.

I'm using the same GPU and Natty with external monitor.

I use it to extend my desktop.

I'm just trying to figure out if I'm the only one with this issue or not.

I have to use the nouveau drivers, because if I don't, my computer will heat up and slow down.

Amy

---

### Post by HotShotDJ on 2011-07-15
> **gamerchick02 said:**
> Sorry to hijack the thread, but HotShotDJ, have you had problems with the binary driver?Hi, Amy --

Yes, I use the proprietary driver directly from NVidia.  I've tried the nouveau with experimental 3d support, and they were so slow, I thought I was going to cry (I use OpenSuSE 11.4 + Gnome 3, so 3d is a must).

I skimmed your other thread and I suspect your issues are related to the fact that when using two monitors at the same time, the NVidia drivers disable GPU scaling.  Although, I haven't experienced the slow-downs that you describe, the chassis fan is on all the time, creating a very noisy environment.  I have used silent mode (the botton marked with an M, third in top-left button pod over keyboard on the PanP5) which quiets things down (although I start to worry about over-heating due to the GPU scaling problem).

I do wonder if your problem might be that your fan is not producing enough air-flow, thereby over-heating your system.  That could account for the system slow-down and possibly the instability with xorg.  Also, you've said that using the nouveau driver prevents the problem, which does seem to support my hypothesis.

Have you tried taking the chassis apart and cleaning out the fan and airway?  If you've already done that, you might write to System76 and ask them to replace the chassis fan.  I would imagine that your PanP5 is no longer under warrantee, so there might be some cost involved. Or you might try one of those laptop cooling mats that are available at most big-box electronic stores (such as Best Buy).

---

