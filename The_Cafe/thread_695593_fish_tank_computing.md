---
title: "fish tank computing"
date: 2008-02-13
forum: The Cafe
---

### Post by R13120(1&lt; on 2008-02-13
A friend and I recently learned it was possible to submerge a computer in mineral oil for cooling. So seeing as we had nothing better to do, we immediately did as much research as our ADHD minds could take. 20 min later we picked up a clear plastic file box, plexi-glass and cleaned out the supply of mineral oil from 3 rite-aids 2 Wallgreens 3 Safeways and a fred meyers. (by the way people look at you funny when you buy laxative in bulk.) 

We cut the plexi-glass and made a mount for the motherboard and attached brackets so it could hang over the top and leave the pugs exposed. We filled her up with oil and it worked fine but it didn't have great circulation so we didn't have the low temp we were looking for. We got a new tank and more oil and tried again. tank 2 was a 5 gallon terrarium (my avatar pic) it worked but the Nvidia card was basically cutting the tank in 2.. bad for circulation.

So what we've got now is a 10 gallon tank that fits everything except the the hard drive and cd in it and it was starting up at 30c and leveling out at 40C 

we got a mini fridge, some plastic tubing (like you'd make a beer bong with), copper flex tubing and a fish tank pump which we later upgraded to an industrial strength pond pump. the copper tubing wraps around the freezer coils inside the fridge and meets the plastic tubing at the holes we drilled in the side of the fridge. the plastic tubing insulates better and goes to the pump and back to the tank where it blows cool oil steadily on the heat sync. 

essentially we made a radiator but we can still keep our beer cold in the fridge. and cover the coils in dry ice for maximum cooling.

any way...
the thermometer in the tank reads 30C while the thermometer in the fridge reads -10C 
BUT the CPU temp in the bios goes up to 50C so i felt around inside the tank to see what was getting warm.  It turns out the heat sync is meant for air use so it's working in reverse trapping heat on the processor and up-ing our CPU temp.

you can't just remove the heat sync because it's pressure sensitive and once that sync is gone it won't boot. <insert idea><yes you>

we have ubuntu running on it and it works fine but we want to overclock it once we've resolved the final heat issue and i have no idea how to do this. so i need to know how to overclock. and any other feed back would be nice too...
thanx.. and here are some [[COLOR="Red"]pics[/COLOR]]("http://s250.photobucket.com/albums/gg276/r1312ock/") the only ones missing are of the 3rd tank.

---

### Post by beercz on 2008-02-13
It looks "cool" :-) (sorry couldn't resist).

Can we have a bigger picture please?

---

### Post by bobbocanfly on 2008-02-13
Haha that story is brilliant. Wish i had some spare parts lying around i could make one of these with

---

### Post by Namtabmai on 2008-02-13
> **R13120(1< said:**
> 
you can't just remove the heat sync because it's pressure sensitive and once that sync is gone it won't boot. <insert idea><yes you>.

What do you mean won't boot? Most modern computers/cpus  have a safety switch off that will prevent the computer from booting if the CPU fan isn't plugged in, but I'm sure I've managed to disable this in the BIOS of a few of my computers.
I've never heard of a motherboard that only works when the pressure of the heat sink is present.

---

### Post by R13120(1&lt; on 2008-02-13
> **Namtabmai said:**
> What do you mean won't boot? Most modern computers/cpus  have a safety switch off that will prevent the computer from booting if the CPU fan isn't plugged in, but I'm sure I've managed to disable this in the BIOS of a few of my computers.
I've never heard of a motherboard that only works when the pressure of the heat sink is present.
maybe that's it then. it was explained to me in passing so i assumed that's what was meant. but the fan makes more sense. either way i'm still relieved. i thought i'd fried it when it wouldn't start up after removing the sync and fan. i'll try the switch. thanks. and i attached pics up top

---

### Post by Rhubarb on 2008-02-13
> **R13120(1< said:**
> you can't just remove the heat sync because it's pressure sensitive and once that sync is gone it won't boot. <insert idea><yes you>

There's no such thing as a pressure sensitive cpu / heatsink.
The reason why it won't boot is either because the motherboard senses no CPU fan, or more likely, that the CPU gets too hot for a brief instant and switches itself off.

I think you have a few problems, one is that the CPU heatsink is designed for the surface tension of air, not oil.
There may not be a good flow of oil passing by the heatsink.
Perhaps you could force the oil past the heatsink with suction rather than by just pumping the cooler oil in the general direction of the CPU.

You need something to take the overall heat away from the bath of oil too.  Sure the fridge helps a little, but your fridge has to dissipate around 400 Watts of heat.

Unfortunately I'm a little tired at the moment, and can't quite work out how you may achieve this (I'm sure it's possible to do).

---

### Post by solitaire on 2008-02-13
How about geting a hacksaw and take the finns off of a sutable heatsink and attach that see if you get any difference in cooling..

---

### Post by pedro_orange on 2008-02-13
Hahahaha!

Thats class mate! Nice one!

---

### Post by mozetti on 2008-02-13
> **Rhubarb said:**
> Perhaps you could force the oil past the heatsink with suction rather than by just pumping the cooler oil in the general direction of the CPU.

Just extend the tube pushing the cool oil all the way into the tank, right up to the CPU. That oughta be enough to make sure the oil around the CPU stays cool enough for a working computer.

---

### Post by dca on 2008-02-13
Just buy one of the older Alienware PCs that had the tubes filled w/ radiator fluid running to the CPU, graphics card(s), etc...

---

### Post by aaaantoine on 2008-02-13
You know, a CPU temp of 50C is actually quite good.  It's usually only considered dangerous when this temperature reaches 90C (though that's a number I learned 10 years ago, and may not still be relevant).

---

### Post by hkgonra on 2008-02-13
I sugesst you do some reading here [http://www.ocforums.com/](http://www.ocforums.com/) , it is the best place to get info on all things about overclocking.

---

### Post by R13120(1&lt; on 2008-02-26
[IMG]http://a41.ac-images.myspacecdn.com/images01/99/l_653570f87f26b6d24a031d14669040b0.jpg[/IMG]
the newest tank

---

### Post by Washer on 2008-02-26
that's just f*ing awesome.

---

### Post by Iam138 on 2008-02-26
> **aaaantoine said:**
> You know, a CPU temp of 50C is actually quite good.  It's usually only considered dangerous when this temperature reaches 90C (though that's a number I learned 10 years ago, and may not still be relevant).

It's no longer relevant. It depends on the CPU. For example 65nm K8 CPu's should not be run over 55C under load for any extended period of time. With 90nm K8 it's a bit higher most can run @ 60-65C under load without experiencing instability.  As for Intel that's the darkside and I know nothing of the darkside. *There seems to be an exception to this when cooling with oil see the link below.

> **hkgonra said:**
> I sugesst you do some reading here [http://www.ocforums.com/](http://www.ocforums.com/) , it is the best place to get info on all things about overclocking.

No it's not....There are much better forums such as overclock.net or extremeoverclocking.com.

To the OP. The guys over @ Puget Custom systems used a radiator from a water cooling set up to solve thier heat problems.  Interestingly enough their temps. were up to 88C prior to installing the radiator but amazingly the system was stable.  You might want to check it out for some ideas. [http://www.pugetsystems.com/submerged.php]("http://www.pugetsystems.com/submerged.php")

---

### Post by K.Mandla on 2008-02-26
Reminds me of the old [Project E.U.N.U.C.H. experiment]("http://totl.net/Eunuch/index.html"), although sinking a computer in mineral oil is much ... cooler. Ha! A pun! Ha! :mrgreen: :roll:

---

### Post by 3rdalbum on 2008-02-26
> **aaaantoine said:**
> You know, a CPU temp of 50C is actually quite good.

Wouldn't it depend what the CPU is? Lm-sensors says that my 65nm Core 2 Duo is running at 18 degrees under heavy load. But I don't think that's correct because the temperature in the room is 30 degrees and I just have stock cooling :-)

Lm-sensors does say that the "Aux temperature" is 34 degrees Celcius, once the computer has warmed up.

---

### Post by hhhhhx on 2008-02-26
> **K.Mandla said:**
> Reminds me of the old [Project E.U.N.U.C.H. experiment]("http://totl.net/Eunuch/index.html"), although sinking a computer in mineral oil is much ... cooler. Ha! A pun! Ha! :mrgreen: :roll:
[SIZE=5][B]247MHz! OMG! :lolflag:
[/B][/SIZE]

---

### Post by Super Jamie on 2009-02-08
haha good old project eunuch, that was so awesome back in the day

anyway, a heatsink is not necessarily made for air, it's made to withdraw heat over a small surface area (the cpu die) into a large surface area (the heatsink fins), so that heat can be carried away via convection into the substance surrounding the fins

normally this substance is air, which the cpu fan then moves away. case fans can help by drawing cooler outside air from the front of the housing, and expelling hot air out the back

so what you need to do is have a moving source of cool mineral oil passing over the heatsinks, and ideally have your point of suction back into the radiator at the point where the oil is hottest, or at least where it encourages the cold input to move towards the hot areas


by the way, for any home-built pc, do research for what the temps of your cpu and northbridge should be. amd and intel both publish a really decent amount of info on their processors. i say 60C is the max i would let a cpu go these days, and keep my hard drives under 50C

---

### Post by Thirtysixway on 2009-02-08
It would be really neat if it was water instead of oil, and you could have fish swimming around your pc :)

---

### Post by HermanAB on 2009-02-08
Hmm, I think a Google Cookie Tin computer setup with a big fan is much less messy...

Cheers,

Herman

---

### Post by Bart_D on 2009-02-08
If you're using the system for occasional computing, extensive techniques to cool the oil are probably not required.  However, if it's being used daily, then the oil simply has to be cooled.....effectively.

Something that is not clear from the pics(**YOUR CAMERA SUCKS**) is the cord running out of the power supply.  Typically, this cord is connected to a second cord which then connects to the wall socket....as opposed to directly connecting the power supply cord to the wall socket.  This is something to keep in mind if sparks are observed at some point in the future.

> **Rhubarb said:**
> ...You need something to take the overall heat away from the bath of oil too.  Sure the fridge helps a little, but your fridge has to dissipate around 400 Watts of heat.

Unfortunately I'm a little tired at the moment, and can't quite work out how you may achieve this (I'm sure it's possible to do).

The solution is the radiator.  Typically holes, the size of the radiator tubing, are drilled in the glass/plastic case to allow them to sit at the edge of the case and cool the oil.  The point of entry of the tubes would have to be sealed with epoxy to ensure that the case is leak proof.  It is highly recommended/required that Socket style CPUs be lined with epoxy...usually, a medium to large sized epoxy tube would be sufficient for a single build.

---

### Post by ArtF10 on 2009-02-08
> **R13120(1< said:**
> A friend and I recently learned it was possible to submerge a computer in mineral oil for cooling. So seeing as we had nothing better to do, we immediately did as much research as our ADHD minds could take. 20 min later we picked up a clear plastic file box, plexi-glass and cleaned out the supply of mineral oil from 3 rite-aids 2 Wallgreens 3 Safeways and a fred meyers. (by the way people look at you funny when you buy laxative in bulk.) 

We cut the plexi-glass and made a mount for the motherboard and attached brackets so it could hang over the top and leave the pugs exposed. We filled her up with oil and it worked fine but it didn't have great circulation so we didn't have the low temp we were looking for. We got a new tank and more oil and tried again. tank 2 was a 5 gallon terrarium (my avatar pic) it worked but the Nvidia card was basically cutting the tank in 2.. bad for circulation.

So what we've got now is a 10 gallon tank that fits everything except the the hard drive and cd in it and it was starting up at 30c and leveling out at 40C 

we got a mini fridge, some plastic tubing (like you'd make a beer bong with), copper flex tubing and a fish tank pump which we later upgraded to an industrial strength pond pump. the copper tubing wraps around the freezer coils inside the fridge and meets the plastic tubing at the holes we drilled in the side of the fridge. the plastic tubing insulates better and goes to the pump and back to the tank where it blows cool oil steadily on the heat sync. 

essentially we made a radiator but we can still keep our beer cold in the fridge. and cover the coils in dry ice for maximum cooling.

any way...
the thermometer in the tank reads 30C while the thermometer in the fridge reads -10C 
BUT the CPU temp in the bios goes up to 50C so i felt around inside the tank to see what was getting warm.  It turns out the heat sync is meant for air use so it's working in reverse trapping heat on the processor and up-ing our CPU temp.

you can't just remove the heat sync because it's pressure sensitive and once that sync is gone it won't boot. <insert idea><yes you>

we have ubuntu running on it and it works fine but we want to overclock it once we've resolved the final heat issue and i have no idea how to do this. so i need to know how to overclock. and any other feed back would be nice too...
thanx.. and here are some [[COLOR="Red"]pics[/COLOR]]("http://s250.photobucket.com/albums/gg276/r1312ock/") the only ones missing are of the 3rd tank.

**[SIZE="4"]Do you keep a fire extinguisher in the house at all times?[/SIZE]**

---

### Post by Paqman on 2009-02-08
> **Super Jamie said:**
> i say 60C is the max i would let a cpu go these days, and keep my hard drives under 50C

Google did a lot of research into hard drive failure modes. One of their more interesting findings was that temperature had very little effect on hard drive reliability.

([source]("http://labs.google.com/papers/disk_failures.pdf"))

---

### Post by Super Jamie on 2009-02-08
> **Paqman said:**
> Google did a lot of research into hard drive failure modes. One of their more interesting findings was that temperature had very little effect on hard drive reliability.

([source]("http://labs.google.com/papers/disk_failures.pdf"))

But they only tested to 50C, and found that in 3-4 yearold drives, a higher temperature does noticeably increase failure rate.

I've had drives hit way higher than that, to the point where the controller drops the drive off the SATA bus.

Keep them below 50, below 40 is even better.

---

### Post by handy on 2009-02-08
You guys were clearly tanked, when you came up with this slick idea. 

If the oil gets too hot you can throw a couple of pieces of fish in there to have with your chips.

Tanks for oil the memories.

I should have stopped before I started, I know. ;-)

---

### Post by Paqman on 2009-02-09
> **Super Jamie said:**
> 
Keep them below 50, below 40 is even better.

If you look at the graph Fig4 in the article, they indicate that the average temp (in a hot data centre) actually tends to a slightly higher failure rate than drives that are at the warmer end. The obvious implication being that actively cooling drives doesn't improve reliability. They're going to be under 50 unless you live on the surface of the sun anyway.

Just thought it was an interesting study anyway. It certainly dispels some of the bumf issuing from cooling manufacturers. I'd say don't waste your money on cooling drives directly and just make sure the case has decent aiflow. If your hotter components are being cooled properly you can rest assured your hard drives aren't an issue.

---

### Post by Super Jamie on 2009-02-09
However, most of us don't live in a datacenter.

I don't know about you, but it's 31C outside in Brisbane, Qld, Australia right now. My un-airconditioned house would probably be getting up to 35C inside. Couple that with a standard cheap ATX case and PC doing alot of hard-drive activity (torrenting, for example) and you'll easily hit over 60C drive temps. I know, mine were until I got an Antec P182 case.

I agree it's an interesting study, and proves that being a drive cooling nazi provides diminishing returns. But it also provides no data for temps over 50C, and for the sake of a few hundred dollars vs all my data, I think I'd rather err on the side of caution :)

---

