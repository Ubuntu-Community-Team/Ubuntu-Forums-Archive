---
title: "Confused About ESM For Ubuntu 14.04"
date: 2022-10-26
forum: Security
---

### Post by mdiemer on 2022-10-26
I have an old machine which needs Nvidia driver 304. Ubuntu 14 allows me to use that driver, and I recently discovered that 14.04's ESM has been extended to 2024. so I can still use this machine with 14.04. It runs great on it because of the Nvidia drivers. 16.04 won't run, even with the driver. I get display failures.

I've been trying to activate ESM for it. I did it before during an earlier run with 14.04, but things have changed. As in, gotten much more complicated. All I want is ESM, so I can use it a couple more years or so. But every time I try to install it, I get routed to Pro, and all kinds of other stuff, like FIP, Azure, etc. I just need ESM for one desktop. I can't figure out how to get that. 

One thing that may be hanging me up: My original SSO account was set up with an old email which I no longer use. I tried changing it, but things got hung up when I clicked on the confirmation URL in my new email. 

In the meantime, until I get this sorted out, should I not use 14.04? I'm very careful, and it is updated, but still it's quite old at this point.

Thanks,

Michael

---

### Post by TheFu on 2022-10-27
14.04 hasn't had any updates since 2019, unless you have ESM working.  There are likely many non-core packages that haven't been updated since 2016.
My strong recommendation is to not allow it on any network, definitely don't allow internet access at all.

ESM is meant to be used by companies with professional IT support staff who understand the issues with running outdated software and can mitigate all those risks.  There are many, many, risks.

CPU costs have dropped. Can't you get a supported GPU and install it?  BTW, I had to do this when my 7200 GS lost nvidia support after a kernel update and nvidia ended proprietary driver support.  Nothing wrong with the card, except the F/LOSS drivers wouldn't output any resolution higher than 1024x768. A week before, it was happily full resolution at 1920x1200 on exactly the same hardware.  My solution was to spend $70 for a current, but cheap, GPU.  It appear the GT 710 is still supported. Perhaps you can find a used one of those somewhere if you absolutely have to stay with nvidia.

OTOH, AMD GPU driver support has become really great since AMD provides the source code to the kernel project.  They sorta just work.  I'm in the process of removing all nvidia hardware here as it stops working ... either dead hardware or crappy driver support.  Decided this about 2 yrs ago. Still have 2 nvidia GPUs running, but a 430 GT needs to be replaced/retired. It is almost dead, doesn't work with a restart, needs a full BRS shutdown/startup to work.  I plan to retire that entire machine (which has been planned for about 4 yrs). ;)  Just need to figure out what to do with the disk storage it holds.

---

### Post by mdiemer on 2022-10-27
Thanks for that, Fu. I am disappointed, because Ubuntu 14 runs so well on this old machine. It actually boots as fast on an old HDD as newer systems do on a SSD. It also looks great. I'm one who liked Unity, and abandoned Ubuntu after 16.04 (although I ran 22.04 briefly on my "new" machine, which is only 8 years old. as opposed to the other, which is 12).

I could upgrade my GPU, I have looked into that. But the machine is so old that it might not be worth it. It could die, and the money would be wasted. Also, last time I looked, prices were through the roof, and with inflation where it is now...

I'm thinking I'll upgrade to 16.04. If I keep it on kernel 4.4, I'll still be able to use the Nvidia drivers. After that, they don't work for this mobo Nvidia 6150SE). I would still need ESM if I do that, as even 16.04 is pretty old at this point.

---

### Post by grahammechanical on 2022-10-27
> But every time I try to install it, I get routed to Pro, and all kinds  of other stuff, like FIP, Azure, etc.

Ubuntu Pro is the improved Ubuntu Advantage. It gives extended cover for many more packages and different types of Ubuntu installation. Such as cloud images. Web links to Ubuntu Advantage are switched to Ubuntu Pro pages. Please note this comment.

> Ubuntu 14.04 LTS &#8216;Trusty Tahr&#8217; will be supported until April 2022 through UA Infrastructure&#8217;s ESM service.

You will find that comment further down this page.

[https://ubuntu.com/blog/ubuntu-14-04-esm-support](https://ubuntu.com/blog/ubuntu-14-04-esm-support)

And then there is this comment about Ubuntu Pro under the heading What You Need:

> An Ubuntu machine running 16.04 LTS, 18.04 LTS, 20.04 LTS or 22.04 LTS             

[https://ubuntu.com/pro/beta](https://ubuntu.com/pro/beta)

Regards

---

### Post by TheFu on 2022-10-27
> **mdiemer said:**
> Thanks for that, Fu. I am disappointed, because Ubuntu 14 runs so well on this old machine. It actually boots as fast on an old HDD as newer systems do on a SSD. It also looks great. I'm one who liked Unity, and abandoned Ubuntu after 16.04 (although I ran 22.04 briefly on my "new" machine, which is only 8 years old. as opposed to the other, which is 12).

I could upgrade my GPU, I have looked into that. But the machine is so old that it might not be worth it. It could die, and the money would be wasted. Also, last time I looked, prices were through the roof, and with inflation where it is now...

I'm thinking I'll upgrade to 16.04. If I keep it on kernel 4.4, I'll still be able to use the Nvidia drivers. After that, they don't work for this mobo Nvidia 6150SE). I would still need ESM if I do that, as even 16.04 is pretty old at this point.

Some of us would love to run our OSes, with support, forever, but Canonical isn't a charity and maintaining each different line of support is expensive.  Just doing the research for what may need to be changed is costly. Plus, Canonical is the packager for most of these things, not the developer, so as the developers keep moving forward for the 50K packages available in each release, Canonical can only really keep up with the most important 2000-3000, which is still a huge effort.  For example, look at the change log just for sshd and ssh-client.  There have been a few releases each year.  Earlier this year, there was a remote execution bug, so all the prior versions would need the correction back-ported.  After all, an LTS should keep running the same version of the software, not any new version.  "New" versions of ssh break compatibility with other systems, so any changes need to be carefully rolled out in a phased way to support new and old releases.  ssh has hardly any dependencies.  Take something like ffmpeg which has 15-30 dependent libraries, each having their own full-time projects, changes, bugs.  It gets ugly, fast.

Paying $100/yr per system to support a dead release is nowhere near enough to cover the costs. If I were estimating how much it costs - which was my job as a development team lead for about 5 yrs - I'd say at least 10 FTEs yearly.  That's in the $2M range and none of those people earn any more direct money for the company - they are overhead.  Obviously, Canonical knows the real numbers for these things and lots of older packages aren't included in their support terms.  On my systems only about &#8532;rd of the packages are in the core Ubuntu support list for 18.04.  I have a 16.04 system around for emergency needs, usually powered off.
```
$ ubuntu-support-status 
Support status summary of 'xxxxxx':

You have 17 packages (2.3%) that can not/no-longer be downloaded
You have 727 packages (97.7%) that are unsupported
```

Just sayin'.  It is a highly specialized system for 1 purpose that I need a few times a year.  A new system has taken over what that box does, but sometimes the historical version is needed.

As for getting a new GPU - how would that be a waste of money?  I'm confused.  When you do eventually replace the computer, reuse the GPU in the new system.  Most of my computer upgrades are where I swap in a new motherboard, CPU and RAM.  Everything else remains, but I get a computer that is 3-5x faster for about $200-$400.  I've never understood why people by complete computers for 3x that amount when 30 minutes with a screwdriver saves so much cash.

---

### Post by mdiemer on 2022-10-27
> **grahammechanical said:**
> Ubuntu Pro is the improved Ubuntu Advantage. It gives extended cover for many more packages and different types of Ubuntu installation. Such as cloud images. Web links to Ubuntu Advantage are switched to Ubuntu Pro pages. Please note this comment.



You will find that comment further down this page.

[https://ubuntu.com/blog/ubuntu-14-04-esm-support](https://ubuntu.com/blog/ubuntu-14-04-esm-support)

And then there is this comment about Ubuntu Pro under the heading What You Need:



[https://ubuntu.com/pro/beta](https://ubuntu.com/pro/beta)

Regards

Thank you for the clarifications. I managed to upgrade to 16.04, and was then able to get ESM attached. I don't know if upgrading did it, or the support ticket I sent to Canonical, but when I logged in to Ubuntu Advantage, my token was there. So I have ESM enabled. So hopefully this will work out.

---

### Post by mdiemer on 2022-10-27
> **TheFu said:**
> 

Just sayin'.  It is a highly specialized system for 1 purpose that I need a few times a year.  A new system has taken over what that box does, but sometimes the historical version is needed.

As for getting a new GPU - how would that be a waste of money?  I'm confused.  When you do eventually replace the computer, reuse the GPU in the new system.  Most of my computer upgrades are where I swap in a new motherboard, CPU and RAM.  Everything else remains, but I get a computer that is 3-5x faster for about $200-$400.  I've never understood why people by complete computers for 3x that amount when 30 minutes with a screwdriver saves so much cash.

You have a point there. When this old Gateway does die, I may do what you do, just replace things as needed and have a new build. assuming it ever does die. I mean, it's 12.5 years old, and still running on the original graphics and PSU. I had upgraded both of those years ago, but they both failed, and I went back to the originals. This thing just won't die, so out of respect for it, I am keeping it going. And running Ubuntu 16, which I also have respect for. They lost me after that.

I also have LXLE focal on another HDD, it works great. LXDE generally does on this rig. I also have yet another system, Trisquel Min, but I had a display failure, so I'm not sure that's going to work. Although it may be due to forgetting to uncheck Hardware Acceleration on Firefox. I have had Bunsen Labs on it also in the past, but I like a true desktop Environment. 

Mostly, I just use this machine to stream music and casual web surfing. I am very careful anyway, but with ESM enabled I feel reasonably safe at this point. I also use it as my tinkering machine. I love trying new distros. but if Ubuntu 16 works out, I'll keep it going. LXLE is definitely a keeper also. Not sure what the third will be. Possibly Bodhi, when they finally come out with version 7.

Addendum: Oh crap, I messed up the quote. I do that now and then. Hope you're not offended. :)

---

### Post by DuckHook on 2022-10-30
It is indeed a shame that computers become obsolete so quickly and contribute so much additional e-waste to our already stressed environment. I used to be big into salvaged HW that could be repositioned into server use or even revitalized for desktop use with minimal upgrades.

More and more though, I'm finding that this goal is becoming untenable. Even Linux is evolving beyond support for really old HW. For example, Ubuntu dropping support for 32-bit HW.

Another factor that forced me to rethink my old salvaging ways was a consideration of electrical consumption: those old workhorses may have been built to last, but they were electricity hogs too. Since a server runs 24/7, by the time one calculates the annual electrical bill, they lose their savings advantage. Electrical efficiency has since become a significant factor for me in deciding if old HW has a place in my SOHO.

Example: my old main production box ate twice as much power as my new one. That's over $200 a year if it is on 24/7.

In your case, a new GPU may end up actually saving you money. Those old video cards ran hot, and new ones, especially if they are high&#8209;efficiency low&#8209;powered non&#8209;gaming ones may return your investment sooner than you think. Besides, they render much better graphics, which is always nice.

---

### Post by mdiemer on 2022-10-31
> **DuckHook said:**
> It is indeed a shame that computers become obsolete so quickly and contribute so much additional e-waste to our already stressed environment. I used to be big into salvaged HW that could be repositioned into server use or even revitalized for desktop use with minimal upgrades.

More and more though, I'm finding that this goal is becoming untenable. Even Linux is evolving beyond support for really old HW. For example, Ubuntu dropping support for 32-bit HW.

Another factor that forced me to rethink my old salvaging ways was a consideration of electrical consumption: those old workhorses may have been built to last, but they were electricity hogs too. Since a server runs 24/7, by the time one calculates the annual electrical bill, they lose their savings advantage. Electrical efficiency has since become a significant factor for me in deciding if old HW has a place in my SOHO.

Example: my old main production box ate twice as much power as my new one. That's over $200 a year if it is on 24/7.

In your case, a new GPU may end up actually saving you money. Those old video cards ran hot, and new ones, especially if they are high&#8209;efficiency low&#8209;powered non&#8209;gaming ones may return your investment sooner than you think. Besides, they render much better graphics, which is always nice.

You raise a good point there about electricity and temperature. Electricity is expensive where I live. As for heat, when I did the upgrade from UB14 to UB16, the CPU revved so much at times, I actually got nervous. I did try a new card about a year ago, but it was actually an old one I got off E bay. I think it was a GT 630. but it didn't work. I did recoup my investment, fortunately. but maybe I'll try again, since this old Gateway Gt5656 quad core just keeps on truckin'. 

Thanks for fixing my last post, by the way. I don't know how I do that, but it happens to me every now and then. I guess I should just do those over, but I'm always afraid I'll mess things up more. My typing and clerical skills in general are atrocious.

---

