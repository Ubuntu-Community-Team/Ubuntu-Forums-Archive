---
title: "System76 desktop or laptop for Virtualization work"
date: 2009-07-28
forum: System76 Support
---

### Post by jocampo on 2009-07-28
Hello guys

I am looking for an affordable System76 solution suitable for moderate to heavy Virtualization use, like Vmware or VirtualBox, basically for labs and study certifications. I know best approach is a server, but would be out of budget inmediatly.

Most important thing I would like to find is Processor which support Virtualization instructions and of couse, a motherboard who can handle more than 4gb of RAM

Do we have something like that in the Laptop/Desktop line? Budget... between $700 and $800

Thanks in advance,

---

### Post by jocampo on 2009-07-28
Bump!

Any comment or advice, anyone with experience with Virtualization and System76 hardware?

---

### Post by bill516 on 2009-07-28
jocampo, you might want to head over to the ExtremeTech website and look for a thread in the Linux section regarding virtual machines.  The two people involved, masinick and jrst, are very knowledgeable about the use of vm's.  They are not talking specifically about System 76 machines but you an learn a lot that would apply to the configuration of a machine intended for the support of vm's.

Then see my posting here on the Intel T6400 CPU.  I thought that Intel's virtualization technology was part of its entire line of dual-core cpus.  Not so.

The best thing to do is to spend time checking Intel specs with regard to support of vm technology.  You really need to make sure that the cpu you use will support it.

---

### Post by Derath on 2009-07-29
I'm currently using a pangolin and virtualization works wonderfully on it... definitely go with the 4Gs, and I believe any of the Core2 Duo's have the virtualization built into them... Currently I'm using a P8400, with 4G ram, and running virtualbox 3.0.2 and no complaints here!

Hope this helps!

---

### Post by jbelmonte on 2009-07-29
I've got a Wild Dog with 8GB of RAM and Virtualization works wonderfully on it.

---

### Post by jocampo on 2009-07-29
Folks

Thanks to all for taking the time and reply, appreciated. Couple of things.

Derath:
I do not see any Pangolin on system76 website, which P8400 processor as an option. How much did you pay for your product, final price ....

Jbelmonte:
What processor are you using on your Wildog, does it support Virtualization instructions, also, how much did you pay for the Wildog?

---

### Post by bill516 on 2009-07-29
> **Derath said:**
> I'm currently using a pangolin and virtualization works wonderfully on it... definitely go with the 4Gs, and I believe any of the Core2 Duo's have the virtualization built into them... Currently I'm using a P8400, with 4G ram, and running virtualbox 3.0.2 and no complaints here!

Hope this helps!

Derath, check your assumption on the core2 duos.  The T6400 bongs to that family and it does not have VT-x capablity.  Like you I had assumed they all do, but apparently they do not.

You and jbelmonte are exactly right about one thing; with the proper CPU these machines will run virtual machines very well.  I do it (on 32 bit guests) with three Gigabytes of RAM, though four would be better.  If HD space allows, running with a static rather than a dynamic space allocation will help performance a bit.

All in all if he orders with the right CPU jocampo should not have a problem.

---

### Post by jocampo on 2009-07-29
Bill, folks ...

Thanks for the help so far. I've found this article: [http://en.wikipedia.org/wiki/X86_virtualization]("http://en.wikipedia.org/wiki/X86_virtualization") will use it to compare and check the System76 processor options. I know the more RAM the better, but wanted to be sure about the processor choice.

Finally, silly question and just my last shoot to avoid a visit to my bank's branch ;-) ... I have a EVO d530 small factor and a OptiPlex™ GX270. I guess I can not updgrade their processors to one which supports virtualizations instructions, right? asking this because $200 bucks getting a new CPU is better than $800.00 on a new machine (wife will not complain too much, lol )

---

### Post by samalex on 2009-07-29
For you guys who use VirtualBox, do you have a 5400 rpm drive or 7200 rpm drive?  I plan on running Win XP through VirtualBox, and given the PC image is on the hard drive I wasn't sure if this would affect performance.

My main reason to run Win XP is to use the AppDev training videos which use a proprietary codec with DRM that only works on Windows :evil:.

I'm just wondering if it's worth the extra $55 for a 7200 RPM drive just for this since batter life is something else I'm concerned with.

Thanks --

Sam

---

### Post by gpstar on 2009-07-29
P9500, 4GB ram, 320GB 7200rpm hd drive in a Bonobo and it works great with Virtualization, I use it everyday. Just waiting now for ram prices to drop more and i'm gonna put 8gb ram in.

---

### Post by jocampo on 2009-07-29
> **samalex said:**
> For you guys who use VirtualBox, do you have a 5400 rpm drive or 7200 rpm drive?  I plan on running Win XP through VirtualBox, and given the PC image is on the hard drive I wasn't sure if this would affect performance.

My main reason to run Win XP is to use the AppDev training videos which use a proprietary codec with DRM that only works on Windows :evil:.

Thanks --

Sam

Yes buddy! ... it does affect, a lot! Mine is 7200rpm. This is my advice regarding the hd portion:

1. You can upgrade your internal drive a faster one , 7200rpm or higher

or

2.Get an external drive or hd enclosure and with 7200rpms or higher and put your VMs hard drivers there.

You will notice a great performance improvement if you use a faster disk subsystem, that happened to me before,

PS: by the way, you should open a new thread for your hd question. You could get more and better answers than mine ;-)

---

### Post by 3Miro on 2009-07-29
I have a pangolin panp4, 4 GB of Ram 5400 HD and 2.4 Ghz 1333 CPU. Newer Pangolin laptops support 8GB.

I use Virtual box and play 32-bit windows game using wine. No trouble or whatsoever.

For heavy use, go with a desktop, but for a Linux laptop with a lot of RAM 7200 HD is an overkill in my views.

---

### Post by jocampo on 2009-07-29
> **3Miro said:**
> I have a pangolin panp4, 4 GB of Ram 5400 HD and 2.4 Ghz 1333 CPU. Newer Pangolin laptops support 8GB.

I use Virtual box and play 32-bit windows game using wine. No trouble or whatsoever.

For heavy use, go with a desktop, but for a Linux laptop with a lot of RAM 7200 HD is an overkill in my views.

Hi 3Miro

Which type and model of CPU? does yours support virtualization instructions?

Thanks,

---

### Post by samalex on 2009-07-29
Hey Guys --

I created a new thread with my hard drive question: [http://ubuntuforums.org/showthread.php?t=1226310]("http://ubuntuforums.org/showthread.php?t=1226310")

I didn't mean to hijack the thread, but given it already had the attention of those doing virtualization I figured I'd ask there.  Bad move I guess #-o

Sam

---

### Post by 3Miro on 2009-07-29
> **jocampo said:**
> Hi 3Miro

Which type and model of CPU? does yours support virtualization instructions?

Thanks,

P8600, however, it is no longer available on any system76 laptops (as far as I can seen on the web-page).

I am running 64-bit Ubuntu and at the same time 32-bit windows XP and 32-bit windows games. I havenot read the xact specifications (intel.com should be helpful for that), but I think this means that virtualization is supported.

---

### Post by jocampo on 2009-07-29
> **3Miro said:**
> P8600, however, it is no longer available on any system76 laptops (as far as I can seen on the web-page).

I am running 64-bit Ubuntu and at the same time 32-bit windows XP and 32-bit windows games. I havenot read the xact specifications (intel.com should be helpful for that), but I think this means that virtualization is supported.

To know if your CPU supports virtualization or not. 

```
egrep ‘(vmx|svm)’ /proc/cpuinfo
```

Maybe you know it already, but re-posting ;-) just in case...

---

### Post by 3Miro on 2009-07-29
Thanks for the command, my CPU does support vmx.

---

### Post by Derath on 2009-07-30
bill516: my apologises, I was thinking of the ones that are currently available.

jocampo: I got mine last year, and they've got new models out now... I can't say that I fully loaded mine, but I did end up paying over $1400, but that's with the 3-year warranty.

---

