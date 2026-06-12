---
title: "Desktop on car batteries?"
date: 2008-09-07
forum: The Cafe
---

### Post by thomasyen on 2008-09-07
Just wondering about this: is it possible to convert a standard desktop machine into one that runs on car batteries?

---

### Post by desertboy on 2008-09-07
Yes, 2 ways one is a cop out and the worst way it also happens to be the easiest, get an inverter.

No. 2 replace the power supply since your power supply is converting 230v AC to 12v DC (&5V DC) it should be relatively easy to replace the power supply with a 12v dc ran one.

Monitor is probably going to be the most hassle as most run on AC but sourcing a DC one shouldn't be difficult.

Won't last long on battery power though and good chance you could knacker your car batteries (Bad source for continuous power, only designed for peek amperage.) You really want to run a desktop off batteries you need deep discharge batteries (Expensive).

---

### Post by insane_alien on 2008-09-07
its possible but you will wear out your car battery very quickly as it is designed to provide a high current and not discharge very much(only supply current for a short time).

get a marine battery, they are built for deep cycles so you can run them flat time and time again without much physical damage.

---

### Post by insane_alien on 2008-09-07
its possible but you will wear out your car battery very quickly as it is designed to provide a high current and not discharge very much(only supply current for a short time).

get a marine battery, they are built for deep cycles so you can run them flat time and time again without much physical damage.

---

### Post by intense.ego on 2008-09-07
Just get a desktop-replacement laptop.

---

### Post by jimv on 2008-09-07
Get a highly energetic hamster and place him on a hamster wheel hooked up to a small generator.  If he fails to produce enough power for your computer, you may supplement his diet with coffee or Redbull, depending on his preferences.

---

### Post by curly_ on 2008-09-07
If you're looking into a computer in your car (aka. carputer) you should look into mini-itx boards. I haven't personally made/seen one, but there is many to see on the net.

[http://mini-itx.com/projects/ice-unit/](http://mini-itx.com/projects/ice-unit/) for example.

---

### Post by thomasyen on 2008-09-16
Thanks everyone. It was just an idea that I had to set up a machine to do some number crunching at night while a solar cell recharged the battery in the day. Seem that it's a bad idea though.

---

### Post by insane_alien on 2008-09-16
its not a bad idea, i've done something similar with a laptop although it was with an exercise bike not solar cells.

all you need is a deepcycle battery, an inverter and a charger connected to your generator/solarcells. 

you could buy a UPS with sufficient capacity if you have the money which would probably save some assembly hassels.

i say go for it.

---

### Post by frank754 on 2008-10-15
This is an interesting topic and I would not discount it. For one, Curly mentioned a mini-ITX unit. I just built one of these a few weeks ago, and the power it requires is well under 200w, in the laptop range. Secondly you can build these for around $200, without monitor, keyboard, sound & mouse.
As the AC power supplies provide a final voltage of 12v DC and less, has anyone come up with a project to build a substitute drawing from a deep cycle battery alone. I would like to find this info (or design one) for ham radio use portably, and use it for my ITX computer design. I could get mobo, peripheral connectors from an old PSU, or else just "Tee in" the 12vdc via a switch at the output of the PSU to the board when not running on AC. Does this sound feasible?
Also, how about using the screen from an old trashed laptop for VGA output, would this be a daunting task (like unsoldering the video card from the motherboard, etc.) ?

---

### Post by RandomJoe on 2008-10-15
The main issue you will have is battery capacity.  Unless your desktop computer happens to be a very efficient one, it's going to take a LOT more than a single "car battery" sized battery to sustain it.

You don't want to take a lead-acid battery below 50% discharge at worst, ideally not less than 20-25% discharge especially if you are going to repeatedly do this.  You can recharge a lead-acid several thousands of times with a 20% discharge, dropping to as little as just a couple hundred if you take the thing all the way to zero.

So, figure out how much power your computer uses while crunching away (using a Kill-A-Watt meter is a good way).  Let's say you find it pulls 80W.  If you want it to run 24x7, then you'll need 80W x 24h = 1920Wh per day.  1920Wh x 5 = 9600Wh total battery capacity to stay in the upper 20%.

If you use a 12V system, 9600Wh / 12V = 800Ah battery capacity.  That's a LOT!  Most low-budget off-grid systems use golf cart batteries which are 6V 220Ah and handle cycling very well, and are relatively inexpensive.  You would need eight of those (two in series for 12V by four sets in parallel for 880Ah).

Now, you need to know how much sun you get per day.  This is not "how long it's sunny", this is "how long you will get very nearly direct full sun" which is considerably shorter.  Where I am, worst-case in winter I get just shy of 5 sun-hours per day.  This number tells us how much solar panel is required.  But battery charging is a lossy process, so you need to add some "extra watts" to account for that.  At best we're talking about 80% efficient.

1920Wh x 1.25 = 2400Wh per day required from panels
2400Wh / 5h full sun per day = 480W from panels.

Panels are are quite optimistically rated, so you'll need to adjust that number up to account.  I've seen some use a x1.5 multiplier for that, which brings us to needing 720W in panels.  You can fairly easily get 200W panels, so four of those.  I was recently looking to buy some, they're around $1,000 US so...

Oh, plus a charge controller to properly charge the batteries without overcharging them.  And all the wiring required.  And mounting for the panels. And...!

All that for an 80W 24x7 load! :eek:

It's a bit sobering - I just went through this myself (thus where I had all the info above) because I wanted to have a system other than a noisy generator to keep my fridge going during outages.

Now, if you can find a much lower powered computer, or if you only intend to run it a few hours each night, the numbers will come down considerably!

If you only run the computer 10P-7A:
80Wx9h = 720Wh
720Wh x 5 = 3600Wh / 12V = 300AH total battery bank capacity
720 x 1.25 = 900Wh from panels / 5 sun-hours = 180W in solar panels

---

### Post by gletob on 2008-10-15
@RandomJoe
Woah

---

### Post by Frak on 2008-10-15
You could do it, but it would flicker a lot.

---

### Post by zmjjmz on 2008-10-15
A Prius battery would do better.

---

