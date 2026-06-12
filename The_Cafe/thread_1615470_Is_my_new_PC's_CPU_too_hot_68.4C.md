---
title: "Is my new PC's CPU too hot? 68.4C?"
date: 2010-11-07
forum: The Cafe
---

### Post by mwshook on 2010-11-07
I just built up a new PC from scratch, installed Maverick, and am in the process of working the kinks out.



The CPU's a AMD Phenom II X2 555 3.2GHz with the stock heatsink/fan.

It idles at **28-30C**. Right now I have it sitting on top of my desk, running 2 instances of burnK7 to stress both cores. The temp is maxing out at about **68.4C.**

Due to space constraints, I'm using a micro ATX case, and I've never built a computer this small. Every internal and external drive bay is occupied. Space is pretty tight with cables everywhere. I don't think the airflow is great. But there is a grated vent on the cover, and there's no obstructions between the CPU fan and the vent. The case came with 2 small rear fans above the connectors. There's a mount for a front fan, but I haven't installed anything.

Is 67C a problem? This is going to be my main PC, not an HTPC or anything. I won't be doing anything intensive like running Folding@Home, but I will do some gaming. I don't want to install a new heatsink, because of the hassle. And I don't want to install a front fan because of the noise. But I will if I have to. I realize small cases may have unique issues

---

### Post by MooPi on 2010-11-07
Yes to hot. Under stress the CPU should be under 50 C. You may want to check the thermal paste or just to see if your heatsink is fastened down completely. I rarely get above 45 C under stress and at idle mine usually hoover around 35-38 C.

---

### Post by NightwishFan on 2010-11-07
Running CPU under stress now and I get 64c. It idles around 45c. I have never noticed any heat or problems.

---

### Post by Bucky Ball on 2010-11-07
> **MooPi said:**
> Yes to hot. Under stress the CPU should be under 50 C. You may want to check the thermal paste or just to see if your heatsink is fastened down completely. I rarely get above 45 C under stress and at idle mine usually hoover around 35-38 C.

Environments and computers are different. You are not really correct in saying this is too hot (although it is a little warm). Just cos yours runs at such and such a temp doesn't mean it will be same for everyone and this is within limits.

Having said that, maverick seems to have some issues with heating and specifically fan control. You might want to try editing the kernel line at boot to read:

```
acpi=copy_dsdt
```

Is the fan switching on and off? Was it before? I would also strongly advise taking a look at this page.

[http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)

As mentioned, check thermal paste and make sure that CPU fan is locked firmly in place. All depending on the fan, click it into place with a screw driver rather than trying to push in with fingers. There usually a slot for this on each of the four attaching lugs.

---

### Post by handy on 2010-11-07
Comfortable operating temperatures vary throughout the range of different CPU's that are currently made, & through history of the things. 

I've run CPU's that sat around 90 degrees C., for years with never a problem.

My Core2Duo T7700  @  2x 2.40GHz 2393MHz, 4096 KB Cache, is always around 45 degrees C. LxSensors tells me that it is ok up to 100 degrees C., but not beyond.

If I were concerned about my CPU's temp', I'd go to the manufacturers site & find out what the spec's say about it.

---

### Post by MooPi on 2010-11-07
I'm just very familiar with AMD and this CPU in particular. Currently AMD cpu's run considerably cooler than the older socket A processors. I'm at the moment testing an over clock with Mprime on an AMD Athlon 620 rated @ 2.6Ghz (OC'd to 3.15) is running mid 40's. I'm certain the processor can take the heat as I think it's rated to go 70 C max, just higher than normal from what I've seen on many modern AMD cpu's.

---

### Post by mcduck on 2010-11-07
> **Bucky Ball said:**
> Environments and computers are different. You are not really correct in saying this is too hot (although it is a little warm). Just cos yours runs at such and such a temp doesn't mean it will be same for everyone and this is within limits.

+1 to this.

And instead of guessing, one can always check the temperature limits for the CPU in question. There's a lot of variance in what different CPU's can take and what's normal for them.

Great link with temp specs for most consumer CPUs: [http://mysite.verizon.net/pchardwarelinks/elec.htm]("http://mysite.verizon.net/pchardwarelinks/elec.htm"). Find your CPU and check the "Max Case Temp" (It means the *CPU casing*, not the computer case temp ;))

In this case, the max temp for Phenom II X2 555 is 70°C, so you are still within limits but I'd say way too close to be comfortable...

I would definitely recommend improving the cooling, such a small case will get easily crowded and you might even really need the front case fan to provide decent airflow through all the cables and stuff squeezed into the case. At the very minimum, get some cable ties and try to tie the cables so that they aren't in the way of the airflow.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2010-11-07
Mine idles at around 55C and warms up to ~75C under full load (tripcode explorer/y-crunch/Folding@Home/JavaNNS). I've left it at full load for weeks at a time and it still works fine.

(Intel Core 2 Duo E6700)

---

### Post by P4man on 2010-11-07
> **MooPi said:**
> I'm just very familiar with AMD and this CPU in particular. Currently AMD cpu's run considerably cooler than the older socket A processors. I'm at the moment testing an over clock with Mprime on an AMD Athlon 620 rated @ 2.6Ghz (OC'd to 3.15) is running mid 40's. I'm certain the processor can take the heat as I think it's rated to go 70 C max, just higher than normal from what I've seen on many modern AMD cpu's.

If you see 40C under full load on all cores, then its misreporting, its that simple. No matter if its AMD or intel, these chips will pull on the order of  80W under full load on all cores (yours has a 95W TDP at stock speed, overclocked it will be way above 100W). Thats a really hot lightbulb on the surface of a postage stamp. NOt even watercooling would keep it below 40C.

[B]
To the OP:[/B] you have nothing to worry about. Im sure you could get better temps with better case ventilation but those temps are not cause for concern.

---

### Post by The Real Dave on 2010-11-07
> **P4man said:**
> If you see 40C under full load on all cores, then its misreporting, its that simple. No matter if its AMD or intel, these chips will pull on the order of  80W under full load on all cores (yours has a 95W TDP at stock speed, overclocked it will be way above 100W). Thats a really hot lightbulb on the surface of a postage stamp. NOt even watercooling would keep it below 40C.

[B]
To the OP:[/B] you have nothing to worry about. Im sure you could get better temps with better case ventilation but those temps are not cause for concern.

My 3Ghz Pentium IV on the other hand sits at 41C under full load :)

OP, according to this [site]("http://www.neoseeker.com/Articles/Hardware/Reviews/pii_555/") you CPU is good to 70C. Each CPU is different, I mean, I've had Pentium IIIs hit over 100C. 

You'll most likely not have a problem, but if that's what it runs at when clean, it'll be hotter when it starts to get dusty. And either way, heat slowly kills computers, a cold computer generally lives longer.

Try to tidy up those messy cables you talked about, making sure they don't restrict airflow. Getting cables that are just about the right size might help in that, rather than having excess cable around the place, especially in a small case.

Also, try to add any fans you can, ensuring they're working with the airflow through the case. You could also think about getting an aftermarket CPU cooler (I'm not sure if you'res is good or bad, some stock coolers are terrible, some are great) or even trying your hand at watercooling.

---

### Post by P4man on 2010-11-07
> **The Real Dave said:**
> My 3Ghz Pentium IV on the other hand sits at 41C under full load :)

Which I bet you a fortune, isnt the actual temperature. I have an old 3 GHz P4 prescot here myself. It always reports ~40 in everest and 50 in speedfan  and lm-sensors. Even when loaded (idle is almost the same, which is a dead give away of wrong reporting). 

When I manually stop the CPU fan, the temperature doesnt rise noticeably in any of these apps. But the heatsink gets scorching hot, almost too hot to touch, and within a minute it triggers thermal throttling according to everest and dmesg. Even though it still reports 40C or 50C depending on the app. Speedfan on the other hand jumps from 52 straight to 90+C in an instant. No steps inbetween. If I let the fan blow again,  temps start dropping and from 90C it goes immediately to 50C again. Nothing in between.

Is the cpu running at 50C under load with the fan? No way. Its a crappy thermal sensor (if not a deliberate attempt to hide the real temps).

---

### Post by CharlesA on 2010-11-07
> **P4man said:**
> Is the cpu running at 50C under load with the fan? No way. Its a crappy thermal sensor (if not a deliberate attempt to hide the real temps).

Indeed. The only real way to tell for sure what temp yer CPU is is to get out a laser thermometer, but with the heatsink in place you can't exactly measure the die temp.

---

### Post by P4man on 2010-11-07
Core2 and newer intel cpu's, as well the newer AMD cpu's all have ondie thermal sensors which are very accurate (but you need the correct software to read them and interpret the raw data, not all programs do that correctly). 

Anyway, I just uploaded a clip to youtube to show what happens to my P4 when I stop the cpu fan, to prove my point:

[http://www.youtube.com/watch?v=_-Nx_gZ5VPU](http://www.youtube.com/watch?v=_-Nx_gZ5VPU)

I stop the CPU fan at 40 seconds in the clip, see what happens.

Now this doesnt mean every Pentium 4 or other cpu runs hotter than reported, but the cpu can NEVER run cooler than the heatsink. Touch it, is it really colder than your skin when you run the cpu under full load? Even if you stop the fan? 

And  p4s dont have a thermal sensor on die, only in the cpu socket (which by definition reports lower values than ondie, even if the sensor works correctly) and those are generally very wrong/buggy and I suspect often even deliberately report too low values to hide how hot these chips really ran.

---

### Post by CharlesA on 2010-11-07
That's the nice thing about the newer processors. Unfortunately I've run into problems where the BIOS read the temp correctly, but the software inside the OS doesn't read it correctly.

It's a BIOS bug or something like that.

---

### Post by MooPi on 2010-11-07
> **P4man said:**
> If you see 40C under full load on all cores, then its misreporting, its that simple. No matter if its AMD or intel, these chips will pull on the order of  80W under full load on all cores (yours has a 95W TDP at stock speed, overclocked it will be way above 100W). Thats a really hot lightbulb on the surface of a postage stamp. NOt even watercooling would keep it below 40C.

[B]
To the OP:[/B] you have nothing to worry about. Im sure you could get better temps with better case ventilation but those temps are not cause for concern.

I believe your talking out of the side of your head. That is simply not true. As reference to the cool nature of the AMD line [http://www.overclockersclub.com/reviews/athlon2_620/17.htm]("http://www.overclockersclub.com/reviews/athlon2_620/17.htm")

My system that I'm over clocking right now on stock heat sink and fan is only warm to the touch at the base of the sink. All four cores are 100% on mprime stress test. I dare say if it were close to 70 C I'd not be able to do that.
I stopped the stress test after my last statement and checked the temp in BIOS. 50 C moments after the conclusion of the test. Very cool indeed :-)

---

### Post by ~LoKe on 2010-11-07
Seems like a lot of misinformation in this thread.

My CPU is aircooled, overclocked to 3.4GHz, and idles at about 27-31, and on load never passes 50.  70 is fine on load, I'd start being concerned at around 80-85 on load, though that's still acceptable.

Also, as mentioned, different processors can tolerate different temperatures, and that can vary between batches, as well.

---

### Post by P4man on 2010-11-07
> **MooPi said:**
> I believe your talking out of the side of your head. That is simply not true. As reference to the cool nature of the AMD line [http://www.overclockersclub.com/reviews/athlon2_620/17.htm]("http://www.overclockersclub.com/reviews/athlon2_620/17.htm")

My system that I'm over clocking right now on stock heat sink and fan is only warm to the touch at the base of the sink. All four cores are 100% on mprime stress test. I dare say if it were close to 70 C I'd not be able to do that.
I stopped the stress test after my last statement and checked the temp in BIOS. 50 C moments after the conclusion of the test. Very cool indeed :-)

If your cpu is showing 50C in the bios at least 10 seconds after you stopped mprime, its rather safe to assume it was running more than "mid 40s" before, no? When you stop the load cpu temperatures easily drop 5-10C in a matter of  seconds, possibly more with a light alu heatsink.

Im not saying those chips dont run cool, I know they do, Ive built machines with them myself, Im just saying  under full load they will certainly exceed 40C ondie temperature without watercooling.

---

### Post by MooPi on 2010-11-07
It was an over night stress test and I'm sure it peaked past 50, but still I'm performing a non scientific test. I actually estimated the 50 C temp due to the time lapse, the BIOS showed 49 C. Simply trying to vet out any errors to see if the OC is stable. But the OP is very close to the thermal ceiling and needs to improve his cooling or his rig will have a considerably shorter than normal life span.

---

### Post by _outlawed_ on 2010-11-07
> **Yownanymous said:**
> There's your problem. If you're going to use Linux for God's sake use something that was done competently, almost from scratch, and not from an already screwed-up base that some fanatics were behind.

Maverick is fine. :popcorn:

---

### Post by NightwishFan on 2010-11-07
Either clairify or I am reporting that as flamebait. If you have a bad experience with Ubuntu that does not mean you are justified in trolling the forums. Ubuntu is a fantastic distribution, it offers a lot of flexibility and commercial options.

---

### Post by howefield on 2010-11-07
Closed for cleaning...

And reopened. Keep the thread on topic and no more drama please. :)

---

### Post by P4man on 2010-11-07
> **MooPi said:**
> It was an over night stress test and I'm sure it peaked past 50, but still I'm performing a non scientific test. I actually estimated the 50 C temp due to the time lapse,.

Would be nice if youd actually test temperatures during stresstests before saying Im talking out of my head, especially since your own observations prove beyond doubt your temps are (likely a lot) higher than your initial claims. The default AMD Athlon II  heatsink is a really light alu heatsink, it cant store much heat, so in the time you quit the apps, rebooted and got in to the bios most of the excess heat would have been blown away by the fan. That could easy make 15-20C difference on that time. On my Core2 system mu temperatures drop >10C within one or two seconds. Thats with a huge, mostly copper cooler.

> But the OP is very close to the thermal ceiling and needs to improve his cooling or his rig will have a considerably shorter than normal life span


No he's not. He is almost 30C from the spec limit for his chip, and that is running a worst case scenerio of a thermal virus. Real world loads wont heat it up nearly as bad, and even if they do, its perfectly acceptable. Extra case fan wouldnt hurt, but there is no pressing need.

---

### Post by CharlesA on 2010-11-07
I've had one chip hit 100C before, and that was because the heatsink came lose (one of the mounts broke off). The only thing that happened was the machine flipped out and shutdown if it hit 100C.

So far I haven't really noticed any problems now that the problem has been fixed.

*shrug*

---

### Post by _outlawed_ on 2010-11-07
> **CharlesA said:**
> I've had one chip hit 100C before, and that was because the heatsink came lose (one of the mounts broke off). The only thing that happened was the machine flipped out and shutdown if it hit 100C.

So far I haven't really noticed any problems now that the problem has been fixed.

*shrug*

Most CPU I've noticed have a 100C limit before the system shuts itself off to save itself.

---

### Post by P4man on 2010-11-07
> **_outlawed_ said:**
> Most CPU I've noticed have a 100C limit before the system shuts itself off to save itself.

I once had an athlon 64 that was faulty. The heatspreader didnt make contact with the die, so no matter how I installed a heatsink, it would not cool the core. Under load it would spike up to 120C and more before shutting down. Probably because it heated up so fast, it would go from 60-70 to 100++ in mere seconds running prime. 

If you wonder why on earth I would test that, i simply thought the readings where bogus since the heatsink was completely cold;  I even tried removing it, booting up and I could touch the cpu heatspreader and it would be luke warm at most. The readings were correct though :D I removed the heatspreader, installed a shim and it was the best overclocker I ever had :D

---

### Post by mwshook on 2010-11-07
Wow, this thread exploded while I went to sleep. I didn't know it was such a "hot topic." (I'm sorry, I'm sorry)

Shortly after I posted, I figured out the sensors app wasn't showing all the temperature sensors. One of the cores was hitting 70.0, right at the listed maximum. (thanks for the link mcduck)

That is a bit too close for my comfort. I'm definitely going to find a quieter front fan. I'm going to try re-clipping the heatsink. If that doesn't help, I think I am going to get a new CPU cooler.

Looking at the cables, I don't like the way the IDE cable from my CD drive loops over the CPU Cooler. But I don't think there's much I can do about it. The drive actually hangs over the CPU fan pretty closely.

Can anyone recommend a low-profile CPU cooler that's fairly quiet and effective?

---

### Post by CharlesA on 2010-11-07
If you want low profile, I'd go with a water cooling block like this one:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16835181010](http://www.newegg.com/Product/Product.aspx?Item=N82E16835181010)

---

### Post by MooPi on 2010-11-07
> **P4man said:**
> 
No he's not. He is almost 30C from the spec limit for his chip, and that is running a worst case scenerio of a thermal virus. Real world loads wont heat it up nearly as bad, and even if they do, its perfectly acceptable. Extra case fan wouldnt hurt, but there is no pressing need.

Op please head warning your heat is within limit but close to MAX. 68.4 is not 30 C from spec limit of 70 C

---

### Post by The Real Dave on 2010-11-07
> **P4man said:**
> Which I bet you a fortune, isnt the actual temperature. I have an old 3 GHz P4 prescot here myself. It always reports ~40 in everest and 50 in speedfan  and lm-sensors. Even when loaded (idle is almost the same, which is a dead give away of wrong reporting). 

When I manually stop the CPU fan, the temperature doesnt rise noticeably in any of these apps. But the heatsink gets scorching hot, almost too hot to touch, and within a minute it triggers thermal throttling according to everest and dmesg. Even though it still reports 40C or 50C depending on the app. Speedfan on the other hand jumps from 52 straight to 90+C in an instant. No steps inbetween. If I let the fan blow again,  temps start dropping and from 90C it goes immediately to 50C again. Nothing in between.

Is the cpu running at 50C under load with the fan? No way. Its a crappy thermal sensor (if not a deliberate attempt to hide the real temps).

Mine doesn't behave like you described. Temperatures read the same across apps, and even in Windows. If I restrict the fan cooling it, I can watch it climb up and up, usually in 2 degree increments. The hottest I've seen it is 76C, at which the system crawled due to thermal throttling. 

Mine too is a Prescot (90nm), a [516]("http://processorfinder.intel.com/details.aspx?sSpec=SL8J9") to be exact.

The reason I get such good temps is because I have set it up to do so. I've added an 80mm exhaust fan, and a 120mm fan blowing air down on the motherboard. Cables that restrict airflow aren't accepted. The stock cooler is a monster, 80mm fan thing with about 90 tiny fins, and copper heat pipes. I've polished the part of the heatsink in contact with the CPU to perfection, and used high quality thermal grease. I've also changed the PWM values to the CPU fan. 48C is seen as a maximum temperature, at which runs at full speed (3200rpm). Above that, and the fan goes crazy, and has been seen at 4500rpm, sounding like a jet. 

Keeping a relatively powerful Pentium IV under 50C under load isn't that hard. My case isn't that big, and doesn't have many fans, just a 120mm, an 80mm exhaust, the CPU fan and the PSU fan. That's it. 

[Pics of the system here btw.]("http://linuxexpresso.wordpress.com/hardware#System64")

Also, reading heatsink temp by touching with your hand, doesn't mean it's above 37C. Your hands are generally much colder than that, which means the heatsink would of course be hotter.

---

### Post by P4man on 2010-11-07
Id like to see the actual spec sheets for that CPU to see if that 70C is Tjunc MAX, Tcase MAX or Tcase for the TDP they provide (last one being my guess, putting an artificially low Tcase is an  easy way to provide a lower TDP rating and that looks good on paper). Unfortunately, the AMD webserver gives me a HTTP 500 for the technical documents. Will try again later.

Any intel spec sheet Ive seen has Tjunc MAX at 95-105C, and that temp is the closest to what an ondie sensor reads. I find it hard to believe AMD chips would be so much less capable of withstanding heat, especially since they dont seem to turn off until they are far hotter. My  Athlon 64 with faulty heatspreader is rated in that list for 70C maximum. It idled at that temp and thermal protection only kicked in around 110C.

Anyway, there is no harm in installing a better heatsink, thats for sure.

---

### Post by CharlesA on 2010-11-07
I tried looking up the spec sheet for it and only found the same 70C rating.

That's hard for me to believe as well.

---

### Post by Dustin2128 on 2010-11-07
warm, but not out of the question. You still may want a more powerful fan to maximize lifespan.

---

### Post by P4man on 2010-11-07
> **The Real Dave said:**
> Mine doesn't behave like you described. Temperatures read the same across apps, and even in Windows. If I restrict the fan cooling it, I can watch it climb up and up, usually in 2 degree increments. The hottest I've seen it is 76C, at which the system crawled due to thermal throttling. 

Prescotts dont throttle that fast. Here throtteling kicks in around 80C and goes full swing around 90C :
[http://ixbtlabs.com/articles2/p4-throttling/](http://ixbtlabs.com/articles2/p4-throttling/)

IF you saw my vid, on mine it kicked in when speedfan reported around 95C and didnt go full swing even at 100C. If yours was crawling at a reported 76C, you can be fairly safe ondie temps where closer to, if not over 90C. 

Anyway, your sensor may not be as flawed as mine, but that isnt the point; the absolute numbers on P4s are never correct; they just give an idea. Each motherboard will report vastly different numbers even if you use the exact same cpu in the same circumstances. Even different programs will report different values.

Now as long as the system is stable and doesnt throttle with a thermal virus, then  thats not something to lose sleep over. Just dont compare those numbers direcly with calibrated ondie sensors in Core2 and later and Athlon II/ Phenoms. And dont think 50C is the maximum temperature in the core, it almost certainly isnt. But thats okay :)

---

### Post by 3Miro on 2010-11-07
Phenom II X4 at 3.2Ghz. In August in Florida and AC set to 27C (80F) it idles at 43C and under full load it gets to 68C. When temperatures in the room fall to 22C then the CPU idles at 36C (when watching YouTube) and goes to low 60C on full load.

This is on a desktop with a stock fan and a lot of fans on the case.

---

### Post by P4man on 2010-11-07
> **CharlesA said:**
> I tried looking up the spec sheet for it and only found the same 70C rating.

That's hard for me to believe as well.

Server is up again for me. You can download it here:
[http://support.amd.com/us/Processor_TechDocs/43375.pdf](http://support.amd.com/us/Processor_TechDocs/43375.pdf)

As I guessed, the 70C is Tcase MAX for their given TDP. It follows directly from the TDP. That page has tables where TDP corresponds to a Tcase MAX. Look at them. The same thermal profile (so applies to the same cpu family), a 95W TDP corresponds to a 70C Tcase MAX, and for instance some ultralow power 25W TDP with that same profile, would correspond to a 55C Tcase MAX.

Does that mean that the lower power cpu will melt over 55C? OF course not. These numbers have nothing to do with do with Tjunction MAX which is the maximum temperature a CPU can operate at. Those numbers are not given,  or at least I cant find them. The numbers that are given are requirements for **heatsinks**.

---

### Post by The Real Dave on 2010-11-07
> **P4man said:**
> Prescotts dont throttle that fast. Here throtteling kicks in around 80C and goes full swing around 90C :
[http://ixbtlabs.com/articles2/p4-throttling/](http://ixbtlabs.com/articles2/p4-throttling/)

IF you saw my vid, on mine it kicked in when speedfan reported around 95C and didnt go full swing even at 100C. If yours was crawling at a reported 76C, you can be fairly safe ondie temps where closer to, if not over 90C. 

Anyway, your sensor may not be as flawed as mine, but that isnt the point; the absolute numbers on P4s are never correct; they just give an idea. Each motherboard will report vastly different numbers even if you use the exact same cpu in the same circumstances. Even different programs will report different values.

Now as long as the system is stable and doesnt throttle with a thermal virus, then  thats not something to lose sleep over. Just dont compare those numbers direcly with calibrated ondie sensors in Core2 and later and Athlon II/ Phenoms. And dont think 50C is the maximum temperature in the core, it almost certainly isnt. But thats okay :)

Mine always seem to get progressively slower after 66C, which is listed as the Tcase for my CPU. Anyway, I've a strong suspicion that my systems CPU throttling is motherboard controlled rather than CPU based, seeing as it mentions it in the BIOS. My systems mobo is a funny Acer make, which pairs directly with this CPU. No other CPU will suit >.<

Here's another article on that site you posted, with a different Pentium IV, where throttling started at 70C, but admittedly continued to 100C.

Edit: Just watched your video. Definately in your case something's going wrong, but I don't think it's something that effects all P4s. I've 5 running in my home at the moment (none of which are dual core or HT btw), between different laptops and servers, and I've never experienced anything like what your video shows.

---

### Post by Windows Nerd on 2010-11-07
Though 68 degrees is within the operating limits of the processor (I see others on this thread have reported a safe operating level of 70 degrees). However, running a processor at that hot all the time is not at all recommended. In general, the cooler a processor is, the longer it lasts. 

It is a general attitude among Linux users to get much more life out of a computer than the average user, as the requirements by most all Linux distributions is significantly lower than that of the constantly growing Windows. If you have the knowledge to, it is completely possible to run most tasks on a lightweight distro with 64 megs of ram. Most computers with that much ram are around 10 or more years old. I can't imagine a computer running at that high a temperature and staying good condition (no crashes/kernel panics  etc) for 10 years.

Sure processors can survive high heat and higher voltage than normal for weeks at a time, but the more heat and voltage present (voltage only really changes if you overclock, which is impossible on a motherboard that fits into a mini-atx case), the shorter the lifetime of the processor.

I would recommend improving airflow in the case, or possibly just getting a bigger case with better cooling options.

If you cannot get a new case, you can always cut out some holes in the case if you are handy, and then add an extra fan.

Scott

---

### Post by mwshook on 2010-11-07
Thanks for all the help.

1. I'm going to get a new CPU cooler, _[this thing by Scythe]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835185097")_. It has the copper crap that's all the rage. And as best as I can tell, it will fit in my case.

2. I'm getting a round IDE cable, so it's not blocking airflow (as much) around the front side of the heat sink. I'll try to tie down the other cables in a more orderly fashion once I get all the hardware finalized.

3. The front fan I had laying around is louder the 4 other fans put together, so I'm not using it. I think it used to be better; I'm not even sure how old it is. So I'm getting something that should be quieter.

As a side note, the reason I'm using a mini ATX case:
We recently bought a new house with a very nice office area built into a corner in the hallway. It has a convenient shelf to put your PC that's *exactly the size of a standard  micro ATX case!* My old case fits into it like a sleeve. It leaves no room for airflow to the side, and very little ventilation in the back. A mini ATX case at least gets some breathing room.  

But you can see why I'm worried about heat. It will probably run hotter when I'm done building it.

---

### Post by deanjm1963 on 2010-11-08
> **mwshook said:**
> I'm going to get a new CPU cooler, _[this thing by Scythe]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835185097")_. It has the copper crap that's all the rage. And as best as I can tell, it will fit in my case.

It's a great cooler - can't say enough about it ... cools my i5 680 much better than the generic intel cooler.

---

### Post by Oxwivi on 2010-11-08
Anyone know the least noisiest fan for a Pentium 4? My fan controller no longer works, and it constantly operates at the max speed, it's very noisy.

---

### Post by P4man on 2010-11-08
> **The Real Dave said:**
> Mine always seem to get progressively slower after 66C, 

66C being the reported temp. So either P4s all start throttling at vastly different temperatures, or P4 motherboards *report* vastly different temps :)

---

### Post by Goldfissh on 2010-11-08
> 1. I'm going to get a new CPU cooler, this thing by Scythe. It has the copper crap that's all the rage. And as best as I can tell, it will fit in my case.

Can I recommend the [Prolimatech Megahalems HS]("http://benchmarkreviews.com/images/reviews/cooling/Best_CPU_Coolers_Q4-2008/Prolimatech_Megahalems_Angle.jpg")? It's what I'm using on my desktop PC, which I haven't seen running over 40C on under stressful conditions. Fantastic HS!

---

### Post by Oxwivi on 2010-11-08
> **Goldfissh said:**
> Can I recommend the [Prolimatech Megahalems HS]("http://benchmarkreviews.com/images/reviews/cooling/Best_CPU_Coolers_Q4-2008/Prolimatech_Megahalems_Angle.jpg")? It's what I'm using on my desktop PC, which I haven't seen running over 40C on under stressful conditions. Fantastic HS!
Oi, that's huge! Didn't he say his computer is small, and already cramped as it is?

---

