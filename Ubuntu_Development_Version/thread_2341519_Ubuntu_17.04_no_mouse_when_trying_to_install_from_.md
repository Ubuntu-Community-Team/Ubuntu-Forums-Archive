---
title: "Ubuntu 17.04 no mouse when trying to install from boot usb"
date: 2016-10-28
forum: Ubuntu Development Version
---

### Post by mordec4i on 2016-10-28
[COLOR=#000000][INDENT]I am trying to install ubuntu 17.04 but when I boot into ubuntu installation usb my mouse is invisible. I can clearly see my pointer icon stuck in the top left corner but when I move the physical mouse around some things get highlighted at times. I tried installing without the mouse but it's impossible to continue the installation without the mouse at the end.

Mouse: logitech g9x, I've also tried my wireless logitech mouse and the same issue.
I have legacy usb enabled in bios[/INDENT]
[/COLOR]
[INDENT][Last edited by mordec4i]("https://ubuntuforums.org/posthistory.php?p=13562946"); 4 Hours Ago at [COLOR=#3E3E3E]10:08 PM[/COLOR].[/INDENT]

---

### Post by Bucky Ball on 2016-10-28
*Thread moved to **Ubuntu Development Version**.*

Welcome. Unsure if you're aware, but 17.04 is a development version, all posts about it go in this area and it is not released until April next year. Not really for regular day-to-day use (not by a long way) at this stage if that's what you are intending to use for. Expect breakage and other issues like your mouse ones (you other thread has also been moved to this forum). 

Advise 16.04 LTS if you are not intentionally trying to install this to test and help by posting your issues here at this point. :)

---

### Post by mordec4i on 2016-10-29
> **Bucky Ball said:**
> *Thread moved to **Ubuntu Development Version**.*

Welcome. Unsure if you're aware, but 17.04 is a development version, all posts about it go in this area and it is not released until April next year. Not really for regular day-to-day use (not by a long way) at this stage if that's what you are intending to use for. Expect breakage and other issues like your mouse ones (you other thread has also been moved to this forum). 

Advise 16.04 LTS if you are not intentionally trying to install this to test and help by posting your issues here at this point. :)

Hello,


The reason I chose this version was because I was advised to use the latest beta so that my hardware would work. I built a high performance pc this year and have an 6700k with a gtx 1080 card. I've been on windows 10 far too long and tried installing different distros and always had problems. On reddit I was told the latest beta is the only one that doesn't cause problems when installing and trying to use with the latest hardware. Do you think the 16.10 would be a better version to install?

---

### Post by Bucky Ball on 2016-10-29
Yea. They work fine on the supported 16.04 LTS.

[https://www.pugetsystems.com/labs/hpc/GTX-1080-CUDA-performance-on-Linux-Ubuntu-16-04-preliminary-results-nbody-and-NAMD-803/](https://www.pugetsystems.com/labs/hpc/GTX-1080-CUDA-performance-on-Linux-Ubuntu-16-04-preliminary-results-nbody-and-NAMD-803/)

* Tip: search for 'gtx 1080 ubuntu 16.04'. Replace the video card with '6700k' for processor. All good. Lots of people have them running sweetly in 16.04 LTS. ;)

I think 16.04 LTS would be the best because it has the longest support (long-term support release, five years to 2021) as opposed to the interim and newly released 16.10 which has nine months support. An LTS is designed for stability and longevity. 16.04 has been around since April. 16.10 has been out less than a month. The latest is not always the greatest. ;)

You'll find 16.04 LTS should work 'out of the box' (I am running a 6700 right now on 16.04 with the NVidia 970). You may need to use a video option   to get the install working (easy, use 'nomodeset') but after that it is a matter of installing the NVidia driver in a couple of clicks and you're there.

Not the best advice telling you to install an unsupported, unreleased version for any reason other than testing. 17.04 is five months away. :-k

Anyway, I'd go for 16.04 LTS and if you need a hand with it, post a new thread in ***Installations and Upgrades*** and you should get some support fairly quickly there. Good luck. :)

---

### Post by dino99 on 2016-10-29
With recent hardware, be ready to workaround some issues. In your case, i suspect the 4.8 kernel not fully supporting some of your chipsets, so try the 4.9 one.
And about the Pascal card, again use the 4.9 kernel with the latest 370 driver

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9-rc2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9-rc2/)
[http://askubuntu.com/questions/47397/how-do-i-add-the-kernel-ppa](http://askubuntu.com/questions/47397/how-do-i-add-the-kernel-ppa)

---

### Post by mordec4i on 2016-10-30
Guess I need to install 16.10 or 17.04 because I wasted all of today trying to install the kernel 4.8, 4.8.5 and 4.9rc1 and rc2 with constant system problems. Needless to say I'm exhausted as I've reinstalled 16.04.1, 4 times today. I've tried many guides and even a youtube video suggested on this forum. With 16.04.1 my mouse works during install but as soon as I upgrade the kernel and restart I get system failure errors. So it would be great if someone would help me solve this mouse issue so that I could install either 16.10 or 17.04

---

### Post by Bucky Ball on 2016-10-30
To greatly improve your chances of support with anything other than 17.04, please start a new thread. Again, this forum is for 17.04 and beyond, not released and supported versions. Thanks.

Best if you install a release, stick to it and post a thread here with a descriptive title and any info you can think of and try and fix whatever problems you are having with that release rather than bouncing around from one release to the next trying to find a fix. That *is* going to waste time. ;)

Reporting things like 'I keep getting system errors' and not posting what those errors are it will take a long time to get any support. Include all information and what you have tried to fix things, include links if possible. Start a new thread about anything other than 17.04 if you are going to stick with that, but be aware that if you do, you are testing. Might not just be your mouse that gets  buggy over the next five months. :)

Lastly, the 6700 and the 1060 are known to work fine in 16.04 LTS. Don't know about 16.10 as is just come out and seeing other issues. Sounds like you are having problems unrelated.

---

### Post by dino99 on 2016-10-30
You really needs to know 'where' the problem(s) stands. The easiest way to make the required tests is to boot on the iso, without doing the installation (put it on a bootable usb stick) (multisystem from liveusb.info is an easy tool to make tests)

---

### Post by mordec4i on 2016-10-30
> **Bucky Ball said:**
> To greatly improve your chances of support with anything other than 17.04, please start a new thread. Again, this forum is for 17.04 and beyond, not released and supported versions. Thanks.

Best if you install a release, stick to it and post a thread here with a descriptive title and any info you can think of and try and fix whatever problems you are having with that release rather than bouncing around from one release to the next trying to find a fix. That *is* going to waste time. ;)

Reporting things like 'I keep getting system errors' and not posting what those errors are it will take a long time to get any support. Include all information and what you have tried to fix things, include links if possible. Start a new thread about anything other than 17.04 if you are going to stick with that, but be aware that if you do, you are testing. Might not just be your mouse that gets  buggy over the next five months. :)

Lastly, the 6700 and the 1060 are known to work fine in 16.04 LTS. Don't know about 16.10 as is just come out and seeing other issues. Sounds like you are having problems unrelated.

You probably didn't read my post because I clearly said I want to solve the mouse issue so I can install the latest beta with the newest kernel so I don't have to keep reinstalling the other versions. So can someone help me get my mouse working in 17.04 installation?

---

### Post by Bucky Ball on 2016-10-30
Ok. Apols. Good luck with it. :)

---

### Post by mordec4i on 2016-10-30
Yeah I solved it by setting nomodeset before install, the problem is after install my mouse still doesn't work. I've tried both 16.10 and 17.04. How do I fix this?

---

