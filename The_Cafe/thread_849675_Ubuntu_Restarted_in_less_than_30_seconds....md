---
title: "Ubuntu Restarted in less than 30 seconds..."
date: 2008-07-04
forum: The Cafe
---

### Post by acelin on 2008-07-04
I restarted Ubuntu today just to see what would happen if I slimmed the startup process.

Less than 30 seconds to desktop.

Windows Vista on the same computer: 5 minutes 47 seconds.

Enough said.

---

### Post by Lostincyberspace on 2008-07-04
Yeah the last kernel was kind of bulky thats why it's so slow.





(just kidding yeah it's really fast)

---

### Post by Can+~ on 2008-07-04
Try installing bootchart to see if you can cut it even more. Mine takes 30 seconds but without any optimization.

*edit*

Oh yeah, I disabled logging modules and bluetooth; I always disable them when installing. :KS

---

### Post by LaRoza on 2008-07-04
> **acelin said:**
> I restarted Ubuntu today just to see what would happen if I slimmed the startup process.

Less than 30 seconds to desktop.

Windows Vista on the same computer: 5 minutes 47 seconds.

Enough said.

Try slimming the Vista (although I doubt you'll get it down that far)

---

### Post by lukjad on 2008-07-04
Can we get a list of the optimization you did? I did a few myself but am on an older PC so an tweak that might just shave off a second for you wil save about seven for me.

---

### Post by Mazza558 on 2008-07-04
How did Vista take 5 minutes? When my laptop used to have Vista (for a month or so), it booted faster than Ubuntu, e.g 55 seconds (Ubuntu is about 2 minutes).

---

### Post by lukjad on 2008-07-04
> **Mazza558 said:**
> How did Vista take 5 minutes? When my laptop used to have Vista (for a month or so), it booted faster than Ubuntu, e.g 55 seconds (Ubuntu is about 2 minutes).

Now, here's my question to you. ***_WHAT DID YOU DO TO UBUNTU?!?!?_***:mad:























Just kidding. (:

---

### Post by Mr. Picklesworth on 2008-07-04
I set up Readahead to autoload my account during the boot proces, and it's had a really amazingly good impact on time to desktop :)
Instead of getting to the desktop being a process with two distinct waits I can turn the computer on, grab a cup of tea, log in... then as soon as the panel appears I know that it is ready to be used - there is next to no wait between my session starting up and my session being ready to use. It's pretty cool. We really need a "preload files for GNOME/KDE/XFCE session" option in the Login administration!

As for Vista time to desktop, it's been faster than Ubuntu's up until I did that tweak to Readahead. At this point, it and Ubuntu are just about equal. Keep in mind that I rarely use Windows except to play games which I generally install first via Wine in Ubuntu then copy over after learning they don't run there... so Windows still feels like it's straight out of the box.
(Barring the hour it just wasted me with numerous updates that couldn't seem to install themselves on the same shutdown sequence, instead choosing to slow down *three successive* shutdowns... and the wonderful NVidia video drivers)

---

### Post by grossaffe on 2008-07-04
we need a new ubuntu disto for those who want quick reboots.  it can be called REBUTU.

---

### Post by lukjad on 2008-07-04
> **grossaffe said:**
> we need a new ubuntu disto for those who want quick reboots.  it can be called REBUTU.

:lolflag:

---

### Post by acelin on 2008-07-04
Try Gobuntu with just basic drivers.

---

### Post by hansdown on 2008-07-04
> **acelin said:**
> I restarted Ubuntu today just to see what would happen if I slimmed the startup process.

Less than 30 seconds to desktop.

Windows Vista on the same computer: 5 minutes 47 seconds.

Enough said.

Unreal!

---

### Post by hansdown on 2008-07-04
> **Lostincyberspace said:**
> Yeah the last kernel was kind of bulky thats why it's so slow.





(just kidding yeah it's really fast)

That's great humour! A new line of work perhaps?

---

### Post by madjr on 2008-07-04
> **Mr. Picklesworth said:**
> I set up **Readahead** to autoload my account during the boot proces, and it's had a really amazingly good impact on time to desktop :)
I can turn it on, and as soon as the panel appears I know that it is ready to be used. It's pretty cool. We really need a "preload files for GNOME/KDE/XFCE session" option in the Login administration!

As for Vista time to desktop, it's been faster than Ubuntu's up until I set up Readahead. At this point, it and Ubuntu are just about equal. Keep in mind that I rarely use Windows except to play games which I generally install first via Wine in Ubuntu then copy over after learning they don't run there... so Windows still feels like it's straight out of the box.

i heard Ibex will boot-up faster, will they use that "**Readahead**" thing you mentioned?

---

### Post by Lostincyberspace on 2008-07-04
> **hansdown said:**
> That's great humour! A new line of work perhaps?
More like the only line ever!

---

### Post by steveneddy on 2008-07-04
I have always had less than one minute boot times from stone cold to desktop, providing I'm on top of the log in screen.

But it will get to the log in screen in 45 seconds.

That's fast enough for me.

The last job I had the owner used his Vista laptop daily and I used my Ubuntu Gutsy (at the time) laptop and he would boot in the morning and it was way over 5 minutes, close to ten minutes sometimes.

He hated the fact that I could boot up and down in under a minute and get more done than him.

Funny.

---

### Post by Lord Xeb on 2008-07-05
My Ubuntu takes about 45 - 50 seconds to desktop. It just depends. But usually it is in the low 40s>_> With WinXP, my IBM ThinkPad T43 took 2 minutes 45 seconds to almost 3 1/2 minutes to freaking boot to desktop. Also, Ubuntu shutdown in less than 30 seconds >_> Compared to XP which took 1-2 minutes.

---

### Post by HansKisaragi on 2008-07-05
Takes me 25 sec to boot for me, according to bootchart.

---

### Post by barbedsaber on 2008-07-05
My ubuntu takes for freaking ever, I need to get LILO fixed, please PM me if you know a lot about LILO, and I will make a thread so everyone can benefit.

---

### Post by YaroMan86 on 2008-07-05
Why use LILO? GRUB is more reliable/easier to configure.

---

### Post by Mr. Picklesworth on 2008-07-05
> **madjr said:**
> i heard Ibex will boot-up faster, will they use that "**Readahead**" thing you mentioned?

Gee, that was cruel of me to not post the link!
Here: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

Ubuntu has used Readahead for a while, but it can be used for much more than it does out of the box. It doesn't preload user sessions since that would make a lot of dangerous assumptions. Naturally, we can happily make those assumptions ourselves and command it to do so.
Warning: Know what you are doing *before* following that guide :P

It doesn't necessarily speed up your startup time, but it solves a big problem we have right now: Logging in and booting up both involve notable, uncomfortable wait times. It is better to have one longer wait after which the computer is completely ready!

---

### Post by barbedsaber on 2008-07-05
> **YaroMan86 said:**
> Why use LILO? GRUB is more reliable/easier to configure.

Looooooong story, but in short, when I use grub, my cd is not recognized by ubuntu or vista. (it is with windows bootloader, and LILO.)

---

### Post by Mazza558 on 2008-07-05
> **lukjad007 said:**
> Now, here's my question to you. ***_WHAT DID YOU DO TO UBUNTU?!?!?_***:mad:

Nothing :( It's just that slow...

It's probably the ATi Drivers and Compiz.

---

