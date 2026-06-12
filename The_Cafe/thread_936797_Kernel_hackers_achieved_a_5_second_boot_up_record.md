---
title: "Kernel hackers achieved a 5 second boot up record"
date: 2008-10-03
forum: The Cafe
---

### Post by brunovecchi on 2008-10-03
They did it for an EEE Pc, using a custom Fedora distribution.
For desktop computers, boot up time is not that important since you turn it on once a day or so (or even less). But for notebooks, mininotebooks, netbooks, etc., boot up time is VERY important.

[**_Slashdot_**]("http://linux.slashdot.org/linux/08/10/02/1933206.shtml").

[**_The actual article_**]("http://lwn.net/Articles/299483/")

The second article explains very nicely with illustrative figures how they did the job.

---

### Post by 3rdalbum on 2008-10-03
You can actually boot your computer in 5 seconds too, excluding BIOS time.

In GRUB, select your kernel line and press "e". I think you have to press "e" a second time to actually edit the arguments line.

The bit where it says "init=/bin/init" or something similar; change that to read "init=/bin/sh".

Press Enter and your system will boot up in probably about 5 seconds, to a command-line. No services will have been started... but it's booted up!

---

### Post by Trail on 2008-10-03
AMAGAD KERNEL HACKERS! DE KERNEL IS HACKED!!!1! I R GOING BACK 2 WINDOWS!!!

(it's not caps, it's shift)

---

### Post by hyper_ch on 2008-10-03
nice work :)

---

### Post by artir on 2008-10-03
I read the article and they are releasing the software in a week or so.
They just replaced upstart with init, a new readahead AKA supereadahead and some patches on the kernel that will be available for 2.6.28, so Jaunty will probably be faster in booting than a mobile phone!

---

### Post by smartboyathome on 2008-10-03
> **artir said:**
> I read the article and they are releasing the software in a week or so.
They just replaced upstart with init, a new readahead AKA supereadahead and some patches on the kernel that will be available for 2.6.28, so Jaunty will probably be faster in booting than a mobile phone!

They also excluded services that Ubuntu needs (Cups, anyone? Wireless support? Sound Support?), which means that Ubuntu may not boot THAT fast.

---

### Post by Npl on 2008-10-03
I sold my TV some months ago, so I cant boot up my Amiga1200 right now... but im sure it took less than 5 seconds till Workbench (a graphical OS) is ready to use... all while running on a measy 50MHz

---

### Post by fedex1993 on 2008-10-03
pretty cool but it wont load wireless support sound support in that little of time i bet.

---

### Post by mips on 2008-10-03
> **fedex1993 said:**
> pretty cool but it wont load wireless support sound support in that little of time i bet.

It will if you compile the modules into the kernel. I don't think they crippled the netbook when they did this experiment.

---

### Post by earthpigg on 2008-10-03
> **fedex1993 said:**
> pretty cool but it wont load wireless support sound support in that little of time i bet.

the article said they cut the kernel's boot time to one second - but estimate they could have cut it down to a half second.

their stated goal was not 'as fast as possible', it was 'five seconds'... meaning they could do it in less, meaning they have wiggle room, meaning if they want sound then they probably have it ;)

---

### Post by Elephantman5 on 2008-10-03
> **Trail said:**
> AMAGAD KERNEL HACKERS! DE KERNEL IS HACKED!!!1! I R GOING BACK 2 WINDOWS!!!

(it's not caps, it's shift)

heh. :)

---

### Post by medic2000 on 2008-10-03
I have an old laptop p3-600 300 mb ram. Its boot time is very long. How can i reduce it? By compiling all modules to kernel?

---

### Post by Ub1476 on 2008-10-03
> **medic2000 said:**
> I have an old laptop p3-600 300 mb ram. Its boot time is very long. How can i reduce it? By compiling all modules to kernel?

Install Arch Linux or even Gentoo if you are up to the task.

---

### Post by MaxIBoy on 2008-10-03
WANT!

WANT! 

WANT!



Looks like I've got an excuse to try compiling a kernel.

---

### Post by medic2000 on 2008-10-03
> **Ub1476 said:**
> Install Arch Linux or even Gentoo if you are up to the task.

Sorry to mention it already Arch :) I am looking for further improvements.

---

### Post by mips on 2008-10-03
> **medic2000 said:**
> Sorry to mention it already Arch :) I am looking for further improvements.

Read up on crux, vector, lfs etc

---

### Post by InfinityCircuit on 2008-10-03
> **smartboyathome said:**
> They also excluded services that Ubuntu needs (Cups, anyone? Wireless support? Sound Support?), which means that Ubuntu may not boot THAT fast.

I don't think so--I see HAL, udev, and network-manager running for the latter two.  No cups, yes, but that would be possible within the time limit with the other kernel hacks they mention.

---

### Post by smoker on 2008-10-03
good news! the future's looking 'quick!' :-)

---

### Post by Frak on 2008-10-03
> **smartboyathome said:**
> They also excluded services that Ubuntu needs (Cups, anyone? Wireless support? Sound Support?), which means that Ubuntu may not boot THAT fast.
If you compile these things into the kernel (if it's possible, as proprietary stuff can't, you_know_why) than you don't have to wait for your module pack to startup. Anyways, I got my bootup time down to 12 seconds by making my own system in Gentoo. It was very speedy, and it even ran Gnome.

---

### Post by Aiello on 2008-10-03
This is why open source rocks.

---

### Post by solitaire on 2008-10-03
Darn!

I need a refresher course in Ubuntu Kernel building then......

where's the best place to read up??

---

### Post by Frak on 2008-10-03
> **solitaire said:**
> Darn!

I need a refresher course in Ubuntu Kernel building then......

where's the best place to read up??
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7#doc_chap3](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7#doc_chap3)

---

### Post by artir on 2008-10-04
The Ubuntu Kernel Master Thread !

---

### Post by stinger30au on 2008-10-04
> **Npl said:**
> I sold my TV some months ago, so I cant boot up my Amiga1200 right now... but im sure it took less than 5 seconds till Workbench (a graphical OS) is ready to use... all while running on a measy 50MHz


i remember the Tandy Colour Computer would be an instant on running at a mere .8 Mhz with a ROM to boot form as well as the Commodore 16 amongst others


aaaahhhh how the cpu sped have increased over the years to amazing speeds and the boot times have slowed oh so much

---

### Post by aysiu on 2008-10-04
> **fedex1993 said:**
> pretty cool but it wont load wireless support sound support in that little of time i bet.
The article seems to indicate that Network Manager was running at the end of 5 seconds.

Does sound really need to be available immediately after bootup?

I would love to have a 5-second bootup to a usable desktop and then have sound load by the time (i.e., later) I had launched an application that used sound.

I hate those "log-in screen ready" and "we're logging you in now" noises anyway.

---

### Post by earthpigg on 2008-10-04
~Instert "I am Reading Your Post Now" Noise here~

---

### Post by Trail on 2008-10-06
~wobbly posts effect~

---

### Post by Npl on 2008-10-06
> **stinger30au said:**
> i remember the Tandy Colour Computer would be an instant on running at a mere .8 Mhz with a ROM to boot form as well as the Commodore 16 amongst othersThats not a graphical multitasking OS tough :)

Commandline-prompt would be pretty much instant-on aswell.

---

