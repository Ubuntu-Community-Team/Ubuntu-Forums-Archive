---
title: "Core 2 Duo and Chipsets Compatability."
date: 2007-01-14
forum: The Cafe
---

### Post by Mr..Yeti on 2007-01-14
The website where I am planning to buy parts for a computer says:
> Important: Intel's new Core 2 Duo are only compatible with Intel 975X, 965 Chipset based motherboards. Please check your motherboard for compatibility.
[http://www.eclipsecomputers.com/product.aspx?code=CPI-E6300O]("http://www.eclipsecomputers.com/product.aspx?code=CPI-E6300O")

Is that true?
What about the all the motherboards that say: > LGA 775 for Intel® Dual Core Pentium® D / Pentium® 4 / Celeron® D, supporting **Core™ 2 Duo Desktop** (Conroe), Presler and Cedar Mill processors Intel® 945G Chipset Do they not work with the Core 2 Duo?

Which people are wrong, or are the both right?

---

### Post by G Morgan on 2007-01-14
I'm typing this on a Core 2 Duo laptop that runs the Intel® 945G Chipset.

---

### Post by Mr..Yeti on 2007-01-14
That's good to know. I guess that means it should work.

Does anyone know if they changed the processors recently?

---

### Post by Mr..Yeti on 2007-01-15
That one sentence is starting to worry me. Could someone put my mind at rest? :-? 

Will the **[Asrock ConRoe945G-DVI]("http://www.eclipsecomputers.com/product.aspx?code=MBA-CR945G")**
work with the **[Intel Core 2 Duo E6300]("http://www.eclipsecomputers.com/product.aspx?code=CPI-E6300O")**?

A simple yes/no will suffice.

---

### Post by Redache on 2007-01-15
They require a Bios Update to become Core 2 Duo compatible and as such are worthless to build a Core 2 system from scratch. It's safer to stick to 975X and 965's.

---

### Post by floke on 2007-01-15
Have no idea if this helps, but I'm running a Tecra A8, core duo 945G set and it runs fine on ubuntu (apart from the sound bug - i.e. only get sound with headphones - I'm sure it's not the chipset's fault though!)

---

### Post by G Morgan on 2007-01-15
> **Redache said:**
> They require a Bios Update to become Core 2 Duo compatible and as such are worthless to build a Core 2 system from scratch. It's safer to stick to 975X and 965's.

Yeah agree here, it's not nice having a system that won't work without a bios update. I've made that mistake in the past and had to send off to get my bios chip changed. Unless they've specifically stated that it has the latest bios I'd avoid.

---

### Post by Mr..Yeti on 2007-01-15
Thanks for that guys. I'm glad you cleared that up.
I guess I'll look into some more expensive mobos then. :)

---

### Post by Redache on 2007-01-15
It's probably the reason why they do it in the first place :P.

Intel are great and all but when you tally up mobo prices it does get fairly expensive. It's why I prefer AMD, although AMD aren't amazing on certain reliability standards but I'm not going to get into that.

---

### Post by cdburgess75 on 2007-01-16
> **Steve.K said:**
> Have no idea if this helps, but I'm running a Tecra A8, core duo 945G set and it runs fine on ubuntu (apart from the sound bug - i.e. only get sound with headphones - I'm sure it's not the chipset's fault though!)

I have the same problem exactly.  Did you ever work it out?

---

### Post by Mr..Yeti on 2007-01-17
This might be an absolutely foolish question... but do you need a processor installed to upgrade your bios? I had assumed that the bios was self contained and could start itself with out anything other than power. But I might be wrong.

What parts do you need to update your bios? floppy/CD drive? Hard Disk? Processor? all? none?

---

### Post by mips on 2007-01-17
> **Mr..Yeti said:**
> This might be an absolutely foolish question... but do you need a processor installed to upgrade your bios? I had assumed that the bios was self contained and could start itself with out anything other than power. But I might be wrong.

What parts do you need to update your bios? floppy/CD drive? Hard Disk? Processor? all? none?

I suspect you will need a processor, ram, display & a media device to load the bios firmware.

If i recall correctly if you boot without cpu/ram you get no display and just a series of beeps from the MB.

---

### Post by futz on 2007-01-17
> **Mr..Yeti said:**
> That one sentence is starting to worry me. Could someone put my mind at rest? :-? 

Will the **[Asrock ConRoe945G-DVI]("http://www.eclipsecomputers.com/product.aspx?code=MBA-CR945G")**
work with the **[Intel Core 2 Duo E6300]("http://www.eclipsecomputers.com/product.aspx?code=CPI-E6300O")**?

A simple yes/no will suffice.
**[COLOR="Red"]YES![/COLOR]** **[COLOR="Lime"]YES![/COLOR]** **[COLOR="Blue"]YES![/COLOR]**

Geesh, it's got the word Conroe in the model number fer cryin out loud. Of course it will work.

Look at the specs: [http://www.asrock.com/product/ConRoe945G-DVI.htm](http://www.asrock.com/product/ConRoe945G-DVI.htm)

---

### Post by futz on 2007-01-17
> **Mr..Yeti said:**
> This might be an absolutely foolish question... but do you need a processor installed to upgrade your bios? I had assumed that the bios was self contained and could start itself with out anything other than power. But I might be wrong.

What parts do you need to update your bios? floppy/CD drive? Hard Disk? Processor? all? none?
You definitely require at least CPU, RAM, video card (or onboard) and a floppy drive (or whatever other device the mainboard may allow to contain the BIOS update image).

---

### Post by ~LoKe on 2007-01-17
> supporting Core™ 2 Duo Desktop (Conroe)
Duh? ;)

---

### Post by Mr..Yeti on 2007-01-18
[COLOR="Red"]Wait![/COLOR] [COLOR="Lime"]Wait![/COLOR] [COLOR="Blue"]Wait![/COLOR][COLOR="LemonChiffon"] (Sorry, Couldn't resist it)[/COLOR]

The **[CPU support list]("http://www.asrock.com/mb/cpu.asp?Model=ConRoe945G-DVI&s=")** says:
The E6300 works with all the Bios'
The E6300(L2) works with P1.30

The Processor product page at Eclipse says the _newer_ core 2 duos don't work on all 945 mobos. Is the E6300(L2) a _newer_ version? If i need a working processor i could not update the mobo to the newer BIOS version, and therefore it would not be compatible.

I really hope you are right, but i am not completly convinced.

---

### Post by futz on 2007-01-18
> **Mr..Yeti said:**
> [COLOR="Red"]Wait![/COLOR] [COLOR="Lime"]Wait![/COLOR] [COLOR="Blue"]Wait![/COLOR][COLOR="LemonChiffon"] (Sorry, Couldn't resist it)[/COLOR]

The **[CPU support list]("http://www.asrock.com/mb/cpu.asp?Model=ConRoe945G-DVI&s=")** says:
The E6300 works with all the Bios'
The E6300(L2) works with P1.30

The Processor product page at Eclipse says the _newer_ core 2 duos don't work on all 945 mobos. Is the E6300(L2) a _newer_ version? If i need a working processor i could not update the mobo to the newer BIOS version, and therefore it would not be compatible.

I really hope you are right, but i am not completly convinced.
I'm not aware of any "newer" Core 2 Duo CPU's. Perhaps you're thinking of the older D model dual core CPU's?

Here's Intel's chart. 
[http://indigo.intel.com/compare_cpu/default.aspx?familyID=1&culture=en-US](http://indigo.intel.com/compare_cpu/default.aspx?familyID=1&culture=en-US)

As you can see, there's only the 4 models of Core 2 Duo, the 6300, 6400, 6600 and 6700. I just checked both places I usually buy from and both of them list only those four models.

---

### Post by ~LoKe on 2007-01-18
I think the new line of E6300's have a buffed up L2 cache.

---

### Post by futz on 2007-01-18
> **~LoKe said:**
> I think the new line of E6300's have a buffed up L2 cache.
Really! Hadn't heard about that one.

I highly doubt that Asrock would ship a board specced for Core 2 Duo without knowing that and making provision for it. Mainboard manufacturers know about these changes way ahead of time. And the last thing they want is a bunch of unhappy customers returning boards because they don't work with the processor they're specced to work with.

---

### Post by ~LoKe on 2007-01-18
> **futz said:**
> Really! Hadn't heard about that one.

I highly doubt that Asrock would ship a board specced for Core 2 Duo without knowing that and making provision for it. Mainboard manufacturers know about these changes way ahead of time. And the last thing they want is a bunch of unhappy customers returning boards because they don't work with the processor they're specced to work with.

In all honesty, when I'm building computers I don't even look for "Core 2 Duo compatible", I just grab whatever Socket LGA775 board that jumps out at me.

---

### Post by futz on 2007-01-18
Ah, here is what the deal is: [http://www.legionhardware.com/document.php?id=605](http://www.legionhardware.com/document.php?id=605)
> As the year 2006 draws very close to an end, Intel will go out with the E6300, E6400, E6600 and E6700 processors representing their Core 2 Duo lineup. That said, Intel plans to greatly expand their Core 2 Duo series in 2007 by introducing at least eight new processors. Surprisingly, just two of these new processors will be clocked higher than the existing E6700. The new E6800 and E6850 processors will be clocked at 2.93GHz and 3.00GHz, while the new E6750 will still operate at 2.66GHz. The rest of the processors are simply designed to strengthen the Core 2 Duo family in numbers, rather than in performance.

The Intel Core 2 Duo E6320 and E6420 for example, are going to be alternatives to the E6300 and E6400, with the only difference being that the new versions will feature the 4MB L2 cache rather than the 2MB L2 cache. This means the E6320 and E6420 should cost a little bit more than the E6300 and E6400 given the larger L2 cache. However according to many sources, both the E6300 and E6320 will retail for just $160 US in the second quarter of 2007. 

That's a quote from Legion Hardware [http://www.legionhardware.com](http://www.legionhardware.com)  If that's correct then the 6300 doesn't change at all.

---

### Post by futz on 2007-01-18
> **Mr..Yeti said:**
> [COLOR="Red"]Wait![/COLOR] [COLOR="Lime"]Wait![/COLOR] [COLOR="Blue"]Wait![/COLOR][COLOR="LemonChiffon"] (Sorry, Couldn't resist it)[/COLOR]

The **[CPU support list]("http://www.asrock.com/mb/cpu.asp?Model=ConRoe945G-DVI&s=")** says:
The E6300 works with all the Bios'
The E6300(L2) works with P1.30

The Processor product page at Eclipse says the _newer_ core 2 duos don't work on all 945 mobos. Is the E6300(L2) a _newer_ version? If i need a working processor i could not update the mobo to the newer BIOS version, and therefore it would not be compatible.

I really hope you are right, but i am not completly convinced.
Hahaha! I didn't click on that CPU support list link till just now. According to that there must be a revised version of the cpu. 

Anyway, if your supplier's wholesaler has any amount of inventory turnover, they'll likely have the latest revision (with the latest BIOS) already shipping. Cheapy OEM boards like that move lots of units. You'll probably have no problems. And if it doesn't work, take it back.

Also, I'd be willing to bet that the board (with older BIOS) would fire up fine even with the newer cpu. It just might not take advantage of any new features/fixes of the new cpu until the BIOS got flashed to P1.30.

Hmm... If there is an (L2) version of the cpu available, why doesn't Intel list it? Possibly they warned manufacturers that it was coming and then  decided not to do the revision, but Asrock already had it listed on their site? Or maybe the (L2) revision is still in the pipe and is coming soon.

---

### Post by Mr..Yeti on 2007-01-18
Thank you very much guys.

Thanks for digging around to find what I couldn't.
I'll buy that soon, tell you if it works.

---

### Post by futz on 2007-01-19
> **futz said:**
> Hahaha! I didn't click on that CPU support list link till just now. According to that there must be a revised version of the cpu. 

Hmm... If there is an (L2) version of the cpu available, why doesn't Intel list it? Possibly they warned manufacturers that it was coming and then  decided not to do the revision, but Asrock already had it listed on their site? Or maybe the (L2) revision is still in the pipe and is coming soon.
Had a look at the CPU Support List for my mainboard, a Gigabyte GA-965P-DQ6. There's no mention of any alternate version of any of the four Core 2 Duo CPU's. Just the four models are listed.

At Asus' site there's the same four CPUs listed. In this list they do specify that the Core 2 Duo CPUs (all four) are revision B2. But there are only those four listed.

I think Asrock's list is bogus. Maybe typed up by someone in Taiwan who doesn't read English spec sheets so good?

---

### Post by MarkieB on 2007-10-12
no longer participating in ubuntuforums.org

---

