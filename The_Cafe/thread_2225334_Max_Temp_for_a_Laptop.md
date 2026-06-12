---
title: "Max Temp for a Laptop"
date: 2014-05-21
forum: The Cafe
---

### Post by user1397 on 2014-05-21
So I have this exact processor: [http://products.amd.com/en-us/NotebookAPUDetail.aspx?id=71](http://products.amd.com/en-us/NotebookAPUDetail.aspx?id=71)

Notice the max temp says 105 C.
 
I'm on windows 8 and it normally runs around 95 C I think, but when I play certain games (namely lotro, even on lowest settings) it goes up to 120 C.  This seems abnormally high to me.

Am I risking damaging my internal components at these temperatures?  I run this laptop inside the house, sitting on a glass table, normally with A/C on in the room.

Note: I used speccy and hwmonitor on windows to check my temps.

---

### Post by mastablasta on 2014-05-21
it will turn itself off if it runs too hot. 

this does seem a bit high for silicon based chip. you could try cleaning the vents.

you can also use speed fan in windows or something like that to adjust fan speed and monitor temperature.

---

### Post by deadflowr on 2014-05-21
Those seems more closer to what the Fahrenheit readings would be.

Are the machine's fans loud, or normal acting?
I ask because I would expect the fans to be running at full-throttle with temps that high.
It would be noticeable.

---

### Post by user1397 on 2014-05-21
> **mastablasta said:**
> it will turn itself off if it runs too hot. 

this does seem a bit high for silicon based chip. you could try cleaning the vents.

you can also use speed fan in windows or something like that to adjust fan speed and monitor temperature.i do use an air duster to clean the fans out from the outside once in a while, maybe i need to do it more often.  i will check out speedfan, didn't know you could do that.

> **deadflowr said:**
> Those seems more closer to what the Fahrenheit readings would be.

Are the machine's fans loud, or normal acting?
I ask because I would expect the fans to be running at full-throttle with temps that high.
It would be noticeable.
the fans seem to be at full throttle when it's this hot.  they are definitely loud, but not like annoying loud (idk, maybe i'm just hard to annoy? hehe)

---

### Post by LastDino on 2014-05-21
Is there any particular area on that lappy that gets extremely hot? Check that by physically touching your lappy's back-side. If that is indeed ''C'', I would say that the software you're using to get those readings is likely to be faulty.  Generally in BIOS, machine is set to shutdown at certain temperature thresholds and what you're listing is way above it.

---

### Post by mastablasta on 2014-05-21
> **ubuntuman001 said:**
> i do use an air duster to clean the fans out from the outside once in a while, maybe i need to do it more often. i will check out speedfan, didn't know you could do that.


if it's overheating and not turning off you would also experience some strange behaviour (crashes, frezes...).

instead of air duster you could try compressed air (valuum clenar if you can access fan to stop the blades. but vacuum clener has to be used in short bursts to avoid generating static electricity. 

then in desktop thermal paste can be re-applied. 

my bro had a real overheating. no matter what he did didn't solve it in the end he replaced the whole cooler and that helped a lot. i thought those coolers can't get "used up" since it's a block of metal. strange that...

---

### Post by user1397 on 2014-05-21
> **LastDino said:**
> Is there any particular area on that lappy that gets extremely hot? Check that by physically touching your lappy's back-side. If that is indeed ''C'', I would say that the software you're using to get those readings is likely to be faulty.  Generally in BIOS, machine is set to shutdown at certain temperature thresholds and what you're listing is way above it.it gets really hot only in the middle to right area on the top of the keyboard next to the screen.  not really anywhere else.i tried two different programs and they both said the same temps (i tried speccy and hwmonitor)

> **mastablasta said:**
> if it's overheating and not turning off you would also experience some strange behaviour (crashes, frezes...).

instead of air duster you could try compressed air (valuum clenar if you can access fan to stop the blades. but vacuum clener has to be used in short bursts to avoid generating static electricity. 

then in desktop thermal paste can be re-applied. 

my bro had a real overheating. no matter what he did didn't solve it in the end he replaced the whole cooler and that helped a lot. i thought those coolers can't get "used up" since it's a block of metal. strange that...isn't an air duster technically compressed air?  anyway it's a laptop so i can't really get into it as far as thermal pastes/coolers

---

### Post by LastDino on 2014-05-22
Is the behaviour consistent with other OS? You can try one or two other than W8 to see if it is OS problem or not. You can also have a look at your hardware configuration guide (either hard-copy you might have received or online) to see which chip is located there and narrow down the suspects. Just because it is noted as CPU temp it doesn't necessarily mean that; that is where the problem lies, I've had an instance when ICH7 chip on Giga mobo getting malfunctioned and in tern, increasing the temperature of whole system. You should also check settings in BIOS which turn off the system when certain threshold of temperature is reached, see what is it set to and consult accordingly.

---

### Post by LastDino on 2014-05-22
And just to satisfy my doubt about it being in Celsius, could you attach a screen-shot?

---

### Post by pqwoerituytrueiwoq on 2014-05-22
a apu will run a bit wormer than a normal cpu cause of the gpu
with every apu desktop i have setup the cpu temperature is way off in linux

---

### Post by user1397 on 2014-05-23
> **LastDino said:**
> Is the behaviour consistent with other OS? You can try one or two other than W8 to see if it is OS problem or not. You can also have a look at your hardware configuration guide (either hard-copy you might have received or online) to see which chip is located there and narrow down the suspects. Just because it is noted as CPU temp it doesn't necessarily mean that; that is where the problem lies, I've had an instance when ICH7 chip on Giga mobo getting malfunctioned and in tern, increasing the temperature of whole system. You should also check settings in BIOS which turn off the system when certain threshold of temperature is reached, see what is it set to and consult accordingly.I haven't tried other OS's because I havent installed any others yet.  Yea not sure how to find what components exactly are there, never seen that before in any user manual for a laptop, but I'm sure if i tried hard enough i could maybe find the schematics.  Not sure about the BIOS settings, I'll have a look.

> **LastDino said:**
> And just to satisfy my doubt about it being in Celsius, could you attach a screen-shot?I attached a screenshot of the normal temps, I will try to add one later while I am running that game.

> **pqwoerituytrueiwoq said:**
> a apu will run a bit wormer than a normal cpu cause of the gpu
with every apu desktop i have setup the cpu temperature is way off in linuxwell good to know, maybe it's just the way it is and i shouldn't worry too much.  still, seems a bit too high, therefore i am worried hehe

---

### Post by RichardET on 2014-05-23
I have a Lenovo B590 with an i3;  fan is almost never heard with Ubuntu, and this is a very cheap laptop.  I doubt that the OS is causing any issues, it must be the hardware design.

---

### Post by user1397 on 2014-08-14
Just as a follow up, I stopped playing that game anyway (got bored of it), and bought one of those laptop cooling pads just as a precaution.  I haven't seen it get that hot in a while now so I guess it's ok.  

I'm thinking it's probably a lot to do with the fact that it's a regular AMD laptop processor, not one of those ultra low powered ones, especially the intel core i series that consume so little power.   But oh well, it was worth the money.

---

