---
title: "I got a great idea for a linux wiki"
date: 2008-08-10
forum: The Cafe
---

### Post by Jordanwb on 2008-08-10
I was configuring a custom kernel for my server. Now I didn't understand about 95% of the stuff that was available (and I did read the help). So I got to thinking "Wouldn't it be helpful if there was a wiki that gave easy to understand information on what each part of the kernel does?"

So what do you think? Would it help joe linux users who want to compile their own kernel? Would you be willing to help?

Personally I'd like to see it happen. Not only others could learn about linux, but you could learn as well (and so could I). If you think it's a good idea, can you suggest hosting sites? For a wiki you really don't need a lot of drive space. I was considering calling the site "Custom Kernel" or something like that.

---

### Post by werries on 2008-08-10
the information is already available on the internet. google, my friend, google.

---

### Post by MaxIBoy on 2008-08-10
A wiki is helpful for this kind of thing, though. If some technical term is used in an explanation, there's a link to the definition of the term which is easily available.

---

### Post by cariboo on 2008-08-11
The problem would be to get people to go to the wiki. Most people when they first try to compile their own kernel never bother to research the hows and whys, they hear that if they compile their own kernel everything will magically work the way it should. I  had to compile a kernel 6 times before I got one that worked and it still didn't have what I needed. This was back in the day of the 2.4 kernel when nobody even thought of an smp kernel. I picked up a dual processor motherboard for fairly cheap on ebay, and to utilize the full power of the twin 223Mhz cpu's I had to compile a kerenl that support my two processors. 

I spent about a week checking what each option in the config file was for and when I was finally ready to compile my kernel it worked with all the options I wanted the first time. After that I used the same config file every time a new kernel version came out. Now I don't bother, the generic kernel does everything I want it to and life is good. :)

Jim

---

### Post by perlluver on 2008-08-11
You mean like this?  [https://help.ubuntu.com/community/Kernel/Compile?](https://help.ubuntu.com/community/Kernel/Compile?)

---

### Post by Dharmachakra on 2008-08-11
> **perlluver said:**
> You mean like this?  [https://help.ubuntu.com/community/Kernel/Compile?](https://help.ubuntu.com/community/Kernel/Compile?)

I think he means something not only on the compiling process but on each individual option you have when you compile. I know [_*Kernel Newbies*_]("kernelnewbies.org") has alot of information on this thought and I think they have a wiki (thought I can't seem to get to it :(). So you'd have to offer something more appetizing than they do. :/

---

### Post by ssam on 2008-08-11
> **Dharmachakra said:**
>  I know [_*Kernel Newbies*_]("kernelnewbies.org") has alot of information on this thought and I think they have a wiki (thought I can't seem to get to it :(). So you'd have to offer something more appetizing than they do. :/

I think it would be best to add this to kernelnewbies. that way you can link in to all the info they already have. it is a good central place, that lots of people visit, so the info will be kept up to date (hopefully).

---

### Post by hyper_ch on 2008-08-11
or do you mean this?  [http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way)

---

### Post by Jordanwb on 2008-08-11
> **werries said:**
> the information is already available on the internet. google, my friend, google.

Yes but even then sometimes the explanations aren't very clear. I have googled and haven't found anything.

> **perlluver said:**
> You mean like this?  [https://help.ubuntu.com/community/Kernel/Compile?](https://help.ubuntu.com/community/Kernel/Compile?)

That's more the process of compiling than what each part does.

> **Dharmachakra said:**
> I think he means something not only on the compiling process but on each individual option you have when you compile. I know [_*Kernel Newbies*_]("kernelnewbies.org") has alot of information on this thought and I think they have a wiki (thought I can't seem to get to it :(). So you'd have to offer something more appetizing than they do. :/

I couldn't figure out how to get to the wiki either. That's the problem. If a user can't find information hey be give up on trying to make his won kernel. For two or so years I was a web admin, and I knew the importance of providing easy to find information.

> **hyper_ch said:**
> or do you mean this?  [http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way)

That's more the process of compiling than what each part does.

---

### Post by Jordanwb on 2008-08-14
So what do you guys think?

---

### Post by az on 2008-08-14
> **Jordanwb said:**
> 
That's more the process of compiling than what each part does.

Since the dawn of time, the greatness of free/libre software has alwas exceeded the greatness of its own documentation.  People like to hack code, but writing documentation about the code (or the program) is secondary - it's a little too much like work.

Fortunately, there are many people who are ready willing, able, and active at writing good documentation.  Unfortunately, you probably won't find a lot of people writing low-level documentation for the kernel.

To begin with, the kernel is very actively developed.  By the time someone would write something about a particular module, the code would change and the document would be obsolete.

Not to mention that very very few people need to recompile a kernel nowadays.  Hardware autoconfiguration is standard.

I just don't think there is a big enough need for this.

---

### Post by Jordanwb on 2008-08-14
> **az said:**
> Since the dawn of time, the greatness of free/libre software has alwas exceeded the greatness of its own documentation.

Ain't that the truth.

> **az said:**
> To begin with, the kernel is very actively developed.  By the time someone would write something about a particular module, the code would change and the document would be obsolete.

If you used a Wiki (what I had in mind), this wouldn't be a major issue. Someone could flag a page as obsolete and it would be removed or updated. Also the documentation doesn't necessarily have to be long, just long enough to make it clear.

> **az said:**
> Not to mention that very very few people need to recompile a kernel nowadays. Hardware autoconfiguration is standard.

I just don't think there is a big enough need for this.

I disagree. While hardware auto-detection is valuable, you can speed up booting by getting rid of unused stuff in the kernel, like SATA/PATA drivers and network device drivers. So if there's less stuff that the kernel can look for, the process is quicker. Also the kernel shipped with Ubuntu supports stuff you should never use, like AppleTalk or Token Ring. For someone who does not know what a particular driver does could result in a lot of wasted time compiling and figuring out what they're supposed to do.

I learned the process of compiling packages from source by trying to compiling my own kernel. Although the compilation of the kernel failed due to clear documentation. Some guy earlier posted a link about "rolling a kernel the Debian/Ubuntu way", there was one step I was like "So what do I do?".

---

### Post by az on 2008-08-16
> **Jordanwb said:**
> 

I disagree. While hardware auto-detection is valuable, you can speed up booting by getting rid of unused stuff in the kernel, like SATA/PATA drivers and network device drivers. So if there's less stuff that the kernel can look for, the process is quicker. Also the kernel shipped with Ubuntu supports stuff you should never use, like AppleTalk or Token Ring. For someone who does not know what a particular driver does could result in a lot of wasted time compiling and figuring out what they're supposed to do.


This hasn't been the case for years.  Eliminating hardware detection will speed your boot time by less than one second.

The fact that the kernel supports hardware you don't have is irrelevant, since the modules will not be loaded unless it its needed.  There are a handful of things that are loaded that you may not use, but they do not decrease system performance at all.

> **Jordanwb said:**
> 
I learned the process of compiling packages from source by trying to compiling my own kernel. Although the compilation of the kernel failed due to clear documentation. Some guy earlier posted a link about "rolling a kernel the Debian/Ubuntu way", there was one step I was like "So what do I do?".

Again, since there are so few reasons to compile your own kernel, you are faced with very few people who are interested in writing documentation for it.

---

### Post by Jordanwb on 2008-08-16
I guess that you're right but still I think that there would be a few valid reasons for wanting to compile your own kernel:

You have unusual hardware and the pre-built kernel doesn't support it. (Okay this may be rare)

A brand new kernel(2.6.26.2 as of posting) has drivers but the currently available one (2.6.24-something as of posting) does not have.

Having drivers built into the kernel instead of modules to save space, time and hard drive access. If you have a 3 month old computer no problem, but my laptop is 7+ years old. So any speed boost I could get is useful and benficial.

You're running Gentoo (which I plan to do on my server).

You have a slow net connection and can't afford to be downloading a newer kernel every week. Some people still use Dial-Up.

---

### Post by az on 2008-08-16
> **Jordanwb said:**
> I guess that you're right but still I think that there would be a few valid reasons for wanting to compile your own kernel:

You have unusual hardware and the pre-built kernel doesn't support it. (Okay this may be rare)


Right, since you would compile an extra module for your running kernel.  You typically would not need to recompile the whole kernel for one driver.

The only exception is when the new driver is stacked on top of new pieces that are only available in the development release.  But you typically would not want to run a dev kernel on a stable desktop.  So although it may happen, it is not desirable.

> **Jordanwb said:**
> 

Having drivers built into the kernel instead of modules to save space, time and hard drive access. If you have a 3 month old computer no problem, but my laptop is 7+ years old. So any speed boost I could get is useful and benficial.


Hardware detection really does not take than much time in the boot process, even on older hardware.  The kernel is fatter (takes up more ram), but that is really negligible these days.  In the mid nineties, when computers had 4 to 8 megs of ram, 64k was a big deal.  Your kernel could take up twice as much ram as it does and your 7 year old laptop would still run the same.

> **Jordanwb said:**
> 

You have a slow net connection and can't afford to be downloading a newer kernel every week. Some people still use Dial-Up.

The kernel source is much larger than the binary.  It would take you a lot longer to download the source for the new kernel than to just download the precompiled binary.

---

