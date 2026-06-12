---
title: "Suggestions on choosing the right VM"
date: 2009-02-10
forum: Virtualisation
---

### Post by chancekang on 2009-02-10
Hey guys, I am running Intrepid with the kernel version of 2.6.27-11. Due to work issues, I need a platform to run VS.Net. So, I am wondering if anyone can suggest a VM for me. What I am looking for is just:

1. Stable(This is the most important thing)
2. Low CPU usage

I have tried VirtualBox in Hardy. It is not bad with the stable issue, but eats too much CPU resources. I was running on a laptop with T7250 + 3 Gig RAM, assigning one core to VB. The CPU usage always went 50% (100% on single core) even I did nothing in the guest OS. It was not a pleasant experience.

Would anyone give some kind suggestions? Thanks in advance!

---

### Post by Simian Man on 2009-02-10
Virtualbox performance can be much increased using the VT-x/AMD-v option.  This allows it to use CPU extensions to scale back on processor usage.  Without this, it has no way of knowing whether the guest is idle or not, so it just keeps executing, often wasting cycles.

---

### Post by konqueror7 on 2009-02-10
i agree with *Simian Man*, VirtualBox is my choice for a VM, been using it in both my winxp and ubuntu machine...

---

### Post by bodhi.zazen on 2009-02-10
You have several options and they all have advantages and disadvantages, thus you will get mostly opinions on a thread like this.

IMO, VirtualBox, VMWare, and if you CPU supports it, KVM are all excellent options.

IMO I find VMWare and KVM to be more stable then Virtualbox. Not to say that virtualbox is in any way unstable, but I have had more problems with it.

I have not been happy with VMWare Server 2.0.x :(

IMO KVM has the least overhead, but I could be worng about that.

I think it is best if you derive a list of what you want and then match the features you need with the application.

---

### Post by dcstar on 2009-02-15
> **bodhi.zazen said:**
> You have several options and they all have advantages and disadvantages, thus you will get mostly opinions on a thread like this.

IMO, VirtualBox, VMWare, and if you CPU supports it, KVM are all excellent options.
.......

Going by the list of problems in this forum at the moment, Virtualbox seems to have a lot more issues than VMware. That could be an indication of more users, or it could be an indication of a less stable VM environment.

FWIW, I use VMware Server 1.0.8 (2.0 annoyed me greatly....) and it does the job for me in a nice, reliable way on my 64 bit system.

---

### Post by niteshifter on 2009-02-15
Hi,

I think Virtualbox is the more popular around here in Ubuntu-land based upon the number of requests about it - but that is purely subjective. One thing about VBox is its sensitivity to host hardware and OS - it seems like no two people get same results. Notice the same with other VM solutions.

For instance, another poster lamented about high CPU usage with VBox. His CPU and RAM specs are better than mine. Curious minded type that I am I exited FF on the host and fired up the Solaris VM (a resource hungry OS) to post this, while watching resource usage on the host's System Monitor. It hit 100% one core while loading but is now bouncing a load of 10% - 70% on both cores - while down converting a batch of MP3's in the host. Go figure ...

My take: Just pick a VM solution. Define clearly what you want and give the pick a trial. No joy? Move on to another. Opinions you get from users here and elsewhere of a given VM solution - while informative to a point - aren't benchmark material. Even the benchmarks that exist "out there" aren't all that useful.

---

### Post by HermanAB on 2009-02-16
Just try them all and see which one works for you.  That is really the only way.  

However, don't bother trying VMware server 2 - it is a POS. Some things should *not* have a built in web server...

Cheers,

Herman

---

### Post by binbash on 2009-02-16
I used vmware workstation and virtualbox.From my experience vmware workstation is more stable and better.

---

### Post by the_unforgiven on 2009-02-16
If you want something light-weight, I suggest go for KVM - it's bare-bones. You might want to check out Redhat's [virt-manager]("http://virt-manager.org/") for a wrapper on top of KVM.

If you want something similar to VMware workstation, VBox is quite good. However, you should note that it's a fast-moving target - both in terms of underlying hypervisor technology as well as GUI.

---

