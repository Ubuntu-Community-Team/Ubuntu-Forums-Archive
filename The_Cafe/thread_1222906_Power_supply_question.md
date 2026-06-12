---
title: "Power supply question"
date: 2009-07-25
forum: The Cafe
---

### Post by Eviltechie on 2009-07-25
I'm about to put a better video card in my computer. In order to do that, I need to upgrade my power supply. The power supply I was thinking of getting only puts out 35 amps, and the video card wants 36. Will I need to worry about that extra amp?

---

### Post by Joeb454 on 2009-07-25
It's possible. It depends if the video card will actually use that much.

What about wattage of the PSU & video card requirements (i.e. 500W etc.)

---

### Post by spoons on 2009-07-25
> **Eviltechie said:**
> I'm about to put a better video card in my computer. In order to do that, I need to upgrade my power supply. The power supply I was thinking of getting only puts out 35 amps, and the video card wants 36. Will I need to worry about that extra amp?

What is the brand of the powersupply? There should be a +3.3V, +5V and +12V. what are these values?

What is the graphics card?

---

### Post by tgalati4 on 2009-07-25
It's probably 36 watts, 36 amps is enough to run 7-10 tons of air conditioning.  Perhaps your card has a really massive heat sink.

Try running it and see what happens.  If your machine crashes after watching a video or playing an intensive game after 10 minutes then you will know that your power supply is not up to powering your video card.

---

### Post by linuxguymarshall on 2009-07-25
[http://educations.newegg.com/tool/psucalc/index.html](http://educations.newegg.com/tool/psucalc/index.html)

---

### Post by Eviltechie on 2009-07-25
This is the power supply.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817703016&Tpk=n82e16817703016](http://www.newegg.com/Product/Product.aspx?Item=N82E16817703016&Tpk=n82e16817703016)  (+3.3V@24A,+5V@24A,+12V@35A,-12V@0.8A,+5VSB@2.5A)

And this is the video card.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130433](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130433) (Minimum of a 500 Watt power supply. (Minimum recommended power supply with +12 Volt current rating of 36 Amp Amps.) Two available 6-pin Molex hard drive power dongles)  [Or something like it]

The newegg calculator said 633.

---

### Post by tgalati4 on 2009-07-25
Wow, you are correct, that is a lot of power.  A general rule of thumb is to have twice as much power as your sustained load.  This gives you 3 dB of headroom for brownouts and transient power needs.  So 633 watts is recommended by newegg and 500 watts is minimum, 800-1000 watts would give you longer service life.  1000 watts would be twice the minimum required and that would give you 3 dB of headroom.  The bigger power supply will also last longer since it's not running at maximum juice all the time.

---

### Post by spoons on 2009-07-25
That PSU should be fine. The graphics card manufacturers overstate the power needed because of the amount of rubbish PSUs out there that don't do what they state. But PC Power and Cooling is a stellar brand that will be just fine.

---

### Post by gletob on 2009-07-25
I think a 600-650 watt PSU would be fine.  to the person who said double it: that is simply overkill.

> **tgalati4 said:**
> It's probably 36 watts, 36 amps is enough to run 7-10 tons of air conditioning.  Perhaps your card has a really massive heat sink.

Try running it and see what happens.  If your machine crashes after watching a video or playing an intensive game after 10 minutes then you will know that your power supply is not up to powering your video card.

Yes a air conditer that large would draw arond 30 amps AT 480 V AC

35 Amps @ 12 V DC is very different than 35 Amps @ 480 V AC

---

### Post by Eviltechie on 2009-07-25
Well I'll take a PSU with a higher wattage if someone can find it. I have a Dell XPS 410, and Dells are a bit different.

---

### Post by tom66 on 2009-07-25
Some cheaper PSUs cannot actually be run at their rated wattage.

Also, the ratings (for things like graphics cards) are often higher than what the actual card will draw. If in doubt try it - most PSUs will cut out if you overrate them so you won't damage them (usually).

---

### Post by JHan816 on 2009-07-25
It requires (2) 6 pin PCI-E connectors from the power supply. It looks like they give you two adapters that convert two 4 pin connectors to the 6 pin PCI-E.  
 
It would use up 4 of your power connectors, but with SATA drives it should not matter.

---

