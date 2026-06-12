---
title: "advice on motherboard that wont post"
date: 2009-09-20
forum: The Cafe
---

### Post by sdowney717 on 2009-09-20
I have a motherboard here that won't post. It doesn't make any of the usual startup sounds, nothing appears on the screen, there are no beep codes. It is getting power, since the fan on the video card runs and the power supply seems to be running. 

I bought this used and was told it was working. My question is this, could it be the power supply which does work on my d510 compaq evo tower of 220 watts is not powerful enough to get the new board running? that PSU is a 20 pin and the board is 24 pin but I have read this will work and I have done this with other boards.
Should it at least post with the 220watt PSU?

[http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?DetailID=830&CategoryID=1&DetailName=Feature&MenuID=44&LanID=0](http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?DetailID=830&CategoryID=1&DetailName=Feature&MenuID=44&LanID=0)

and the processor is a single core 3.4ghz.

I pulled it all out and set it up barebones, I even tried pulling the memory, but still nothing.

---

### Post by Warpnow on 2009-09-20
220 watts will power any stock CPU and motherboard. However, it may power nothing else, such as GPU, CD, HD, ect. A 220watt psu prolly puts out like 150 or something in actual situations.

If the motherboard won't post, and all power connectors are connected, and the CPU is good...you can always use it as a door stop...

---

### Post by Exodist on 2009-09-20
Have you tried pulling EVERYTHING except the CPU and RAM out and seeing if you get a response?

If you can try the RAM and CPU in another system. If they are good something my be quirky with you Mobo. It may be a BIOS issue or just flat out DOA.

---

### Post by Firestem4 on 2009-09-20
My advice is to clear the CMOS by flipping the CMOS battery for 10~15 seconds. I mean flipping by removing the battery and placing it upside in the battery slot for 10 to 15 seconds, then remove it and replace it normally.

Make sure everything is seated correctly while you are doing this. Cables, chips, cards, etc. Pull them out and put them back in to make sure.

That is usually the magic answer in getting systems to POST.

Secondly, if it is a RAM issue. The best way to be able to test them are to try them in a known-good computer (that is obviously compatible with the Mhz of the RAM). If thats not an option, try swapping your RAM in different slots. You may have a bad module or socket. (I had this issue with my last motherboard. 4 actual sticks of RAM, and one socket/RAM went bad. when i removed it and tried the ram in the different sockets I discovered that the actual motherboard RAM socket #3 had fried).

As the others have suggested if those dont work unplug everything except the RAM or CPU and try to boot. You will get POST errors if it sucessfully boots but then you have narrowed what the actual problem is. If that fails then you may have a problem with your motherboard, CPU, RAM (if you didn't test that they were working) or your power supply. Though I should mention that it is rarely the CPU. It happens but it is quite rare.

---

### Post by Skripka on 2009-09-20
I'd get a real PSU and try again.

---

### Post by Skripka on 2009-09-20
> **Firestem4 said:**
> Though I should mention that it is rarely the CPU. It happens but it is quite rare.

It was NOT uncommon for P4 Northwood CPUs, which the OP is likely running a Pentium4.  Back in the day, boosting the CPU voltage past 1.7V on a P4 for overclocking would result in SNDS.  Sudden Northwood Death Syndrome. 

[http://www.xbitlabs.com/news/cpu/display/news6375.html](http://www.xbitlabs.com/news/cpu/display/news6375.html)

---

### Post by Firestem4 on 2009-09-20
> **Skripka said:**
> It was NOT uncommon for P4 Northwood CPUs, which the OP is likely running a Pentium4.  Back in the day, boosting the CPU voltage past 1.7V on a P4 for overclocking would result in SNDS. ** Sudden Northwood Death Syndrome**. 

[http://www.xbitlabs.com/news/cpu/display/news6375.html](http://www.xbitlabs.com/news/cpu/display/news6375.html)

Lol never heard that one before...interesting.

---

### Post by j7%&lt;RmUg on 2009-09-20
Your psu should not be the problem, right now im running my whole computer(mobo, cpu, 2 hard drives, my 9600gt, 2gb of ram, wireless card) on a 255 watt psu, so if i can run all that on 255 watts then you should be ok.

i reckon its your motherboard, if no bios comes up and the motherboard doesnt beep.

Try a different motherboard if you can.

---

### Post by coolbrook on 2009-09-21
There may be some CMOS clearing jumper(s) on the board as well.  I can see the manual at the link sdowney717 posted but I can't check it at the moment.

The OP isn't running a P4.  That was made clear in the post.

---

### Post by Skripka on 2009-09-21
> **nisshh said:**
> Your psu should not be the problem, right now im running my whole computer(mobo, cpu, 2 hard drives, my 9600gt, 2gb of ram, wireless card) on a 255 watt psu, so if i can run all that on 255 watts then you should be ok.

i reckon its your motherboard, if no bios comes up and the motherboard doesnt beep.

Try a different motherboard if you can.

It depends on how old the PSU is.  As time goes on they lose output, and efficiency.  I would never BOTHER even trying to run a machine nowadays on a 200W PSU.  It is quite easy on full bore to pull 300W on a power-hungry single core CPU....and a 220W PSU couldn't even do that when it is/was new.


[http://www.silentpcreview.com/article28-page3.html](http://www.silentpcreview.com/article28-page3.html)

---

### Post by Skripka on 2009-09-21
> **coolbrook said:**
> 
The OP isn't running a P4.  That was made clear in the post.

Where does he makes this clear?  He is running an Intel LGA775 board, witha 3.4gHz single core CPU.  

I can't think of other choices that meet those criteria, last I knew.

---

### Post by mcduck on 2009-09-21
> **Skripka said:**
> It depends on how old the PSU is.  As time goes on they lose output, and efficiency.  I would never BOTHER even trying to run a machine nowadays on a 200W PSU.  It is quite easy on full bore to pull 300W on a power-hungry single core CPU....and a 220W PSU couldn't even do that when it is/was new.


[http://www.silentpcreview.com/article28-page3.html](http://www.silentpcreview.com/article28-page3.html)

You'd need some pretty hardcore overclocking to get any CPU to use 300W. Even the most hungry Xeons and Itaniums use less than 200W, and most of the desktop stuff stays well under 100W under full load, the most hungry CPU's topping around 130W. [http://users.erols.com/chare/elec.htm]("http://users.erols.com/chare/elec.htm")

The systems should definitely be able to boot with a 220W PSU, assuming the PSU really provides those 220 watts (which of course might not always be the case with cheapest PSUs.)

I'd start by double-checking all the cables. Of course there's always the possibility that the motherboard is simply broken, the previous owner bent it too much or something..

---

### Post by Skripka on 2009-09-21
> **mcduck said:**
> You'd need some pretty hardcore overclocking to get any CPU to use 300W. Even the most hungry Xeons and Itaniums use less than 200W, and most of the desktop stuff stays well under 100W under full load, the most hungry CPU's topping around 130W. [http://users.erols.com/chare/elec.htm]("http://users.erols.com/chare/elec.htm")

The systems should definitely be able to boot with a 220W PSU, assuming the PSU really provides those 220 watts (which of course might not always be the case with cheapest PSUs.)

I'd start by double-checking all the cables. Of course there's always the possibility that the motherboard is simply broken, the previous owner bent it too much or something..

The linky is only TDP, not electrical consumption of CPUs.  In any case, I was meaning 300W for a full desktop system-not just the CPU, even if that isn't what came out of my keyboard (I need more caffeine) ;)

---

### Post by mcduck on 2009-09-21
> **Skripka said:**
> The linky is only TDP, not electrical consumption of CPUs.  In any case, I was meaning 300W for a full desktop system-not just the CPU, even if that isn't what came out of my keyboard (I need more caffeine) ;)

Sure, but a processor with a TDP less than 200 watts can't have power consumption too much above that, and definitely nowhere near hundred watts above TDP.

But yeah, if the OP has some of the more power hungry CPU's, and perhaps a couple of fast hard drives and a graphics card the complete rig would easily go over the 220 watts.

---

### Post by sdowney717 on 2009-09-23
well, I have more information. I talked with ECS technical support and they said board should post with that PSU. I also bought another 400 watt PSU and it still did not post. ECS tech and I went thru all the memory and other components and memory is ok. SO ECS suggested the board was damaged. Anyhow the seller has put in a claim for damaged in shipping which if you look at the box you will see how the end is crushed. The end of the box has been crushed like an accordion. Must have taken quite a blow impact to do that.

---

