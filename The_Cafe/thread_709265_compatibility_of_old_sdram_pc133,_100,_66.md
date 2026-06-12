---
title: "compatibility of old sdram: pc133, 100, 66"
date: 2008-02-27
forum: The Cafe
---

### Post by afeasfaerw23231233 on 2008-02-27
i think it is right to post this here: i find out there's an interesting phenomenon on old box [pII, pIII] -- if you insert different brand of SDRAM with the same speed, it is very likely the speed will drop. e.g. my pIII 933mhz box have 3 stick of ram: 2 x hynix PC133 128MB and 1 x NEC[?] PC133 128MB. but if you put them together they would run at PC100. if you put only two of them they would run at pc133. would it be even better if i just install 2 of them? the trade-off is losing 1/3 memory for 1/3 faster speed. i wonder if you guys encounter similar problem

---

### Post by tnseditor on 2008-02-27
I haven't had any problem with ram speeds with the older computers I have worked with.  I am not an expert, but I would rather have more ram than faster.  Especially today I think that more ram is better.

---

### Post by koleoptero on 2008-02-27
I've had issues with sdram in the past. I had 2x128mb and when I tried to install another one (pc133 too) they just wouldn't work.

In your case though I'd go with using them all. The drop in performance will be greater if ram fills up and the system starts swapping.

---

### Post by BDNiner on 2008-02-27
I have had problems in the past with old motherboards that have 3 memory slots. You have less performance with 3 sticks installed as opposed to 2.

---

### Post by sp0nge on 2008-02-27
Greater performance in what way? And how noticable is this? I have a box with this 3rd slot and I've been thinking about filling it. I'd like to know more about how much effect (negative or positive) this could have on the machine.

---

### Post by futureproof on 2008-02-27
I know with DDRII memory that if you use both channels the overall speed of the ram drops.  I don't think many motherboards support all DIMM slots being used at full speed.  Try a google search for more answers but I'm sure it's a common thing.

---

### Post by Iam138 on 2008-02-27
Faster bandwidth does not always equal better performance. In your case the speed difference b/t PC100 and 133 is neglible (33Mhz obviously). So you gain 33MHz @ the expense of 128MB which in the case of your PIII you need all the RAM you can get as it will take load off the CPU as well as reducing the need for the system to resort to your swap which will definitely give you performance hit.

In short you will likely notice better performance by adding more MB but unlikely you'll see any difference b/t 100 & 133MHz.

---

### Post by afeasfaerw23231233 on 2008-02-29
> Faster bandwidth does not always equal better performance. In your case the speed difference b/t PC100 and 133 is neglible (33Mhz obviously). So you gain 33MHz @ the expense of 128MB which in the case of your PIII you need all the RAM you can get as it will take load off the CPU as well as reducing the need for the system to resort to your swap which will definitely give you performance hit.

In short you will likely notice better performance by adding more MB but unlikely you'll see any difference b/t 100 & 133MHz.
yes, i think so. so my mobo is now running 3 x 128MB PC133 at PC100 speed
> I know with DDRII memory that if you use both channels the overall speed of the ram drops. I don't think many motherboards support all DIMM slots being used at full speed. Try a google search for more answers but I'm sure it's a common thing.

this box is using sdram so it doesn't support dual channel, speed should not drop even i fill up all 3 slots. i am sure if i use the same brand of ram [e.g. kingston pc133 128mb x 3] then i can run at pc133. however i only have mixed brands of ram stick in hand.

---

### Post by Iam138 on 2008-02-29
> **afeasfaerw23231233 said:**
> yes, i think so. so my mobo is now running 3 x 128MB PC133 ad PC100 speed

this box is using sdram so it doesn't support dual channel, speed should not drop even i fill up all 3 slots. **i am sure if i use the same brand of ram [e.g. kingston pc133 128mb x 3] then i can run at pc133. however i only have mixed brands of ram stick in hand**.

Maybe,maybe not, some old boards will indeed reduce the bandwidth if all the slots are filled ( I had an old MSI socket A board that did the same thing). This is true even today with some boards utilizing DDR2 as mentioned by futureproof. Regardless it's always a better idea to run matched DIMMS if possible.

---

### Post by ssam on 2008-02-29
how can you tell what speed you ram is running at?

---

### Post by az on 2008-02-29
If you use only the two different branded sticks, can you still get your box to use the ram at pc100?  If so, then it would be an interesting idea to benchmark the performance with the same amount or ram but at different speeds.


Run super pi ubuntu with all combinations of two out of three sticks.  Then try with all three sticks.

Please post the result.

---

### Post by Iam138 on 2008-02-29
> **ssam said:**
> how can you tell what speed you ram is running at?

Good question. I have yet to find a way to do this in Linux despite all my googleing. I suppose he is reading the setting via BIOS or using CPU-Z in Windows.

*I can't get any of the newer versions of CPU-Z too run under Wine properly either.

> **az said:**
> If you use only the two different branded sticks, can you still get your box to use the ram at pc100?  If so, then it would be an interesting idea to benchmark the performance with the same amount or ram but at different speeds.


Run super pi ubuntu with all combinations of two out of three sticks.  Then try with all three sticks.

Please post the result.


Probably won't see a whole lot of difference in any of them as superPI is more dependent on latency rather than bandwidth.  Interesting experiment none the less.

---

### Post by forrestcupp on 2008-02-29
It depends on the motherboard.  Some mobos will run them all the right speed, and others don't work well with different brands or sticks that have a different number of chips on them.

> **Iam138 said:**
> 
In short you will likely notice better performance by adding more MB but unlikely you'll see any difference b/t 100 & 133MHz.
I agree with this.  I recently studied this out for my own purposes.  I found that having more memory at lower bandwidth is better than having less memory at a higher bandwidth.

But by all means, do what az said and benchmark both and post your results.  That would be very interesting because when I studied it out, I never found any actual benchmarks on it.

---

### Post by regomodo on 2008-02-29
same with my old motherboard

x2 pc3200 1GB -- runs at pc3200
x3 pc3200 1GB -- runs at pc2700

Found that out whilst randomly reading the manual. 2 years after i bought the board.

A bit annoying but i gave it away so i don't have to worry about that anymore

---

### Post by information_entropy on 2008-02-29
Older P3 and P4 Intel SDRAM motherboards (D815xxxx –> D845xxxx) show the configured
memory speed on the boot splash screen and/or in the BIOS setup screen.
Some boards from other manufactures (like Tyan) from this time period do the same. 

The rules are more complex that just how many sticks of memory you have.
They are based on the number of sides of memory on those sticks.

The rules for Intel boards with three memory slots are shown below.
Many other motherboards from this era followed the same rules.

```

1. If the number of SDRAM devices is greater than nine, the DIMM will be double sided.
2. Front side population / back side population indicated for SDRAM density and SDRAM organization.

NOTE: If more than four rows of 133 MHz SDRAM are populated, the BIOS will initialize installed memory up to 512 MB at 100 MHz.

When installing memory, note the following: 

Non-SPD DIMMs will always revert to a 100 MHz with 3-3-3 timing SDRAM bus. 

Mixing Non-SPD DIMMs with SPD DIMMs will always revert to a 100 MHz with 3-3-3 timing SDRAM bus. 

The BIOS will not initialize installed memory above 512 MB.

At boot, the BIOS displays a message indicating that any installed memory above 512 MB has not been initialized. 

Mixed memory speed configurations (133 and 100 MHz) will default to 100 MHz. 

133 MHz SDRAM operation requires a 133 MHz system bus frequency processor. 

The board should be populated with no more than four rows of 133 MHz SDRAM (two double-sided or one double-sided plus two single-sided DIMMs). 
100 MHz SDRAM may be populated with six rows of SDRAM (three double-sided DIMMs)

```


The rules for motherboards with four SDRAM memory slots are different.
The rules for motherboards with DDR or DDR2  memory slots are different. 

Free Advice:;-)

Used 128mb and 256mb SDRAM sticks are now so cheap that they are being sold by the pound.
If you decide to buy some from your local computer recycling center,
look for single sided modules and make sure they are SPD.

---

### Post by afeasfaerw23231233 on 2008-03-02
thanks for all of your suggestion and information. but here is the situation of my three boxes, have a look on the below if you guys have time:
box 1: P4 mobo with 768MB RAM. 1x256MB ddr266[single side] and 1x512MB ddr266[double side] . according to my motherboard manual, it has 3 slots but only support up to three banks of memory. it uses up 3 banks in 2 slots, so it runs perfectly in ddr266[pc2100], the bus speed doesn't drop.
box 2: it is an old PIII mobo. it has two ram slot and according to the user manual it support up to 4 banks of memory at the speed of pc133. i installed two sticks of ram on this board: 1x128MB PC133 [double side], 2x258MB PC133 [single side]. so it uses up 2 slot and 3 banks but it only runs at PC100 speed! according to the manual it should be running PC133!
but if i plug only one of the two, it is able to run at PC 133.
box 3: it is also an old PIII mobo. it has 3 ram slot and the manual said it supports up to 6 banks of memory with full 3 slots installed. i installed 3 stick of 128MB RAM on it: 2x128MB PC133[single side] and 1x128MB PC133 [double side]. therefore it has only used up 3 slot and 4 banks. but it only runs at PC100. if i unplug one stick of ram, it runs at PC133, how strange!
but i didn't experience incompatible ram speed isuue  in another 4 boxes, but now i do not process them.

box 4: a PII mobo with 3 sdram slots, according to the manual it supports 3 sticks of ram with maximum 6 banks at the speed of PC66. so i install three stick of PC66 128MB ram [double side] and it used up 6 banks. they run at PC66, perfect! [but i later realised that the min. speed of SDRAM is PC66, i never heard of something called PC33. unless it is EDO RAM?]  [but later this box is very unstable and hang up frequently so i sent it to the bin. i think that it's the problem of mobo but later i find out it's the problem of PSU -- one of the big cap swells. what a pity!]
box 5: a PII mobo with 3 sdram slots, according to the manual it supports 6 banks at PC100, so i install 1x128MB PC100 [double side] , 1x32MB PC100 [double side] and 1x32MB PC100 [single side]. it used up 5 banks and all ran at PC100 perfectly! [this box was unstable after a few months and i throw the mobo away. at that time i didn't know how to resolder the capacitor --- the capacitors of the mobo burst. if i could do that i may still be using this box now!]
box 6: it's a super socket 7, k6-2 mobo, it has three slots and the manual said it supports 6 banks at PC100. i installed 1x64MB PC100 [single side], 2x32MB PC100[double side], and they run perfectly at PC100
box 7: it's also a super socket 7, k6-2 mobo. it has two slots and the manual said it supports 4 banks at PC 100. i installed 2x128MB PC100 [double side] and therefore it used up full 4 banks but it ran perfectly at PC100. strange! i sent this box back to my relatives.

you may wonder why i remember all the details of the ram configuration of these old boxes. it's because everytime i finished repairing a computer i always run cpu-z and sandra to test it and save the data in a file [at that time i am still using windows and didn't install any ubuntu yet.]. my conclusion is that for those old boxes [pII, PIII, early P4, k6/-2/-3] the ram may match the max. speed randomly. but if i choose the similar type of memory --- such as single/double side, same capacity, same brand...etc, then it has a better chance to meet the max. speed. but what i got in my hand are just those extra ram obtained from unrepairable mobos.

> Older P3 and P4 Intel SDRAM motherboards (D815xxxx &#8211;> D845xxxx) show the configured
memory speed on the boot splash screen and/or in the BIOS setup screen.
Some boards from other manufactures (like Tyan) from this time period do the same.

The rules are more complex that just how many sticks of memory you have.
They are based on the number of sides of memory on those sticks.

The rules for Intel boards with three memory slots are shown below.
Many other motherboards from this era followed the same rules.
thanks for your helpful information! but it still cannot explain why my box2 and box3 cannot run PC133. their cpu have an FSB 133mHz and use not more than 4 rows. ram are SPD. why are they still running at PC100?

> Free Advice:

Used 128mb and 256mb SDRAM sticks are now so cheap that they are being sold by the pound.
If you decide to buy some from your local computer recycling center,
look for single sided modules and make sure they are SPD.
thanks for your advice but i don't wanna spend a dime on the old boxes. the price of a second hand PC133 512MB single side SDRAM is more expensive than a new DDRII800 1G. so it seems very odd to me to buy an old part with such a price.

> If you use only the two different branded sticks, can you still get your box to use the ram at pc100? If so, then it would be an interesting idea to benchmark the performance with the same amount or ram but at different speeds.
Run super pi ubuntu with all combinations of two out of three sticks. Then try with all three sticks.
Please post the result.> 
I agree with this. I recently studied this out for my own purposes. I found that having more memory at lower bandwidth is better than having less memory at a higher bandwidth.

But by all means, do what az said and benchmark both and post your results. That would be very interesting because when I studied it out, I never found any actual benchmarks on it.

i also agree with this. so i fill up the ram slots though i know it's slower. but i am a linux noob. i don't know how to find the benchmark software [though i know i may search it in this forum, but i am too lazy to do so!] And once i had finished repairing a computer, i am too lazy to pick it out and unplug a stick of ram, run the benchmark, replug and run....etc. sorry i may do this if my box need repair next time. but i hope that they won't have any problem again.
thanks for your advice agian

---

### Post by futureproof on 2008-03-06
every MB i have had displays the ram speed during post,  you might have to go into bios and turn off the splash screen/silent boot setting to get it to display everything.  you can manually set the timings too, but i wouldn't recommend it unless you know what youre doing.


Make sure the timing on the RAM is the same too.  I have tried putting DDRII 800  in 2 slots before and because one of the sticks was rated at 6-6-6-12  and one was at 5-5-5-15  it dropped the speed to the lower one.

---

