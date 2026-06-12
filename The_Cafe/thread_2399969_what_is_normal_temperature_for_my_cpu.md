---
title: "what is normal temperature for my cpu?"
date: 2018-08-31
forum: The Cafe
---

### Post by marchello_lippi2 on 2018-08-31
Hi all, 
I wonder what is normal temperature for my cpu? It is Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz. The indicator in tray shows 84, I suppose it is Celsius as this is what is used in my country. But can not find information about what is normal. Please advise.

---

### Post by Frogs Hair on 2018-08-31
I would consider 84 C to be high. My (net-book)  i5-2540M CPU @ 2.60GHz runs about 35 to 42 C when browsing and listening to music. Hardware temperatures are _generally_ displayed in Celsius.

```
coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +40.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:        +36.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:        +39.0°C  (high = +86.0°C, crit = +100.0°C)

```

52 to 60 C is average for a medium load.

[https://www.computerhope.com/issues/ch000687.htm](https://www.computerhope.com/issues/ch000687.htm)

---

### Post by poorguy on 2018-08-31
> **marchello_lippi2 said:**
> Hi all, 
I wonder what is normal temperature for my cpu? It is*** Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz***. The indicator in tray shows 84, I suppose it is Celsius as this is what is used in my country. But can not find information about what is normal. Please advise.

Google is your friend.

Max temp*** 105 degrees Celsius ***so anything under that would be good it mainly depends on what you are doing and ambient room temperature.  

Install and run ***lm-sensors*** and then install ***psensor*** or ***xsensors ***to monitor your processor temperature.

[https://ark.intel.com/products/85212/Intel-Core-i5-5200U-Processor-3M-Cache-up-to-2_70-GHz](https://ark.intel.com/products/85212/Intel-Core-i5-5200U-Processor-3M-Cache-up-to-2_70-GHz)

[http://www.cpu-world.com/CPUs/Core_i5/Intel-Core%20i5-5200U%20Mobile%20processor.html](http://www.cpu-world.com/CPUs/Core_i5/Intel-Core%20i5-5200U%20Mobile%20processor.html)

---

### Post by deltamind on 2018-09-03
Is this on idle? If idle then yes it's hot.

---

### Post by RabbitWho on 2018-09-09
A cheap lenovo I have, some celeron processor or other. Running at 53 degrees Celsius right now. All I have open is a web browser.

---

### Post by marchello_lippi2 on 2018-09-09
As I can see, it has few sensors, I believe intel cpu should not show this hight value. I can see that other sensors display less values. Not sure which sensor should it be though.

---

### Post by poorguy on 2018-09-10
> **marchello_lippi2 said:**
>  I believe intel cpu should not show this hight value. 

If all is working well and you aren't experiencing ***random restarts*** or*** random shut downs*** I wouldn't worry about anything.

I've got laptops that produce so much heat out of the*** rear vent / side vent*** that I raise them off the table surface and set them on empty ash trays ***so they will vent sufficiently***.
[I][B]
Laptops always run pretty warm to hot[/B][/I] from my experience as everything is*** crammed into such a small space*** and ***no room to dissipate the heat created*** which is why they have*** a high failure rate***.

My opinion only.

---

### Post by marchello_lippi2 on 2018-09-10
I believe it is just wrong sensor set by default, because I do not experience any random restarts etc, also I do not feel any unusual temperature when touching my laptop. I can compare this to my previous laptop that was just not clean and thus was hot after just few minutes of work. So.. the question is how do I set proper sensor in the tray indicator settings, can not find any information about it. No urgency though. Thanks for each input anyway.

---

### Post by poorguy on 2018-09-10
Hey marchello_lippi2,


I use*** psensor*** and it seems to be right on with ***lm-sensors***.


***These may help.***

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

[https://packages.ubuntu.com/search?keywords=lm-sensors](https://packages.ubuntu.com/search?keywords=lm-sensors)

[https://askubuntu.com/questions/53762/how-to-use-lm-sensors](https://askubuntu.com/questions/53762/how-to-use-lm-sensors)

---

### Post by marchello_lippi2 on 2018-09-17
[COLOR=#DD4814][COLOR=#000000][nicbrown]("https://ubuntuforums.org/member.php?u=2107061"),[/COLOR][/COLOR]
I think it's rather not realistic display value as it would burn my legs when I sit and hold my notebook.

---

### Post by marchello_lippi2 on 2018-09-17
Upd: The thermo paste is few weeks old and they cleaned my notebook inside in the pc shop service.

---

### Post by yetimon_64 on 2018-09-18
> **poorguy said:**
> If all is working well and you aren't experiencing ***random restarts*** or*** random shut downs*** I wouldn't worry about anything.

I've got laptops that produce so much heat out of the*** rear vent / side vent*** that I raise them off the table surface and set them on empty ash trays ***so they will vent sufficiently***.
[I][B]
Laptops always run pretty warm to hot[/B][/I] from my experience as everything is*** crammed into such a small space*** and ***no room to dissipate the heat created*** which is why they have*** a high failure rate***.

My opinion only.

> **marchello_lippi2 said:**
> Upd: The thermo paste is few weeks old and they cleaned my notebook inside in the pc shop service.

If you have recently had the laptop serviced and the thermal paste replaced and are still getting those temperatures then I suspect the make/model of laptop you bought may fall into the category that poorguy describes. You may very well be able to find other makes/models of laptop, with that same processor, that will give cooler temps. It sounds like it could possibly be a design/quality problem with whatever make you have purchased.

I used to have an Acer laptop, with an Intel chip that performed pretty much as you are describing here heat wise. About 80 to 85 deg C was pretty much normal running temp even on very low loads; I forget what processor model it had but it was an Intel chip (with 4 virtual cores registering to the OS, but I can't remember if it was a hyper-threaded dual core or a proper quad core machine).

My current laptop is a "HP Envy 17" with a hyper-threaded dual core i7 5500U processor (4 virtual processors). On idle, about 5 % CPU usage, it is currently running at 47 deg C. But to ensure that temp stays reasonable I do very similar to what poorguy describes by raising it up off the hard surface by using four half inch copper saddles. As well as lifting it off the surface I am now in the habit of pointing a pedestal fan across the laptop to force more air movement so as to remove any excess heat generated as quickly as possible. Because of heat buildup I NEVER run it on my lap and would only do so if I could find a suitable base with inbuilt fans; I think they are called "cooling pads". Though it would need to be a HUGE, and heavy, cooling pad for a 17 inch laptop so I haven't bothered looking for one.

When the heat in this laptop starts hitting about 75 to 80 degrees the fans inside "roar" loudly but are very good in that they have never let the CPU get past 98 deg C; with critical being 105 deg C on this model. Because the laptop uses such powerful (you can read that as "loud" :-)) fans I can transcode video with all four virtual cores registering 100 % loading and the CPU stays at 97 or 98 deg C. There are some models of laptop that doing transcoding video, that is loading up so heavily, would likely kill of the laptop with "heat stroke/CPU meltdown" very quickly. Close monitoring with lm-sensors while doing such tasks is critical on these types of machine.

Just out of interest; what make and model is your laptop?
 It may pay to check if other people are reporting heat issues specific to the make and model of the laptop (not just with the CPU model itself). From my experiences with laptops I tend to agree with what poorguy posted.

---

### Post by ryleyrushh on 2018-10-04
I have the same intel. Mine is always running at 82°C and it is okay. The closer it is to 100 the more dangerous situation is.

---

### Post by poorguy on 2018-10-09
Back in the days of ***Windows XP*** my first real dual core experience was with an ***Intel Pentium D 820 Smithfield***.

[https://ark.intel.com/products/27512/Intel-Pentium-D-Processor-820-2M-Cache-2-80-GHz-800-MHz-FSB-](https://ark.intel.com/products/27512/Intel-Pentium-D-Processor-820-2M-Cache-2-80-GHz-800-MHz-FSB-)

This processor was referred to as the*** "flame thrower" ***and it did for the most live up to its name when using the ***Intel oem heat sink fan***.

This processor ran temperatures anywhere from ***55 degrees Celsius*** to ***75 degrees Celsius*** with the oem heat sink fan continuously ramping to maximum rpm and never throttled down or shut down.

Intel Processors in the old days of the Pentium were designed and built and seem to be able to handle the high heat that was generated by its "NetBurst Architecture".

With the release of the Core 2 Duo processors temperatures dropped considerably although with four cores and more on one single die normal operating temperatures seem to be climbing high once again.

---

### Post by entropie2 on 2018-10-29
I am using a i5-7600T desktop cpu in a laptop cooled via heatpipe and a cooler at the end. Its quiet all the time at around 5% cpu usage and 41 degrees Celsius. I consider the Intel CPUs to be very efficient, especially under Linux, didnt know some run at 80 degrees when idling. 80 degrees is the standard temp my gaming-laptop has, when under load and thats a i7-7700HQ. 
That i5 I really like, the whole system, including the display at half the brightness uses 10 W and gives me 9 hours battery life for a whole work day.

---

