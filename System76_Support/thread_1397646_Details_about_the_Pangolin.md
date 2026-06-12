---
title: "Details about the Pangolin"
date: 2010-02-03
forum: System76 Support
---

### Post by satsujinka on 2010-02-03
While waiting for my current laptop to show signs of dieing, I've been looking at the Pangolin. And I'm curious about a few things.

[LIST=1]
[*]I tend to shutdown my computer rather than suspend/hibernate, so the speed of the BIOS is rather important to me. How long does the Pangolin take to get to grub? My current laptop takes about 6 seconds but 10 is good enough.
[*]What features does the BIOS have? Under/over volting/clocking?
[*]Can the BIOS turn off the ATI card? Or rather is the hardware such that it would support [Hybrid  Graphics]("http://www.phoronix.com/scan.php?page=news_item&px=Nzk1NQ")? (link to an article on Phoronix about hybrid graphics coming to Linux)
[*]What type of motherboard does it have? (I would assume it's a P55 based board)
[/LIST]
That's all I can think of for now, but I may come up with more.

---

### Post by linusr on 2010-02-04
5. How long battery last after full charge?

---

### Post by thomasaaron on 2010-02-04
> I tend to shutdown my computer rather than suspend/hibernate, so the speed of the BIOS is rather important to me. How long does the Pangolin take to get to grub? My current laptop takes about 6 seconds but 10 is good enough.

Using the highly scientific one-one-thousand, two-one-thousand benchmarking method, I got to eleven.

> What features does the BIOS have? Under/over volting/clocking?

The BIOS is pretty standard. It has neither of those.

> Can the BIOS turn off the ATI card? Or rather is the hardware such that it would support Hybrid Graphics? (link to an article on Phoronix about hybrid graphics coming to Linux)

No.

> What type of motherboard does it have? (I would assume it's a P55 based board)

Not sure. Will have to ask R&D.

> How long battery last after full charge? 
1.5 - 2 hrs.

---

### Post by satsujinka on 2010-02-04
Thanks for the reply. 11 seconds is good enough, though it's rather unfortunate that the bios doesn't have any extra features.

I do have to ask for clarification (and you'll probably have to ask R&D.) Even if the bios doesn't have the ability to turn off the graphics card it's still possible that hybrid graphics may work. So I would like to know if the no you gave me applied to hybrid graphics as well? Though considering how new the technology is for linux it wouldn't surprise me if it hasn't been tested.

---

### Post by thomasaaron on 2010-02-04
I'm not really up to speed on hybrid graphics, but if I understand that article, it allows you to switch back and forth between gpus on a system that has TWO gpus, right?

If so... the Pangolin only has one graphics card, so that wouldn't work.

However, I did just glance at the article. So, if I missed the point, I'll give it a deeper look tomorrow morning.

---

### Post by satsujinka on 2010-02-04
The cpu is an Arrandale model, so it should have a built in gpu. So unless intel is selling mobile i5 without the built in gpu the Pangolin does have 2 gpus.

Sources:[URL="http://en.wikipedia.org/wiki/Arrandale"]
http://en.wikipedia.org/wiki/Arrandale[/URL]
[http://en.wikipedia.org/wiki/List_of_Intel_Core_i5_microprocessors#.22Arrandale.22_.28standard_voltage.3B_32_nm.29](http://en.wikipedia.org/wiki/List_of_Intel_Core_i5_microprocessors#.22Arrandale.22_.28standard_voltage.3B_32_nm.29)
[http://en.wikipedia.org/wiki/List_of_Intel_Core_i7_microprocessors#.22Arrandale.22_.28standard_voltage.3B_32_nm.29](http://en.wikipedia.org/wiki/List_of_Intel_Core_i7_microprocessors#.22Arrandale.22_.28standard_voltage.3B_32_nm.29)

---

### Post by Lee_Machine on 2010-02-04
Satsujinka,
 
You are correct, there are two GPU's one on the same die as the CPU, and the other is the ATI card. 

As far as hybrid graphics goes on Linux, I wouldnt count on it anytime soon.

For one thing Intel video drivers on all systems is sometimes poor. 


[http://www.notebookcheck.net/Intel-Core-i5-520M-Notebook-Processor.23749.0.html](http://www.notebookcheck.net/Intel-Core-i5-520M-Notebook-Processor.23749.0.html)

---

### Post by satsujinka on 2010-02-04
There is currently a lot of work on getting switchable graphics working (a link is in my first post) and I wouldn't be surprised if it made it into most distros by next year. I'm also aware of the state of Intel's drivers (I have an Intel GPU in my current laptop.) Fortunately, the driver for Arrandale's GPU is already working (or it should work as it's the same as in the [Clarksdale]("http://www.phoronix.com/scan.php?page=article&item=intel_clarkdale_gpu&num=1")) so switchable graphics is currently a possibility. Besides, even if the Arrandale GPU is pretty poor, the reason for using it is just to save energy when you aren't plugged into a wall.

EDIT: Wikipedia and notebookcheck seem to disagree a bit. Wikipedia says the GPU in the i5 models is the same speed as the i7 but notebookcheck says it's clocked lower (which is true of the CPU part, as i7 is high end and i5 is mid-range.) Though maybe I'm misunderstanding and notebookcheck is referring to lower volted models compared to higher volted models.

---

### Post by linusr on 2010-02-05
if switchable graphics is not an option, will it be possible to switch off discrete ATI GPU in BIOS and use IGP?

---

### Post by thomasaaron on 2010-02-05
There is nothing in the BIOS that would allow this type of functionality.

---

### Post by samalex on 2010-02-05
Per the GPU's I just read this on Phoronix:

**Today, Delayed GPU Switching Comes To Linux**
[http://www.phoronix.com/scan.php?page=news_item&px=Nzk1NQ](http://www.phoronix.com/scan.php?page=news_item&px=Nzk1NQ)

Not sure if it applies to what you guys are talking about though...

Take care,

Sam

---

### Post by satsujinka on 2010-02-05
@samlex
That's the link I posted in my first post. Btw, an update [hybrid graphics 2]("http://www.phoronix.com/scan.php?page=news_item&px=Nzk0OQ").

@thom
There's not an immediate need for the BIOS to support turning off the graphics card. That can be done after booting up (and the patch talked about in the linked article can do so.) I had just asked if it could as that would mean that the Pangolin could support hybrid graphics. But since it doesn't have that option we have to be a bit more technical. If you could it would be lovely if you forwarded the links I've provided (the ones relating to hybrid graphics) to the R&D team and asked if they could look into it (there's no need to provide the functionality yet, all I want to know is if it could work.)

---

### Post by thomasaaron on 2010-02-05
OK, I'll forward it to them.

---

### Post by satsujinka on 2010-02-05
Thank you. I greatly appreciate your help.

---

### Post by linusr on 2010-02-07
does pangolin ships with universal AC adapter?

Dell AC adapter which I bought in UK, but can use in India, Canada by using only an PIN adapter..

---

### Post by thomasaaron on 2010-02-08
It does have a universal adapter, although we don't actually provide the European plug adapter.

Please note that we do not sell Internationally, other than in Canada.

---

### Post by linusr on 2010-02-08
> **thomasaaron said:**
> It does have a universal adapter, although we don't actually provide the European plug adapter.

Please note that we do not sell Internationally, other than in Canada.

thnx thomasaaron, for clarifying

At the moment I live in Canada, till I buy my next laptop :D

but I don't want to end up buying an AC adapter when I return back to India

---

### Post by satsujinka on 2010-02-26
By the way another update on the status of hybrid graphics in linux. Looks like we may see it in the 2.6.34 kernel.

[http://www.phoronix.com/scan.php?page=news_item&px=ODAxOA](http://www.phoronix.com/scan.php?page=news_item&px=ODAxOA)

---

