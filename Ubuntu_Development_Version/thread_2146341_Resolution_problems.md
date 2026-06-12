---
title: "Resolution problems"
date: 2013-05-18
forum: Ubuntu Development Version
---

### Post by MarkX on 2013-05-18
When are the monitor resolution peroblems going to be solved? Countless thousands of people have monitors that are not detected and are stuck on low resolution. Long winded "fixes" either don't work to begin with or don't work because versions change. I am absolutely fed up with this!!!

---

### Post by dino99 on 2013-05-18
Do i need to understand you are one of the countless ?  Bad, bad mood :(
but devs cant fix user's misunderstanding or non genuine usages, and so on
here we can help about detailed trouble; but whining is useless.

---

### Post by grahammechanical on 2013-05-18
And I am absolutely fed up with people like you demanding of people like me answers that we cannot give!!! See, I know where the exclamation mark key is also!!!!

Take this up with the owners of proprietary video drivers or help the developers of the open source video drivers. Or pay a lot of money for a proprietary operating system, the owners of which force monitor makers to provide drivers for their hardware.

I consider this post to be an abuse of the forum.

---

### Post by MarkX on 2013-05-18
Oh dear, I see what the problem is. 
Nobody who knows how to write Linux is actually able to make a GUI so one can set *ANY* desired resolution manually.

---

### Post by ventrical on 2013-05-18
> **MarkX said:**
> Oh dear, I see what the problem is. 
Nobody who knows how to write Linux is actually able to make a GUI so one can set *ANY* desired resolution manually.


 We don't even know what kind of monitor you have. In Ubuntu +1 , which is beta testing rolling release, we share specs with each other so we can trouble shoot problems. A lot of graphical video adapter drivers have been obsoleted so you may have to use Xubuntu or Lubuntu flavours to get proper screen resolution.

What is the make/brand of your graphical adapter card?

---

### Post by cariboo on 2013-05-18
Unless the op provides some more information, this thread will be closed, as complaining and demanding a solution here, doesn't do much good. A well written bug report without any dramatics will go much further  towards solving the problem. After all, You catch more flies with honey than you do with vinegar.

---

### Post by MarkX on 2013-05-18
It's an Orion 1770a with vga output, 1280x1024 60  and has lasted for years. I could get it working up to about Ubuntu 9.x, then even longwindedly farting around with xrandr stopped working too.
If you want a bug report search for "resolution" in the forums where you'll find all manner of people who just want to type the correct resolution and refresh rate into a box.
I know that too high a resolution could kill very old CRTs, but a warning and disclaimer would take care of that.

Of course if you want to kill this thread instead of actually bothering to do anything about this age old problem, go ahead. Or you could blame Xorg and wash your hands.

---

### Post by mcellius on 2013-05-18
Most of the people here aren't developers.  They're testers, for the most part, and some are pretty knowledgeable, but most are not involved with writing the code.  Try to remember that this is Linux, not Windows.  You didn't pay anything for it.  You got it for free from people and organizations that believe in the principles of software freedom, most of whom donate their time and efforts to it.  You're free not to use it, of course, but a better solution might be to jump in and help.  Standing off to the side throwing a tantrum isn't going to get you anything.

---

### Post by QIII on 2013-05-18
Hello, MarkX!

Although your ire is understandable, you must realize that this is a community of people who use Ubuntu and we are not in Canonical's employ.  We are not the people who do the development.

There are a handful of developers who may, from time to time, come to the forums - but that is a singularly rare occurrance. 

What you find here are not actual "bug reports".  They are requests for help in getting something to work where it is in the power of those who answer to help.  The proper place to report a bug is on [https://launchpad.net](https://launchpad.net) or through the bug reporting functionality in Ubuntu.

There is no use in making demands of us.  We don't make the changes.  Leaving the thread open or closing it has nothing to do with whether or not a bug will be fixed.

Thanks and best wishes!

---

### Post by MarkX on 2013-05-18
I "help" by recommending it to people but what I see now is endless changes being made that people don't want (Unity, for a major one and I gather they now  want to dump firefox) instead of fixing basic things that don't work properly. 
If people with touchscreens, mobiles and the need for clouds and the latest gismos want Linux, then give them their own distro, call it Mobuntu, if you like, but don't turn upside down what could have become the best OS every few months just for the sake of it. I'm becoming a silver surfer and our numbers are rocketing.  WE DON'T WANT CHANGE! We need a rock steady, easy and familiar OS!

---

### Post by QIII on 2013-05-18
Those are things that would probably best be directed at Canonical.  We can certainly talk about them here, but the efficacy of such discussions in bringing about change is doubtful.

Use the forum to discuss, not to demand.  We can't change anything.  We can, however, file bug reports -- which this thread is not.

In any case, I must warn you that if you continue to have a poor attitude or are disrespectful to other members or to staff, then your ability to even have a discussion on the forums could be curtailed.

---

### Post by cariboo on 2013-05-19
@MarkX, we all have bad days, but I'm stilling willing to help you solve your problem, all you need to do is answer a few questions.

[LIST=1]
[*]When/what version was the last to detect your monitor correctly?
[*]What graphics adapter does your system use?
[*]Have you checked to see if it is a hardware problem? Bad cable, bent pins in the connectors, etc.
[/LIST]

Your complaints about Unity won't be answered here, as we have no control over the DE, I see you are using Lubuntu, if you dislike the changes in the default DE, then some of the other Ubuntu based flavours may suit your needs better, I'd suggest you also try Xubuntu and Kubuntu.

Links to Saucy isos for the other flavours are listed in [this]("http://ubuntuforums.org/showthread.php?t=2146077") sticky

---

### Post by dino99 on 2013-05-19
A few things to help you with a CRT display:

- as the world is a "dynamic" rollup game, and ours too, you need to follow it too
- as the time have elapsed, nowadays "xorg" is playing a second role compared to the kernel which now directly deal with X. So a non suitable xorg.conf can badly disturb the kernel logic : the default now is to erase that conf file . But there is some cases where you still need it: and CRT display is one of this case. You need to set it with the appropriate entries settings, like in that post: [http://ubuntuforums.org/showthread.php?t=2107475&p=12472675#post12472675](http://ubuntuforums.org/showthread.php?t=2107475&p=12472675#post12472675) . So play with modelines and modesettings and dmidecode to tweak it correctly. Googling around might help you find oldish CRT xorg.conf entries.
- example: [http://www.google.fr/webhp#hl=fr&sclient=psy-ab&q=crt%2Bxorg.conf%2Bsettings+entries&oq=crt%2Bxorg.conf%2Bsettings+entries&gs_l=hp.3...945020.967337.2.971964.30.30.0.0.0.0.112.1781.29j1.30.0...0.0...1c.1.14.psy-ab.Z-b4K0DNGtY&pbx=1&bav=on.2,or.r_qf.&bvm=bv.46751780,d.d2k&fp=34741c71f2576fe1&biw=1674&bih=925](http://www.google.fr/webhp#hl=fr&sclient=psy-ab&q=crt%2Bxorg.conf%2Bsettings+entries&oq=crt%2Bxorg.conf%2Bsettings+entries&gs_l=hp.3...945020.967337.2.971964.30.30.0.0.0.0.112.1781.29j1.30.0...0.0...1c.1.14.psy-ab.Z-b4K0DNGtY&pbx=1&bav=on.2,or.r_qf.&bvm=bv.46751780,d.d2k&fp=34741c71f2576fe1&biw=1674&bih=925)

---

### Post by jerrylamos on 2013-05-19
For a while on a 1024x600 netbookI was using an external monitor TV which had 1366x768 resolution.  After thrashing the internet a bit I wound up with this exec:

#!/bin/bash
xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1366x768_60.00
xrandr --output VGA1 --mode 1366x768_60.00

which I had to run on every boot.  No clear idea what all those numbers are or how to figure out what they should be.  "If it works, don't fix it."

Then on sale I bought a 1600x900 monitor, I think $89 or so.  Resolution problem is ubiquity on install anything past 1024x768 insists on rotating 90 degrees and doesn't even have a choice of "normal".  After install, turn off mirror displays, turn off laptop monitor, then select 1024x768 and apply.  After that, I can re-open displays and set 1600x900 with normal rotation.  Yes there's a launchpad bug.  Yes, nobody's interested,,,,

---

### Post by VinDSL on 2013-05-19
> **dino99 said:**
> [...] nowadays "xorg" is playing a second role compared to the kernel which now directly deal with X. So a non suitable xorg.conf can badly disturb the kernel logic : the default now is to erase that conf file . But there is some cases where you still need it [...]
True!

The only reason I run xorg.conf is for Digital Vibrance Control (DVC), so called -- the #1 reason for running an nVidia card IMO.  ;)

Nowadays, you need to be more_and_more careful with xorg.conf.  For instance, if I manually set my xorg.conf to native res, these days, it borks my display.  I *need* to set size/freq to "Auto".

Used to be the other way around.  "Auto" always chose the wrong frequency.  I *had* to manually set it to 60Hz.

Guess the kernel is handling this sort of stuff now...

---

### Post by ventrical on 2013-05-20
> **MarkX said:**
> I "help" by recommending it to people but what I see now is endless changes being made that people don't want (Unity, for a major one and I gather they now  want to dump firefox) instead of fixing basic things that don't work properly. 
If people with touchscreens, mobiles and the need for clouds and the latest gismos want Linux, then give them their own distro, call it Mobuntu, if you like, but don't turn upside down what could have become the best OS every few months just for the sake of it. I'm becoming a silver surfer and our numbers are rocketing.  WE DON'T WANT CHANGE! We need a rock steady, easy and familiar OS!

CentOS is about as Debian steady as it goes.!!  I understand the reference to 'silver surfer', but I am also a tester. Here.. we test and break things in hopes that it does become more stable and steady.

---

### Post by MarkX on 2013-05-21
Ok, thanks folks for listening. I wish I knew a way to tell Canonical. Too busy IRL to do it now though.

---

### Post by cariboo on 2013-05-21
> **MarkX said:**
> Ok, thanks folks for listening. I wish I knew a way to tell Canonical. Too busy IRL to do it now though.

Try the [ubuntu-x mailing list]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-x"), this list is for discussing the problem you are having with X, not a place for opinions.

---

