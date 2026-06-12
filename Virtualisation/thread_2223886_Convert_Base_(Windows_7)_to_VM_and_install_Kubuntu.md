---
title: "Convert Base (Windows 7) to VM and install Kubuntu as Primary"
date: 2014-05-13
forum: Virtualisation
---

### Post by Brent_Wassell on 2014-05-13
I'm looking to turn my base OS Windows 7 into a VM and then run Kubuntu 14.04 64bit as my main OS - and then run Windows 7 as needed inside of VMWare for work applications.

Any tips/guides/process for doing this?

Volume Windows 7 licensing so should be good to go there...

---

### Post by TheFu on 2014-05-14
There are thousands of tips. I don't use VMware products, but tuning of VMs is basically the same as tuning real OSes - with one extra caveat. 

Don't be a hog. Sharing is good.

That means, don't over allocate anything for the VM.
* Min CPU
* Min RAM
* Min storage

[http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) is not VMware specific, but explains what and why.  BTW, I have a Win7 VM doing TV recording for the last 2+ yrs. Works well.

Why VMware when KVM is F/LOSS, extremely stable, and likely faster?

---

### Post by KillerKelvUK on 2014-05-14
Not attempted but if I were to give this a bash I'd probably use CloneZilla to grab the Win partition and boot record...create my vm guest with as close a spec to the original as possible i.e. disk bus type and overall block capacity...then use CloneZilla within the guest to restore the Win partition but effectively into your vm disk, then comes the faffing with Win to get it back to life.

I run a Win7 guest in a KVM host, no issues...the lastest 14.04 release addresses some of the core networking bugs which plagued making this simple in 12.04 and the USB passthru is now resolved.  Performance wise using the virtio drivers in windows for disk and network I think its pretty damn good, only problem you'll have is enabling these post win install (if you're going to try KVM that is).  The corp I work for is a MS shop so I need Win+Office for that, have run all this from a vm for nearly a year now...stepping away from a native MS OS was the best!  Make sure to pay attention to TheFu's tuning points though <*LIFE SAVER*>

---

### Post by Brent_Wassell on 2014-05-15
Thank you for the tips.

The company I work for has VMWare Licenses - and we have a lot of VMs preconfigured with certain applications that are easy to grab and bring over.

I have never used KVM - is it a baremetal hypervisor itself?  IE would I install that on the root of my machine - and then run different VMs on top of that?  Or, does it require a Host OS?

As far as using CloneZilla or other means - I guess I'm wondering the best way to do a P to V (physical to virtual) conversion for my current Windows 7 OS.  I suppose I could do a fresh install - it definitely wouldn't hurt.

Thanks.

---

### Post by Brent_Wassell on 2014-05-15
One more very important question.

My laptop has 16GB of RAM as I run lots of VMs on it currently.

If I change my main OS to Kubuntu 14.04 - do I have to install a 64-bit version to utilize my laptops hardware?

I ask because it recommends a 32-bit install - but I want to make sure my system can recognize and use all of my RAM available.

---

### Post by TheFu on 2014-05-15
> **Brent_Wassell said:**
> Thank you for the tips.

The company I work for has VMWare Licenses - and we have a lot of VMs preconfigured with certain applications that are easy to grab and bring over.

I have never used KVM - is it a baremetal hypervisor itself?  IE would I install that on the root of my machine - and then run different VMs on top of that?  Or, does it require a Host OS?

As far as using CloneZilla or other means - I guess I'm wondering the best way to do a P to V (physical to virtual) conversion for my current Windows 7 OS.  I suppose I could do a fresh install - it definitely wouldn't hurt.

Thanks.

VMware makes 6 different virtualization tools. Which are you using? The P2V method will care.

KVM is not bare metal anymore than ESXi is. KVM is a KERNEL MODULE for Linux. You can put as much or as little OS on it  - your choice. Plus it is tested like the entire Linux kernel is tested and gets performance improvements from the community that other "hypervisors" don't integrate very quickly. Plus Linux works on 1,000s more HW configs than ESXi - I've been burned numerous times with unsupported hardware for ESX/ESXi over the years. Picky, picky.

I haven't ever done a Windows P2V conversion successfully, always ended up re-installing.  Don't use Windows much anymore, so that isn't too hard - also only install packages from ninite these days - sorta a poor-man's APT repo - and don't load desktop programs on Win anyway - not safe on the internet anymore.  The only thing that sucks when moving Windows is that my media center settings are all lost and transferring them over ends up with corruption thanks to all the registry crap that isn't transferred too (I guess). 

So ... you can screw around with P2V stuff for 3 days only to find out it didn't work
OR
you can bite it, reinstall and get to reconfiguring Windows.

You know ... Linux migrations of any sort are much, much, much easier and loosing settings is just crazy talk these days.

---

### Post by TheFu on 2014-05-15
> **Brent_Wassell said:**
> One more very important question.

My laptop has 16GB of RAM as I run lots of VMs on it currently.

If I change my main OS to Kubuntu 14.04 - do I have to install a 64-bit version to utilize my laptops hardware?

I ask because it recommends a 32-bit install - but I want to make sure my system can recognize and use all of my RAM available.

Your questions are inconsistent. I find them confusing.
Who recommends 32-bit?  Certainly NOT ubuntu. They've recommended 64-bit since 2010.  I don't know anything about Kubuntu - stopped using KDE back in the 1990s.

32-bit will limit any process to 4G total RAM, provided PAE mode is installed and working. The hostOS will be able to access all 16G of RAM, but with important limitations. Read up on that at help.ubuntu.com.

If I had 16G of RAM, there would be NO QUESTION - 64-bit OS. Heck, with 4G of RAM there isn't any question - 64-bit OS is still the answer. Is this a server or a desktop install?  Are most of the VMs servers or desktops? What sort of workloads?  If it is a laptop, I doubt you'll be laoding ESXi.

---

### Post by Brent_Wassell on 2014-05-15
It's a laptop.

Would definitely not be loading ESXi.

I guess it's KDE that doesn't recommend 64-bit...
[[img]http://s30.postimg.org/nvza0zbul/Screen_Shot755.jpg[/img]](http://postimg.org/image/nvza0zbul/)

I don't think I'll mess with P2V I'll just do a clean install.  Easier / neater.

---

