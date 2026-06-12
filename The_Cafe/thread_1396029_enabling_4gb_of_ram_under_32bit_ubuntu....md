---
title: "enabling 4gb of ram under 32bit ubuntu..."
date: 2010-02-01
forum: The Cafe
---

### Post by pirlo89 on 2010-02-01
Hello everyone.

I have a 4GB of ram and my 32bit ubuntu tells me that i have 3.4GB . And i know that if i want to enable the full 4GB i have to Install PAE enabled kernel.

But the thing is that i have just reinstalled ubuntu (because of a problem with my ATI card) and i am afraid that installing PAE enabled kernel well mess up my system.

So any comments about how it went with you guys well be appreciated.

Also, i am a CS student and i write my software on my ubuntu OS. Will my code be affected by that ? (like if i declare a data type, will it affect how much it reserves for it?)

Thanks in advance :)!

---

### Post by samantha_ on 2010-02-01
> **pirlo89 said:**
> Hello everyone.

I have a 4GB of ram and my 32bit ubuntu tells me that i have 3.4GB . And i know that if i want to enable the full 4GB i have to Install PAE enabled kernel.

But the thing is that i have just reinstalled ubuntu (because of a problem with my ATI card) and i am afraid that installing PAE enabled kernel well mess up my system.

So any comments about how it went with you guys well be appreciated.

Also, i am a CS student and i write my software on my ubuntu OS. Will my code be affected by that ? (like if i declare a data type, will it affect how much it reserves for it?)

Thanks in advance :)!
The PAE kernel doesnt change how your apps will function - it is still 32 bit.
Nope, many people have done it without messing up their system.

besides, there isnt a big difference between 3.4 and 4gb of ram.

---

### Post by NoaHall on 2010-02-01
While in theory it makes your system run as 36bit as opposed to 32 bit(which is why more ram is supported), I don't think it affects your code(or at least, you don't need to do anything other than you would normally). Then again, I always use 64 bit, so I'm not sure on the practical side of it.

---

### Post by Skripka on 2010-02-01
> **samantha_ said:**
> The PAE kernel doesnt change how your apps will function - it is still 32 bit.
Nope, many people have done it without messing up their system.

besides, there isnt a big difference between 3.4 and 4gb of ram.

In all honesty, if the OP is already in a just-reinstalled vanilla state, he should just go and install 64bit.  No dicking around with PAE and kernel extensions.

---

### Post by nmaster on 2010-02-01
as far as the data type goes... it depends.  if you're programming in C, then use the sizeof function to make sure your code is more portable.  In java, those things are standardized.

---

### Post by pirlo89 on 2010-02-01
> **Skripka said:**
> In all honesty, if the OP is already in a just-reinstalled vanilla state, he should just go and install 64bit.  No dicking around with PAE and kernel extensions.

well, i installed it like a week ago and every application that i need is installed. but i have a free internal hard drive (160 GB) , so i guess i could try the 64bit :-k

---

### Post by Warpnow on 2010-02-01
The server kernel has PAE, so it would work.

 sudo sudo apt-get install linux-headers-server linux-image-server linux-server

For the record, I'd just install 64 bit ubuntu.

---

### Post by ssam on 2010-02-01
pae kernel won't effect you programs, and wont change the size of data types.

though i believe it gives a small (few percent) decrease in performance. any reason not to use 64bit which will give a performance boost due to better optimisation.

---

### Post by FuturePilot on 2010-02-01
> **Warpnow said:**
> The server kernel has PAE, so it would work.

 sudo sudo apt-get install linux-headers-server linux-image-server linux-server

For the record, I'd just install 64 bit ubuntu.

You don't need the -server kernel anymore for PAE. There is now a -generic-pae kernel. Anyways, give 64bit a shot. PAE is a hack.

---

### Post by pirlo89 on 2010-02-01
Thanks for all the comments :) .

I will try the 64bit.

---

### Post by TheNessus on 2010-02-01
a noobish question related to thread: Is there a way for me to utilize my entire 2GB RAM with 32bit? got only 1.5.

---

### Post by Skripka on 2010-02-01
> **TheNessus said:**
> a noobish question related to thread: Is there a way for me to utilize my entire 2GB RAM with 32bit? got only 1.5.

That would likely be because you're using an on-board Intel gfx unit, correct?

If so-then it is nothing to do with 32/64bit, everything to do with your choice of hardware.

---

### Post by TheNessus on 2010-02-01
> **Skripka said:**
> That would likely be because you're using an on-board Intel gfx unit, correct?

If so-then it is nothing to do with 32/64bit, everything to do with your choice of hardware.

Nvidia 8400 actually.

---

### Post by Skripka on 2010-02-01
> **TheNessus said:**
> Nvidia 8400 actually.

Tower or laptop?  

Does it have it's own memory, or is it utilizing system memory?  I'd guess the later.

---

### Post by TheNessus on 2010-02-01
> **Skripka said:**
> Tower or laptop?  

Does it have it's own memory, or is it utilizing system memory?  I'd guess the later.

lappy. I don't know how to answer your second question though.

---

### Post by NoaHall on 2010-02-01
> **TheNessus said:**
> a noobish question related to thread: Is there a way for me to utilize my entire 2GB RAM with 32bit? got only 1.5.

It's being used :) It just doesn't look like it.

---

### Post by TheNessus on 2010-02-01
> **NoaHall said:**
> It's being used :) It just doesn't look like it.

bummer, it's getting crowded in there. I'll make it 4, I guess. :)

---

### Post by FuturePilot on 2010-02-01
I have a GeForce 8400M and it has its own memory. My RAM is reported correctly. I suspect something else is going on with your computer.

---

### Post by TheNessus on 2010-02-01
> **FuturePilot said:**
> I have a GeForce 8400M and it has its own memory. My RAM is reported correctly. I suspect something else is going on with your computer.

Alright, thanks. Do you have any ideas? How do I give a summery of its internal workings here?

---

### Post by MaxIBoy on 2010-02-01
PAE kernels are nice if you have an "entrenched" system... but if you've seen the benchmarks, PAE kernels are just slightly slower than standard 32-bit kernels, while 64-bit kernels can be somewhat faster compared either. See this article:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

