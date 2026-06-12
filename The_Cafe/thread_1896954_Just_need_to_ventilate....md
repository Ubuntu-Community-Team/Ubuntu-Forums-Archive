---
title: "Just need to ventilate..."
date: 2011-12-18
forum: The Cafe
---

### Post by NikoC on 2011-12-18
... and ask you guys to help me put things in perspective!

I've been around linux and ubuntu for quite some time, it must have been 6 years or more! Recently I switched to Kubuntu 11.10, because I'm not a huge fan of the new Ubuntu desktop experience, flavours differ, right?

I use my laptop (dell E6510) on a professional level, i.e. I teach practical courses in biochemistry and physiology at university and have been happy with the progress made by ubuntu over the years! It actually has become or is becoming mature and my main OS. Yet after the last kernel upgrade (3.0.0-15) suddenly suspend no longer works, resulting in a black screen after resume. I use this function quite often, as I spend time either in the lab, either in the office and drag my pc along, so not having to shutdown time and time again is quite 'nice'.

For this bug, no solution is available yet and by far I'm not leaving the 'linux way'... but sometimes, maybe it's the gloomy weather outside affecting my mood, I don't feel like thinkering for hours -again- to get things running, especially when all was fine before (no, installing previous and older kernels, suggested solutions, etc. don't do the trick either)... though I have to admit, it is quite fulfilling to get things working after a couple of hours of command line :-)

And maybe I'm wrong, but I think these regressions and subsequent inconveniences are partly co-responsible for people not embracing or appreciating linux to the fullest. Somewhere along the line you get an excellent fine tuned system, running fast as lightning and out of the blue a bug pops up reducing productivity, creating an 'Oow no not again feeling'... though the annoyance is minor in my case, it still is another annoyance in a long line of annoyances! And I'm not sure if 'loosing' time like this would be tolerated in a corporate environment!

Your thoughts? Preferably positive ones ;-)

---

### Post by mikewhatever on 2011-12-18
Regressions happen, even in a corporate environment. Not really sure there is anything we can do.

On a more practical note, 3.0.0-15 seem to be still in the proposed repository, or, in other words, in testing. Perhaps you shouldn't be testing, if that particular machine needs stability.

---

### Post by BC59 on 2011-12-18
You are using kernel 3.0.0-15, so I assume you are installing pre-released updates.
How you can use your computer in professional level and simultaneously using the same computer for experimenting purposes? 
Using pre-released staff means you are confronting crashes every once in a while.

---

### Post by keithpeter on 2011-12-18
Hello NiKoC

Ventilation is always good!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/904569](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/904569)

Suggest you add yourself to the bug above? Looks related.

[http://ubuntuforums.org/showthread.php?t=1891915&highlight=install+a+previous+kernel](http://ubuntuforums.org/showthread.php?t=1891915&highlight=install+a+previous+kernel)

This post suggests a method for booting into previous kernel by un-installing the recent one. I'd personally just set the 3.0.0.14 kernel as my 'default' in grub and leave the linux package installed so that a future updated kernel will be installed.

PS: I have Debian Stable on this PC as my stable fallback

---

### Post by HermanAB on 2011-12-18
Well, don't fix it if it ain't broke!

Once you got your machine to work properly again, turn the auto-update / auto-screw-up feature off.

---

### Post by Docaltmed on 2011-12-18
I know what you mean...I'm sitting here in front of a laptop with quad cores, more memory than you can shake a stick at, graphics to make your eyes water...and I have to reboot the damn thing after every time it goes into suspend. I should dig around and see if I can come up with a solution for it, roll up my sleeves, fire up a terminal, but I really don't feel like doing that right now.

Meh. It's part of the price I pay for having extraordinarily flexible, configurable, powerful and free software. 

Fair trade-off, I think. 

Good luck with the resume thing. I know, it's a PITA.

---

### Post by NikoC on 2011-12-18
And that's why I like the forum that much :)

Always some good advice! Hadn't really thought about disabling pre-released updates, so I'll try that as soon as I'm on my linux machine! I wasn't really consciously aware that I was using pre-released sources, must have ticked it some day out of curiosity and never really had any problems before! So unticking would roll back my current kernel!

I'll also subscribe to the bug report!

Should have 'ventilated' on Wednesday and save me a couple of days of irritation ;-)

Thanks

---

### Post by mikewhatever on 2011-12-18
> **NikoC said:**
> And that's why I like the forum that much :)

Always some good advice! Hadn't really thought about disabling pre-released updates, so I'll try that as soon as I'm on my linux machine! I wasn't really consciously aware that I was using pre-released sources, must have ticked it some day out of curiosity and never really had any problems before! So unticking would roll back my current kernel!

I'll also subscribe to the bug report!

Should have 'ventilated' on Wednesday and save me a couple of days of irritation ;-)

Thanks


Unticking the proposed repository will not roll anything back or forward. Either uninstall 3.0.0-15 or select an older kernel from the Grub menu.

---

### Post by NikoC on 2011-12-19
> **mikewhatever said:**
> Unticking the proposed repository will not roll anything back or forward. Either uninstall 3.0.0-15 or select an older kernel from the Grub menu.

Will do! I've been directed to some useful pages concerning the matter! Thanks!

---

### Post by whatthefunk on 2011-12-19
[annoying_English_teacher]I usually use a fan for ventilation.  Maybe an open window.  
However, when I want to **vent** I usually post a rant on the forums:)[/annoying_English_teacher]

---

### Post by forrestcupp on 2011-12-19
> **whatthefunk said:**
> [annoying_English_teacher]I usually use a fan for ventilation.  Maybe an open window.  
However, when I want to **vent** I usually post a rant on the forums:)[/annoying_English_teacher]

Maybe the OP just needs some fresh air. :)

---

### Post by Bucky Ball on 2011-12-19
Advisable for production machines/servers to use LTS releases. Most stable, currently 10.04 LTS, supported until April 2013. Wouldn't dream of using 11.10 on my work machine. As far as I can see it is fairly buggy on some machines and may/may not get all these fixed before EOL. Next LTS (12.04) out next April and that would be a main focus for devs at moment. You may want to seriously think about sticking with LTS releases if you want reliability/stability (the latest releases are not necessarily the greatest and no always advisable for this) but I'd wait a few months after 12.04 is released before installing.

(PS: LTS releases give you the option of upgrading to the next LTS release when available via Software Sources (Update Manager>Settings).)

---

### Post by BrokenKingpin on 2011-12-19
I do feel your frustrations. I had a similar issue with the touchpad on my netbook where it was broken from an update.

I think the issue is that the kernel is so big and there are so many devices to support it is impossible for them to test everything when they make a change. Hopefully this gets better as time goes on.

As a possible quick solution to your suspend issue, why not boot with your old kernel from the grub menu, at least until they push out a fix?

---

### Post by NikoC on 2011-12-19
Well the sun was shining today, installed kernel 3.0.0-14 and locked it as suggested! Unmarked pre-released updates, good to go and happy again :-)

Thanks folks!

---

### Post by Artemis3 on 2011-12-19
> **NikoC said:**
> Will do! I've been directed to some useful pages concerning the matter! Thanks!

From personal experience, never ever enable Proposed (thats for package developers), it can break your system, specially when a new release is coming. Backports is fine tho.

Also, serious work needs stability, consider staying in LTS once its out in April; the 6 month releases should only be used with hobby machines you don't mind breaking from time to time (ie. home) where you have plenty of time to research issues and apply solutions.

---

### Post by Bucky Ball on 2011-12-19
> **Artemis3 said:**
> 

Also, serious work needs stability, consider staying in LTS once its out in April; the 6 month releases should only be used with hobby machines you don't mind breaking from time to time (ie. home) where you have plenty of time to research issues and apply solutions.

+1. A stable LTS on one partition and whatever latest release for tweaking, learning, experimenting on another partition. Bugs in six monthly release may never be fixed by the time their support ends ...

---

### Post by user1397 on 2011-12-20
Hmm so I just installed kubuntu 11.10 on my laptop, and it seems to have this issue with any kernel...:(

---

### Post by NikoC on 2011-12-20
> **Bucky Ball said:**
> +1. A stable LTS on one partition and whatever latest release for tweaking, learning, experimenting on another partition. Bugs in six monthly release may never be fixed by the time their support ends ...

True, yet a small remark: a couple of months ago I received a new laptop from work and hardware support is significantly better on the latest (K)Ubuntu release, that was mainly the reason for me to do the upgrade!

But now I've learned the hard way, that once you got your system up and running on a 'professional' machine, you should keep it that way and avoid pre-released updates! It's only since a year or so that I actually made the full switch to linux, in the past it was only for 'playing' around!

---

### Post by shreepads on 2011-12-20
> **Bucky Ball said:**
> Advisable for production machines/servers to use LTS releases. Most stable, currently 10.04 LTS, supported until April 2013. Wouldn't dream of using 11.10 on my work machine. As far as I can see it is fairly buggy on some machines and may/may not get all these fixed before EOL. Next LTS (12.04) out next April and that would be a main focus for devs at moment. You may want to seriously think about sticking with LTS releases if you want reliability/stability (the latest releases are not necessarily the greatest and no always advisable for this) but I'd wait a few months after 12.04 is released before installing.

(PS: LTS releases give you the option of upgrading to the next LTS release when available via Software Sources (Update Manager>Settings).)

Not too sure about that... Because of the way it works you are often significantly behind the curve if you're running the standard LTS version, in terms of both hardware (e.g. no TRIM for SSD) and software (e.g. extremely old GStreamer).

Yes you can use backports but they don't always work well (and come with a if-it-doesn't-work-don't-blame-us support policy). For e.g. using the kernel backport to get SSD support on Lucid didn't work too well for me (power management issues)...

---

### Post by forrestcupp on 2011-12-20
> **NikoC said:**
> True, yet a small remark: a couple of months ago I received a new laptop from work and hardware support is significantly better on the latest (K)Ubuntu release, that was mainly the reason for me to do the upgrade!

But now I've learned the hard way, that once you got your system up and running on a 'professional' machine, you should keep it that way and avoid pre-released updates! It's only since a year or so that I actually made the full switch to linux, in the past it was only for 'playing' around!

Good observation. Most of the time, doing an upgrade after the release will be fine. It's the alphas, betas, and pre-released updates that are usually the cause of trouble. But if you're upgrading a production machine, you should always remember to back up all of your sensitive files and data.

---

### Post by burntpuppy on 2011-12-21
I had a similar issue with my Dell e5510, I ended up reverting to 3.0.0.13, issues went away. BTW I didn't select this update from a development directory, it was put there by the updater.
Pat

---

### Post by jackill on 2012-01-21
I have asus u30sd laptop. Yesterday I've upgraded to 3.0.0-15 and my suspend stop to work. I.e. I select suspend, my screen turns black (but not off) then it on again and offer me an unlock screen dialog.

I have to say that that the laptop already had problem with sleep and they was corrected by custom script in /etc/pm/sleep.d. And this script turns off all usb buses when notebook goes to sleep and turns on them back when it's wake up.

So I find out that usb do not come back. And that mean that part of script no longer work.

I've check dmesg but didn't find any problem.

Script turning off only ehci. I found another script that turns off also xhci bus.

You can find it there [http://kubuntu.ru/node/9111](http://kubuntu.ru/node/9111) (that's Russian resource)

And now my laptop suspend and hibernate without any problem on 3.0.0-15 (by the way packages hibernate and uswsusp were already installed on my laptop).

Maybe it will help someone there who has the same problem with suspend.

---

