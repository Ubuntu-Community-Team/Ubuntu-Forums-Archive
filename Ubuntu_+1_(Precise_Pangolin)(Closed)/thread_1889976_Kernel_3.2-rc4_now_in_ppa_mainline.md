---
title: "Kernel 3.2-rc4 now in ppa mainline"
date: 2011-12-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2011-12-02
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/)

---

### Post by Harry33 on 2011-12-03
This is in Precise official repos now too.

Here:
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-3.7](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-3.7)

---

### Post by 3vi1 on 2011-12-03
> **Harry33 said:**
> This is in Precise official repos now too.

Here:
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-3.7](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-3.7)

Hmmm...  What exactly is the difference between those two kernels?

As you may have seen in the other thread.  The one in the official repos fails to work on my system when using nvidia-current (285 and 290) as have all of the 'official' 3.2 kernels.  Oddly, the rc4 that Paul linked works fine.

:confused:

---

### Post by paul_in_london on 2011-12-03
> **3vi1 said:**
> Hmmm...  What exactly is the difference between those two kernels?

As you may have seen in the other thread.  The one in the official repos fails to work on my system when using nvidia-current (285 and 290) as have all of the 'official' 3.2 kernels.  Oddly, the rc4 that Paul linked works fine.

:confused:

The kernels in ppa mainline are vanilla AFAIK - i.e. they don't have the ubuntu "sauce" that you'll see mentioned in the changelogs.

3.2.0-3.8 (amd64) is apparently building at the moment and should come through as an update soon.


```
https://launchpad.net/ubuntu/+source/linux/3.2.0-3.8/+build/2982063
```

EDIT - Changelog:

```
Changelog

linux (3.2.0-3.8) precise; urgency=low

  [ Andy Whitcroft ]

  * armhf -- add d-i configuration
  * armhf -- disable ABI checks for armhf
  * armhf -- add arch to getabis config
 -- Andy Whitcroft <email address hidden>   Sat, 03 Dec 2011 14:22:52 +0000
```

Doesn't say so explicitly, but it will presumably be based on rc4.

---

### Post by paul_in_london on 2011-12-03
3.2.0-3.8 (amd64) built ok:

```
https://launchpad.net/ubuntu/+source/linux/3.2.0-3.8/+build/2982063
```

Download from launchpad or just wait for the updates to turn up.

---

### Post by zika on 2011-12-03
> **paul_in_london said:**
> 3.2.0-3.8 (amd64) built ok:

```
https://launchpad.net/ubuntu/+source/linux/3.2.0-3.8/+build/2982063
```Download from launchpad or just wait for the updates to turn up.
"386" package that contains *all.deb is not finished yet. So, it would be an incomplete install...

---

### Post by paul_in_london on 2011-12-03
> **zika said:**
> "386" package that contains *all.deb is not finished yet. So, it would be an incomplete install...

Oops! Sorry, forgot to check that! Thanks for pointing it out.

---

### Post by 3vi1 on 2011-12-03
> **paul_in_london said:**
> 3.2.0-3.8 (amd64) built ok:

```
https://launchpad.net/ubuntu/+source/linux/3.2.0-3.8/+build/2982063
```

Download from launchpad or just wait for the updates to turn up.

Same symptoms:

```

Dec  3 15:20:58 saturn kernel: [    4.614087] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  285.05.09  Fri Sep 23 17:31:57 PDT 2011
Dec  3 15:21:09 saturn kernel: [   16.267342] NVRM: RmInitAdapter failed! (0x27:0x38:1193)
Dec  3 15:21:09 saturn kernel: [   16.267348] NVRM: rm_init_adapter(0) failed

```

So, apparently it's some patch/build-option that Canonical is adding that's causing the issue with my video.

Launchpad seems to be timing out quite a bit right now, so I'll go do my Machine Learning homework anf file a bug for it tomorrow.

---

### Post by paul_in_london on 2011-12-03
> **3vi1 said:**
> Same symptoms:

```

Dec  3 15:20:58 saturn kernel: [    4.614087] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  285.05.09  Fri Sep 23 17:31:57 PDT 2011
Dec  3 15:21:09 saturn kernel: [   16.267342] NVRM: RmInitAdapter failed! (0x27:0x38:1193)
Dec  3 15:21:09 saturn kernel: [   16.267348] NVRM: rm_init_adapter(0) failed

```

So, apparently it's some patch/build-option that Canonical is adding that's causing the issue with my video.

Launchpad seems to be timing out quite a bit right now, so I'll go do my Machine Learning homework anf file a bug for it tomorrow.

But weren't you saying in the other thread that there was some suggestion the nvidia driver is buggy with cards that have larger amounts of RAM? If a newer kernel is still loading the same graphics driver it's not necessarily going to start working correctly. Or maybe I misunderstood what you were saying?

EDIT: You did say it was working with the 3.1 kernels so it could be related to a regression in 3.2 or maybe the problem was "masked" by a bug in 3.1 that has been fixed in 3.2.

---

### Post by VinDSL on 2011-12-03
Heh!  I installed 3 different Linux 3.2.x kernels yesterday.

Every one of them failed on this machine.  Same ol' thing:

[LIST]
[*]No network service, e.g. no Internet
[*]Hangs on shutdown, e.g. cannot reboot
[/LIST]
Other than that, 3.2.x works fine.  :D

---

### Post by 3vi1 on 2011-12-03
> **paul_in_london said:**
> But weren't you saying in the other thread that there was some suggestion the nvidia driver is buggy with cards that have larger amounts of RAM? If a newer kernel is still loading the same graphics driver it's not necessarily going to start working correctly. Or maybe I misunderstood what you were saying?

Yes, there were posts to that effect, but it was still pretty nebulous as to whether or not I was running in to the same problem as those guys, as at least one of them had an additional message in their kernel log that indicated a vmap issue.  And, the fact that the rc4 kernel works fine makes it really murky to me as to whether or not it's the driver after all.

At any rate, I'm going to give them the symptoms/data and see if it makes more sense to them than to me.  If they say it's invalid/wont-fix/nvidia's, then I can at least start questioning nVidia as to when their next driver will be available for testing.  I'd hate to see 12.04 come out and find that a large number of people with high end hardware can't even start Unity in 3D mode.

---

### Post by VinDSL on 2011-12-03
> **paul_in_london said:**
> EDIT: You did say it was working with the 3.1 kernels [...]
I know you're 'talking' to someone else, but...

Linux 3.1.0-2.x / nVidia 285.05.09 works a treat on this machine!  Flies like the wind...

I've run all sorts of Kernels on this box, including Unity on top of Liquorix, and never had problems like this.

IMO, there is definitely something amiss in Linux 3.2  ;)

> **3vi1 said:**
> I'd hate to see 12.04 come out and find that a large number of people with high end hardware can't even start Unity in 3D mode.
I'm (basically) running a high-end Gaming Machine, circa 2005.  LoL!

I suppose we're talking apples n' oranges.

I don't have any problem with my nVidia card / drivers, but...

From everything I've read in this +1 Forum, in various threads, the common denominator appears to be hardware related issues - on both old iron & uber new.

It's akin to Goldilocks & The Three Bears:

[LIST]
[*]This one is too old
[*]This one is too new
[*]But, this one is just right
[/LIST]

---

### Post by paul_in_london on 2011-12-03
> **3vi1 said:**
> Yes, there were posts to that effect, but it was still pretty nebulous as to whether or not I was running in to the same problem as those guys, as at least one of them had an additional message in their kernel log that indicated a vmap issue.  And, the fact that the rc4 kernel works fine makes it really murky to me as to whether or not it's the driver after all.

At any rate, I'm going to give them the symptoms/data and see if it makes more sense to them than to me.  If they say it's invalid/wont-fix/nvidia's, then I can at least start questioning nVidia as to when their next driver will be available for testing.  I'd hate to see 12.04 come out and find that a large number of people with high end hardware can't even start Unity in 3D mode.

Oh, ok. I didn't realise it was working for you with 3.2-rc4. We'll have to see what happens with the next nvidia driver...

---

### Post by paul_in_london on 2011-12-03
> **VinDSL said:**
> I know you're 'talking' to someone else, but...

Linux 3.1.0-2.x / nVidia 285.05.09 works a treat on this machine!  Flies like the wind...

I've run all sorts of Kernels on this box, including Unity on top of Liquorix, and never had problems like this.

IMO, there is definitely something amiss in Linux 3.2  ;)


I'm (basically) running a high-end Gaming Machine, circa 2005.  LoL!

I suppose we're talking apples n' oranges.

I don't have any problem with my nVidia card / drivers, but...

From everything I've read in this +1 Forum, in various threads, the common denominator appears to be hardware related issues - on both old iron & uber new.

It's akin to Goldilocks & The Three Bears:

[LIST]
[*]This one is too old
[*]This one is too new
[*]But, this one is just right
[/LIST]

No problem - thanks for the input. The vagaries of hardware! This box is about 5 years old, but working pretty well. Minimal install + GS + xorg-edgers and ricotz-testings ppas. :)

---

### Post by 3vi1 on 2011-12-03
> **VinDSL said:**
> I know you're 'talking' to someone else, but...

Linux 3.1.0-2.x / nVidia 285.05.09 works a treat on this machine!  Flies like the wind...

I've run all sorts of Kernels on this box, including Unity on top of Liquorix, and never had problems like this.

IMO, there is definitely something amiss in Linux 3.2  ;)

Yeah... 3.1's worked great for me too...  I'm just trying to help troubleshoot this 3.2 weirdness before we get to beta and people notice.  :)

I've had USB3.0 issues with 3.2 on this machine also... but the 3.2rc4 kernel linked at the beginning of this thread appears to be working great for me across the board. 

On the other hand, I have a CR-48 running the stock 3.2 kernels, and it's never had any trouble whatsoever.

---

### Post by IanW on 2011-12-04
> **paul_in_london said:**
> Doesn't say so explicitly, but it will presumably be based on rc4.

The announcement for 3.2.0-3.7 stated that it was based on rc4.

---

### Post by kuvanito on 2011-12-04
hi guys,i am three years old into ubuntu and always want to have the latest cutting edge softwares in my ubuntu,so i went ahead and installed the latest kernel following this steps i found and everything worked to a tee,i am very happy about it,i had to remove my nvidia before a rbooted and my nvidia is now recognized as a Gallium 0.4 on NV4C that's weird..but never the less i am happy.```
Install latest kernel 32bit by going here:
http://kernel.ubuntu.com/~kernel-ppa/mainline/

1-download linux-image-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb
2-download linux-headers-3.2.0-030200rc4_3.2.0-030200rc4.201112012035_all.deb
3-download linux-headers-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb
4-open a terminal and type cd Downloads
5-sudo dpkg -i linux-image-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb
6-sudo dpkg -i linux-headers-3.2.0-030200rc4_3.2.0-030200rc4.201112012035_all.deb
7-sudo dpkg -i linux-headers-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb
8-sudo apt-get update
9-sudo apt-get upgrade
10-sudo apt-get install -f
11-see note:sudo reboot.

Note:Remove any Nvidia Drivers before a Reboot.(sudo apt-get remove nvidia*)
```
good luck

---

### Post by Harry33 on 2011-12-04
> **VinDSL said:**
> Heh!  I installed 3 different Linux 3.2.x kernels yesterday.

Every one of them failed on this machine.  Same ol' thing:

[LIST]
[*]No network service, e.g. no Internet
[*]Hangs on shutdown, e.g. cannot reboot
[/LIST]
Other than that, 3.2.x works fine.  :D

Does the PP official repo version (3.2.0-3.8 rc4) still work OK for you.
They work fine in my setups.

---

### Post by VinDSL on 2011-12-04
> **Harry33 said:**
> Does the PP official repo version (3.2.0-3.8 rc4) still work OK for you.
They work fine in my setups.
No.

I've tried 3.2.everything, and so far, they've all exhibited the same two problems.

It's almost like Linux 3.2x doesn't support whatever onboard chipset this mobo is using for networking.

If this keeps up, I'll toss a 3rd party nic in here (I've probably got 10 of them in my closet) and see if that works.

---

### Post by paul_in_london on 2011-12-04
Not sure why 3.2.0-3.8 (amd64) hasn't come through for me yet as an update from the repos.

Anyway, I dowmloaded **linux-headers-3.2.0-3_3.2.0-3.8_all.deb** from here:

```
launchpad.net/ubuntu/precise/i386/linux-headers-3.2.0-3/3.2.0-3.8
```

**linux-headers-3.2.0-3-generic_3.2.0-3.8_amd64.deb** from here:

```
launchpad.net/ubuntu/precise/amd64/linux-headers-3.2.0-3-generic/3.2.0-3.8
```

and **linux-image-3.2.0-3-generic_3.2.0-3.8_amd64.deb** from here:

```
launchpad.net/ubuntu/precise/amd64/linux-image-3.2.0-3-generic/3.2.0-3.8
```

---

### Post by Harry33 on 2011-12-05
> **paul_in_london said:**
> Not sure why 3.2.0-3.8 (amd64) hasn't come through for me yet as an update from the repos.

Anyway, I dowmloaded **linux-headers-3.2.0-3_3.2.0-3.8_all.deb** from here:

```
launchpad.net/ubuntu/precise/i386/linux-headers-3.2.0-3/3.2.0-3.8
```**linux-headers-3.2.0-3-generic_3.2.0-3.8_amd64.deb** from here:

```
launchpad.net/ubuntu/precise/amd64/linux-headers-3.2.0-3-generic/3.2.0-3.8
```and **linux-image-3.2.0-3-generic_3.2.0-3.8_amd64.deb** from here:

```
launchpad.net/ubuntu/precise/amd64/linux-image-3.2.0-3-generic/3.2.0-3.8
```

This was because the linux metapackage was not in repos then.
Well it is now:
[https://launchpad.net/ubuntu/precise/+source/linux-meta/3.2.0.3.3](https://launchpad.net/ubuntu/precise/+source/linux-meta/3.2.0.3.3)

---

### Post by paul_in_london on 2011-12-05
> **Harry33 said:**
> This was because the linux metapackage was not in repos then.
Well it is now:
[https://launchpad.net/ubuntu/precise/+source/linux-meta/3.2.0.3.3](https://launchpad.net/ubuntu/precise/+source/linux-meta/3.2.0.3.3)

Ah - thanks Harry! Hadn't thought of that. :)

---

