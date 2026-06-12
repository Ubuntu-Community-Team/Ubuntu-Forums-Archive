---
title: "performance benchmarks"
date: 2008-11-18
forum: The Cafe
---

### Post by stonecoldjha on 2008-11-18
i came across this :[http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1).

it clearly indicates that ubuntu is getting slower and slower.how do we explain this?to me,ubuntu has always been a high performance OS.is this a result of complacency,or something that naturally comes along as things like ubuntu get apparently better?what about ubuntu9.04 ?will it set new standards in performance(i just don't mean smaller boot times,but general performance and speed on the fly,speed and responsiveness that shows in multi-tasking etc.)?also,i wanted to know if work is going on to create an ubuntu distro that would kick the living daylights out of any other OS,be it even macOS-X,when it comes to **speed and performance**?

is there any linux kernel being developed to significantly boost performance?what about ext4,is that better than reiser file systems?

---

### Post by jenkinbr on 2008-11-18
I do know that kernel 2.6.28 is supposed to support ext4, so possibly Jaunty should see this option, as intrepid is running kernel 2.6.27-x

---

### Post by binbash on 2008-11-18
you can manually compile your kernel for speed or you can try archlinux or gentoo linux if you want speed.

You can change ubuntu's default config files to gain boost also.That is up to you.

---

### Post by stonecoldjha on 2008-11-18
so,is gentoo faster than ubuntu?how is ubuntu compared to other OS in this regard?

---

### Post by binbash on 2008-11-18
gentoo is 9 x faster than ubuntu, and archlinux is also 6-9x faster than ubuntu.

But at gentoo it depends at your make.conf file.If you know what to use with your system, if you know linux very well, it is the fastest distro with archlinux.However installation is 10x harder than ubuntu :D

PS : gentoo is also a rolling distro you dont  have to install or upgrade a new version every 6 months.If you want everything works out of the box, there is no better choice than ubuntu (for debian based)

---

### Post by stonecoldjha on 2008-11-18
what makes gentoo and archlinux so fast?cant i have an ubuntu that is just that fast,i mean,even in the near future?

---

### Post by PierreDeKat on 2008-11-18
One thing to keep in mind is that there are different gauges for "performance". Yes, you can look at raw speed to perform a particular operation.

And if you don't mind graphics confined to 16 colors, little or no animations, limited software choices, etc., then you can go that route. Make your box the fastest there is at performing calculations, if that's what you need to do: perform calculations.

But if you want a little more than that, Ubuntu offers a nice balance between speed and "comfort", if you will. 

It's kinda like a BMW, maybe: not as fast, but more comfortable than Lotus; not as comfortable, but better performance than a Cadillac.

---

### Post by mentallaxative on 2008-11-18
I suspect binbash is applying a bit of gentoo-friendly hyperbole. The most significant speed increases come from using less memory-intensive applications, not differences in compiler flags.

The OS will get slower over time as it inevitably grows bigger and supports more features/drivers/random crap.

---

### Post by artir on 2008-11-18
> **stonecoldjha said:**
> i came across this :[http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1).

it clearly indicates that ubuntu is getting slower and slower.how do we explain this?to me,ubuntu has always been a high performance OS.is this a result of complacency,or something that naturally comes along as things like ubuntu get apparently better?what about ubuntu9.04 ?will it set new standards in performance(i just don't mean smaller boot times,but general performance and speed on the fly,speed and responsiveness that shows in multi-tasking etc.)?also,i wanted to know if work is going on to create an ubuntu distro that would kick the living daylights out of any other OS,be it even macOS-X,when it comes to **speed and performance**?

is there any linux kernel being developed to significantly boost performance?what about ext4,is that better than reiser file systems?

According to phoronix, Ubuntu x64 is actually faster than Leopard(which is  64 bits). Mac leopard only won ubuntu on graphical related things (coz our graphical stack kinda suck.)(But GEM, MPX,DRI2,XI2 and that stuff will solve it)

---

### Post by stonecoldjha on 2008-11-19
and what about ext4?is it good enough to compete against reiser4?

---

### Post by jdong on 2008-11-19
No. At least in terms of performance, absolutely not -- btrfs is supposed to compete with reiser4, ext4 is a natural step up from ext3. reiser4 was also fairly unsafe with data, causing kernel panics, etc so the idea of using it as a primary filesystem is simply insane. Oh yeah, all upstream development is DEAD on it since the author is no longer able to work on the project.



Bryce Harrington and other developers have been talking about these benchmarks quite a bit on the developer mailing lists and they've traced most of the performance regressions down to upstream projects (the kernel, X.org, C libraries, etc). The follow-up benchmark on Fedora shows that they've suffered similar performance degradation way before we did, because they are a bit more aggressive at picking the latest versions of everything upstream.


I don't think the fix to any of this is switching distros -- I've seen a LOT of people whining and complaining and recompiling, but nobody really trying to chase down exactly what is causing the slowdown.

---

