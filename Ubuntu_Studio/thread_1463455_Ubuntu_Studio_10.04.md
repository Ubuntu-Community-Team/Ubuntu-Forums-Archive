---
title: "Ubuntu Studio 10.04?"
date: 2010-04-27
forum: Ubuntu Studio
---

### Post by seagullplayer77 on 2010-04-27
Anyone know what the deal with Ubuntu Studio 10.04 is? I've checked the Ubuntu Studio website, and it doesn't look like they've updated it since 9.10 came out. I've tried Google as well, and there's a conspicuous lack of information about the new Ubuntu Studio release. That's kind of disconcerting, IMO.

Maybe I'm stupid and I missed it, but is there a page with some general info---fixes, new features/programs, that sort of thing---on Ubuntu Studio Lucid? I'd like to find out more about the latest version before I commit to downloading the ISO and trying it. I tried upgrading to 9.04 a year ago, but it was an absolute nightmare and I switched back to 8.04 after a few days. I don't want a repeat this time around, but it's hard to make any judgments since there isn't any information to be had.

I read something here about there being no realtime kernel for the 10.04 release, but the thread was a few months old. Has that been sorted out by now? Ubuntu Studio wouldn't really be Ubuntu Studio without an RT kernel, ya know?

---

### Post by AutoStatic on 2010-04-27
> **seagullplayer77 said:**
> I read something here about there being no realtime kernel for the 10.04 release, but the thread was a few months old. Has that been sorted out by now? Ubuntu Studio wouldn't really be Ubuntu Studio without an RT kernel, ya know?There will be no RT kernel for 10.04 simply because the RT kernel patch devs didn't develop a patch for 2.6.32. Maybe an alternative kernel will be available, at least I hope so, but not in the offical repositories. And besides, through the years parts of the RT patch code have been integrated in the main kernel so my bet is that 2.6.32 will be pretty usable for multimedia production, even without a RT kernel.

Edit: the alternative to a rt kernel is a 2.6.32 preemptive kernel: [http://cdimage.ubuntu.com/ubuntustudio/daily/20100427/lucid-alternate-amd64.list](http://cdimage.ubuntu.com/ubuntustudio/daily/20100427/lucid-alternate-amd64.list)

---

### Post by trulan on 2010-04-27
> **seagullplayer77 said:**
> Anyone know what the deal with Ubuntu Studio 10.04 is? I've checked the Ubuntu Studio website, and it doesn't look like they've updated it since 9.10 came out. I've tried Google as well, and there's a conspicuous lack of information about the new Ubuntu Studio release. That's kind of disconcerting, IMO.
You won't see an update on the Ubuntu Studio site until Lucid is officially released (which is in two days BTW)

As far as the RT kernel, 2.6.31-rt (the same one used by Karmic) is in the Lucid repos.  I'm not sure what, if any, problems will arise from using a slightly different kernel version than generic.  And there's also the 2.6.32 preemptive kernel Autostatic mentioned (Am I correct to assume that this one has the merged RT code turned on in the kernel config?)

And for guys like me who tend to get bored with any edge that's not cutting enough, we can compile the 2.6.33-rt series ourselves and use that (works very well, BTW).

---

### Post by seagullplayer77 on 2010-04-27
> **trulan said:**
> You won't see an update on the Ubuntu Studio site until Lucid is officially released (which is in two days BTW)

As far as the RT kernel, 2.6.31-rt (the same one used by Karmic) is in the Lucid repos.  I'm not sure what, if any, problems will arise from using a slightly different kernel version than generic.  And there's also the 2.6.32 preemptive kernel Autostatic mentioned (Am I correct to assume that this one has the merged RT code turned on in the kernel config?)

**And for guys like me who tend to get bored with any edge that's not cutting enough, we can compile the 2.6.33-rt series ourselves and use that (works very well, BTW).**

So no realtime kernel. I guess I can live with that for a little while. Kernel updates come out on a pretty regular basis anyway, and I'd imagine it'd only be a matter of time before they came out with a realtime update.

As for compiling my own kernel, how would I go about doing that? I've read about it plenty of times, but I've never worked up the gumption to try it. What benefits (beside RT capability) would compiling my own kernel have? Could you recommend me a good tutorial? The semester's over in about a week and a half, and I'll need something to keep me busy :).

---

### Post by AutoStatic on 2010-04-28
> **seagullplayer77 said:**
> So no realtime kernel. I guess I can live with that for a little while. Kernel updates come out on a pretty regular basis anyway, and I'd imagine it'd only be a matter of time before they came out with a realtime update.10.04 uses kernel branch 2.6.32 and will stick with that. There will be no RT patch for 2.6.32 according to the kernel devs responsible for this patch. So as long as 10.04 will be maintained there will be no official 2.6.32 RT kernel. There is the preemptive kernel which has probably the already merged RT code enabled, and then there's a 2.6.31 branch RT kernel apparently (it's not included on the daily build of the DVD I checked though).
At least, that's what I can make of the rather scarce info that is available.

---

### Post by seagullplayer77 on 2010-04-28
Hmm . . . no realtime capabilities at all. That's too bad. I guess I'll just have to make due with the low-latency version of the vanilla kernel then. Any other news on what Ubuntu Studio 10.04 is going to bring to the table? I'm not sure why there's so little information on it. It's not like it's a trade secret or something.

---

### Post by AutoStatic on 2010-04-28
> **seagullplayer77 said:**
> Hmm . . . no realtime capabilities at all. That's too bad. I guess I'll just have to make due with the low-latency version of the vanilla kernel then.That's not totally true, Ubuntu Studio does provide a 2.6.32 preemptive kernel which will probably perform better than the generic kernel when it comes to realtime audio processing.

> **seagullplayer77 said:**
> Any other news on what Ubuntu Studio 10.04 is going to bring to the table? I'm not sure why there's so little information on it. It's not like it's a trade secret or something.I think it has something to do with the size of the Ubuntu Studio dev team and the fact that they're probably all voluntaries. They're probably working their *sses off getting everything ready for the 10.04 release and probably have little time updating on their progress.

---

### Post by sgx on 2010-04-28
> **AutoStatic said:**
> That's not totally true, Ubuntu Studio does provide a 2.6.32 preemptive kernel which will probably perform better than the generic kernel when it comes to realtime audio processing.

I think it has something to do with the size of the Ubuntu Studio dev team and the fact that they're probably all voluntaries. They're probably working their *sses off getting everything ready for the 10.04 release and probably have little time updating on their progress.

I have a pclinuxos with a 2.6.32 preemptive kernel, and I was able to use
hydrogen, zynaddsubfx, rakarrack, and Reaper with 3 vsts, and record the output into timemachine and audacity, without issues, so productivity is
not severely limited, if at all. I had realtime disabled in qjackctl, I
should try it enabled later.
Cheers

---

### Post by seagullplayer77 on 2010-04-28
> **sgx said:**
> I have a pclinuxos with a 2.6.32 preemptive kernel, and I was able to use
hydrogen, zynaddsubfx, rakarrack, and Reaper with 3 vsts, and record the output into timemachine and audacity, without issues, so productivity is
not severely limited, if at all. I had realtime disabled in qjackctl, I
should try it enabled later.
Cheers

How much latency were you dealing with? Anything more than about 5 ms would is unacceptable for me. Any more than that, and the latency starts to become apparent in multi-track recordings.

When I referred to the low latency version of the vanilla kernel, I guess I meant the 2.6.32 preemptive kernel. I'd read somewhere that the devs *did* develop a special low latency kernel that was based on the generic 2.6.32 kernel, but I wasn't aware that it had a special name.

Time will tell . . . I probably won't DL the ISO for another couple of weeks anyway. That'll give me time to study for finals and it'll give the devs time to sort the major bugs. Since it's an LTS, there shouldn't be that many, but . . .

---

### Post by trulan on 2010-04-29
> **seagullplayer77 said:**
> So no realtime kernel. I guess I can live with that for a little while. Kernel updates come out on a pretty regular basis anyway, and I'd imagine it'd only be a matter of time before they came out with a realtime update.

As for compiling my own kernel, how would I go about doing that? I've read about it plenty of times, but I've never worked up the gumption to try it. What benefits (beside RT capability) would compiling my own kernel have? Could you recommend me a good tutorial? The semester's over in about a week and a half, and I'll need something to keep me busy :).
I'll post some info later - no time to write it up right now.  I'll probably start a new thread geared toward using the 2.6.33-rt series in Lucid as I'm sure that is something that quite a few people will want.

A brief summary of the issues I've encountered so far with 2.6.33-rt:
1. The NVidia drivers need patching
2. The Broadcom drivers need patching
3. The VMWare modules need patching
4. The initramfs modules don't get built without a bit of hassle.
Fun stuff!

---

### Post by seagullplayer77 on 2010-04-29
> **trulan said:**
> I'll post some info later - no time to write it up right now.  I'll probably start a new thread geared toward using the 2.6.33-rt series in Lucid as I'm sure that is something that quite a few people will want.

A brief summary of the issues I've encountered so far with 2.6.33-rt:
**1. The NVidia drivers need patching**
2. The Broadcom drivers need patching
3. The VMWare modules need patching
4. The initramfs modules don't get built without a bit of hassle.
Fun stuff!

I'll have to check out that thread. You're planning on posting it in this subforum, I assume?

The part about patching the NVidia drivers is the only part that really bothers me. I run a dual monitor setup, and it was impossible to get it to work right with 9.04. That's one of the main reasons I switched back to Hardy. I don't have a Broadcom card and I don't use VMWare, so neither of those are issues, but the NVidia drivers might be.

---

### Post by sgx on 2010-04-29
> **seagullplayer77 said:**
> How much latency were you dealing with? Anything more than about 5 ms would is unacceptable for me. Any more than that, and the latency starts to become apparent in multi-track recordings.

When I referred to the low latency version of the vanilla kernel, I guess I meant the 2.6.32 preemptive kernel. I'd read somewhere that the devs *did* develop a special low latency kernel that was based on the generic 2.6.32 kernel, but I wasn't aware that it had a special name.

Time will tell . . . I probably won't DL the ISO for another couple of weeks anyway. That'll give me time to study for finals and it'll give the devs time to sort the major bugs. Since it's an LTS, there shouldn't be that many, but . . .
To be honest, I have no proof of the accuracy of any latency monitor, and
if I can't hear it, I have no frame of reference to adjust it, nor any audible motivation.  Maybe a good test idea for the Phoronix test team
Cheers

---

### Post by apparatus on 2010-04-30
> **trulan said:**
> You won't see an update on the Ubuntu Studio site until Lucid is officially released (which is in two days BTW)

As far as the RT kernel, 2.6.31-rt (the same one used by Karmic) is in the Lucid repos.  I'm not sure what, if any, problems will arise from using a slightly different kernel version than generic.  And there's also the 2.6.32 preemptive kernel Autostatic mentioned (Am I correct to assume that this one has the merged RT code turned on in the kernel config?)

And for guys like me who tend to get bored with any edge that's not cutting enough, we can compile the 2.6.33-rt series ourselves and use that (works very well, BTW).


If I get this correctly, I could still install Ubuntu 10.04 and still have realtime capabilities by using the  2.6.31-rt kernel instead of the one that is installed by standard? Is this correct? I get a little confused when reading about all the different kernels...

---

### Post by mango42 on 2010-04-30
> If I get this correctly, I could still install Ubuntu 10.04 and still have realtime capabilities by using the 2.6.31-rt kernel instead of the one that is installed by standard?

My take on this is that if the devs have decided not to provide a real time kernel then either they have considered it unnecessary or it's just too much work to maintain for vocational coders.

Whichever, we have a great system already in Karmic - why try to mix and match?

This is all supposition anyway - Lucid will be brilliant, I've no doubt :P

---

### Post by Bungo Pony on 2010-04-30
I've got two PCs requiring Ubuntu Studio, and I've been anxiously awaiting the release of 10.04. Seeing nothing is a real bummer for me, and I'm hoping they actually do release something within the next few days

---

### Post by AutoStatic on 2010-04-30
:confused:

[http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads)
[http://cdimage.ubuntu.com/ubuntustudio/releases/10.04/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/10.04/release/)

---

### Post by trulan on 2010-04-30
> **apparatus said:**
> If I get this correctly, I could still install Ubuntu 10.04 and still have realtime capabilities by using the  2.6.31-rt kernel instead of the one that is installed by standard? Is this correct? I get a little confused when reading about all the different kernels...
That's correct.  There may be modules that will need to be backported to work on 2.6.31-rt in Lucid - hardware drivers and such.  I've been working with the 2.6.33-rt series and have not booted 2.6.31-rt in Lucid since the early alpha stage of things, so I don't know how fully supported this kernel will be in Lucid.
> **mango42 said:**
> My take on this is that if the devs have decided not to provide a real time kernel then either they have considered it unnecessary or it's just too much work to maintain for vocational coders.
It's not that the devs didn't consider it necessary - it's that Thomas Gleixner  and company (who are not at all connected to Ubuntu) simply skipped creating an rt patch for the 2.6.32 series and instead went directly to 2.6.33.  And Ubuntu, in keeping with their standard release cycle, used 2.6.32 for Lucid as it was the 'current stable' kernel at time those things were frozen for the release cycle.
> **seagullplayer77 said:**
> The part about patching the NVidia drivers is the only part that really bothers me. I run a dual monitor setup, and it was impossible to get it to work right with 9.04.
I had the nvidia drivers working at one point on my desktop with 2.6.33-rt.  I haven't worked with them lately and as of this week there seems to be yet another breakage with them.  I haven't checked out yet.

---

### Post by apparatus on 2010-05-01
> **trulan said:**
> That's correct.  There may be modules that will need to be backported to work on 2.6.31-rt in Lucid - hardware drivers and such.  I've been working with the 2.6.33-rt series and have not booted 2.6.31-rt in Lucid since the early alpha stage of things, so I don't know how fully supported this kernel will be in Lucid.

Alright, thanks.

> **trulan said:**
> I'll probably start a new thread geared toward using the 2.6.33-rt series in Lucid as I'm sure that is something that quite a few people will want.

I'm looking forward to this thread!

---

### Post by giuliano1969 on 2010-06-21
I heard rumors on phoronix that 10.04 will have inserted the preemptive kernel, along with the rt and standard kernel
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_lucid_kernels&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_lucid_kernels&num=1)

I can't find the preemptive kernel in my 10.04 32bit release.

Has it been postponed ?

---

### Post by trulan on 2010-06-21
The lowlatency kernel, which I believe is the same as the preemptive you refer to, is only available for 64 bit.  I don't know why.

---

