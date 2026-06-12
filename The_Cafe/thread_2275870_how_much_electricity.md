---
title: "how much electricity"
date: 2015-04-29
forum: The Cafe
---

### Post by kashei on 2015-04-29
Hi i was just wondering,  is there a way i can find out how much my computer consumes power? (watts) 

i know its possible on laptops, but how do i check on desktop???     


thanks

---

### Post by mattharris4 on 2015-04-29
Would this help?  You simply plug the device in, plug the computer through the device and run the computer like normal.  Here is a link:  [http://www.amazon.com/P3-P4400-Electricity-Usage-Monitor/dp/B00009MDBU](http://www.amazon.com/P3-P4400-Electricity-Usage-Monitor/dp/B00009MDBU)

---

### Post by tgalati4 on 2015-04-29
A Kill-a-watt is quite handy.  On a desktop computer you can research the CPU and get the TPD (total power dissipation) of the processor, for instance a older Pentium4 is about 95 watts.  There is typically a sticker on the back, near the power cord that will have the wattage, amps, and voltage that the computer is rated for.  Power = Volts * Amps * PowerFactor.  For a resistive load, PF = 1.  Desktop power supplies are typically 80 to 90% PF.

Post the specifications of your desktop and others can give you an estimate of that class of desktop.  I have several older desktops and they run 85 to 150 watts depending on the number of disk drives and the graphics card installed.  A gaming rig will burn more power than a simple email/web machine.

A RaspberryPi runs 2-4 watts.

---

### Post by Bucky Ball on 2015-04-29
*Thread moved to **The Cafe**.*

I'm thinking you would also need to consider the power consumption of your monitor. 

The PSU is everything, the heart of the machine. Work out what you are using and match that to an appropriate name brand, 80-85+ efficient, reliable PSU with long-life expectancy and plenty of safety switches. It will pay for itself.

There are plenty of  PSU calculators out there to figure out approximately what you're using. The Antec one is probably best, but offline right now. 

[http://powersupplycalculator.net/](http://powersupplycalculator.net/)
[http://www.coolermaster.outervision.com/](http://www.coolermaster.outervision.com/)

If you only watch Youtube vids, listen to music, surf the net, and check emails, don't do it with a 700watt generic silver box or any other kind of PSU (plenty do). If you are, reducing the wattage, maximizing the efficiency and extending the life of your PSU is a sure way of saving money and resources, regardless of the power your individual components are using. ;)

You could make an itemised list of the components in your box then hunt down the specs/power consumption for each online, if you have the time ...

Is there anything in the BIOS which tells how much you're using? That probably wouldn't be representative of power consumption when running Ubuntu and doing things.

---

### Post by mcduck on 2015-04-29
> **mattharris4 said:**
> Would this help?  You simply plug the device in, plug the computer through the device and run the computer like normal.  Here is a link:  [http://www.amazon.com/P3-P4400-Electricity-Usage-Monitor/dp/B00009MDBU](http://www.amazon.com/P3-P4400-Electricity-Usage-Monitor/dp/B00009MDBU)

+1 to this, the only way to get real numbers is to measure how much power the PSU is drawing from the wall.

Any software will only be able to tell you what the internal components are using, but the PSU isn't 100% efficient, and the rating on the PSU will tell how much power it can output to your components, not how much it will actually *[I]use*[/I]. (And like Bucky Ball mentioned, you might want to be able to measuer both the computer itself, and all connected devices like the display you are using...)

At least in Finland every electric company will happily borrow you a electricity usage monitor for free, don't know if they are as customer-friendly where you live but it's always worth asking... ;)

---

### Post by kashei on 2015-04-29
> **mcduck said:**
> +1 to this, the only way to get real numbers is to measure how much power the PSU is drawing from the wall.

Any software will only be able to tell you what the internal components are using, but the PSU isn't 100% efficient, and the rating on the PSU will tell how much power it can output to your components, not how much it will actually *[I]use*[/I]. (And like Bucky Ball mentioned, you might want to be able to measuer both the computer itself, and all connected devices like the display you are using...)

At least in Finland every electric company will happily borrow you a electricity usage monitor for free, don't know if they are as customer-friendly where you live but it's always worth asking... ;)

yeah....its not happening in Connecticut.....

---

### Post by kashei on 2015-04-29
i have an old dell tower 12 years old....but i change bunch things in it over time,,,,,i know video card makes a diff, ram,  how many hdd (i have 2 on it)......and i never turn it off, may be once every couple of weeks

so i just want it to know for the hell of it,  but its weird though, how come there is an app for it on laptop, but not on desk top

---

### Post by Bucky Ball on 2015-04-30
> **kashei said:**
> .....and i never turn it off, may be once every couple of weeks



Strongly advise an 85+ power supply if you don't already have one. You will definitely save some money in the long-term. Even though the machine is 12, when it eventually dies you take the PSU with you as a good one is rated to 600,000+ hours.

Don't know why there's an app for lappy and not desktop. Strange.

---

### Post by mcduck on 2015-04-30
I'd say power monitoring app on a laptop has a decent chance of telling you some real numbers, at least when the laptop is running on battery power, since you can measure what's been drawn from the battery. (When you plug it into the wall, the numbers won't be accurate any more). Adn of course running on battery power is the most important time when you'd usually want to pay attention to your power use.

However on a desktop you'll never have a closed system like that, you are _always_ drawing the power from outside of the computer. The only way to get a decent power monitoring app would be to integrate the feature in the PSU itself, to monitor the power it's drawing from the wall, and then allow the computer to read values from there.

Also the power efficiency on PSU's is not a static number, but depends on how much power is used at the time, often resulting in much lower efficiency when less power is used (meaning most of the time as you are not likely to build a desktop machine that would use the PSU to its upper limits, and then run it like that all the time). So in many cases 1000W PSU rated at 90% efficiency might actually end using more power with your computer than a 500W PSU rated for 80% efficiency, since the later one will be running closer to it's optimum level (which is also what is used when defining the efficiency rating)

---

### Post by tgalati4 on 2015-04-30
The reason there is no power application for the desktop is because the ACPI does not show a battery.  With a battery, you can measure charge and discharge rate and integrate those values over time to get total power used.  With a plugged-in PC, there is no battery to charge.  The ACPI/BIOS handles the charge and discharge of the battery and Linux can read those values.  No such data on a desktop computer.

> tgalati4@Mint17 ~ $ acpitool -B
  Battery #1     : present
    Remaining capacity : unknown, 100.0%
    Design capacity    : 4000 mA
    Last full capacity : 1946 mA, 48.65% of design capacity
    Capacity loss      : 51.35%
    Present rate       : 0 mA
    Charging state     : Full
    Battery type       : Li-ion 
    Model number       : GARDA71
    Serial number      : 1315
tgalati4@Mint17 ~ $ acpitool -B
  Battery #1     : present
    Remaining capacity : unknown, 98.51%, 00:00:00
    Design capacity    : 4000 mA
    Last full capacity : 1946 mA, 48.65% of design capacity
    Capacity loss      : 51.35%
    Present rate       : 1376 mA
    Charging state     : Discharging
    Battery type       : Li-ion 
    Model number       : GARDA71
    Serial number      : 1315


---

### Post by TheFadedBrit on 2015-04-30
Kill A Watt is a really handy tool Well done guys!

---

