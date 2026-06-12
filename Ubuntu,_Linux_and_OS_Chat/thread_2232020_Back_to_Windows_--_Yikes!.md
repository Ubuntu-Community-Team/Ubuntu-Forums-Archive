---
title: "Back to Windows -- Yikes!"
date: 2014-06-29
forum: Ubuntu, Linux and OS Chat
---

### Post by websquad on 2014-06-29
I've had it with Ubuntu 14.04 -- at least for a while.  I've been spending too much time trying to find a 14.04 configuration that would work for me -- for my projects -- for my workflow.  

I need three monitors.  This was a no-brainier configuration under Windows XP and then Windows 7 (I've not ventured into the never-never land of Windows 8).  No special drivers.  No fuss.  I just added a used graphics card snatched off of Craig's list, plugged it in, plugged in a couple of monitors, clicked a few mouse buttons, and I was off and running (well, I later added a 4th monitor, cause (1) I could and (2) I had one gathering dust).  Stardock Fences mades icon management a breeze.

The way I do websites (I'm a hand-coder), my work-flow begs for three monitors -- so I need at least three.

I've spent (wasted?) hours looking through the forum for some happy camper that has 14.04 (the thought of stability is appealing) and three monitors in an extended desktop array.  My conclusion is that 14.04 ain't ready for prime time in the configuration I want.

So, I'll pop-in a reminder on my calender a year from now and see what's happening.  Meanwhile, I'll quit worrying about 14.04.  *Except I have it on an old laptop I saved from the recycle bin -- works fine!*

Sigh.

My "Ubuntu" rig: a Dell Optiplex 745 Minitower with an Intel Q965 Express Chipset, Intel Core 2 Duo processor, 8GB RAM, and a 305W power supply, integrated graphics adapter.  Since I'm not a game player, my graphics needs are simple.

So long for now.

---

### Post by philinux on 2014-06-29
Moved to Ubuntu, Linux and OS chat

---

### Post by mastablasta on 2014-06-30
first - Windows 8.1 is not THAT bad. i was a bit afraid of it but they ocnfigured it nicely on my working mashcine so appart from different launcher and few strange sjhortcuts nothing of notice...

second - Ubutnu was not really made with multiple monitors in mind. have you tried other desktops such as those in Kubuntu, Xubuntu or perhaps the one in Linux Mint Cinnamon?

not sure what the issues were you encountered and what you expect to have. i onyl tried Kubuntu a couple of times on 2 screens (mainly by "mistake" since GPU recognised TV as screen one :-) ). anbyway different resolutions, different dispalys all worked well. monitor is 19" 4:3 ratio (8 or 9 years old), TV is a lot bigger (i think 42" or something like that with 16:9 ratio). no issues with this setup (except i didn't want the TV as first interface (easilly changed). oh and the GPU is old AMD Radeon that has only opensource drivers available.

what were your issues? what GPU you used? if you use two GPU you likely need proprietary drivers. and for that it's best to use nVidia. i am not sure if opensource would work. though they might. i never tried with more cards (i don't have enough GPU cards for that). i do know that people do use linux with multiple monitors. might be good to know what issues you had so others can avoid them.

yeah Windows still has better drivers support. in the end use what works best for you.

---

### Post by websquad on 2014-06-30
[FONT=trebuchet ms]mastablasta,[/FONT] thanks for your input.  It just so happened that yesterday afternoon I found, in one of several stacks in my home office, a sealed and otherwise unused copy of Windows 7 32/64-bit.  I loaded the 64-bit and the license number validated on-line with Microsoft.  

My main objective for this system is to have a backup machine using open-source applications, including Gimp.  I'll purchase a graphics card from amazon.com that supports three monitors and advertises itself to support Ubuntu/Linux, and if the market place (demand driven, I assume) catches up so that an idiot like me can install multiple displays, I'll switch over to some version of Linux/Ubuntu.  Thanks for your comments.

For what it is worth, I tried one low-end card from the used computer store, and it would only support two monitors under Ubuntu and would not support desktop extension.

[SIZE=4]***[FONT=comic sans ms]Bob[/FONT]***[/SIZE]
[SIZE=1]<><[/SIZE]

---

### Post by QIII on 2014-06-30
Hello!

Just for giggles and grins, I thought I'd let you know that I use three monitors with a single desktop spanning them.

If you are having difficulty doing that, then the culprit is more than likely OEM support, not Linux itself.  Remember that OEMs write drivers, not Microsoft nor Canonical.  That it works in Windows is due to the fact that the OEMs make sure it does so it can be blessed and included in the MS driverbase and thus be PnP.  So let's not say Trusty is not ready for prime time.

Be that as it may, you have  need that can be better fulfilled using Windows, so, by all means, use Windows! :)


[http://i.imgur.com/MZ0yu0a.jpg](http://i.imgur.com/MZ0yu0a.jpg)

---

### Post by websquad on 2014-06-30
QIII -- 

[LIST=1]
[*]What video graphic adapter do you use (make & model number)?
[*]What is the source (including version) of your device driver?
[*]Can the device driver be installed without excessive command line activity?
[*]Bottom line: can a Linux/Ubuntu install this?
[/LIST]

Thanks!

---

### Post by QIII on 2014-06-30
Definitely using Linux, as I have for years.

This is on a venerable old XFX ATI HD 5870 with two DVI outputs, a VGA output and a Display Port.  It is Eyefinity enabled, which allows it to output on both DVI ports and the Display Port.  Eyefinity is what makes this possible with this card, and Eyefinity works with Linux.

The GPU is driven by the ATI Driver available from the Trusty repo.

It can be installed quite easily without touching the terminal by using the additional drivers GUI.


If you want to use the terminal, as is my preference:

```
sudo apt-get install fglrx-updates fglrx-amdcccle-updates xvba-va-driver
```

followed by 

```
sudo amdconfig --initial
```

Reboot.

For some hardware acceleration:

```

sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```

---

### Post by DuckHook on 2014-07-03
[ATTACH=CONFIG]254409[/ATTACH]
Screenshot of my four-monitor system with all monitors (1200x1600) configured in portrait mode. Running on stock radeon driver &#8213; lspci info below:```
duckhook@19th_hole:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950] [1002:679a]
    Subsystem: Hightech Information System Ltd. Device [1787:201c]
    Kernel driver in use: radeon
```One monitor attached to each of following outputs: DVI, HDMI, DP1, DP2.

Since 12.10, has worked out of the box with absolutely no muss, no fuss. Had to compile AMD proprietary driver in 12.04, but that worked flawlessly thereafter also.

Hope this helps.

---

### Post by squakie on 2014-07-03
Duckhook:  all I can say is WOW!

---

### Post by websquad on 2014-07-03
> **DuckHook said:**
> [ATTACH=CONFIG]254409[/ATTACH]
Screenshot of my four-monitor system with all monitors (1200x1600) configured in portrait mode.
Duckhook, all I can say is Wow x 4!  What an exciting configuration.  Thanks for sharing.

---

### Post by impliedconsent2 on 2014-07-03
> **DuckHook said:**
> One monitor attached to each of following outputs: DVI, HDMI, DP1, DP2.

Since 12.10, has worked out of the box with absolutely no muss, no fuss. Had to compile AMD proprietary driver in 12.04, but that worked flawlessly thereafter also.

Hope this helps.

Ditto on 3 monitors 14.04 DVI-I; DVI-D; HDMI.  Attached a 4th to the (Haswell 4670k) Intel 4600 via HDMI and it worked flawless as well - the monitor, well, lets just say that when bigger dogs run, they get tangled in stuff at the expense of other stuff. :KS

---

### Post by DuckHook on 2014-07-03
For what it's worth, people tend to report problems in multi-monitor setups when they try to run two or more different video cards. When running everything out of a single card, Linux tends to do fine &#8213; provided the card is relatively recent and therefore supported.

Although it looks impressive at first glance, this setup was not all that expensive. The AMD 7950 set me back some, but the monitors were all second-hand items from an office clearance that I bid for when they were upgrading their equipment. Old LG 2010Ps that I bought for $30 each. The DP converter cables ended up costing almost as much! The only drawback is that these old monitors consume a lot of electrons and really overheat my den in the summertime. Toasty warm in winter, though.

Also, when doing multiple monitors, it's best to make all of your monitors the same size (even the same model, as I did). I've found that the fewer the variables, the less you need to juggle to get things working.

---

### Post by themainliner2 on 2014-07-07
All I can add to this is my own best wishes for you back in Windows. I find it increasingly frustrating in that (Windows) environment, as I become more proficient (at home) in Linux, and I have about a decade more engineering experience in Windows (professionally). I only have two monitors. They work perfectly in all mah linux installs including Ubuntu 14:04. I'm using the nVidia proprietary driver, with mah aging 460 GTX, and there are some sweet GUIs out there that install the the driver no issue: see **Additional Drivers** in Ubuntu. In Debian the **SMXI** script ([smxi.org]("http://smxi.org")) is text based but also automates the driver install - no problems. Linux and Ubuntu are more than capable of running your setup. Better luck finding the answer that works for you next time you come back. In 2004 - 6 I oscillated between the two OSes, Windows and Linux, until I finally jumped when I got all my particular needs addressed.

I hope you do the same. Come back soon!

---

