---
title: "Which System76 laptop has the best battery life?"
date: 2010-06-21
forum: System76 Support
---

### Post by otakuj462 on 2010-06-21
Hi,

I was just wondering, what kind of battery life people are getting on System76 machines?

Let me know. Thanks,

Jake

---

### Post by thomasaaron on 2010-06-21
Right now, it would be the Lemur Ultrathin... with about 3+ hours of battery life. (I'm not including netbooks.)

---

### Post by otakuj462 on 2010-06-23
> **thomasaaron said:**
> Right now, it would be the Lemur Ultrathin... with about 3+ hours of battery life. (I'm not including netbooks.)

thomasaaron, thanks for the reply. I'm looking for a laptop with at least 5+ hours battery life for moderate usage, so I guess I'll hold off on a System76 purchase.

Thanks again,

Jake

---

### Post by slyblade900 on 2011-10-09
I was on to purchasing one too. Thanks for the reply. I guess i'll try my luck somewhere else

---

### Post by 3Miro on 2011-10-09
I can get almost 3 hours with my i7/8GBRAM Pangolin Performance. The Lemur should get at least 4, some tweaking may be needed. Look up Jupiter applet.

---

### Post by isantop on 2011-10-10
> **slyblade900 said:**
> I was on to purchasing one too. Thanks for the reply. I guess i'll try my luck somewhere else

All of our current systems can get around 3 hours of battery life. I should note that there is currently a bug in the Linux kernel that causes battery life to be much lower than it should be. Once this bug is resolved, we expect battery life across the board to improve, particularly in the Pangolin range.

---

### Post by Dave_L on 2011-10-10
Do you have any more information about the kernel bug?

---

### Post by fuduntu on 2011-10-10
> **Dave_L said:**
> Do you have any more information about the kernel bug?

Yep - There isn't one.

Hope it helps. :D

---

### Post by jbelmonte on 2011-10-11
> **fuduntu said:**
> Yep - There isn't one.

Hope it helps. :D

Is Fuduntu spreading FUD?

[http://linux.slashdot.org/story/11/10/07/237222/kernel-bug-means-linux-power-usage-remains-high]("http://linux.slashdot.org/story/11/10/07/237222/kernel-bug-means-linux-power-usage-remains-high")

---

### Post by Dragonbite on 2011-10-11
Should also include that some, but not all, of the systems have an extended or larger battery as an option.

---

### Post by fuduntu on 2011-10-11
> **jbelmonte said:**
> Is Fuduntu spreading FUD?

[http://linux.slashdot.org/story/11/10/07/237222/kernel-bug-means-linux-power-usage-remains-high]("http://linux.slashdot.org/story/11/10/07/237222/kernel-bug-means-linux-power-usage-remains-high")

No, I am not spreading FUD.  Phoronix is spreading FUD.

[http://www.fewt.com/2011/09/about-kernel-30-power-regression-myth.html](http://www.fewt.com/2011/09/about-kernel-30-power-regression-myth.html)

---

### Post by jbelmonte on 2011-10-11
> **fuduntu said:**
> No, I am not spreading FUD.  Phoronix is spreading FUD.

[http://www.fewt.com/2011/09/about-kernel-30-power-regression-myth.html](http://www.fewt.com/2011/09/about-kernel-30-power-regression-myth.html)

Are you referencing your own blog?

What is your opinion on [Launchpad Bug Report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131")?

---

### Post by fuduntu on 2011-10-11
> **jbelmonte said:**
> Are you referencing your own blog?

What is your opinion on [Launchpad Bug Report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131")?

Yes, why wouldn't I when I did all of the research and presented it on my blog?

Had you read it, you would have found my opinion on 760131 (referenced in the article found on my blog) as an example of *doing it wrong*.

---

### Post by jbelmonte on 2011-10-11
> **fuduntu said:**
> Yes, why wouldn't I when I did all of the research and presented it on my blog?

There is nothing wrong with referencing your own blog, but failing to identify it as such makes it seem like you wanted everyone to believe it was an independent source. 

> **fuduntu said:**
> Had you read it, you would have found my opinion on 760131 (referenced in the article found on my blog) as an example of *doing it wrong*.

I did read the blog, but I wasn't sure it was you. That's why I asked. Now I know it is you, I know your stance.

I guess the bottom line for me is that if my battery life goes down after an kernel update, it is the kernel's fault. Whether someone calls it a "regression" or a "bug" or tries to tell me theat I'm "doing it wrong" is just semantics. Linux power management is getting worse and needs to be imporoved. If Juniper or tuned actually help, then they should be included as an option during installation or upgrade. YMMV

---

### Post by fuduntu on 2011-10-11
> **jbelmonte said:**
> There is nothing wrong with referencing your own blog, but failing to identify it as such makes it seem like you wanted everyone to believe it was an independent source. 

I did read the blog, but I wasn't sure it was you. That's why I asked. Now I know it is you, I know your stance.


You are probably the last person at UF that didn't know.  It's common knowledge here, there was no intent.

> **jbelmonte said:**
> 
I guess the bottom line for me is that if my battery life goes down after an kernel update, it is the kernel's fault. Whether someone calls it a "regression" or a "bug" or tries to tell me theat I'm "doing it wrong" is just semantics. Linux power management is getting worse and needs to be imporoved. If Juniper or tuned actually help, then they should be included as an option during installation or upgrade. YMMV

The point of "you are doing it wrong" is that if the battery life goes down after a kernel update and you have 15 applications all doing work that you didn't have running before the kernel update, the problem isn't the kernel update, it is just a busy system that doesn't match the baseline.  It is not an issue of semantics, it is an issue of proper testing.

Regardless, there is a workaround to the kernel disabling ASPM when it determines the BIOS to be buggy.

Use it if you are OK with the risk of instability for a few extra minutes of power.  The point remains that it is not a bug in the kernel.

;)

---

### Post by jbelmonte on 2011-10-12
> **fuduntu said:**
> You are probably the last person at UF that didn't know.  It's common knowledge here, there was no intent.

This is not the only thing about which I have been the last person to know.

> **fuduntu said:**
> The point of "you are doing it wrong" is that if the battery life goes down after a kernel update and you have 15 applications all doing work that you didn't have running before the kernel update, the problem isn't the kernel update, it is just a busy system that doesn't match the baseline.  It is not an issue of semantics, it is an issue of proper testing.

Regardless, there is a workaround to the kernel disabling ASPM when it determines the BIOS to be buggy.

Use it if you are OK with the risk of instability for a few extra minutes of power.  The point remains that it is not a bug in the kernel.

;)

I understand your point about testing. However, many people, myself included, while doing their normal activities have seen battery life reduced after the kernel upgrade. I know this is not testing, but is does point to a problem. Let's assume I agree with you that it is not a kernel bug or regression. Then the poor/reduced battery life under a standard install of Ubuntu on a laptop indicates a deficiency in Ubuntu. The fact that in a dual boot situation with Windows, battery life is substantially better under Windows also indicates a deficiency in Ubuntu for mobile computing.  Yes, there are workarounds that might help somewhat, but with the risk of instability. That risk/reward ratio doesn't seem worth it to me. 

I understand the decision of the developers to force ASPM to turn off on systems that report that it is unsupported. I also understand the difficulties inherent in making correct decisions when complete information on BIOS and hardware drivers are not forthcoming from their developers. I just hope this doesn't mean we are stuck forever with sub-optimal battery life under Ubuntu.

People have been talking about [Coreboot]("http://ubuntuforums.org/showthread.php?t=887170") on this forum for a couple of years. Could this or something like it help for dedicated Linux Systems?

Your signature touts Fuduntu as "A Linux distribution offering stability, incredible performance and unparalleled battery life." I think I will give it a try on my laptop. I may be the last to know, but I can learn.

---

### Post by regixmfn on 2011-10-12
Three hours does seem a little short, for a laptop. I was actually thinking about putting down some cash on one of these well designed systems. Battery life isn't much an issue.. However, will there be an increase of battery life?

---

### Post by isantop on 2011-10-13
> **fuduntu said:**
> Yep - There isn't one.

Hope it helps. :D

Actually, there is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

The information is in the bug report.

---

### Post by fuduntu on 2011-10-13
> **isantop said:**
> Actually, there is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

The information is in the bug report.

lol

---

### Post by Dragonbite on 2011-10-18
Is the Lemur that is on the site now the same as the Lemur Thin mentioned?  I'm curious about the battery life of this one.

I have heard about the power regression issue with the kernel and the kernel developer know about it too.  There is an article describing it nicely here, [[COLOR="Blue"]_Kernel comment: Untapped power saving potential_[/COLOR]]("http://www.h-online.com/open/features/Kernel-Comment-Untapped-power-saving-potential-1361906.html").

The good thing is it is a kernel (soft) issue and not something to do with the hardware as much.  So eventually this (should) get cleared up and then after an upgrade, certain systems may see their battery lasting longer!

---

### Post by webfiend on 2011-10-18
> **isantop said:**
> All of our current systems can get around 3 hours of battery life. I should note that there is currently a bug in the Linux kernel that causes battery life to be much lower than it should be. Once this bug is resolved, we expect battery life across the board to improve, particularly in the Pangolin range.

Does this three hour estimate apply for the new Lemur Ultra as well?

---

### Post by isantop on 2011-10-18
I'm not 100% sure what the battery life on the new model is like, but it will be different from the old one. I would estimate towards a little over three hours right now, since it's similar to the Pangolin hardware-wise, but it has a slightly smaller screen.

---

