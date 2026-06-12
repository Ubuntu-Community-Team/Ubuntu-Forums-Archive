---
title: "What is the performance difference between 32-bit and 64-bit?"
date: 2017-08-20
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2017-08-20
Here's the specs of my desktop:

GATEWAY GT5432
2x AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
4GB DDR2 RAM
500GB HHD

As you can see, my desktop is a 64-bit, but I installed Xubuntu 16.04 32-bit on it because at the time, I was unsure what bit my desktop was.

But when the next LTS release comes, which is 18.04, I'm planning on installing Lubuntu 18.04 64-bit on my desktop, because I installed Lubuntu 16.04 32-bit on my dad's old laptop, and I kinda liked it.

What difference in performance should I expect between 32-bit and 64-bit?

---

### Post by Perfect Storm on 2017-08-20
I hardly think you'll notice any difference between the two. It would be another matter if you had more RAM to take advantage of.

---

### Post by ardouronerous on 2017-08-20
4GB is the maximum for this desktop.

---

### Post by wildmanne39 on 2017-08-20
Pretty much what AI said with a little explanation.

[http://www.tomshardware.com/forum/id-1750546/whats-speed-difference-bit-bit-processor.html](http://www.tomshardware.com/forum/id-1750546/whats-speed-difference-bit-bit-processor.html)

---

### Post by vocx on 2017-08-20
> **ardouronerous said:**
> ...
What difference in performance should I expect between 32-bit and 64-bit?
There is not much difference. It is basically a technical difference that most people should not be worried about.

Essentially, 32-bit systems limit you to 4 GB in RAM, which was fine for most computing done in the 1990s. The 64-bit system allows you to use up to 18 446 744 073 GB of RAM, which is... a lot. Most users don't need to worry about this distinction, although it is important in certain environments, for example, virtualized servers, and supercomputers, which need a lot of RAM, in the order of 100 GB to 1000 GB of RAM.

So, there is not much difference. Of course, if you use a 64-bit chip now, it is probably noticeably faster than a 10-year old 32-bit CPU. This is not just because it is 64-bit, but because in general the CPUs are faster and better nowadays than they were some years ago. So, if somebody made a purely 32-bit chip today, it probably would also be faster than an older 32-bit chip.

---

### Post by exhile on 2017-08-20
Google Chrome is no longer supported on 32-bit Ubuntu o/s's. You have to use the 64-bit version of Ubuntu in order to use Google Chrome.

---

### Post by him610 on 2017-08-20
> Google Chrome is no longer supported on 32-bit Ubuntu o/s's. You have to use the 64-bit version of Ubuntu in order to use Google Chrome.
Chromium 32-bit is still available, and can be downloaded and installed.

@ardouronerous I had a Shuttle system from around 2008 with similar specs, Athlon X2 5600+ w/4GB. I believe the most recent version of Xubuntu 64-bit installed on it was 1604. I never had any problems with it. Had to clean house - too many computers lying around.

---

### Post by ardouronerous on 2017-08-20
> **vocx said:**
> There is not much difference. It is basically a technical difference that most people should not be worried about.

Essentially, 32-bit systems limit you to 4 GB in RAM, which was fine for most computing done in the 1990s. The 64-bit system allows you to use up to 18 446 744 073 GB of RAM, which is... a lot. Most users don't need to worry about this distinction, although it is important in certain environments, for example, virtualized servers, and supercomputers, which need a lot of RAM, in the order of 100 GB to 1000 GB of RAM.

So, there is not much difference. Of course, if you use a 64-bit chip now, it is probably noticeably faster than a 10-year old 32-bit CPU. This is not just because it is 64-bit, but because in general the CPUs are faster and better nowadays than they were some years ago. So, if somebody made a purely 32-bit chip today, it probably would also be faster than an older 32-bit chip.

I wonder why the manufacturer limited the hardware to 4GB RAM when the processor is 64-bit, since 64-bit can handle more than 4GB RAM, or maybe things were different back in 2008 when this computer was manufactured?

> **wildmanne39 said:**
> Pretty much what AI said with a little explanation.

[http://www.tomshardware.com/forum/id-1750546/whats-speed-difference-bit-bit-processor.html](http://www.tomshardware.com/forum/id-1750546/whats-speed-difference-bit-bit-processor.html)

Thanks for the info! :)

> **him610 said:**
> Chromium 32-bit is still available, and can be downloaded and installed.

@ardouronerous I had a Shuttle system from around 2008 with similar  specs, Athlon X2 5600+ w/4GB. I believe the most recent version of  Xubuntu 64-bit installed on it was 1604. I never had any problems with  it. Had to clean house - too many computers lying around.

And Chrome's apps works well with Chromium too.

My desktop was manufactured in 2008 too. That's good to hear. Thanks for sharing! :)

---

### Post by vocx on 2017-08-20
> **ardouronerous said:**
> I wonder why the manufacturer limited the hardware to 4GB RAM when the processor is 64-bit, since 64-bit can handle more than 4GB RAM, or maybe things were different back in 2008 when this computer was manufactured?
...

Probably the same reason today's motherboards are limited to 16 GB, 32 GB, 128 GB RAM. It's all about cost-benefit, and expected usage. Even if your processor can handle 1000000 GB RAM, is it really realistic that you will be using that much memory?

I don't recall many people using 64-bit systems in 2008. As I recall, the Linux kernel immediately supported 64-bit CPUs, and several Linux distributions were readily available in 64-bit. However, most Windows installations that I recall were still 32-bit, even if using 64-bit processors.

Truth is, most people don't need much computing power. Unless you are running complex calculations every single minute, most computers just sit there waiting for instructions to actually do some computing work.

---

### Post by mastablasta on 2017-08-21
> **ardouronerous said:**
> I wonder why the manufacturer limited the hardware to 4GB RAM when the processor is 64-bit, since 64-bit can handle more than 4GB RAM, or maybe things were different back in 2008 when this computer was manufactured?


they are still limiting it. some even solder the ram on it (you can't add more or take some away). i have a 64bit PC that is limited to 8 GB max. to mkae ti weirder it came with 2GB ram and Win7 starter preloaded which can only handle 2 GB max.

as for the question, the performance difference should be that much. but more and more programs get only 64bit versions. a 64bit OS can run 32bit programs but not that doesn't work the other way arround.
also i think you might see some benefit if you do some video transcoding or editing. not sure how much the increase would be but that task needs computing.

---

### Post by ClickXT on 2017-08-22
If you have the 4GB - I'd use 64-bit to make sure the system utilizes the full 4GB for sure.

---

### Post by oldos2er on 2017-08-22
CPU intensive tasks e.g. video encoding will be faster on 64 bit compared to 32, given adequate RAM.

---

### Post by ardouronerous on 2017-08-24
> **ClickXT said:**
> If you have the 4GB - I'd use 64-bit to make sure the system utilizes the full 4GB for sure.

Okay, thanks for all the clarifications! :)

> **oldos2er said:**
> CPU intensive tasks e.g. video encoding will be  faster on 64 bit compared to 32, given adequate RAM.

Faster? Even if my Desktop is using a 500GB HDD?

---

### Post by cariboo on 2017-08-25
> **ardouronerous said:**
> Okay, thanks for all the clarifications! :)
Faster? Even if my Desktop is using a 500GB HDD?

Desktop storage eg: a hard drive is much slower than ram.

---

### Post by james222 on 2017-09-06
I don't think that you will notice much difference in two but as you are already have the 64 bit then you should go for it.

---

### Post by yoshii on 2017-09-07
According to the WineHQ.org website, 32-bit Wine is more stable and supported than 64-bit Wine.  I'm not sure if this is affected by which OS type you choose (32-bit or 64-bit) but it's a related factor if you plan on using the computer with Wine (for Windows compatible programs).  It's kinda sad to see 32-bit support drifting backwards a little bit because there's so much still-useful software and hardware and still otherwise a lot of backwards compatibility and older stuff is usually a lot cheaper, especially if pre-used.  I have had some systems with a lot of RAM but I've NEVER needed any more RAM than 4 GB, even when doing hard disk and MIDI recording and VST(i) work for music production.  I watch plenty of videos, even do some minor video editing.  I never noticed any need for more than 4 GB RAM.  But I do like the idea of creating a ginormous RAM drive and using that for more serious video editing use.  I haven't tried that yet though.

---

