---
title: "Hardware Experts - I cannot trace this problem..."
date: 2009-12-17
forum: The Cafe
---

### Post by Roasted on 2009-12-17
I'm building two basic rigs for my brothers as Christmas gifts this year, and both of them won't boot up and I don't understand why.

Proc - [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103687](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103687)
RAM - [http://www.newegg.com/Product/Product.aspx?Item=N82E16820141369](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141369)
Board - [http://www.newegg.com/Product/Product.aspx?Item=N82E16813138167](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138167)
PSU - [http://www.newegg.com/Product/Product.aspx?Item=N82E16817159023](http://www.newegg.com/Product/Product.aspx?Item=N82E16817159023)

Proc is AM3.
Board is AM3.
RAM is DDR3 - supported by board.

The board and processor are also sold as a combo item on NewEgg, so that alone suggests they're 100% compatible. Plus I called Biostar and the technician also confirmed the exact processor I got is compatible.

I have two spare machines here besides the two I'm building. We'll refer to them as "HP" and "Spare tower".

I've done the following to the two new problematic systems:

Reseated processor on each system.
Swapped the processors between each system.
Reset the CMOS on each system.
Changed the BIOS jumpers on each system.
Tried the PSUs I got with them, plus the HP and spare tower PSUs, all 4 power on fans and LEDs - but never boots.
Tried all 4 PSUs on my HP and spare tower, all 4 boot those two systems fine, suggesting the 2 PSUs I got for these rigs are okay.
I never get any video output to my monitor whatsoever.
Pulled video card out and tried to run onboard video, no output whatsoever.
I've tried 2 LCD monitors - 17 and 22 inch.
I've tried 2 VGA cables - both of which I confirmed as working on other systems.
I took the motherboard out of the case, held it in mid-air by the plastic cpu fan, and powered it on to make sure it wasn't getting grounded out in the case.
I powered on the board with no RAM - constant beeps as expected. But I never get a single POST beep to confirm it's firing up.
I attempted boot with only 1 stick of RAM, repeating this process for each of the 4 sticks of RAM I have, individually trying to boot each one.

So, I'm at a loss. 8 days before Christmas and two systems that won't boot.

Swapped out every part combination I could think of, no dice.

The Biostar tech also made a comment, that if it was a CPU problem, the system would display some sort of error, like "Invalid Processor."

I find it hard to believe I'd have two DOA boards like this, but I don't know where else to go with it.

What do you guys suggest? I know systems can be sensitive to the power they receive. Is it possible I happen to have 4 PSUs that just can't fully boot this system? 

I'm really trying and hoping that this is something I'm doing wrong. But to the best of my few short years of doing this in the field, I've done everything I can think of besides getting other parts to swap out to see what's bad.

What should I do?

---

### Post by fatcrab on 2009-12-17
Did you read the reviews on the ram? I see that it has been deactivated and it only has 2 reviews.It may be a bad batch.

---

### Post by Skripka on 2009-12-17
> **fatcrab said:**
> Did you read the reviews on the ram? I see that it has been deactivated and it only has 2 reviews.It may be a bad batch.

This.

---

### Post by Xbehave on 2009-12-17
DO you have any known good hardware to test with?
Personally i always suspect the mobo, but it looks like it could be bad ram this time.
0) If it's not getting to post the problem is with mobo/cpu/ram/psu so unplug and forget about everything else (HDD/CD/monitor) for now.
1) Test the ram in another computer with a liveCD and memtest
2) Test each component separately in a known good setup (if possible) (and possibly not including the PSU as a bad psu can mess up good hardware)

---

### Post by Roasted on 2009-12-17
> **Xbehave said:**
> DO you have any known good hardware to test with?
Personally i always suspect the mobo, but it looks like it could be bad ram this time.
0) If it's not getting to post the problem is with mobo/cpu/ram/psu so unplug and forget about everything else (HDD/CD/monitor) for now.
1) Test the ram in another computer with a liveCD and memtest
2) Test each component separately in a known good setup (if possible) (and possibly not including the PSU as a bad psu can mess up good hardware)

I've done the best I could with what I have to work with. My systems at home are not compatible with DDR3 ram, so I cannot test the RAM in any other systems. 

I was trying to figure out how I could somehow memtest this RAM. I run memtest a lot at work, so I'm very familiar with the procedure. But I have no clue how I could do this.

Maybe I should contact a local computer shop and see if I can bring in the system and they help me out by just shoving a DDR3 stick in there and see if it boots. If it does, blam. We know where the issue is.

---

### Post by Exodist on 2009-12-17
> **Roasted said:**
> I'm building two basic rigs for my brothers as Christmas gifts this year, and both of them won't boot up and I don't understand why.

Proc - [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103687](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103687)
RAM - [http://www.newegg.com/Product/Product.aspx?Item=N82E16820141369](http://www.newegg.com/Product/Product.aspx?Item=N82E16820141369)
Board - [http://www.newegg.com/Product/Product.aspx?Item=N82E16813138167](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138167)
PSU - [http://www.newegg.com/Product/Product.aspx?Item=N82E16817159023](http://www.newegg.com/Product/Product.aspx?Item=N82E16817159023)

Proc is AM3.
Board is AM3.
RAM is DDR3 - supported by board.

The board and processor are also sold as a combo item on NewEgg, so that alone suggests they're 100% compatible. Plus I called Biostar and the technician also confirmed the exact processor I got is compatible.

I have two spare machines here besides the two I'm building. We'll refer to them as "HP" and "Spare tower".

I've done the following to the two new problematic systems:

Reseated processor on each system.
Swapped the processors between each system.
Reset the CMOS on each system.
Changed the BIOS jumpers on each system.
Tried the PSUs I got with them, plus the HP and spare tower PSUs, all 4 power on fans and LEDs - but never boots.
Tried all 4 PSUs on my HP and spare tower, all 4 boot those two systems fine, suggesting the 2 PSUs I got for these rigs are okay.
I never get any video output to my monitor whatsoever.
Pulled video card out and tried to run onboard video, no output whatsoever.
I've tried 2 LCD monitors - 17 and 22 inch.
I've tried 2 VGA cables - both of which I confirmed as working on other systems.
I took the motherboard out of the case, held it in mid-air by the plastic cpu fan, and powered it on to make sure it wasn't getting grounded out in the case.
I powered on the board with no RAM - constant beeps as expected. But I never get a single POST beep to confirm it's firing up.
I attempted boot with only 1 stick of RAM, repeating this process for each of the 4 sticks of RAM I have, individually trying to boot each one.

So, I'm at a loss. 8 days before Christmas and two systems that won't boot.

Swapped out every part combination I could think of, no dice.

The Biostar tech also made a comment, that if it was a CPU problem, the system would display some sort of error, like "Invalid Processor."

I find it hard to believe I'd have two DOA boards like this, but I don't know where else to go with it.

What do you guys suggest? I know systems can be sensitive to the power they receive. Is it possible I happen to have 4 PSUs that just can't fully boot this system? 

I'm really trying and hoping that this is something I'm doing wrong. But to the best of my few short years of doing this in the field, I've done everything I can think of besides getting other parts to swap out to see what's bad.

What should I do?


Question? Are you familiar with a voltage/ohm tester? If so, completely unplug the Power Supplies and test them. Power Supplies should come one, but  you have to jumper them off on the softrelay cable that connects to the motherboard. If it starts up its not the PSU.

If the PSUs are good, re attach them to the motherboards checking all connections.
REMOVE all cards and RAM from the system. Only the CPU/FAN should be installed.
The system should half way start up and beep like hell at you. If it does its not mobo.

If thats working, re install the RAM (one stick at a time). If the system boots up and you get the bios post screen, keep installing RAM till you do not.  After you have added all the RAM, move on to the addon cards until you have narrowed down the issue. 


Other thoughts, check the motherboard manufacturers website for TESTED RAM, CPU and Power Supplies. Always best to use tested hardware.


post back what you find out..

---

### Post by Roasted on 2009-12-17
I have no cards or hard drives plugged in. We're working with:

PSU
CPU
Mobo
RAM

only. That's it. I tried 1 stick at a time and went through all 4 sticks on both boards. Nothing worked. :( 

On NewEgg's chat now. Trying to get them exchanged for a different brand. One of the reviews said it didn't work with their motherboard despite being DDR3 1066 compliant - maybe that's my same issue?

---

### Post by Skripka on 2009-12-17
> **Roasted said:**
> I have no cards or hard drives plugged in. We're working with:

PSU
CPU
Mobo
RAM

only. That's it. I tried 1 stick at a time and went through all 4 sticks on both boards. Nothing worked. :( 

On NewEgg's chat now. Trying to get them exchanged for a different brand. One of the reviews said it didn't work with their motherboard despite being DDR3 1066 compliant - maybe that's my same issue?

You're using El Cheapo RAM, PSU, etc...anything is possible.  Do you have Non-El-Cheapo DDR3 around that you can try?  

Be warned, Biostar hardware does some funny non-standard things.  Getting my BioStar mainboard to work was a combination of hopeful thinking, and blind luck-as the documentation sucks, and no one know exactly what all the BIOS options do.

---

### Post by Roasted on 2009-12-17
> **Skripka said:**
> You're using El Cheapo RAM, PSU, etc...anything is possible.  Do you have Non-El-Cheapo DDR3 around that you can try?  

Be warned, Biostar hardware does some funny non-standard things.  Getting my BioStar mainboard to work was a combination of hopeful thinking, and blind luck-as the documentation sucks, and no one know exactly what all the BIOS options do.

"El Cheapo" is still worlds better than the two systems these rigs will be replacing.

Socket A AMD 128mb RAM stock with Windows ME from 1999, anyone? :lolflag:

I RMA'd the RAM and I'll be placing a new order for newer RAM. If this doesn't work, I'm returning the whole damn thing and jumping off a cliff. 

The facts are this:

- The power supplies work in other systems.
- Working power supplies from other systems don't work with these rigs.
- The motherboard beeps with no RAM in - an indication it works.
- The motherboard has no response otherwise. No post beep, etc.
- Reseated processor, RAM, etc.
- Verified from Biostar direct that the processor I have is -indeed- supported.

I can't memtest cause I can't boot.

What else could it be? After talking with you guys and looking at more information about memory it seems to be a very likely cause.

Plus, the RAM I bought is already deactivated on NewEgg - and it only had a few reviews - one of which said "This RAM did not work in my board, yet it was fully supported. I tried other RAM of a different brand and had no issues whatsoever with the newer brand."

---

### Post by sydbat on 2009-12-17
I'd go with the "bad RAM" idea. If you can, find a computer that has DDR3 capabilities and test them there. Maybe a friend of yours has a newer box you can test with?

---

### Post by Skripka on 2009-12-17
> **Roasted said:**
> "El Cheapo" is still worlds better than the two systems these rigs will be replacing.

Socket A AMD 128mb RAM stock with Windows ME from 1999, anyone? :lolflag:

I RMA'd the RAM and I'll be placing a new order for newer RAM. If this doesn't work, I'm returning the whole damn thing and jumping off a cliff. 

The facts are this:

- The power supplies work in other systems.
- Working power supplies from other systems don't work with these rigs.
- The motherboard beeps with no RAM in - an indication it works.
- The motherboard has no response otherwise. No post beep, etc.
- Reseated processor, RAM, etc.
- Verified from Biostar direct that the processor I have is -indeed- supported.

I can't memtest cause I can't boot.

What else could it be?

Bad mainboard.  I'd also put your CPUs in any old AM2/AM3 socket just for kicks...  Got any other DDR3 rig around to test your memory?

It is wierd to get 2 or 4 lemons of anything in one shipment though. :confused:

---

### Post by Lvcoyote on 2009-12-17
> **Roasted said:**
> "El Cheapo" is still worlds better than the two systems these rigs will be replacing.

Socket A AMD 128mb RAM stock with Windows ME from 1999, anyone? :lolflag:

I RMA'd the RAM and I'll be placing a new order for newer RAM. If this doesn't work, I'm returning the whole damn thing and jumping off a cliff. 

The facts are this:

- The power supplies work in other systems.
- Working power supplies from other systems don't work with these rigs.
- The motherboard beeps with no RAM in - an indication it works.
- The motherboard has no response otherwise. No post beep, etc.
- Reseated processor, RAM, etc.
- Verified from Biostar direct that the processor I have is -indeed- supported.

I can't memtest cause I can't boot.

What else could it be? After talking with you guys and looking at more information about memory it seems to be a very likely cause.

Plus, the RAM I bought is already deactivated on NewEgg - and it only had a few reviews - one of which said "This RAM did not work in my board, yet it was fully supported. I tried other RAM of a different brand and had no issues whatsoever with the newer brand."

The fact that PSU's are working in other systems doesnt mean a thing actually.  What wattage and +12v amps do the PSU's from the other machines have??  I don't care if you spend $50 or $5000 on a new system, to power it with a $29 PSU is not a good thing.

---

### Post by Skripka on 2009-12-17
PS-You *did* seat your PSU cables  fully didn't you?

My brother had a similar case on an Intel LGA775/DDR3 rig...ended up being CPU power wasn't seated fully, by milimeters.

---

### Post by NoaHall on 2009-12-17
> **Lvcoyote said:**
> The fact that PSU's are working in other systems doesnt mean a thing actually.  What wattage and +12v amps do the PSU's from the other machines have??  I don't care if you spend $50 or $5000 on a new system, to power it with a $29 PSU is not a good thing.

This.

---

### Post by Lvcoyote on 2009-12-17
Also, do you have both the 24 pin main cable and the 4-pin cable plugged in to the motherboard??  Both are are required obviously for it to boot.

---

### Post by Roasted on 2009-12-18
> **Lvcoyote said:**
> Also, do you have both the 24 pin main cable and the 4-pin cable plugged in to the motherboard??  Both are are required obviously for it to boot.

Yep.

No dice.

Like I said, I read some negative reviews on the RAM - saying it just didn't work in some systems while other brands worked fine of the same DDR type and same clock speed.

I'm RMAing the ram for a refund and just 2-daying a new brand of RAM to give that a shot. Then we'll go from there.

I really... really don't think the power supplies are the issue. I don't care what opinions are out there about it - I ran the PSUs through my meter and power supply tester - everything checks out 100% on both of them. I'm just not at all convinced whatsoever that the PSUs are a factor.

So we'll go from here and see what happens.

---

### Post by Exodist on 2009-12-18
> **Skripka said:**
> You're using El Cheapo RAM, PSU, etc...anything is possible.  Do you have Non-El-Cheapo DDR3 around that you can try?  

Be warned, Biostar hardware does some funny non-standard things.  Getting my BioStar mainboard to work was a combination of hopeful thinking, and blind luck-as the documentation sucks, and no one know exactly what all the BIOS options do.
Though 20 years ago they were pure junk. Every motherboard I have purchased in the past 7 years has been Biostar. They are excellent products now.

---

### Post by Exodist on 2009-12-18
> **Roasted said:**
> "El Cheapo" is still worlds better than the two systems these rigs will be replacing.

Socket A AMD 128mb RAM stock with Windows ME from 1999, anyone? :lolflag:

I RMA'd the RAM and I'll be placing a new order for newer RAM. If this doesn't work, I'm returning the whole damn thing and jumping off a cliff. 

The facts are this:

- The power supplies work in other systems.
- Working power supplies from other systems don't work with these rigs.
- The motherboard beeps with no RAM in - an indication it works.
- The motherboard has no response otherwise. No post beep, etc.
- Reseated processor, RAM, etc.
- Verified from Biostar direct that the processor I have is -indeed- supported.

I can't memtest cause I can't boot.

What else could it be? After talking with you guys and looking at more information about memory it seems to be a very likely cause.

Plus, the RAM I bought is already deactivated on NewEgg - and it only had a few reviews - one of which said "This RAM did not work in my board, yet it was fully supported. I tried other RAM of a different brand and had no issues whatsoever with the newer brand."


Defiantly a bad batch of RAM. New RAM should have you fixed up. Indication that it beeps at you wit no RAM in the system and then doesnt do anything when RAM is in the system means. ITs RAM..

Biostar makes quality motherboards. I have purchased about 12 in the past 6 years with 0 issues on all of them. Solid products.

You do want to make sure you got at least a 400w "quality PSU tho" 400watts may be more then your gonna use, but the extra wattage will help keep the heat down and the stain on electronics.

---

### Post by starcannon on 2009-12-18
Grab some Kingston Value Ram, and a Vantec Power Supply. 
Just reiterating what has already been said, and offering up some brands that I have found to be very reliable.

GL

---

### Post by Gizenshya on 2009-12-18
As far as I can tell, everything should work together like a champ.

Either a very lucky bad pair of mobos, or a bad batch of RAM.  My money is on the RAM being bad.  I strongly suspect a quality control or tolerance issue on PQI's part.

The thing that really sucks is that that mobo doesn't also support the DDR2 standard.  That would have made troubleshooting much easier.  Everyone has at least one known good DDR2 stick around somewhere :p


The Power supplies definitely are not the problem.  If anything on a power supply is overdrawn they immediately shut down.  They usually have to be unplugged to be reset to try again (unless a fuse blows, then it must be changed), but again, this definitely is not your problem. The PSU's you chose are perfectly fine, btw.

And, as it seems you've found out, the next step is to get ahold of another set of DDR3 RAM modules.  I love Newegg for stuff like this.  They treat their customers great, even when they aren't required to.  I think they are one of the few companies in existence today that realize that they gain more from doing thins that from leaving their customers out to dry.  +1 newegg!

---

### Post by CharlesA on 2009-12-18
I'll throw my hat in with the "bad RAM" group. I had a similar problem with some gskill DDR2 1066 RAM that caused a system not to post. Had to RMA it for different brand.

I've not heard of PQI before, but then again, I usually stick with Corsair, OCZ or Kingston. (and sometimes Patriot)

---

### Post by PurposeOfReason on 2009-12-18
I'm going with RAM here, but for laughs hook up a HDD and see what happens.

---

### Post by Roasted on 2009-12-18
> **CharlesA said:**
> I'll throw my hat in with the "bad RAM" group. I had a similar problem with some gskill DDR2 1066 RAM that caused a system not to post. Had to RMA it for different brand.

I've not heard of PQI before, but then again, I usually stick with Corsair, OCZ or Kingston. (and sometimes Patriot)

I ran PQI in another system with no issues, but this was back in DDR 400 days.

I see a lot of PQI flash drives around too - also had good luck with them as well.

I'm really banking on just getting single 2gb sticks of Crucial or something.

---

### Post by Xbehave on 2009-12-18
If you think the ram is bad can't you just send it back and get it replaced? It's under warranty and all that, worst case senario they actually test the ram at their end (unlikely) and tell you it works so you end up paying 2xP&P but get known good ram (actually that's probably best case, because if the ram is from a dodge batch the replacement may be too)

---

### Post by Roasted on 2009-12-18
> **Xbehave said:**
> If you think the ram is bad can't you just send it back and get it replaced? It's under warranty and all that, worst case senario they actually test the ram at their end (unlikely) and tell you it works so you end up paying 2xP&P but get known good ram (actually that's probably best case, because if the ram is from a dodge batch the replacement may be too)

Thing is I've heard people say that they had bad luck with certain brands of RAM in general. I RMA'd the PQI RAM and ordered Crucial - which Biostar confirmed they have the least amount of issues with Crucial/OCZ/Gskill/Kingston.

---

### Post by alphaniner on 2009-12-18
Do you get any beep codes when you power on?  If you have RAM issues you should get some beeps.  Try without and RAM if you haven't already.  If you don't get beeps then, I'd say something is definitely wrong with the mobo.

The only other things I can suggest are resetting CMOS with the jumper, and/or going all the way and popping out the CMOS battery.  If you try this you should remove the graphics card and connect to the onboard video.

---

### Post by Roasted on 2009-12-19
> **alphaniner said:**
> Do you get any beep codes when you power on?  If you have RAM issues you should get some beeps.  Try without and RAM if you haven't already.  If you don't get beeps then, I'd say something is definitely wrong with the mobo.

The only other things I can suggest are resetting CMOS with the jumper, and/or going all the way and popping out the CMOS battery.  If you try this you should remove the graphics card and connect to the onboard video.

Yep. I did ALL of that on BOTH boards. I'm running onboard video so the graphics card is out of the picture. I DO get beeps with the RAM out, but I never get anything with the RAM in. It doesn't POST or anything. Both systems do this.

I think I mentioned, there were only 2 reviews of that RAM, 1 of them being "This RAM simply did not work on my MSI board." Yet this person got another brand, same type (DDR3 1066) and it worked fine in their MSI board. So I guess it's possible for RAM to be insanely picky like that. *shrug* I have no idea what else it could be.

I called Biostar and they spoke highly of a few brands, including Crucial, so I grabbed 2 (2gb) sticks of Crucial. We'll see how it goes!

---

### Post by CharlesA on 2009-12-19
> **alphaniner said:**
> Do you get any beep codes when you power on?  If you have RAM issues you should get some beeps.  Try without and RAM if you haven't already.  If you don't get beeps then, I'd say something is definitely wrong with the mobo.

I had a similar thing happen with an Abit mobo that didn't like some Patriot memory that I got. It just wouldn't post, no beep codes, nothing. Popped in some OCZ and it worked fine. I still don't know if it didn't like the Patriot RAM since that RAM worked with 2 other systems, but didn't have any timings listed. *shrugs*

> **Roasted said:**
> Yep. I did ALL of that on BOTH boards. I'm running onboard video so the graphics card is out of the picture. I DO get beeps with the RAM out, but I never get anything with the RAM in. It doesn't POST or anything. Both systems do this.

That's what one of my systems did, I'm not sure about the other 3 cuz I don't want to mess with them. :P

> I think I mentioned, there were only 2 reviews of that RAM, 1 of them being "This RAM simply did not work on my MSI board." Yet this person got another brand, same type (DDR3 1066) and it worked fine in their MSI board. So I guess it's possible for RAM to be insanely picky like that. *shrug* I have no idea what else it could be.

Could be. I'm guessing that it's deactivated since there was a problem with them. Only newegg knows for sure why tho.

> I called Biostar and they spoke highly of a few brands, including Crucial, so I grabbed 2 (2gb) sticks of Crucial. We'll see how it goes!

Whenever I go to buy memory for any new machines I build, I check the mobo manufactuer's website to see what RAM and CPU are compatible with the mobo. It's not always going to help, but it'll give you some ideas.

---

### Post by Roasted on 2009-12-19
> **CharlesA said:**
> 
Whenever I go to buy memory for any new machines I build, I check the mobo manufactuer's website to see what RAM and CPU are compatible with the mobo. It's not always going to help, but it'll give you some ideas.

Yeah man, I hear that. The guy I talked to said he didn't have any solid documentation in terms of "this exact memory worked with this board" but he did tell me about brands that were the least problematic.

He didn't seem familiar with PQI. He heard of the brand, but didn't hear enough good OR bad about their RAM with Biostar boards, so I went with the "well these are the least problematic brands" picked a good priced one and ran with it.

The RAM is already in the next state over. We'll see if that solves my problem.

---

### Post by CharlesA on 2009-12-19
Hope it does. Good luck!

Figured I'd throw this out there. If I do have problem with memory, I tend to return it (since I usually buy computer junk online from newegg or amazon) and buy it at a B&M store (so I save on shipping, and it's easier to return if it turns out it wasn't the memory)

---

### Post by happyhamster on 2009-12-19
Reminds me of a system I built a month ago: same processor (Athlon 245), AM2+ motherboard (not AM3) but with same chipset (a Gigabyte GA-MA785GM-US2H board). Result was the same: the board wouldn't boot, although the fans were spinning, etc. In the end it turned out that the board was pretty picky about the PSU. First one I used was a good (albeit somewhat older) Antec PSU. It also didn't boot with any of the crappy spare OEM PSU's I had lying around. It did boot with a Corsair VX450W or a Seasonic S12-380 though, both of which are good, solid PSU's.

Good luck with your build.

---

### Post by Roasted on 2009-12-19
> **happyhamster said:**
> Reminds me of a system I built a month ago: same processor (Athlon 245), AM2+ motherboard (not AM3) but with same chipset (a Gigabyte GA-MA785GM-US2H board). Result was the same: the board wouldn't boot, although the fans were spinning, etc. In the end it turned out that the board was pretty picky about the PSU. First one I used was a good (albeit somewhat older) Antec PSU. It also didn't boot with any of the crappy spare OEM PSU's I had lying around. It did boot with a Corsair VX450W or a Seasonic S12-380 though, both of which are good, solid PSU's.

Good luck with your build.

Did you pull the RAM and boot it? Did it beep over and over?

I mean, I don't know. Anything is possible. I just think it's stupid on how picky certain parts can be. Oh I work with this RAM but not this RAM. This PSU but not that PSU.

Although I'm not betting it's the PSU, I know it's still a very small possibility. Four power supplies (2 were identical, so 3 different power supplies) all failed - yet worked on other all other systems I tried. If it's going to come down to me having this kind of headache to build -any- system because some parts play nice while others don't, then next time my *** is hitting up dell.com before I go off building custom rigs again. And uh - I don't want that to happen! :lolflag:

---

### Post by alphaniner on 2009-12-19
According to the manual, the board has a pair of LEDs for diagnosing basic problems:

[IMG]http://i969.photobucket.com/albums/ae180/tomatocatsup/Untitled3.png[/IMG]

What code do you get?

---

### Post by Roasted on 2009-12-19
On the right where PH1, PH2, PH3 are - they're all solidly lit up.

LED 1 - Flashing on/off in a steady fashion.
LED 2 - OFF

I see that LED 1 - ON/LED 2 - OFF = memory error. But my LED 1 is flashing. Would the LED's on the right side (PH1, PH2, PH3) being all solid and lit up be an indicator that I am getting proper power to the board? Is this indication of a memory error?

Thank you for finding the code for me. That's a start.

---

### Post by john_spiral on 2009-12-19
back to basics:

boot off the Ubuntu CD, choose the option to test RAM/memory run overnight

viola, ram tested.

---

### Post by Roasted on 2009-12-19
> **john_spiral said:**
> back to basics:

boot off the Ubuntu CD, choose the option to test RAM/memory run overnight

viola, ram tested.

Can't. I never get any video output to even select "Boot to CD".

See my frustrations now?

---

### Post by happyhamster on 2009-12-19
> **Roasted said:**
> Did you pull the RAM and boot it? Did it beep over and over?
Didn't test that.

> 
I mean, I don't know. Anything is possible. I just think it's stupid on how picky certain parts can be. Oh I work with this RAM but not this RAM. This PSU but not that PSU.
Yeah, it can be a pain. Best you can find on the net are people describing working configurations I guess. Next best thing are reviews of the single parts.

> 
I see that LED 1 - ON/LED 2 - OFF = memory error. But my LED 1 is flashing. Would the LED's on the right side (PH1, PH2, PH3) being all solid and lit up be an indicator that I am getting proper power to the board?
Yes, very likely. There's still the odd chance that the PSU isn't correctly communicating with the motherboard (power might be fine, but perhaps the motherboard doesn't properly receive the signal that that's the case).

> 
 Is this indication of a memory error?
The manual doesn't say anything, and perhaps because of:
> 
I contacted support asking them what that meant. They didn't know. They said (Quote),"The LED is a guide, at this moment the flashing is not a normal error report, so that is why it’s not on the book."
[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16813138143](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16813138143)

Let's hope the new memory will do the trick. Good luck.

---

### Post by Roasted on 2009-12-19
> **happyhamster said:**
> 

I contacted support asking them what that meant. They didn't know. They said (Quote),"The LED is a guide, at this moment the flashing is not a normal error report, so that is why it’s not on the book."

So ultimately, what do you assume this to mean in regard to my issue?

Do you believe the flashing is not normal is being caused by a faulty board? Or is the RAM still a safe bet?

I just wasn't sure how to take that when it was noted as the flashing is not a normal error report.

---

### Post by Skripka on 2009-12-19
> **Roasted said:**
> So ultimately, what do you assume this to mean in regard to my issue?

Do you believe the flashing is not normal is being caused by a faulty board? Or is the RAM still a safe bet?

I just wasn't sure how to take that when it was noted as the flashing is not a normal error report.

If new RAM doesn't fix you up (gawd forbid)....

Call BioStar, if they are clueless (still) and then NewEgg.   Call NewEgg, and ask one of their guys what the best course is....It seems to my quite unlikely nowadays to get 2 lemons in the same shipment of the same part, and quite frankly these things should just work.  Doesn't matter what the warranty by NewEgg at time of sale was, call them anyway and they should do you right.

You may have 2 dead boards (if the RAM doesn't work) ...in any case I'd probably RMA the boards (either refund, or credit to different or same new boards), and ask NewEgg what to do with the spare DDR3 you won't really need (either keep as a test for the time being, or RMA).  Then you have to decide whether to try again at the same mainboard, or go to a different brand.

The hassle sucks, especially trying to meet an Xmas deadline.

---

### Post by happyhamster on 2009-12-19
> **Roasted said:**
> So ultimately, what do you assume this to mean in regard to my issue?

Do you believe the flashing is not normal is being caused by a faulty board? Or is the RAM still a safe bet?

I just wasn't sure how to take that when it was noted as the flashing is not a normal error report.
Sorry, I was just commenting on the lack of info in the manual, I didn't mean to worry you. It just means that an error is reported, but Biostar appears not to know what's wrong, or perhaps AMI, the BIOS's author, chose that code for "unknown error" or such.

Anyway, spinning fans, lit LEDS, error-feedback, and a beeping speaker (when removing memory) are all indications of a functioning motherboard. I would say: first test the new RAM before worrying any further.

---

### Post by gn2 on 2009-12-19
This is why I like to buy hardware from my local PC shop.
Last time i had a RAM issue like this I got it swapped over the counter immediately and the problem was fixed in a matter of minutes.
The problem was that although the RAM was perfectly OK, it just wouldn't work in the motherboard, a change to a different brand did the trick.
Local shop is slightly more expensive, but the service is outstanding.

Shameless plug: [Everest-tech Aberdeen]("http://www.etstore.co.uk/index.asp").

---

### Post by Roasted on 2009-12-20
> **gn2 said:**
> This is why I like to buy hardware from my local PC shop.
Last time i had a RAM issue like this I got it swapped over the counter immediately and the problem was fixed in a matter of minutes.
The problem was that although the RAM was perfectly OK, it just wouldn't work in the motherboard, a change to a different brand did the trick.
Local shop is slightly more expensive, but the service is outstanding.

Shameless plug: [Everest-tech Aberdeen]("http://www.etstore.co.uk/index.asp").

The only "computer shops" in my area are Staples and Best Buy.

I'm sorry - but I'll wait 2 months to get my parts in before I pay double to buy them local instead of online. If it was an actual computer shop that perhaps had competition with decent prices, I'd be all about that. But Staples and Best Buy really leave me no choice.

---

### Post by Roasted on 2009-12-22
RAM was supposed to be delivered yesterday. Didn't get it. I know those poor guys are working around the clock, but I was really bummed cause it diminished any chances of me being able to 2 day/overnight anything else from tuesday on if the RAM wasn't it.

So here I am, at 7:40 moping around like damnit, damnit, damnit, tuesday is almost gone, now what if I have to wait till tomorrow and the RAM doesn't work? Gahhh...

I'm upstairs in the kitchen, someone knocks on the door. By the time I open it, the UPS guy is already hopping back in the truck. I yelled out thank you and he waved his hand. I could tell he was in a rush. Poor guy probably trying to unload the truck while the wife is on his cell like WHERE ARE YOU!?!? 

Alas, the RAM. Weeee. I come down, plug it in, fire up the motherboard... nothing.

GAHHHHHHHHHHHHH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I was about to kill. Then I heard a POST beep. LOLOL IT WORKED.

:guitar::guitar::guitar::guitar::guitar:

---

### Post by CharlesA on 2009-12-22
That's awesome! Glad you got it working.

---

### Post by Exodist on 2009-12-22
LOL glad its working :-)

---

### Post by MooPi on 2009-12-22
[B]Merry Christmas !!!!!!!!
[/B]Man you are a nice brother.

---

### Post by happyhamster on 2009-12-22
Oooh great! Congrats :)

---

### Post by Roasted on 2009-12-22
> **MooPi said:**
> [B]Merry Christmas !!!!!!!!
[/B]Man you are a nice brother.

It's not just me. My parents are chipping in too. It's "our" gift to both of my brothers.

One is graduating HS and going to commute to a college around here, and the other will be a junior. It's just at the point where it makes sense for them to have computers newer than 10 years old - which is what they currently run.

So take that into account plus the fact all 3 of us had no clue what to get them. Figured we'd dish out and make it work as a gift from me + parents.

I'm giving them a nice surprise. I'm dual booting these hizzies. :P XP Pro SP3 and Kubuntu 9.10. :guitar:

---

### Post by Gizenshya on 2009-12-22
Congrats!  gald it got working before Christimas.  Now you have a story as well :)

What ever happened with that PQI RAM?  refund?  Did newegg trade it out with what you got?  (just curious)

XP-SP3 is the best Windows/proprietary OS by far, IMO.  Great choice.

Ditto for Kubuntu, btw ;)  Well, the Ubuntu part of it, anyway.  I've never really used KDE :p  (at least, not in the last several years.  perhaps I should give it a good whirl...)

---

### Post by Roasted on 2009-12-22
> **Gizenshya said:**
> Congrats!  gald it got working before Christimas.  Now you have a story as well :)

What ever happened with that PQI RAM?  refund?  Did newegg trade it out with what you got?  (just curious)

XP-SP3 is the best Windows/proprietary OS by far, IMO.  Great choice.

Ditto for Kubuntu, btw ;)  Well, the Ubuntu part of it, anyway.  I've never really used KDE :p  (at least, not in the last several years.  perhaps I should give it a good whirl...)

NewEgg can only refund for cash, or replace for like products. So they couldn't swap out the PQI RAM for Crucial or anything else. To do that, I had to return the PQI RAM for a refund and re-order the Crucial RAM. No big deal, it got the job done. NewEgg was gracious enough to waive all additional charges (restock, etc) considering the nature of the problem. i.e. - it wasn't user error (I got the right stuff) but it just simply didn't work.

XP SP3 is what they currently run, but their systems can barely ka-chunk it along. They're gamers, so they game as much as they can and tolerate the slow performance. Even Ultima Online, which is an online 2d RPG game from the late 90s pegs their processors to 100%.

About Kubuntu - yeah, I've been a long time Gnome user. But I tried out KDE and, man, KDE is really solid. Pretty much everything I was told about it (it's bloated, it's slow, etc) was the exact opposite. As the story goes, 4.0 was so-so, nice but some bugs, 4.1 small fixes, 4.2+ complete overhaul. Running 4.3.2 and it's solid. In fact, on a fresh boot it uses less RAM on my system than Gnome does. LoL?? 

But anyway, some people drive Camaros, others drive Firebirds. At the end of the day, we'll still have a good time at the track.

---

### Post by alphaniner on 2009-12-22
grats!

---

