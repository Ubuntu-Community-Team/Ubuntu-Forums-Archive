---
title: "The Idling Ibex - Ubuntu is becoming slow"
date: 2008-10-27
forum: The Cafe
---

### Post by Ub1476 on 2008-10-27
[Tests done by Phoronix.com]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1") indicate that since 7.04, Ubuntu has in some areas become much slower. 

Well, I certainly hope this will be tuned. At least considering that Snow Leopard (OS X) is aiming for top speed, and Ubuntu can't stay behinde in neither looks nor speed..

---

### Post by Jim! on 2008-10-27
Whew, long read! That was a very interesting article thanks for posting it up. I'm not surprised that 7.04 was faster in some aspects since as an OS becomes more modern it requires more resources (look at Vista compared to Windows XP, though thats probably a bad comparison since Vista is a major resource hog). Theres also a chance it was just the hardware used but we wont know until they've done more tests. 

The tests seemed quite accurate from what they said and the results they posted though so Ubuntu looks to be getting increasingly slower in *some* tasks. Hopefully this will motivate some devs to work on increasing performance in speed.

I like what was written here:
> Major slowdowns after Ubuntu 7.04 "Feisty Fawn" in so many different tests certainly weren't what we head expected. This is our first time carrying out an Ubuntu comparison of recent releases on a large scale using a significant number of tests. It's likely the first time such a study has even been conducted. The tests that experienced performance losses initially we assumed were due to a regression with GCC but the tests extended beyond the ones built from source to include Java ones that use compiled byte-code and even the PHP-driven XML test.

A number of significant kernel changes had went on between these Ubuntu Linux releases including the Completely Fair Scheduler, the SLUB allocator, tickless kernel support, etc. We had also repeated many of these tests to confirm we were not experiencing a performance fluke or other issue (even though the Phoronix Test Suite carries out each test in a completely automated and repeatable fashion) but nothing had changed. Ubuntu 7.04 was certainly the Feisty Fawn for performance, but based upon these results perhaps it would be better to call Ubuntu 7.10 the Gooey Gibbon, 8.04 the Hungover Heron, and 8.10 the Idling Ibex.

We will continue our testing process to see if we can find the underlying cause(s) of these performance problems along with testing out other hardware to see if this was an isolated hardware incident. You can test out the performance of your Linux desktop by installing the Phoronix Test Suite and running any of the numerous tests or suites that ship with this open-source software. We also intend on repeating these tests on other distributions to see if this is an Ubuntu-specific problem or perhaps there's a wider issue at hand.

There is quite a bit of testing going on within the free software community as it pertains to usability and compatibility, but not enough focus on performance. If this is indeed a widespread but unknown problem, hopefully it will be worked out in time for Ubuntu 9.04, especially with Ubuntu Linux appearing on more low-performance netbooks. Whatever the case may be, there's quite a bit of room for improving the performance on the Linux desktop.

---

### Post by Mazza558 on 2008-10-27
I knew it! The releases after 7.04 did actually feel slower than usual (though 8.10 is much faster than 8.04 for me)

---

### Post by FuturePilot on 2008-10-27
Well, the  big goal for Jaunty is speed, so hopefully we can get that speed back.

---

### Post by billgoldberg on 2008-10-27
> **Ub1476 said:**
> [Tests done by Phoronix.com]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1") indicate that since 7.04, Ubuntu has in some areas become much slower. 

Well, I certainly hope this will be tuned. At least considering that Snow Leopard (OS X) is aiming for top speed, and Ubuntu can't stay behinde in neither looks nor speed..

I don't care what those tests say, Ubuntu 8.10 is much faster on both my computers.

---

### Post by lukjad on 2008-10-27
> **Mazza558 said:**
> I knew it! The releases after 7.04 did actually feel slower than usual (though 8.10 is much faster than 8.04 for me)
I felt this too. I have an old PC and you can tell when a distro gets sluggish. The speed was going down. One thing I should point out, is that 7.10 and 8.04 were trying to look good. I think that is what slowed them down.

EDIT: I haven't tried 8.10 yet, so we'll see.

---

### Post by artir on 2008-10-27
I think the problem lies in the kernel;
MacSlow asked them if they are going to test the other distros to find if the slowdown is shared across them.

---

### Post by regomodo on 2008-10-27
#

---

### Post by Prefix100 on 2008-10-27
I'm not that surprised tbh, newer operating systems are always slower on older hardware than the OS before it.

But, it would be nice if Jaunty was to fix this, and give us a **really** speedy distro.

---

### Post by perfectska04@hotmail.com on 2008-10-27
The Phoronix test results don't really surprise me, Ubuntu is indeed becoming slower. However, it's also become more and more compatible with new and old hardware alike. 

Since Ubuntu is the one distro that tries to cater to everyone, some of the packages and settings meant to improve another user's experience may be hindering yours. I find this an acceptable tradeoff, but there may be others who will jump ship to arch/gentoo, etc.

Either way, you can always improve performance in Ubuntu releases by tweaking certain settings or disabling default scripts/services and there is no lack of performance guides going around.

---

### Post by LarsKongo on 2008-10-27
> **perfectska04@hotmail.com said:**
> Since Ubuntu is the one distro that tries to cater to everyone, some of the packages and settings meant to improve another user's experience may be hindering yours. I find this an acceptable tradeoff, but there may be others who will jump ship to arch/gentoo, etc.
It would be better if there were an "advanced button" in the installation process that would allow us to install the packages and services we need instead of throwing everything at us at once. Opensuse allows me to select and de-select extra packages. (when I tried the netinstall.) I think it's an important feature the developers should consider.

---

### Post by Ozor Mox on 2008-10-27
> **LarsKongo said:**
> It would be better if there were an "advanced button" in the installation process that would allow us to install the packages and services we need instead of throwing everything at us at once. Opensuse allows me to select and de-select extra packages. (when I tried the netinstall.) I think it's an important feature the developers should consider.

Burn the alternate CD and select 'Install a command-line system'. Once the base system is installed, you can install what you like on top of it using apt.

---

### Post by gjoellee on 2008-10-27
Well, the Intrepid was really fast until the Alpha 6 release, then it suddenly become slower. However Kubuntu seams to be a lot faster (overall) if you have enough RAM...

---

### Post by LarsKongo on 2008-10-27
> **Ozor Mox said:**
> Burn the alternate CD and select 'Install a command-line system'. Once the base system is installed, you can install what you like on top of it using apt.
Yup, I usally do that. But I think such a minor and "standard" feature could fit on the default live-cd. :p

---

### Post by giorgosts on 2008-10-27
May be 'cause from 7.10 onwards the 3d desktop effects are enabled by default.

Similar behavior in vista with or without aero

---

### Post by LowSky on 2008-10-27
Anyone else think it quite interesting that processors have become faster and faster yet Operating systems still seem slower.
I really put the blame on storage devices as everything but that has really seen improvement. Standard hard drive still spin at 7200RPM regardless of how big they get, and its replacing technology in SSD hard drives is to expensive and not as stable as the old plater type. I think that Hard Drive technology is lacking compared to the rest of system perfomance.

---

### Post by Jim! on 2008-10-27
> **giorgosts said:**
> May be 'cause from 7.10 onwards the 3d desktop effects are enabled by default.

Similar behavior in vista with or without aero

You didn't read the article? - Compiz was disabled. This was a pretty thorough test.

---

### Post by SomeGuyDude on 2008-10-27
I dunno, the Ibex alphas weren't any slower than Gutsy on mine, and given that I couldn't get Feisty to recognize my display at all, I'm not gonna quibble on that front.

---

### Post by lukjad on 2008-10-27
I rarely read ten page articles. ;)

---

### Post by Isaac_x on 2008-10-27
Definitely more tests should be done, and if the problem is widespread then it should be addressed. A 50% drop in performance seems unreal, some /. poster suggested it's a processor clocking issue, in that 8.04's power-saver slows down the CPU to save power. Should be easy to check.

---

### Post by init1 on 2008-10-27
> **Ub1476 said:**
> [Tests done by Phoronix.com]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1") indicate that since 7.04, Ubuntu has in some areas become much slower. 

Well, I certainly hope this will be tuned. At least considering that Snow Leopard (OS X) is aiming for top speed, and Ubuntu can't stay behinde in neither looks nor speed..
Yeah Hardy is lethargic on my laptop. I really hope that Intrepid is faster.

---

### Post by regomodo on 2008-10-27
#

---

### Post by SunnyRabbiera on 2008-10-27
In my case both hardy and Ibex are faster then Gutsy, Ibex seems to run at good speed in both virtual and live CD tests though I have not done a full install yet with ibex and dont intend to because I intend to stick with hardy

---

### Post by benny bronx on 2008-10-27
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1")

My observation, since 6.06, is no.  However, it is a somewhat interesting read.

---

### Post by perlluver on 2008-10-27
> **benny bronx said:**
> [http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1")

My observation, since 6.06, is no.  However, it is a somewhat interesting read.

This was already posted, just today.  Link: [http://ubuntuforums.org/showthread.php?t=960205](http://ubuntuforums.org/showthread.php?t=960205)

---

### Post by Ozor Mox on 2008-10-27
In my experience using Ubuntu on two computers and Xubuntu on another two, ranging in age from about 4 years old to steam powered, is that no it is not getting noticeably slower. Two important things though:

1. Those with older computers and hardware does not necessarily play nicely with Ubuntu may well see Ubuntu slowing down. Those with newer computers and well supported hardware may see no difference.

2. Ubuntu is supposed to be a modern operating system. Each new release of Ubuntu adds new features and keeps up with the latest technology. Inevitably it is going to get slower on old hardware. Compared to Windows Vista, Ubuntu actually still runs well on very old hardware. Why would people complain about that when there are so many other options for them like custom building Ubuntu, installing the lighter Xubuntu, or installing a distribution that is *designed* to be lightweight?

Of course bloating the OS and adding useless features is never good, but that's different.

---

### Post by xpod on 2008-10-27
I know it slowed down for me a bit with Hardy but that`s all changed again with ibex,for me of course.It`s certainly faster as far as booting up & shutting down is concerned anyway.
There`s plenty faster distro`s around or even just a bare bones *buntu is much much faster but i`m quite happy with the full blown Ubuntu and it`s tardiness.

---

### Post by phoronix on 2008-10-27
> **Isaac_x said:**
> Definitely more tests should be done, and if the problem is widespread then it should be addressed. A 50% drop in performance seems unreal, some /. poster suggested it's a processor clocking issue, in that 8.04's power-saver slows down the CPU to save power. Should be easy to check.

Enhanced Intel SpeedStep Technology was disabled during our tests, as mentioned in the article.

---

### Post by benny bronx on 2008-10-27
> This was already posted, just today

Yea, I just saw that now. Beaten to the punch by 9 hours.

---

### Post by cardinals_fan on 2008-10-27
Default Ubuntu hasn't impressed me with speed since Edgy.  Feisty was the point of no return (I'm not sure why).

---

### Post by Presto123 on 2008-10-27
Phew...I still think it is MUCH faster than my Vista partition. I'm definitely happy about that. I believe that the difference in speed on my laptop is 3 minutes +/- for Vista and 1 minute for Ubu 7.10. I really need to test this for sure, but I swear that if I didn't have some paranoia about deleting Windows off of my Lappy, I would.

---

### Post by bapoumba on 2008-10-28
Threads merged.

---

### Post by nrs on 2008-10-28
Yes, new releases mean newer features, heftier requirements, etc. But let's get real here, differences between releases are relatively minor, it's been mostly slow and steady evolution, GNOME releases in particular are especially conservative. there's no legitimate reason for such a decrease in a little over a year. 

Something is definitely up.

---

### Post by djsroknrol on 2008-10-28
> There is quite a bit of testing going on within the free software community as it pertains to usability and compatibility, but not enough focus on performance. If this is indeed a widespread but unknown problem, hopefully it will be worked out in time for **Ubuntu 9.04**, especially with Ubuntu Linux appearing on more low-performance netbooks. Whatever the case may be, there's quite a bit of room for improving the performance on the Linux desktop.

He'll be waiting a long time for that version...LOL

---

