---
title: "help me with keeping the kernel up to date."
date: 2013-04-30
forum: Ubuntu Studio
---

### Post by ERRRIMMAD on 2013-04-30
It's a bit hard to understand this about Ubuntu Studio, from what I understand it's a Low Latency Kernel.

I'm using Ubuntu Studio 12.04, because it is LTS.

How do I upgrade the Kernel to the newest LTS for Ubuntu Studio, I mean is their a wiki page about the latest Ubuntu Studio LTS Kernel or something.

How do I find this information? I know that the Low Latency Kernel is slower than the generic, and that the Real Time even slower because of processor priorities, but it's not the information I'm looking for.

It's nice to know this stuff, but what I want to know is how do I upgrade to the latest supported LTS Kernel for Ubuntu studio and where do I find a page relating to this information, I'm not wanting to compile a Kernel or anything, I want the Kernel to be stable, it does not need to be the most cutting edge Kernel, just the most stable LTS up to date Kernel.

Any help would be great, this is a completely new area to me, updating the Kernel, is there a way to update it simply through the update manager or something?

Thanks.

---

### Post by cub on 2013-05-01
I'm not sure I follow the issue. You want to upgrade to the latest 12.04 LTS kernel? That should follow from the usual updates either through Update Manager or 'sudo apt-get update && sudo apt-get upgrade'. That should include the latest kernel that is tested for 12.04.
The cutting edge kernels are implemented in the 12.10 and 13.04 releases, as I understand it.

---

### Post by ERRRIMMAD on 2013-05-01
Thanks cub, yeah, that's because I don't 100% understand this myself. if I do "uname -r" in terminal it spits back 3.2.0-39-lowlatency, is this the latest release?

It would seem that the update manager does update the Kernel from what I have read, but I have not found any clear statement from Ubuntu about if this is true or not.

I want to stick with the 12.04 version for stability, at least this is what I believe ( I could be misunderstanding this whole thing), so I don't want Raring Ringtail or Quantal Quetzal Kernels if I'm correct because they are not long term support.

And I'm 100% sure I don't want to compile my own Kernel because I want the benefits both for myself and Ubuntu that come with using the stock Kernel, if I compile my own Ubuntu will not use my data reports to make their OS better and the updates will be 100% use at my own risk, which in a way they already are, LOL, but at least this way the updates are tested on the specific kernel build I'm using.

---

### Post by zequence on 2013-05-01
Hi, I'm the linux-lowlatency maintainer. Usually, linux-lowlatency follows linux-generic in the update cadence. A new kernel every 3 weeks or so. Sometimes more often. 
It might happen time to time that -lowlatency will fall behind, but not often.

If you do an update right now, you'll find a new kernel in the repo, released at the same time as linux-generic. Latest linux-lowlatency is now 3.2.0-41.45.

Ubuntu has done a stable release update introducing linux 3.5 to Precise. linux-lowlatency has not gone the same path yet, but the 3.2 kernel is quite up to date, and will be in the future too.

---

### Post by ERRRIMMAD on 2013-05-01
Thanks zequence. =D

Yes, I ran update manager and it updated my Kernel to 3.2.0-40 low latency, so that answered my question, thanks so much for every ones help, don't know why I was having so much trouble understanding this topic.

Also, I found this website that seems to keep track of the Kernels for 12.04, in case anyone else was wondering. [https://launchpad.net/ubuntu/precise/+source/linux-lowlatency](https://launchpad.net/ubuntu/precise/+source/linux-lowlatency)

---

