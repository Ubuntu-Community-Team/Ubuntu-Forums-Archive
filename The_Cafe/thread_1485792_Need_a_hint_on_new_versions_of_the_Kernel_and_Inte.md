---
title: "Need a hint on new versions of the Kernel and Intel Graphics."
date: 2010-05-17
forum: The Cafe
---

### Post by Macchi on 2010-05-17
Hello Fellows,

I would like to get some hint on kernel development regarding Graphic Management of older Intel 910 & 855 etc. Can we expect support for that type of hardware?

We have different machines, mainly laptops 5 - 2 years old, at work and at home that use the integrated graphic. Unfortunately they do NOT work with the latest Lucic kernels.

The problems are around since the release candidate and it is hopeless, the systems either don't boot or crash the LTS-release! 

When can be expected to have stable support for Intel 85x or 91x?
When will we have a new kernel version (33) for Lucid?

---

### Post by hoppipolla on 2010-05-17
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Hope that helps, it certainly helped me!

I actually ended up using workarounds A and F together, I found that got me the best performance :)

---

### Post by Macchi on 2010-05-17
Thanks. I have already helped some fellows here in the forum by reminding them on the same WORKAROUND. Actually I was asking if a SOLUTION will arrive and possibly WHEN!

This bug around intel graphics has been on launchpad since january and was ignored even through the 10.04 LTS release. It is a confirmed bug but I see no actions to solve it. 

Now I am concerned that this bug might be forgotten by Ubuntu developers in the near future. If that is the case then I have to change my open source strategy at a professional level. If Ubuntu fails to work with computers that are from 5 to 1/2 years old then we will be in big trouble. It will be very difficult to convince my clients to invest in Ubuntu.

---

### Post by cariboo on 2010-05-17
Your issue really has nothing to do with the kernel, the problem is that the maintainers of the driver aren't keeping up with changes to Xorg-xserver, ATI and Nvidia suffer from the same problem.

---

### Post by Macchi on 2010-05-18
> **cariboo907 said:**
> Your issue really has nothing to do with the kernel, the problem is that the maintainers of the driver aren't keeping up with changes to Xorg-xserver, ATI and Nvidia suffer from the same problem.

Thank you for your answer Cariboo907.
I am aware of the challenges that Linux developers and users have to withstand regarding the struggle with new devices all the time.

But THIS IS DIFFERENT: Functionality on those machines with Intel graphics 85X 91X etc used to work fine for years. Given some acceptable limitations, such as living without cosmetic desktop effects. 

Now these machines are not working with the newest kernels for 10.04. The workarounds are not a solution because they do not allow reliable operation. For instance the system crashes completely if attempting to play an mp3 file from Firefox! 

That is why I am interested in finding out if this is a temporary problem or if it is a dead end for Ubuntu on older machines etc.




FOR THE RECORD:
I am the IT manager of an industry and we are about to be forced to give up the strategy of moving from Windows to Ubuntu on all machines (up to 50 machines). This migration requires both extending the life of older machines ( at most 6 years) AND the ability to install on newer hardware. It is an all or nothing race, because the IT environment has to be homogeneous across the organization. 
Otherwise it would have been easier to just cope with the cost a "bulldozer solution", scrapping everything and using the pre-installed OS of the new machines. 

We have to use a LTS release and the 8.04 is not coping with certain hardware combinations. Thus we had high hopes for the 10.04 that so far has been a disappointment regarding stability. Unfortunately this occurs on top of a series of problems we had with 9.04 and 9.10, thus leaving us with zero credibility to try to convince the organization of the advantages of Linux on security and stability...

It seems that the kernel and drivers move apart from each other on certain areas. Is it true?

---

