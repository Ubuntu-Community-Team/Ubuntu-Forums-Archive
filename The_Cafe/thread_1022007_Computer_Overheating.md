---
title: "Computer Overheating?"
date: 2008-12-26
forum: The Cafe
---

### Post by elmer_42 on 2008-12-26
Alright, for Christmas I got [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121272) HD4850 (:D) and it's just great. I've got catalyst and catalyst-utils both at v8.12 in Arch Linux. On Windows I have the latest Catalyst drivers and the Catalyst Control Center. The weird thing is that my computer shut down suddenly while I was playing Nexuiz (at max settings, *always* over 60fps, no matter what) just a little bit earlier. Yesterday it did the same thing, but I was playing Battlefield 2 in Windows. I noticed that the air coming out of the back fan was pretty warm. Could it be overheating? Are there any other things that would cause these symptoms?

If it is overheating, should I just get some better fans or what? As of now, I have the two stock fans that the case came with, one intake on the side and one exhaust on the back. I also have a [Cooler Master Hyper TX2](http://www.newegg.com/Product/Product.aspx?Item=N82E16835103031) on my CPU and the heatsink-fan on my new HD4850. There is room for one more fan in the front area of the case. My current plan is to buy 3 [Yate Loons](http://www.jab-tech.com/YATE-LOON-120mm-Case-Fan-D12SL-12-pr-3009.html) (they come well-recommended from a friend of mine) and have the front fan intake, with the back two fans being exhaust. This way I can get negative pressure, which I hear is good for temperatures. How does this plan sound?

---

### Post by handy on 2008-12-26
If you are over-clocking it I would bring it back to standard clock speed.

Do the Catalyst drivers give you any information on the cards temperature, or any controls to keep it from over heating?

Does the card take power directly from the PSU, is your PSU powerful enough for your machine now that it has this card?

---

### Post by mips on 2008-12-26
What does the cabling inside your case look like (a picture would be nice)?

---

### Post by elmer_42 on 2008-12-26
> **handy said:**
> If you are over-clocking it I would bring it back to standard clock speed.

Do the Catalyst drivers give you any information on the cards temperature, or any controls to keep it from over heating?

Does the card take power directly from the PSU, is your PSU powerful enough for your machine now that it has this card?
- I'm not overclocking it, but I brought my CPU back to normal speed.
- On Windows they do, but not so here in Linux
- It takes power via a 6 pin PCIe plug. I have a Corsair 650TX, which should be powerful enough. If It's not I'm going to be uber-mad, I just got this thing.

Click to enlarge thumbnails of my PC's insides. Sorry they're so grainy, I hope they're good enough to be able to make out details. The red wire that is out on the bottom of the case leads to the fan that is on the side of the case.
[[img]http://arch.kimag.es/thumbs/63626868.jpg[/img]](http://arch.kimag.es/share/63626868.jpg)[[img]http://arch.kimag.es/thumbs/46363327.jpg[/img]](http://arch.kimag.es/share/46363327.jpg)

---

### Post by Skripka on 2008-12-26
1stly, Do you have lm-sensors installed, and if so what does it tell you?  What model of CPU are you running?  An AMD 125W CPU like mine (see sig) has a max temp of only 65C.

2ndly, what is the ambient temp in your room where your machine is?

3rdly, nothing bothers me more than untidy cables gangling everywhere-hint hint hint.

4thly, I'd definitely invest in either more fans or a better case-id this is overheating.  My LianLi came with 2X120mm fans, and 2X80mm fans-stock....in addition to my graphics card having it's own ducted exhaust.

---

### Post by elmer_42 on 2008-12-26
> **Skripka said:**
> 1stly, Do you have lm-sensors installed, and if so what does it tell you?  What model of CPU are you running?
2ndly, what is the ambient temp in your room where your machine is?
3rdly, nothing bothers me more than untidy cables gangling everywhere-hint hint hint.
4thly, I'd definitely invest in either more fans or a better case-id this is overheating.
[LIST=1]
[*]Yes I do. I've got an AMD 64 X2 5000+ that's running at about 30 degrees Celsius.
[*]Not too sure, but the thermostat in a nearby hall says 64 degrees Fahrenheit, which is about 17 or 18 degrees Celsius.
[*]Sorry 'bout that, but I did my best to zip-tie things so they wouldn't be gangling everywhere. What do you think I could do to improve things?
[*]Like I said, I'll probably buy three Yate Loon fans. If at that point things are still too hot I'll be looking into a new case.
[/LIST]

---

### Post by inxygnuu on 2008-12-26
1 thing... ***_NICE COMPUTER!!!_***

Answer: Is your fan secured? I had a CPU overheating problem because the fan was not on correctly.

---

### Post by Nepherte on 2008-12-26
Just figure out the temperature of your card. The latest cards tend to get very hot ( 100°C is not abnormal). If the card gets too hot, it's possible the computer will simply shut down in Windows but that doesn't seem the case here. As long as you don't experience any problems, I'd say you're just fine.

---

### Post by Skripka on 2008-12-26
> **elmer_42 said:**
> [LIST=1]
[*]Yes I do. I've got an AMD 64 X2 5000+ that's running at about 30 degrees Celsius.
[*]Not too sure, but the thermostat in a nearby hall says 64 degrees Fahrenheit, which is about 17 or 18 degrees Celsius.
[*]Sorry 'bout that, but I did my best to zip-tie things so they wouldn't be gangling everywhere. What do you think I could do to improve things?
[*]Like I said, I'll probably buy three Yate Loon fans. If at that point things are still too hot I'll be looking into a new case.
[/LIST]

For idle temps 30C is good for a 18C room.  Under full load (i.e. Nexuiz, games etc)-if you don't have any handy way of checking temps during load--the next best things to try:

-Clean off the fan grills, they collect lots of dust and particles by design-and can get clogged easily

-Run your computer under load with the side panel off, to see if more air circulation helps with temps.  Of course-don't dare touch any of the components while booted.

-For left over cable snakes I hide them in the unused 5.25" bays.  The zip-ties I fully approve of it is the cables hanging in the middle of the case that bugs me :) . Every little thing can help when improving cooling air flow; especially in a case with very poor air-flow to start...which in this case is made worse by a large graphics card.  In your box there's no room for air to flow straight from intake to exhaust-which can cause major heat issues.  Tidying cables won't do much here-due to the lack of air-flow in the best of times, but it cannot hurt.

-I presume the CPU cooler is mounted with Arctic Silver5 at the interface between CPU and cooler?

---

### Post by elmer_42 on 2008-12-26
> **Skripka said:**
> -Clean off the fan grills
-Run your computer under load with the side panel off, to see if more air circulation helps with temps.
-For left over cable snakes I hide them in the unused 5.25" bays.
-I presume the CPU cooler is mounted with Arctic Silver5 at the interface between CPU and cooler?
- I did that while I was putting in the new GPU
- This thought kind of scares me. Since one of my fans (the intake) is on the side, and the only other one is on the back, I'm afraid to remove half of the fans.
- I did my best, and I was going to do this, but having the big ball of cables zip-tied where they are right now kept them more secure, they sort of flopped about when I tried zip-tying them in the spare bays.
- I think that's what I've got. I alcohol'd off the original thermal stuff and put on some "Arctic Silver Ceramique" I got from Newegg.
> **Nepherte said:**
> Just figure out the temperature of your card. As long as you don't experience any problems, I'd say you're just fine.
I think that random shutdowns are a problem. I think it got up to about 75C in Battlefield 2, but I wasn't actively watching.
> **inxygnuu said:**
> 1 thing... ***_NICE COMPUTER!!!_***
Is your fan secured?
Thank you, I feel blessed to have it. As far as I know, both fans are secure. The CPU heatsink-fan has worked fine all this time and the GPU heatsink-fan doesn't feel like it's loose at all.

---

### Post by Skripka on 2008-12-26
> **elmer_42 said:**
> - I did that while I was putting in the new GPU
- This thought kind of scares me. Since one of my fans (the intake) is on the side, and the only other one is on the back, I'm afraid to remove half of the fans.
- I did my best, and I was going to do this, but having the big ball of cables zip-tied kept them more secure, they sort of flopped about.
- I think that's what I've got. I alcohol'd off the original thermal stuff and put on some "Arctic Silver Ceramique" I got from Newegg.


As far as removing the sidepanel-Use an office fan as a substutute.  Just about any old fan one has lying around their house moves more air faster than computer case fans.  Short of getting real data off the thermostats under load-this is the next best test.  If you can contrive a full-load CPU/GPU activity to keep your machine at full load for 5 minutes or so--to see how far north the temps go, reading data off lm-sensors.

Usually thermostats in computers read low-and sometimes they die.  So even if thermostats are pumping out data-it isn't necessarily accurate.  I have an UnderPoweredBookG4 in Me Casa that has a dead thermostat in it-that will cause the machine to crash due to "overheat" even if the machine is physically cold to the touch.

---

### Post by elmer_42 on 2008-12-26
> **Skripka said:**
> As far as removing the sidepanel-Use an office fan as a substutute.  Just about any old fan one has lying around their house moves more air faster than computer case fans.  Short of getting real data off the thermostats under load-this is the next best test.  If you can contrive a full-load CPU/GPU activity to keep your machine at full load for 5 minutes or so--to see how far north the temps go, reading data off lm-sensors.
Alright, I guess I'll see what I can do about getting an office fan in here.

---

### Post by mips on 2008-12-26
Start by cleaning up your cabling you cabling, it looks messy and restricts airflow.
Why your gfx card does not have ducted vents I don't know but the current config seems lacking.
You would probably require more fans or some sort of better circulation.
You could probably get aftermarket cooling for your card or some sort of ducted vent that expells hot air via one of the back slots.

---

### Post by handy on 2008-12-26
Then when it all gets too noisy you will have to go the way of a silent PC, with water or phase cooling instead of all these fans; & use SSD's instead of these noisy HDD's.

The battle never stops. ;-)

---

### Post by MaxIBoy on 2008-12-26
If you're getting random resets, it could be your RAM. Try running memtest86+ for a while (we're talking 15 hours here,) see if you find any errors.

If not, then it might be your motherboard.

---

### Post by smartboyathome on 2008-12-26
I'm having a similar problem with my laptop. I have to use a usb cooling pad right now which keeps the temperature below 150F, but without that cooling pad, temperatures can skyrocket to near 200F (Almost 100C!). Most of the problem with it is that the graphic card (intel, integrated), CPU, and other stuff which gets hot are all on one side of the computer, as when one side is very hot, the other can be pretty cool. Is there any way to improve my laptop's cooling problem short of taking it apart?

---

### Post by elmer_42 on 2008-12-26
> **MaxIBoy said:**
> If you're getting random resets, it could be your RAM. Try running memtest86+ for a while (we're talking 15 hours here,) see if you find any errors.
My RAM was acting up earlier, but that was because I didn't have the two new sticks seated properly. The resets aren't entirely random, they happen when there are fairly intense 3D graphics applications running. It's only happened to me twice, but that's only because I've not run any games after the second time for fear of another overheat.

---

### Post by Skripka on 2008-12-26
> **smartboyathome said:**
> I'm having a similar problem with my laptop. I have to use a usb cooling pad right now which keeps the temperature below 150F, but without that cooling pad, temperatures can skyrocket to near 200F (Almost 100C!). Most of the problem with it is that the graphic card (intel, integrated), CPU, and other stuff which gets hot are all on one side of the computer, as when one side is very hot, the other can be pretty cool. Is there any way to improve my laptop's cooling problem short of taking it apart?

Nope.

The trade off you get with: small, lightweight, and fast

is [U]lots and lots of heat.  
[/U]
The GOOD news is that the bottom of your laptop is hot-so the heat is being transferred away from circuitry.  Aside from placing your laptop on a cooling surface, there isn't much else you can do.

---

### Post by smartboyathome on 2008-12-26
> **Skripka said:**
> Nope.

The trade off you get with: small, lightweight, and fast

is [U]lots and lots of heat.  
[/U]
The GOOD news is that the bottom of your laptop is hot-so the heat is being transferred away from circuitry.  Aside from placing your laptop on a cooling surface, there isn't much else you can do.

Ok, thanks. I guess I will just have to suffice until I get a new laptop.

---

### Post by Skripka on 2008-12-26
> **smartboyathome said:**
> Ok, thanks. I guess I will just have to suffice until I get a new laptop.

Remember, every laptop has this problem.  Some moreso than others-depending on how small they are and how powerful they are.  Just because you're spending money on better hardware doesn't mean your issue will go away-in fact odds are good it will be worse.

---

### Post by Skripka on 2008-12-26
> **elmer_42 said:**
> My RAM was acting up earlier, but that was because I didn't have the two new sticks seated properly. The resets aren't entirely random, they happen when there are fairly intense 3D graphics applications running. It's only happened to me twice, but that's only because I've not run any games after the second time for fear of another overheat.

Another thought-you could try googling to see if Windows keeps a log file of crashes....Mac and Linux do-but they're *nix.

---

### Post by smartboyathome on 2008-12-26
> **Skripka said:**
> Remember, every laptop has this problem.  Some moreso than others-depending on how small they are and how powerful they are.  Just because you're spending money on better hardware doesn't mean your issue will go away-in fact odds are good it will be worse.

Yeah, I was thinking of getting a netbook next with an SSD, which should be better with heat (from what I hear).

---

### Post by MaxIBoy on 2008-12-26
> **elmer_42 said:**
> My RAM was acting up earlier, but that was because I didn't have the two new sticks seated properly. The resets aren't entirely random, they happen when there are fairly intense 3D graphics applications running. It's only happened to me twice, but that's only because I've not run any games after the second time for fear of another overheat.
Sometimes, RAM only has problems if it's reached a certain temperature. Also, sometimes the error is in a high sector of RAM, where it won't be a problem until RAM usage gets very high.

---

### Post by elmer_42 on 2008-12-26
> **MaxIBoy said:**
> Sometimes, RAM only has problems if it's reached a certain temperature. Also, sometimes the error is in a high sector of RAM, where it won't be a problem until RAM usage gets very high.
I guess I'll run memtest86+ overnight, then.

---

### Post by elmer_42 on 2008-12-27
Alright, I started the latest CD version of memtest86+ before I left for a movie, and by the time I got back my computer had shut down. What, exactly, does this mean? Did it find some sort of fault with the RAM?

**e:**I'm a retard. I forgot to plug the CPU fan back in after I swapped PSUs. xD

---

