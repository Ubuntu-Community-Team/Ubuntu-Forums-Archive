---
title: "Nvidia card going plaid.  Advice?"
date: 2011-09-05
forum: The Cafe
---

### Post by drawkcab on 2011-09-05
Over the past week or so my 3-yr-old Nvidia 9600m GT card has taken to overheating such that the display either "goes plaid" or fails entirely.  The failure is accompanied by a high whine/whistle that sounds, well, awful.  The failure occurs both in Linux and in Windows so it is not a software/driver/settings issue. I'm worried that this problem portends a catastrophic hardware failure.  :(

My question is this:  Am I right to understand that such damage to the gpu is irreversible?  Given the fact that I need my lappy for work, should I be looking around for a replacement before it totally fails?  What has been your experience?  :confused:

Any insight you can provide would be great.  Thanks in advance.

---

### Post by cariboo on 2011-09-05
If the problem happens in both OSs, it's only a matter of time before it completely fails. Some laptops have replaceable graphics adapters,  but if you need your laptop for work, that may not be an option.

---

### Post by drawkcab on 2011-09-05
Thanks for your input cariboo.  I'm going to go fix myself a stiff drink, check my bank account, shop the labor day sales and then cry myself to sleep.

[IMG]http://owstarr.com/wp-content/uploads/2008/09/mushroom-cloud.jpg[/IMG]

---

### Post by arvevans on 2011-09-05
Similar problem here with the same chip set in a desktop computer.
Once the problem was found to be overheating, I fastened a heat sink with fan to the video chip.  Thus far (8 months) it has been stable.

---

### Post by mips on 2011-09-06
> **drawkcab said:**
> 
Any insight you can provide would be great.  Thanks in advance.

Dunno if it will help but it's worth a try.

Open the laptop up, clean out any dust etc with a paint brush and compressed air.

Remove the fan & heatsinks cleaning again. Clean off the old thermal paste with isopropyl alcohol or methelated spirits. Apply some new Arctic Silver 5 and reassemble.

You never know, it could be a cheap fix.

Another more severe option would be to strip the MB out and reflow it in your oven.

---

### Post by snip3r8 on 2011-09-06
> **drawkcab said:**
> Thanks for your input cariboo.  I'm going to go fix myself a stiff drink, check my bank account, shop the labor day sales and then cry myself to sleep.

[IMG]http://owstarr.com/wp-content/uploads/2008/09/mushroom-cloud.jpg[/IMG]

I have that exact picture on my wall which i got out of the hip2b2 magazine(which was founded by shuttleworth) ...small world

---

### Post by forrestcupp on 2011-09-06
At the very least, you need to back everything up before you're screwed. Some laptops have replaceable GPUs, but most do not. Even if you try mips' suggestion of cleaning it and replacing the heat sink paste, you still had better back everything up first.

> **mips said:**
> 
Another more severe option would be to strip the MB out and reflow it in your oven.

Ha, ha. I'm gonna have to try that!

---

### Post by Dangertux on 2011-09-06
Well for what it's worth -- there are some pretty decent deals at Best Buy if you have one near you or are willing to purchase online. 

I recently purchased a Gateway NV30xx laptop from them for less then $300. It's nothing spectacular performance wise, but if you don't have ridiculous needs for whatever work it is you do it performs pretty well.

It ran Natty out of the box just fine -- 10.04/10.10 needed a decent amount of tweaking to get 3d acceleration working properly. (AMD ATI HD3000 graphics adapter)

Network connectivity was fine out of the box on 10.04, 10.10 and 11.04 (haven't tried 11.10)

They also have an acer, a dell and a toshiba in the same price range if you're feeling adventurous. 

Hope that helps.

---

### Post by forrestcupp on 2011-09-06
> **Dangertux said:**
> 
I recently purchased a Gateway NV30xx laptop from them for less then $300. It's nothing spectacular performance wise, but if you don't have ridiculous needs for whatever work it is you do it performs pretty well.

It ran Natty out of the box just fine -- 10.04/10.10 needed a decent amount of tweaking to get 3d acceleration working properly. (AMD ATI HD3000 graphics adapter)

I recently bought a Gateway NV57H13u. I can testify that mine ran Ubuntu out of the box, too. Mine has Intel HD Graphics 3000, though, not ATI.

---

### Post by kaldor on 2011-09-06
I'm gonna be a fanboy and recommend a supported AMD Radeon card :)

---

### Post by Lucradia on 2011-09-06
The only thing you need to know about video cards, really, is the following:

AMD / ATI = Better Texture Rendering

- What this means: You can render textures faster, better, smoother, on-the-fly.

NVIDIA = Better Dynamics and Lighting and Particle Calculations

- What this means: You can do dynamics such as free-flowing hair, lights through water, along with blooming, etc. faster and easier.

Now, when do these two cards blur the line? Well, for AMD / ATI, it's still the same even with the newest 6990. However, NVIDIA's GTX 5xx+ Line now has dynamic tessellation, making it have better texture rendering, and able to handle more "Infinite Direction" dynamic rendering content.

Overall, the GTX 5xx+ Series is the way to go. If you have the money. (Note, I mentioned 5xx+ but only 560+ has dynamic tessellation, IE: Higher tier.) Unfortunately, since it's getting close to the end of the year, NVIDIA May be getting ready to release a new line-up. I suggest waiting to be honest.

Also, never get PNY. if you do, remove the plastic covering the card, it's useless, and creates a lot of heat issues.

---

### Post by drawkcab on 2011-09-06
Thanks for the tips everyone.

I've been looking at 14"-15" laptops in the $600-$800 range (lenovo has some hot labor day deals right now.)  I'd like to go with a discrete graphics card because I do have some ridiculous needs in terms of gaming (which is why I dropped a pile of cash on a 9600m gt a few years back.)

1.  The nvidia optimus hybrid graphics cards (looking at the 5xx series specifically) appear to be a bit of a nightmare in linux right now.  I am aware that the bumblebee and ironhide projects are rolling and that maybe the kernel will catch up someday but I'm not holding my breath here.

2.  We all know the recent history of ATI and its support for Linux.  I actually loved my old AMD/ATI laptop from a earlier in the decade but I'm wondering if it will become a nightmare of equal proportions.

I'm not really super confident in either of these choices.

---

### Post by drawkcab on 2011-09-06
> **mips said:**
> Dunno if it will help but it's worth a try.

Open the laptop up, clean out any dust etc with a paint brush and compressed air.

I clean it about every 3 months or so and just cleaned it again of course.  But I'm worried about the fact that the damage is already done and that I'm headed for a failure.

> **mips said:**
> Remove the fan & heatsinks cleaning again. Clean off the old thermal paste with isopropyl alcohol or methelated spirits. Apply some new Arctic Silver 5 and reassemble.

I'll probably give this a try even if I buy a new laptop.  Couldn't hurt, right?

> **mips said:**
> Another more severe option would be to strip the MB out and reflow it in your oven.

Beyond my abilities but I know this had worked for some.  At any rate the gpu is relatively stable most of the time.  It's just that once every few days it crashes, usually while I'm in the middle of something important.

---

### Post by forrestcupp on 2011-09-07
> **drawkcab said:**
> I'd like to go with a discrete graphics card because I do have some ridiculous needs in terms of gaming (which is why I dropped a pile of cash on a 9600m gt a few years back.)

Just beware that sometimes AMD puts a low end, crappy, onboard GPU in there and they call them "discrete graphics", even though they're really not. My point is, don't just go by a label that says "discrete graphics"; know what you're getting.

---

