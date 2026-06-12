---
title: "CPU temperature"
date: 2010-10-22
forum: System76 Support
---

### Post by Mendel314 on 2010-10-22
My sensors read that my cpu is around 80 C.  This sounds hot to me. Should I be concerned? I have a pan p7 with an i7 m620.  How hot should it be? what would be too hot?

---

### Post by isantop on 2010-10-22
That does seem a little high, though not dangerous yet. Make sure your fan and vents are clear of dust and debris, and that they are not blocked. Also, make sure silent mode is off by pressing the "M" hotkey. If the fan speeds up, then silent mode was on, and the CPU may run a little warm. It should come down in temperature soon.

---

### Post by z08595 on 2010-10-24
What exactly is the function of the "M hotkey?"  My computer was running with a very loud fan for hours on end until I pressed it after reading the previous post.  Then it slowed down (but still ran) while increasing my CPU temp from 42 C to 48 C.

---

### Post by bukwirm on 2010-10-24
CPU temperature sensors can be somewhat unreliable. If your computer is not crashing, it's probably not too hot - but isantop's suggestions are a good idea anyway.

---

### Post by Noah0504 on 2010-10-25
> **z08595 said:**
> What exactly is the function of the "M hotkey?"  My computer was running with a very loud fan for hours on end until I pressed it after reading the previous post.  Then it slowed down (but still ran) while increasing my CPU temp from 42 C to 48 C.
I think it stands for mobile.  I know it will quiet down the fans, but other laptops have a similar feature that increase battery time.  Fans don't spin as much, CPU doesn't operate as fast.  Just not sure exactly how much the button does on System76 computers.

---

### Post by TBABill on 2010-10-25
I had a laptop in my lapt that got to 86C when 10.04 (and Mint 9, based on 10.04) first came out (before they fixed the heat issue). I had the fans unobstructed and it just felt terrible in my lap and I was literally sweating. I did not keep it installed and moved back to PCLinuxOS. However, 10.04.1 fixed the issue and my machine runs cool now. If you are at 80C you are very very hot and probably dangerously hot for your hardware. Your machine hits critical probably around 100C and that's where it just cuts off on you. But being at 80 is simply too high under normal usage. If you run that way all the time it could be an obstruction. If you dual boot and run cool in Windows then it's something with your configuration.
 
Do you have the CPU Frequency Scaling monitor installed? At least you can tell what speed your processor is running at. If it's set to performance, then you are at 100% all the time. Enabling ondemand or powersave mode will greatly reduce CPU heat. But if you are experiencing heat from your GPU then you likely have a driver issue (open source drivers are not so great for power regulation yet and often keep the GPU at 100%!). Have you enabled a proprietary driver if available?

---

### Post by Mendel314 on 2010-10-25
I do have a scaling monitor. I have it sent to ondemand, and it usually hovers around 1.2 ghz.  Performance jumps it to 2.67. Even still, it operates really hot.  It's hovering around 72C rt now, the hottest it has been today was 83.  Where might I download a proprietary driver for the i7 M620? and more importantly (I could probably find this driver myself somewhere) how do I use it without accidentally killing my machine?

  The fan is definitely on, btw, I know the M hotkey and I have been too afraid of the temp to ever turn off the fan.  I have read that the i7 runs hot, and the sensor applet says that 189C is critical.  I am suspicious of that number. Even if the i7 can hit 189, something tells me other stuff (including my hand) can't withstand that heat.

I don't know how long this has been the case. I only recently enabled a thermometer widget, and since then I have been worrying about its readout.  How inaccurate are these sensors? If it's plus or minus 5C, I'm still concerned about the readout.  If it's 25C, then why bother with them in the first place?

---

### Post by endotherm on 2010-10-25
when you say "thermometer gadget" do you mean the Sensors-Applet gnome panel widget? if so, did you run sensors-detect after installing lm-sensors? perhaps thermometer is a s76 custom thing. 

189 max seems about twice what I would expect. from what I see, the TJMax for i7's is in the 95-100C range. I am seeing that the i7's run hot, but that is awful high for a CPU.

i would generally suspect that you need to repaste your CPU. somtimes the factory just doesn't do it quite right.

---

### Post by Mendel314 on 2010-10-25
> **endotherm said:**
> when you say "thermometer gadget" do you mean the Sensors-Applet gnome panel widget? if so, did you run sensors-detect after installing lm-sensors? perhaps thermometer is a s76 custom thing. 

189 max seems about twice what I would expect. from what I see, the TJMax for i7's is in the 95-100C range. I am seeing that the i7's run hot, but that is awful high for a CPU.

i would generally suspect that you need to repaste your CPU. somtimes the factory just doesn't do it quite right.

Yes, I mean Sensors-Applet running in Awn. I also have a ring sensor screenlet, measured by what reads as "acpi temperatures THM0"

---

### Post by endotherm on 2010-10-25
> **Mendel314 said:**
> Yes, I mean Sensors-Applet running in Awn. I also have a ring sensor screenlet, measured by what reads as "acpi temperatures THM0"

ahh, is teh ACPI temp the one that is always reading high? ACPI is differant from CPU and usually has a much higher value. 
if you run from a terminal 
```
sudo sensors
```
do you get any output?
also did you run sensors-detect while installing lm-sensors?

---

### Post by Mendel314 on 2010-10-26
> **endotherm said:**
> ahh, is teh ACPI temp the one that is always reading high? ACPI is differant from CPU and usually has a much higher value. 
if you run from a terminal 
```
sudo sensors
```do you get any output?
also did you run sensors-detect while installing lm-sensors?

It seems I have only one sensor...the ACPI one.  The sensor labeled cpu and the one labeled acpi are always the same, and when I run sudo sensors, I get the same readout again.  does this mean I'm in the clear? if the acpi temp stays within a range higher than that which the cpu should hit, It'll still be ok?

---

### Post by endotherm on 2010-10-26
> **Mendel314 said:**
> It seems I have only one sensor...the ACPI one.  The sensor labeled cpu and the one labeled acpi are always the same, and when I run sudo sensors, I get the same readout again.  does this mean I'm in the clear? if the acpi temp stays within a range higher than that which the cpu should hit, It'll still be ok?

sounds like you should be fine, but just to make sure your sensors are correctly configured, try running this command ( answering Yes to all questions):
```
sudo sensors-detect
```

and then when it's done, run 'sudo sensors' again and see if you get any different results. 

here is an interesting bug/thread on the SpeedFan site (I've used speedfan in windows for years; good stuff): [http://www.bugtrack.almico.com/view.php?id=314](http://www.bugtrack.almico.com/view.php?id=314)

looking around on the web, i'm seeing a lot of indications that everyones ACPI implementation is differant, and that they often produce erroneous results. not sure what to tell you beyond that though.

---

### Post by Mendel314 on 2010-10-26
> **endotherm said:**
> sounds like you should be fine, but just to make sure your sensors are correctly configured, try running this command ( answering Yes to all questions):
```
sudo sensors-detect
```and then when it's done, run 'sudo sensors' again and see if you get any different results. 

here is an interesting bug/thread on the SpeedFan site (I've used speedfan in windows for years; good stuff): [http://www.bugtrack.almico.com/view.php?id=314](http://www.bugtrack.almico.com/view.php?id=314)

looking around on the web, i'm seeing a lot of indications that everyones ACPI implementation is differant, and that they often produce erroneous results. not sure what to tell you beyond that though.

I did that yesterday, answered yes to all questions, the results I gave are from afterwards
I guess if the only temp I see is acpi, I just won't worry about it. I'll try to keep it under 85, and assume the cpu is significantly cooler

---

### Post by endotherm on 2010-10-26
the only other thing i can think of, is that wineHQ shows that coretemp for windows MAY run correctly in wine. not sure if it's worth bothering with. sorry I can't be of more help, and good luck

---

### Post by TBABill on 2010-10-26
189 ºC = 372.2 ºF There is no way that machine can have a max for the CPU of 189C. Nothing in that machine should ever approach temps like that so I would suspect either the reading is just false or the temperature should be in degrees F? I saw you said it's ACPI, but the number just isn't making sense. 
 
I think we bake cakes at a lower temp than that maximum temp :)

---

### Post by Mendel314 on 2010-10-26
that number is the number that an desklet gives as "critical". My computer has never approached that number.  The hottest I've seen it was 91, but the temps are definitely in celsius

---

### Post by TBABill on 2010-10-26
If you hit 91C regularly then you can likely expect a major failure in your computer at some point. I pushed my laptop to 86C when 10.04 released and it got so hot I was sweating while sitting in an air conditioned room. At 99C or 100C my machine will shut off automatically. And if your hard drive gets that hot it will likely fail quickly. I would be very concerned if those temps are accurate.

Since it is a System76 I would ask for recommendations from them directly to determine if something particular to your machine may be going on. Do you by chance have any version of Windows installed to compare temps in each OS? Normal temps in 10.04 and other distros such as PCLinuxOS, openSUSE and Mint are around 62 as a high temp. 91 would worry me that a hardware failure would happen soon if those temps are normal.

---

### Post by Mendel314 on 2010-10-27
Right now its at 65, it usually will stay under 80, I have only seen 91 once.  After a few hours though, it almost always will rise slowly until it hits high seventies, then it hovers around 80.  It is too hot to have on a lap, and it is too hot to keep my hand next to the vent for too long.  I will see 81-83 as the max temp most times I use it.  86-91 is rare. I usually just shut it off and reboot it if it gets that hot.

I dont have any windows on the computer.  I have been meaning to get some more ram so I can run vbox, but that won't help me for comparison. It should just run hotter then.

I run 10.04 with Kubuntu

---

### Post by TBABill on 2010-10-27
When it gets hot have you tried using top or htop to see if maybe something is pushing your cpu usage at that time and driving up heat? If you have a process that is really pushing it for some reason maybe shutting down that process could help? Just a guess again...

---

### Post by Mendel314 on 2010-10-27
> **TBABill said:**
> When it gets hot have you tried using top or htop to see if maybe something is pushing your cpu usage at that time and driving up heat? If you have a process that is really pushing it for some reason maybe shutting down that process could help? Just a guess again...

Definitely Firefox to some extent
when firerfox starts, the acpi temp jumps at least 3-4 degrees, and if its video, by more.  The more firefox windows/tabs, the hotter it gets I guess.  Any way to get around that?

I was running about 74, then closed firefox, quickly fell to 65.  Then I started firefox again, up to 69 in no time.

---

### Post by TBABill on 2010-10-27
Possibly try Chromium or Opera for browsing to see if they make a difference. If they do, perhaps a Firefox extension or something (besides the heat inherently created by using Flash) is the cause.

---

### Post by Mendel314 on 2010-10-28
I tried Chromium, it still gets hot (If I'm online, I'm streaming video) 
Why does Flash make the computer so hot?

---

### Post by gradinaruvasile on 2010-10-28
Its very simple - it uses lots of CPU processing. It is the worst player i have ever seen (from the resource usage standpoint).
Launch top in a terminal when you start Firefox and see why.

Be very careful with the cpu temp issue, on laptops you can have a fried cpu or motherboard easily if you let it run hot for extended periods - the abrupt heating/cooling cycles will affect the materials in time.
Put a temperature monitoring applet in the taskbar to see the temps. If it starts to get hot, open a system monitor or top and investigate the issue (look for the most cpu-consuming processes). Normally a 40-50 C (or lower) idle temperature should be ideal for laptops (less for desktops).

Solutions:
Install flashblock in Firefox or Chrome (Opera has a built-in switch for that). This will not play any flash objects on the page, but puts a frame on their place and if you click it, it will play its content.

Trick - flash movies are cached locally - usually in the /tmp/ folder (or some flash player clients put them in the browsers cache). They have random names, but if you browse the folder you can see the biggest file. I dont play them in the browser, just pause them and they will be cached locally in the backgrond. After the caching is finished, i copy them in another location - when you close the page, the original will be deleted. The copied file can be played with any player with normally low cpu usage.

---

### Post by Mendel314 on 2010-10-28
thanks, I think this is what I'll do. I knew about the tmp folder caching, I just don't do it all the time.  Perhaps I shall start. The Flashblock is probably the closest to a solution.

My acpi hovers between 62-66 when there is no flash playing, so I guess the only solution is to prevent flash.

---

### Post by d3v1150m471c on 2010-10-28
Make sure your computer is in a space where the fans provided plenty of air flow. This is pertinent on laptops where ventilation is of poor design. Make sure the laptop/desktop is still on a hard and stable surface so not to wobble or be slid around from usage. On a laptop it is probably a good investment to purchase a cooling fan that will fit underneath. Make sure your fan and input/output vents aren't blocked by dust or debris.

---

### Post by gradinaruvasile on 2010-10-28
> **d3v1150m471c said:**
> Make sure your computer is in a space where the fans provided plenty of air flow. This is pertinent on laptops where ventilation is of poor design. Make sure the laptop/desktop is still on a hard and stable surface so not to wobble or be slid around from usage. On a laptop it is probably a good investment to purchase a cooling fan that will fit underneath. Make sure your fan and input/output vents aren't blocked by dust or debris.

This.

And you should consider buying a laptop cooler. I have one older p4 laptop that overheated constantly, bought one cooler and no problems since.

---

### Post by Mendel314 on 2010-10-28
Just installed flashblock and went out and bought a cooler.  I put my comp thru its paces, streaming several vids, and didn't go over 67. I guess problem solved

> **gradinaruvasile said:**
> This.

And you should consider buying a laptop cooler. I have one older p4 laptop that overheated constantly, bought one cooler and no problems since.

---

### Post by endotherm on 2010-10-28
> **Mendel314 said:**
> Just installed flashblock and went out and bought a cooler.  I put my comp thru its paces, streaming several vids, and didn't go over 67. I guess problem solved
getting a nice heavy all aluminum cooling plate was the best thing I ever did for my dv9000. had been idling in the high 50's and exceeding 70 under a load, it is now idling in the low 40's (30's in the winter).

---

### Post by Mendel314 on 2010-10-28
I got an aluminum cooling thing from Antec.  Instead of going up to 87-91 under heavy load, it doesnt go above 67.  It seems to idle at 59, when it used to idle at 62-65.  In any case, I'd say the cooling pad is doing its job.

---

