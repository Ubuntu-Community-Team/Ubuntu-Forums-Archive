---
title: "Changing 333MHz to 250MHz helps to lower CPU temperature?"
date: 2016-11-14
forum: The Cafe
---

### Post by KayeNg on 2016-11-14
Hi guys! In my last post I stated that my motherboard is ASRock Wolfdale1333-D667 , and that I wanted to upgrade the processor from:

[COLOR=#000000]"Single core Intel Celeron 430 (-UP-) speed: 1795 MHz (max)"

to 

[/COLOR]Intel Core 2 Duo E8400

[COLOR=#000000]which I did.   I noticed that the upgraded processor, E8400, actually runs hotter than the old single core.  It went as high as 90 degrees.  That's dangerous, correct?

So I went into BIOS and saw the Overclocking options as (three of them total):

Auto
CPU, PCIE Sync
CPU, PCIE Async

I tried the third one, (CPU, PCIE Async), and I changed the 333MHz to something like 250MHz.

I now notice that the temperature does not go up as high.  The difference is quite substantial.  From 70+ or 80+ to now just 60+.  Watching videos in youtube does not seem to be affected.

Did my tampering with the overclocking actually help or am I just doing something differently?  Can anyone confirm if what I did actually had something to do with the improvement?  (Not really an expert so bear with me please).

If it really did the trick, can I lower it a bit more to further decrease the temperature without affecting performance? Basically sometimes I just do light photo editing or surf the web with youtube in the background playing music or watching some news (although I just listen to it because I'm editing photos).

Thanks a lot guys![/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by kpatz on 2016-11-14
In general, the faster the processor, the more heat it generates.  Basically you're underclocking your new CPU which will make it run cooler but you won't get as much performance that you paid for out of it.  I recommend installing a better heatsink/fan to keep the new CPU cooler.

Also, did you use thermal paste when you installed the new CPU?  That's important.

---

### Post by poorguy on 2016-11-14
if you really want to keep your processor temp down try lowering the core voltage on the processor (vcore).
A Core 2 Duo does run hotter than a Celeron so you might want to consider a new processor HSF and you don't need to buy a super duper expensive one.

---

### Post by KayeNg on 2016-11-14
No, I did not use thermal paste.  Can you recommend a good brand? Regarding buying a better heat sink / fan, can any one fit in any motherboard? If not, what do I have to know before buying one?

What can I expect from lowering the core voltage besides a decrease in temperature?  

What is HSF?  

By the way, the core 2 duo is already the "new" one (2nd hand), upgraded from the celeron.

---

### Post by kpatz on 2016-11-14
HSF = heatsink/fan.

Lack of thermal paste could be the entire issue.  Get some Arctic Silver 5.  Clean the top of the CPU (heat spreader or die) with rubbing alcohol, and also clean the bottom of the HSF, apply a small amount (like the size of a rice grain) of AS5 on the top of the CPU die or heat spreader, then use a razor blade to spread it so it's thinly covering the entire top of the CPU's heat spreader or die.  Then reinstall the HSF and see what your temperatures look like.

If it's still running warm and you're using the Celeron heatsink on the Core2, you may need to get a bigger HSF.  Find one that's compatible with your CPU socket type.  Googling E8400 shows it to be a LGA 775 socket type, does that sound like what you have?

Lowering core voltage will decrease temps but if you lower it too much the system will become unstable and crash.  Dropping clock speed and core voltage together should help.  But I'd fix the HSF/thermal paste issue first and see if that takes care of it.

---

### Post by poorguy on 2016-11-14
HSF is what is known as Heatsink fan which is what sets on top of your processor to keep it cooled properly.

Thermal paste recommendation Arctic Silver 5.

As mentioned above lack of thermal paste could be your problem with heat so try it before buying another heatsink fan.

Some how to from the intel website click on this one. **How to apply TIM**

[http://www.intel.com/content/www/us/en/support/processors/000005576.html](http://www.intel.com/content/www/us/en/support/processors/000005576.html)

---

### Post by poorguy on 2016-11-14
> **kpatz said:**
> HSF = heatsink/fan.

Lack of thermal paste could be the entire issue.  Get some Arctic Silver 5.  Clean the top of the CPU (heat spreader or die) with rubbing alcohol, and also clean the bottom of the HSF, apply a small amount (like the size of a rice grain) of AS5 on the top of the CPU die or heat spreader, then use a razor blade to spread it so it's thinly covering the entire top of the CPU's heat spreader or die.  Then reinstall the HSF and see what your temperatures look like.

If it's still running warm and you're using the Celeron heatsink on the Core2, you may need to get a bigger HSF.  Find one that's compatible with your CPU socket type.  Googling E8400 shows it to be a LGA 775 socket type, does that sound like what you have?

Lowering core voltage will decrease temps but if you lower it too much the system will become unstable and crash.  Dropping clock speed and core voltage together should help.  But I'd fix the HSF/thermal paste issue first and see if that takes care of it.
Excellent advice given here.

---

### Post by KayeNg on 2016-11-15
Thanks guys, really appreciate it.  


Just to let you know, I haven't applied any thermal paste yet nor installed a new HSF, but I have underclocked the CPU to 250MHz (from 333MHz) and, since I could not find anything in BIOS that reads "core voltage", I enabled something called "SpeedStep".  

(In other words, I did two things:  manually underclock and SpeedStep)

Now I'm not sure, but I think SpeedStep made my system unstable, because when I turn the computer on, I get "boot error".  Comments?

I would also like your opinion about this Intel response to a question about altering voltage and clock:  

[https://communities.intel.com/thread/107024](https://communities.intel.com/thread/107024)

[COLOR=#3D3D3D][FONT=intel-clear]"In regard to your inquiry, actually we always recommend to use the processor at stock configurations, increasing or decreasing the voltage might caused damage to it, and lowering the voltage will increase the AMPs but again, we do not recommend to do that.[/FONT][/COLOR]

[COLOR=#3D3D3D][FONT=intel-clear]Altering PC clock or memory frequency and/or voltage may (i) reduce system stability and use life of the system, memory and processor; (ii) cause the processor and other system components to fail; (iii) cause reductions in system performance; (iv) cause additional heat or other damage; and (v) affect system data integrity."

Cheers!

[/FONT][/COLOR]

---

### Post by poorguy on 2016-11-15
My best advice for you is to apply some thermal paste and I believe that your problem with heat will be solved.
I am running several core 2 duo processors using HSF from celeron processors without any temp problems.

As far as the info from intel is probably true it is mainly directed towards people who overclock their systems.

---

### Post by mastablasta on 2016-11-16
apply the thermal paste! it has to be there. you can mess arround with udnerclocking later. it is easy to apply. just make sure oyu clean the heatsink and CPU well first. without paste the heat can not efficiently transfer from the CPU ot the cooler (heatsink).

then, if problem persist get a new heatsink. reapply the paste.

had a similar issue when CPU heatsink decided to pop out of the mobo. until i clean the old paste, applied a new one i got nowhere, not it is as it should. cosy temps.


i then installed psensor to monitor the temp.

---

### Post by KayeNg on 2016-11-21
I finally bought a 30 gram thermal paste, although it is a cheap one because no one sells Arctic Silver where I live.  Cost about U.S. $2.00 only.

Average CPU (Intel E8400) temperature is now 40+ to 50+ , and does not go up to 80+ anymore, although I was expecting it to be constant at 30 because I have a desktop computer running E5300 which averages 30 degrees.   But it still is a big improvement.  And I've changed CPU settings back to default (no more underclocking).

Poorguy you said you have several core 2 duos, do they get the same temperature as mine? (40+ , 50+)  Should I aim for a lower temperature? But I don't think I'll be able to buy a high speed HSF for socket 775 anymore.   

I also don't know if the paste would last, being so cheap(?) and made in China.

By the way, I applied it very thinly.  I used about 3/4 size of a pea.

---

### Post by kpatz on 2016-11-21
The E5300 is a slower chip so it's going to produce less heat than a E8400.  40-50 is pretty good.  Arctic Silver may bring it down a few more degrees.  You put a small amount of paste on, right?  Too much paste can cause high temps as well.  I like to put a tiny amount on and then spread it across the metal top of the CPU (heat spreader) with a razor blade, before putting the HSF on.  You want as much metal-to-metal contact as possible, with the paste filling in the gaps, to get the best heat transfer.

---

### Post by mastablasta on 2016-11-22
to reduce it even further you would need to buy a better cooller.

my celeron E3300 also has arround 40-50 usually. sometimes 60. it has a crappy cooler. and even arctic silver can't save it from that. :)

---

### Post by KayeNg on 2016-11-22
Yes kpatz I applied the paste exactly like you would. Thanks guys!!! :)

---

### Post by poorguy on 2016-11-22
> **KayeNg said:**
> Poorguy you said you have several core 2 duos, do they get the same temperature as mine? (40+ , 50+)  Should I aim for a lower temperature? But I don't think I'll be able to buy a high speed HSF for socket 775 anymore.   

I also don't know if the paste would last, being so cheap(?) and made in China.

By the way, I applied it very thinly.  I used about 3/4 size of a pea.

My Core 2 Duos run 46 to 51 degrees c all the time as I'm running them using a Celeron HSF and they run fantastic.
I don't use any fancy thermal paste what I use is white transistor paste that I have used in my electronics business for years.
The important thing about applying thermal paste is to not over use and you sound as though you applied it well as you temps have dropped.
I'm sure that I will be crucified by some on my choice of thermal paste. 
The paste you bought and applied will work fine.
Check the temps now and then and enjoy using your computer. ;)

---

### Post by kurt18947 on 2016-11-23
I recently read an article on Toms Hardware (I think) about thermal paste. Their recommendation was to not spread it but put a dot about the size of a pea in the center then clamp the heat sink. Their contention was that spreading the paste could introduce tiny air pockets that would be insulators slowing the heat transfer from processor to heatsink.

---

### Post by poorguy on 2016-11-23
> **kurt18947 said:**
> I recently read an article on Toms Hardware (I think) about thermal paste. Their recommendation was to not spread it but put a dot about the size of a pea in the center then clamp the heat sink. Their contention was that spreading the paste could introduce tiny air pockets that would be insulators slowing the heat transfer from processor to heatsink.
I thought this was interesting.

[https://www.youtube.com/watch?v=EyXLu1Ms-q4](https://www.youtube.com/watch?v=EyXLu1Ms-q4)

I have applied thermal paste several different ways and to be honest could never see any difference.
I have also tried the special fancy thermal paste and the 2 to 3 degree difference that I seen wasn't worth the cost IMO.
I still use the white silicon transistor paste that we use on transistors and never have any issues at all.
I also believe in the dot method only because it does make the most sense.
Use whatever method which you feel most comfortable with.
This is my opinion based on my own experience. 

Happy Thanksgiving to All.

The PoorGuy

---

