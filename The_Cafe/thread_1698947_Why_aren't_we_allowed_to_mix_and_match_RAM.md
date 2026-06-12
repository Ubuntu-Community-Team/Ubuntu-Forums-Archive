---
title: "Why aren't we allowed to mix and match RAM?"
date: 2011-03-03
forum: The Cafe
---

### Post by brawnypandora0 on 2011-03-03
I've been using 256MB SDRAM for the last ten years. My motherboard slot has DDR1 slots, but I don't understand why my motherboard manual says installing a DDR1 RAM stick alongside SDRAM is forbidden?

---

### Post by maqtanim on 2011-03-03
At first glance, I thought you are saying that Ubuntu is prevented you not to use the RAMs! :lolflag:

---

### Post by HereInOz on 2011-03-03
It sounds a little like you may have one of those rare old boards which have both SD and DDR slots.  If this is the case, then it is usually not possible to mix the RAM, due to the different speeds, and the way that the operating system addresses the different types of RAM.

So it is either one or the other.  It was the same with the even older boards which had both EDO and SD slots in them.  It was one or the other, not a mix of both, for the same reasons.

Hope this helps.

---

### Post by brawnypandora0 on 2011-06-10
> **HereInOz said:**
> It sounds a little like you may have one of those rare old boards which have both SD and DDR slots.  If this is the case, then it is usually not possible to mix the RAM, due to the different speeds, and the way that the operating system addresses the different types of RAM.

So it is either one or the other.  It was the same with the even older boards which had both EDO and SD slots in them.  It was one or the other, not a mix of both, for the same reasons.

Hope this helps.

What about mixing and matching DDR1 and DDR3?

---

### Post by Paqman on 2011-06-10
> **brawnypandora0 said:**
> What about mixing and matching DDR1 and DDR3?

I don't think there would be any board that could accept DDR1 and DDR3. I've got one that does DDR2 and DDR3. No mixing and matching allowed.

---

### Post by forrestcupp on 2011-06-10
The only thing you can usually mix and match are different speeds of the same kind of RAM. Then, if your motherboard can handle that, it usually defaults all of the RAM to the slowest speed.

---

### Post by 3Miro on 2011-06-10
Current hardware is very sensitive to RAM speed. Even small deviations can make the entire system unstable. Hence you can only use the same type of RAM running at the same speed and it is recommended that you use the same manufacturers as different models can have slight variations.

---

### Post by LowSky on 2011-06-11
I always like when people ask questions like these. They are like the questions people ask about car parts, for example, "Why can't I use the same oil filter on my Golf that's on my sister's Accord."
Here is why you cannot mix and match. Apart from significant speed differences, or running in dual or triple channel modes. The picture says it all
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Desktop_DDR_Memory_Comparison.svg/511px-Desktop_DDR_Memory_Comparison.svg.png[/IMG]

---

### Post by Bandit on 2011-06-11
> **brawnypandora0 said:**
> I've been using 256MB SDRAM for the last ten years. My motherboard slot has DDR1 slots, but I don't understand why my motherboard manual says installing a DDR1 RAM stick alongside SDRAM is forbidden?

Best way I can put it is it would be like putting a V6 ignition on a V8 engine.. The timing wouldnt work, never mind the speed and the fact it wouldnt fit. But even if your mother board magically had both slots, you would get memory issues. 

I guess it would be possible if the board had 2 separate memory controllers. But that is unlikely.

---

### Post by slooksterpsv on 2011-06-11
Yeah I can understand not mixing types like DDR1 with SDRAM or DDR2 with DDR3, but I used to always hear you want to install same size pairs and not one bigger than the other - yet I've never had any issues and some computers come out that way. The only thing I could get from it is with RDRAM you HAD to install it in PAIRS of the SAME SIZE.

Other than that, no stability issues, nothing, but that's the only mixing I do.

---

### Post by Macskeeball on 2011-06-11
> **slooksterpsv said:**
> Yeah I can understand not mixing types like DDR1 with SDRAM or DDR2 with DDR3, but I used to always hear you want to install same size pairs and not one bigger than the other - yet I've never had any issues and some computers come out that way. The only thing I could get from it is with RDRAM you HAD to install it in PAIRS of the SAME SIZE.

Other than that, no stability issues, nothing, but that's the only mixing I do.

I've read that in a certain kind of system (dual channel, I think?) mixing different sizes can hurt performance.

---

### Post by Bandit on 2011-06-11
> **slooksterpsv said:**
> Yeah I can understand not mixing types like DDR1 with SDRAM or DDR2 with DDR3, but I used to always hear you want to install same size pairs and not one bigger than the other - yet I've never had any issues and some computers come out that way. The only thing I could get from it is with RDRAM you HAD to install it in PAIRS of the SAME SIZE.

Other than that, no stability issues, nothing, but that's the only mixing I do.

Well if its the same memory standard you can interchange them for the most part. Some mother boards are picky, some dont seem to care.

But yea you can have say a 1GB chip in one slot and a 512k in another. You can also have a DDR400 chip in one slot and a DDR333 in another. Now if you do put a slower chip in like the DDR333, the system will drop the DDR400 chip down to 333speeds. 

One reason it is recommend to keep matching pairs is for example like my computer that have 4 matching sticks (2 pairs) of DDR2-800. This is because my motherboard support Dual Channel. Thus letting me get twice the bandwidth from my memory and to use Dual Channel you must have matching sticks with same timing, capacity, speed. Which is why you should by them in pairs shipped that way from the factory. If I was to replace one chip that wasnt the same specs, the system would fall back to single channel and my speed would QQ a lot..

---

### Post by slooksterpsv on 2011-06-11
> **Bandit said:**
> ...

But yea you can have say a 1GB chip in one slot and a 512k in another. You can also have a DDR400 chip in one slot and a DDR333 in another. Now if you do put a slower chip in like the DDR333, the system will drop the DDR400 chip down to 333speeds. 

...

Wow I wouldn't even install a 512k chip if I had a 1GB, not sure I'd see much change with 512k ;) hehe. Yeah I've interchanged DDR400 with DDR333, 266 doesn't work well when interchanging with 333 or 400.

---

### Post by Bandit on 2011-06-11
> **slooksterpsv said:**
> Wow I wouldn't even install a 512k chip if I had a 1GB, not sure I'd see much change with 512k ;) hehe. ...
LOL I ment MB.. Yall gota remember first computer I used only had 128k, then my tandyHX only had 256k.


I wouldnt make a effort unless performance was to bad. But if the 512MB is slower then the 1GB then I wouldnt add it, But if it was same speed I would.

---

### Post by LowSky on 2011-06-11
I'm running 12 GB in dual channel mode the board has 4 slots, 2 filled with 8gb the other two with4 gb... all the same speed at ddr3-1600

chip size doesnt matter... only frequency.

---

### Post by 3Miro on 2011-06-11
> **slooksterpsv said:**
> Yeah I can understand not mixing types like DDR1 with SDRAM or DDR2 with DDR3, but I used to always hear you want to install same size pairs and not one bigger than the other - yet I've never had any issues and some computers come out that way. The only thing I could get from it is with RDRAM you HAD to install it in PAIRS of the SAME SIZE.

Other than that, no stability issues, nothing, but that's the only mixing I do.

This is a requirement only for dual-channel. My laptop uses 2GB and 1GB for total of 3GB and it is fine.

Dual-channel is very sensitive to timing so you should use the same manufacturer and different ones may have slightly different timing and cause the whole thing to crash.

---

### Post by disabledaccount on 2011-06-11
The problem is that most of those "myths" about memory modules selection is just not important if modules are used within specs - no overclocking -> modern memory controllers are very flexible. But when modules are used on the edge of physical possibilities (overvoltage, different signal strengths, termination voltages) then everything becomes important.

So we are allowed to mix modules, because in most cases it will work. OC needs extreme care, knowledge and experience to get good results/performance

---

