---
title: "Laptop energy consumption"
date: 2008-01-06
forum: The Cafe
---

### Post by cknight on 2008-01-06
I'm a recent convert to using a laptop which I'm loving, if only because its specs are better than my desktops.  Anyway, I'm trying to be more green yet I love leaving my computer on all day for my frequent but short access sessions.  With boot times around 1 1/2 minutes, its a bit of a drag booting up every hour or so for a quick minute or two surfing.

So, my question is:
1) How much energy does a relatively mediocre spec'd laptop use, especially in comparison to my low spec desktop?  (no fancy graphics cards, etc in either)

Bear in mind that when I leave either laptop or desktop running I turn the monitor off completely.

How would such energy consumption compare to a 60/100 watt standard incandescent light bulb?

Thanks!

---

### Post by Tmi on 2008-01-06
> **cknight said:**
> How would such energy consumption compare to a 60/100 watt standard incandescent light bulb?

I'm not really sure at all, but I'd guess that a laptop idling with the lid closed would not exceed 60W.

---

### Post by barbedsaber on 2008-01-06
I think your average laptop uses about 10% of the power of  your average desktop.

---

### Post by gn2 on 2008-01-06
Depends on the hardware in the laptop.

I would expect that idling it would draw less than 50w.
(just a guess)

---

### Post by metalpancake on 2008-01-06
You can try putting it into suspend mode when you aren't using it.

---

### Post by Blutack on 2008-01-06
Battery capacity in watts/time it last on battery till it dies = power consumption in watts
Rough guide obviously, assumes you don't have any battery only powersaving stuff.

---

### Post by oldb0y on 2008-01-06
I wouldn't worry too much about the power-consumption. And I think it is well under 60watt at idle.

Btw: I love your sig Blutack:)

---

### Post by Blutack on 2008-01-06
Thanks oldb0y...
You're the second tonight :-)

---

### Post by macogw on 2008-01-06
You can checkout [http://lesswatts.org](http://lesswatts.org) which is Intel's guide to saving energy for Linux laptops.

---

### Post by GSF1200S on 2008-01-06
Well, that largely depends on the laptop's specs and what its capable of. 

For instance, my laptop (specs below) will run only about 1.5 hours, but I think thats largely due to the fact that it does not support cpu frequency scaling, so my cores are sitting at 2.16Ghz all the time. As far as I know, the clock speed of the processor, the FSB speed, the speed of the GPU depending on whether youre using it, and how you use the computer are the biggest factors.

I never really cared as I use my laptop like a portable desktop, so I could be slightly off here...

---

### Post by jpittack on 2008-01-06
My guess is your laptop is consuming around 30 watts, with idle around 25 or less.  Suspend is below a single watt, hibernate below that.  How long it takes to consume this amount, I have no idea.  Right click on the battery icon and look at power history.  That is where my numbers are coming from.  To lower consumition, take a look at a few threads in the forums.  There is no one place that has everything.  Keep the warnings in mind.

I suggest taking a look at your batteries watt*hours.  If you know how to get that into watts per hour, you might have a good number.

---

### Post by cknight on 2008-01-07
Thanks for all the replies.  There may be a bit of confusion as I'm not so interested in the power usage when the laptop is unplugged.  I'm more interested in how much power it consumes sitting idle (with screen off), but plugged in.  So far, it sounds like less than a standard light bulb, though I appreciate that many factors are involved depending on my laptops specs.  I'd love to hibernate my sessions but so far it just crashes the OS when I try to resume.  Something to work on anyway...

Out of curiosity, why do desktops consume so much more power, assuming a like for like spec comparison?

---

### Post by curuxz on 2008-01-07
> **cknight said:**
> Thanks for all the replies.  There may be a bit of confusion as I'm not so interested in the power usage when the laptop is unplugged.  I'm more interested in how much power it consumes sitting idle (with screen off), but plugged in.  So far, it sounds like less than a standard light bulb, though I appreciate that many factors are involved depending on my laptops specs.  I'd love to hibernate my sessions but so far it just crashes the OS when I try to resume.  Something to work on anyway...

Out of curiosity, why do desktops consume so much more power, assuming a like for like spec comparison?

Because desktops are built to be as cheep as possible and power consumption is generally not seen as a great concern. Laptops are almost always built to maximize battery life and hence every last drop of power is conserved.

---

### Post by kendon on 2008-01-07
for the hibernation problem you might want to try the tux-on-ice project. my hp sometimes had the keyboard disabled (which makes it pretty difficult to enter the password...) after hibernation or standby, haven't had that problem since installing tux-on-ice.

my hp nx 6325 with turion x2 and 2gb ram draws about 35 watts of 220v ac current when idling with display ON with feisty.

---

### Post by gn2 on 2008-01-07
A friend of mine has a power meter that will measure the draw, it looks like a plug in timer.

His Acer desktop PC uses 20% less electricity idling on Ubuntu 7.10 than when idling on Vista Premium.

---

### Post by curuxz on 2008-01-07
> **gn2 said:**
> A friend of mine has a power meter that will measure the draw, it looks like a plug in timer.

His Acer desktop PC uses 20% less electricity idling on Ubuntu 7.10 than when idling on Vista Premium.

Thats because vista is a steaming pile of shite, I just got a new laptop yesterday, it lasted all of 30mins before i reformatted the drive to axe the unbelievably slow vista for a lightning fast kubuntu install!

---

### Post by PetePete on 2008-01-07
if you look at your laptops power cable it should have a  transformer in it (large plastic bit in the cable) on that it says how much watt it can provide.
mine is 75w. and thats for a 2ghz amd mobile laptop, no fancy gfx. with screen off and cpu scaling (down to 800mhz) i guess it can't be more than half that? 30w or something.

hmm i wonder how much the wireless router and modem consume?!

---

### Post by cknight on 2008-01-07
> **PetePete said:**
> 
hmm i wonder how much the wireless router and modem consume?!

Haha, good point.  I'm probably burning as much power with the wireless router as I am with my idle laptop.

---

### Post by GSF1200S on 2008-01-07
> **cknight said:**
> Thanks for all the replies.  There may be a bit of confusion as I'm not so interested in the power usage when the laptop is unplugged.  I'm more interested in how much power it consumes sitting idle (with screen off), but plugged in.  So far, it sounds like less than a standard light bulb, though I appreciate that many factors are involved depending on my laptops specs.  I'd love to hibernate my sessions but so far it just crashes the OS when I try to resume.  Something to work on anyway...

Out of curiosity, why do desktops consume so much more power, assuming a like for like spec comparison?

Im not sure how this will work with Gnome, but I always had problems with suspend/hibernate until I tried kpowersave. I dont see what it does different- but I swear the moment I installed it, my suspend/hibernate started to work perfectly...

---

### Post by Jussi Kukkonen on 2008-01-07
> **cknight said:**
> Thanks for all the replies.  There may be a bit of confusion as I'm not so interested in the power usage when the laptop is unplugged.  I'm more interested in how much power it consumes sitting idle (with screen off), but plugged in.  So far, it sounds like less than a standard light bulb, though I appreciate that many factors are involved depending on my laptops specs

Definitely less than a bulb. My old thinkpad idled at ~10W IIRC. 

> 
Out of curiosity, why do desktops consume so much more power, assuming a like for like spec comparison?

There is a lot of demand for low-power laptops (because low-power == long battery life), but almost no demand for low-power desktops. People just aren't that green. Also, comparisons are difficult since there are no standards.

There's hope though -- noise is something that especially media PC manufacturers are trying to get rid of and being low-power often means less fans...

---

### Post by jpittack on 2008-01-07
If you are using ati's drivers, you will not have suspend and hiberate working.  I am using mesa drivers and they work just fine.  As for the the power meter, I am very interested in getting one of these do dads.  Are they available from online retailers like newegg?  What is the proper name I should be searching for?

---

### Post by gn2 on 2008-01-08
> **jpittack said:**
>  What is the proper name I should be searching for?

This is the type of beastie: [http://www.smarthome.com/9034.html](http://www.smarthome.com/9034.html)

---

### Post by jespdj on 2008-01-08
Use powertop to see how much power your computer uses, and to get hints and tips on lowering the energy usage:
```
sudo apt-get install powertop
sudo powertop
```
My Dell XPS M1330 on batteries uses between 17 and 20 Watts when it's idle, and it goes up to 35 Watts when it's not idle.

---

### Post by PetePete on 2008-01-08
> **jespdj said:**
> Use powertop to see how much power your computer uses, and to get hints and tips on lowering the energy usage:
```
sudo apt-get install powertop
sudo powertop
```
My Dell XPS M1330 on batteries uses between 17 and 20 Watts when it's idle, and it goes up to 35 Watts when it's not idle.

what repo is that in? i get error "Couldn't find package powertop" thought i had all of the common repos!

---

### Post by PetePete on 2008-01-08
ah i see, you have to have gutsy :(

---

### Post by jpittack on 2008-01-08
> **jespdj said:**
> My Dell XPS M1330 on batteries uses between 17 and 20 Watts when it's idle, and it goes up to 35 Watts when it's not idle.

What is your battery life and which battery are you using, as well as which graphics card?  I have taken up quite an interest in this particular machine.

---

