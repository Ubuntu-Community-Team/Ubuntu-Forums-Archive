---
title: "Power supply question"
date: 2014-07-24
forum: The Cafe
---

### Post by waterlubber on 2014-07-24
I recently finished building a rather pleasant PC, it really shines in multitasking due to the quad-core processor. Anyhow, on the power supply, it says 550 watts. However, it also says on the rating plate "120 volts in, 10A." A small amount of extremely difficult math leads us to believe it draws a maximum of 1.21GIGAWATTS! (Just kidding, 1.2kW). Anyway, it says the efficiency is also 79%.
550 = .79x 
x = 696 watts. 
Hao? Is my power supply spec sheet a cake?

---

### Post by fkkroundabout on 2014-07-24
i was playing with one of these lately, quite fun
[http://www.eco-eye.com/graphics/ecoeye-plugin.jpg](http://www.eco-eye.com/graphics/ecoeye-plugin.jpg)

it shows you how many watts your computer - or any other electric device - is drawing at the present moment, and also if you leave it plugged for a while can tell you how many kWh you are using over time. it's a difficult kind of statistic to work out theoretically, because there are many different factors that do and do not affect how much power is drawn at once. for that reason the kWh is a more reliable measurement than just the watts measurement

found this when i was doing a little infomation searching
[http://i.imgur.com/GK6lJhz.png](http://i.imgur.com/GK6lJhz.png)
mac minis, and probably a variety of HTPCs, are extremely power efficient compared to standard desktop computers -- simply because they use laptop parts

i also found that OSX - on an unofficial and potentially inefficient AMD kernel - uses about a quarter more power than ubuntu, on the same hardware.

---

### Post by waterlubber on 2014-07-24
> **fkkroundabout said:**
> i was playing with one of these lately, quite fun
[http://www.eco-eye.com/graphics/ecoeye-plugin.jpg](http://www.eco-eye.com/graphics/ecoeye-plugin.jpg)

it shows you how many watts your computer - or any other electric device - is drawing at the present moment, and also if you leave it plugged for a while can tell you how many kWh you are using over time. it's a difficult kind of statistic to work out theoretically, because there are many different factors that do and do not affect how much power is drawn at once. for that reason the kWh is a more reliable measurement than just the watts measurement

found this when i was doing a little infomation searching
[http://i.imgur.com/GK6lJhz.png](http://i.imgur.com/GK6lJhz.png)
mac minis, and probably a variety of HTPCs, are extremely power efficient compared to standard desktop computers -- simply because they use laptop parts

i also found that OSX uses more power than ubuntu, on exactly the same hardware
OSX has fancier graphics and I assume mless optimization, there are programs out there that limit power consumption. I've seen those Ecoeye things as "WattsUp" in america. I think I'll just stick an ammeter on it and do some math, :P. I'll be careful, I'll use clip leads and stand back when I turn on the power. I dearly hope that the PSU doesn't draw more than 10A, or else it'll cook my meter.

---

### Post by Bucky Ball on 2014-07-24
Some around here have heard me bang on about this before, but the PSU is the heart of the beast. A silver box PSU just won't cut it. They are generally less than 70% efficient, good in winter as a heater, and dangerous. 

Always buy a name brand 80+ or, better still, 85+ efficiency rated (it's clearly stated on the box and specs) quality PSU that is the right size for your setup. A quality power supply rated at 85+ will not only save resources, the environment and a bit of your cash, it will outlast any silver box by a long way and will have a million and one safety switches built in, unlike its cheaper counterparts. A quality PSU may cost a little more (and not a lot more), but the benefits are multiple. 

And they are rated a lot more factually on the box and specs.

Old, but food for thought, is the section on PSUs in the last link in my signature regarding building a PC.

That's me, for what it's worth. Good luck. 

(* If your PSU has no brand name on it, switch off, take it out, recycle it or save for a spare if you need it for another machine, and head to the local PSU supplier. Antec used to have a good and realistic calculator for PSU power requirements which you might like to have a look at if still there. There should be others about. ;))

---

### Post by grahammechanical on 2014-07-24
Are you not looking at the rating for the mains power input? In the UK the mains voltage is 240 volts and a rating of 240 volts x 5 amps would = 1.2 KWatts per hour. We get the same power from half the amperes because the voltage is doubled.

 If you ever get close to drawing 550 Watts output from the power supply you will be glad that its mains input is rated far higher than its output. It needs to be higher because inefficiencies will cause a lot of the energy to be converted to heat.

The heaver the PSU, then better the quality of the build.

---

### Post by nerdtron on 2014-07-24
On 2012 I was buying cheap 550 Watt power supplies. Problem is I thought I was saving money, the first one literally smoked and melted down a power cable. Then I bought another one, which lasted only about 6 months. My computer was on almost all day almost everyday.

Finally I decided to buy a 600 Watt power supply. One that is heavier and has a bigger fan and doesn't feel any cheap. The price a bit higher but not much. Since then no issue and less heat. Peace of mind. :D

---

### Post by Bucky Ball on 2014-07-24
> **nerdtron said:**
> On 2012 I was buying cheap 550 Watt power supplies. Problem is I thought I was saving money, the first one literally smoked and melted down a power cable. Then I bought another one, which lasted only about 6 months. My computer was on almost all day almost everyday.

Finally I decided to buy a 600 Watt power supply. One that is heavier and has a bigger fan and doesn't feel any cheap. The price a bit higher but not much. Since then no issue and less heat. Peace of mind. :D

Evidencing what I outlined in my previous post. When a cheap power supply goes, it can take out some, if not all, of the components in the box, leaving the user thinking, 'Perhaps I should have spent that extra $40!'. Even worse if it blows flames out the back of the box and sets the curtains alight and burns the house down (it would not be the first time this has happened). A no brainer: buy quality, energy-efficient ticker for your machine. Just don't think about it. ;)

---

### Post by tgalati4 on 2014-07-25
It's possible that your power supply pulls 10 amps during start-up.  The capacitors fill up and can can draw a lot of current when you first power on.  Otherwise, a power meter should correspond to the ~700 watts (at full load) and ~80% efficiency.  Be sure that your uninterruptable power supply can take 1200 watts, because if you have a power drop, your power supply might draw that much in an instant.  If you simply put your PC on a 700 VA UPS, then a power drop might cause the UPS to fail and you might lose data.

---

### Post by pqwoerituytrueiwoq on 2014-07-25
120 volts in, 10A that is the main's AV voltage in the US, this is in AC
standard Wall outlets can only handle 15 amp
a quality PSU will never cost under 40 USD (before rebate), typical for a 500-600W would be 60-70 USD, if it is not a seasonic unit reasurch it before buying

---

### Post by ssam on 2014-07-28
The 10 amp, may just mean that it has a 10 amp fuse. A 5 amp fuse would be cutting it a bit fine (a PSU can often manage going over its rating for a short while). The PSU should never actually draw 10 amps.

---

