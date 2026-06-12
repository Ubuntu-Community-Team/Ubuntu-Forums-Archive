---
title: "What's the compromise with the low-latency kernels"
date: 2010-05-09
forum: Ubuntu Studio
---

### Post by Nathan_M on 2010-05-09
Aside from all the confusion with version numbers and the preemptive kernel and stuff that's going on at the moment.....

What's the compromise involved in having a real-time kernel? I figure there must be a compromise, otherwise the low-latency kernel would be the standard kernel, and the existing generic kernel would be a slightly crappier kernel! Previously, the low-latency kernel has caused bugs that needed ironing out, but now that it's just a slightly different configuration of the existing kernel (whatever that means!!!), I haven't noticed any. Does anyone know why the real-time kernel hasn't replaced the generic kernel?

---

### Post by l0xin on 2010-05-09
I think it has to do with stability... the pre-emptive kernel being (potentially) less stable than the generic, and the real-time being (potentially) less stable again (it's advised to evaluate each in that order, i.e. to use the real-time kernel as a last resort). I read somewhere that an application, in the wrong/right circumstances, has the ability to bring the entire system down when using the real-time kernel, whereas with the standard/generic, that shouldn't be able to happen.

---

### Post by trulan on 2010-05-09
That's a very good assessment.  I'll add a little bit more if that's OK.  There are basically two issues (this is a non-scientific generalization):

1. Speed - the preemptive kernel, and even more so the real time kernel, will likely be slower for a lot of tasks, such as gaming and complex 3d graphics.  The mandate of the real time kernel is not "as fast as possible" but "as fast as specified".

2. Stability - Preemption means making sure a few select processes get completed in precisely the time specified.  In my case they are jackd, ffado, and ohci1394.  Ffado sees a huge benefit from this.  As long as those processes are well-behaved, all is well.  But if one of those processes hangs, or has a memory leak, it can potentially take down the whole system because it has been given preemptive priority, or the permission to interrupt almost everything else the system wants to do.

So there are four levels of preemption in the linux kernel config - Server (no preemption), Desktop (a little preemption), Low-latency (more preemption), and with the RT patch, Real Time (complete preemption).

It's a fascinating concept, and I usually end up using the RT kernel for eveything, just because I like it and it makes life more fun.  Even seeing how much lower my frame rate is on games (and watching the NVidia driver crash occasionally in games on my one machine) is something I find intriguing.  (I don't play many games, in case you were wondering.)

---

### Post by Bucky Ball on 2010-05-09
The compromise is you have a problem with Nvidia drivers. If you don't need nvidia drivers, nothing. I've been using Xubuntu with the rt studio kernel for yonks and its great.

The Nvidia driver fix I think has something to do with changing the time in your BIOS, installing the Nvidia driver, then I think you can safely change it back again. I've never bothered cause don't really need on this machine. ;)

---

### Post by Nathan_M on 2010-05-11
> **trulan said:**
> That's a very good assessment.  I'll add a little bit more if that's OK.  There are basically two issues (this is a non-scientific generalization):

1. Speed - the preemptive kernel, and even more so the real time kernel, will likely be slower for a lot of tasks, such as gaming and complex 3d graphics.  The mandate of the real time kernel is not "as fast as possible" but "as fast as specified".

2. Stability - Preemption means making sure a few select processes get completed in precisely the time specified.  In my case they are jackd, ffado, and ohci1394.  Ffado sees a huge benefit from this.  As long as those processes are well-behaved, all is well.  But if one of those processes hangs, or has a memory leak, it can potentially take down the whole system because it has been given preemptive priority, or the permission to interrupt almost everything else the system wants to do.

So there are four levels of preemption in the linux kernel config - Server (no preemption), Desktop (a little preemption), Low-latency (more preemption), and with the RT patch, Real Time (complete preemption).

It's a fascinating concept, and I usually end up using the RT kernel for eveything, just because I like it and it makes life more fun.  Even seeing how much lower my frame rate is on games (and watching the NVidia driver crash occasionally in games on my one machine) is something I find intriguing.  (I don't play many games, in case you were wondering.)

Thanks, that's a great explanation of how it works... I figured it must be one of those cases where solving one problem automatically creates another one, and the only way to solve that is to compromise on the first solution (there must be a philosophical name for that; "the ..... paradox", or something). 

I think I'll keep running a dual boot, only using the rt when I have to, even if the potential problem is only theoretical for me.

---

### Post by Bucky Ball on 2010-05-11
Nvidia drivers will be a problem. In my experience there isn't any other, as reported. Good luck with it all. :)

---

### Post by sgx on 2010-05-12
For the curious, pclinuxos 2010 has both a preemptive kernel, and
nvidia 3d driver installed by default. I did not detect any slowness during unscientific testing, using a kde4 setup, and a usual array of linux audio apps and wine based vsts. I'm probably going to set up
one of those, minus the newer klunkier kde, and pick a new motherboard for a speedy Ubuntu setup, once the spearcatchers have caught the last
few spears. :)

---

### Post by panmanphil on 2010-05-12
Thought I'd point out that with lucid, the new open source nvidia driver is much better than the old one. For me it is much better than the proprietary one. It is NOT supported in the RT kernel though. 

Does anybody have any ideas when the kernel ppa is going to have a new rt kernel based on the 2.6.33 branch of the kernel? Before this release it sounded like it was not that far off?

---

### Post by JayRobert on 2010-05-13
Not sure about the 2.6.33 branch, but here is [a helpful thread]("http://ubuntuforums.org/showthread.php?t=1470264") on building it from source.  (I'm hoping to have time this weekend to try it.)

Also, I am not having trouble with nvidia, but I am having trouble getting the gstreamer-bad plugin to work, and also having odd problems with the network connections since installing 10.04.  My ethernet card doesn't work at all now through the cable (could be the card, I suppose, but I doubt it - it's only three months old), so I've been using a USB connection.  Mostly it works fine, but occasionally it 'resets' (for lack of a better word) to a loopback setting when I boot.  It has done this with the .21 preempt, the .22 preempt, the karmic 2.6.31-10-rt kernel, and 2.6.31-12.21-realtime kernel from Alessio Bogani.

I never had a problem running 2.6.31-10-rt with 9.10 karmic, so that is what I used for everything.  The video problems are getting to be a hassle though, so I've been thinking of adding the generic kernel as a boot option so I can watch youtube.  (I use the rt kernels for audio only; don't produce any video stuff.)

---

### Post by trulan on 2010-05-13
> **panmanphil said:**
> Thought I'd point out that with lucid, the new open source nvidia driver is much better than the old one. For me it is much better than the proprietary one. It is NOT supported in the RT kernel though.
Are you saying this open source driver (nouveau I think) isn't supported under any RT kernel, or that it's just not available on 2.6.31-rt?  I would think it could be gotten to work on 2.6.32 or newer, I would not be surprised if there's no backport for 2.6.31-rt.  The nouveau code is in the 2.6.33 kernel, I believe - you can set the config to build in the nouveau staging driver.

But I only have one computer with an NVidia chip (an onboard), and I have never been able to get it to boot at all with the nouveau driver.  It was hit or miss with the NVidia binary driver on Jaunty's RT kernel and is a little flaky on 2.6.33-rt as well.  (Works great with 2.6.31-rt and any generic kernel, on the binary driver).  So I don't have a machine to test this properly.

---

### Post by panmanphil on 2010-05-13
> **trulan said:**
> Are you saying this open source driver (nouveau I think) isn't supported under any RT kernel, or that it's just not available on 2.6.31-rt?  I would think it could be gotten to work on 2.6.32 or newer, I would not be surprised if there's no backport for 2.6.31-rt.  The nouveau code is in the 2.6.33 kernel, I believe - you can set the config to build in the nouveau staging driver.

But I only have one computer with an NVidia chip (an onboard), and I have never been able to get it to boot at all with the nouveau driver.  It was hit or miss with the NVidia binary driver on Jaunty's RT kernel and is a little flaky on 2.6.33-rt as well.  (Works great with 2.6.31-rt and any generic kernel, on the binary driver).  So I don't have a machine to test this properly.

The generic lucid kernel and the nouveau driver both work for my ASUS laptop. You are correct, there is no support for the nouveau driver for the older realtime kernel. I set mine to use the older nv driver. I followed the other suggestion here for building a kernel, it reminded me of the ppa and yes there is a new 2.6.33 rt kernel available! Unfortunately the nouveau driver doesn't work with that one either.

drmOpenDevice: node name is /dev/dri/card0
[drm] failed to load kernel module "nouveau"

But 5.6ms latency does work so I think I'll stick with this one for awhile and use the nv driver until nouveau is working.

---

