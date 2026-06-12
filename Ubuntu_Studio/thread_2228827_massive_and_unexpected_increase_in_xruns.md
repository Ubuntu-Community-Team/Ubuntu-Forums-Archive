---
title: "massive and unexpected increase in xruns"
date: 2014-06-09
forum: Ubuntu Studio
---

### Post by halfbeing on 2014-06-09
Hello.

Recently I have noticed a massive increase in the number of xruns I get when using Jack. I can't time it exactly, but it is possible that this may be a consequence of the upgrade to Trusty.

I use Jack to run Reaper via wine-rt (real-time Wine). Wine-rt is a non-Ubuntu package, was therefore installed independently and so has not been upgraded for a long time, i.e. it is the same version of wine-rt I have been using both before and after this problem started occurring.

Before I could run at around 10ms latency with not very many xruns. Now if I run at 20ms latency with anything but the very lightest plugin load in Reaper, I get huge numbers of xruns. If I run at 10ms latency the buzzes and crackles are constant. I have checked that there are no other applications using huge amounts of CPU (the biggest user is Chromium, but it hasn't been using all that much CPU.

I remember I had this problem several years ago when a nicely behaving Jack unexpectedly turned nasty. I ended up switching to Windows until an unresolvable interrupt conflict made Windows 7 behave even worse and I was forced to switch back to Linux, where Jack had started to play nicely again for no obvious reason. But now I have come full circle.

Does anyone have any idea what is causing this variable behaviour?

---

### Post by CrocoDuck on 2014-06-16
Hi! It is hard to say why, since only you can know your configuration and how an update could have broken it. My suggestion is to try to set up best you can the configuration of your system again, as well as have a good look at jack messages (you could repost them too, btw ;)). [Here]("http://www.linuxmusicians.com/viewtopic.php?f=19&t=10837") I summed up the intervetion required to set up a lowlatency linux (it is about ArchBang linux, but most is pretty general). Have a look at [here]("http://wiki.linuxaudio.org/wiki/system_configuration") also.

---

### Post by halfbeing on 2014-06-17
Thanks very much for those links. My goodness it's complicated! I will work through those howtos when I get a bit more time. For the time being I have switched to working on an old desktop machine, also running Ubuntu Studio, and I am getting few enough xruns that I can do some decent recordings. As a fairly wild guess, I wonder  whether the difference in performance might have something to do with an IRQ conflict, although not the same IRQ conflict that I had when I tried to use Windows. But that is nothing more than a hunch.

---

### Post by CrocoDuck on 2014-06-17
> **halfbeing said:**
> As a fairly wild guess, I wonder  whether the difference in performance might have something to do with an IRQ conflict, although not the same IRQ conflict that I had when I tried to use Windows. But that is nothing more than a hunch.

This could give some hint that way:

```

cat /proc/interrupts

```

```

ps -eLo pid,cls,rtprio,pri,nice,cmd |grep -i "irq"

```

rtirq should be helpful (and default installed, if I am not wrong). Have at look at [here]("http://wiki.linuxaudio.org/wiki/system_configuration#rtirq"), adjust the line RTIRQ_NAME_LIST="rtc snd usb i8042" to your needs (keep the timers, as rtc, first place). Make sure the users have [access to the timers]("http://wiki.linuxaudio.org/wiki/system_configuration#hardware_timers"). Depending on your BIOS you could be able to assign IRQs manually to some device (if you try it remember: be very careful with BIOS! If you spot some IRQs conflict try with rtirq configuration first). Have you [set the noatime parameter]("http://wiki.linuxaudio.org/wiki/system_configuration#noatime") for your filesystem? It can be very effective. If you have a ext3/ext4 filesystem try it!

[QUOTE=halfbeing]My goodness it's complicated![/QUOTE]

Naah... not as much as you would guess at first sight... You just have to edit some configuration file... You want to save backups of the confs you edit by the way (doing so you will be able to "undo" if something go wrong ;-)). A week ago I had to format my computer due to hardisk failure (damm you old drives!), I've took only 15 minutes to sit my configuration back (I think I am the person for which the tutorial I wrote is more useful... that page is a backup my configuration :p). Give a go to [quickscan]("http://wiki.linuxaudio.org/wiki/system_configuration#quickscan"): it will check your system and suggest what to do!

---

### Post by halfbeing on 2014-06-17
Thanks for such a comprehensive answer! I will bookmark it and get onto it in a day or two when I have time.

Thanks also for sharing your music. Some of it I enjoyed very much. I look forward to hearing more. Here is what I finally managed to record last week once I'd switched to that other machine :D [https://soundcloud.com/i-am-robert-persson](https://soundcloud.com/i-am-robert-persson)

---

