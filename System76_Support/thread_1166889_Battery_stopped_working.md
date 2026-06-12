---
title: "Battery stopped working"
date: 2009-05-22
forum: System76 Support
---

### Post by earrame on 2009-05-22
Yesterday (5/21) my Pangolin (panp4i) began shutting down without warning when running on battery.

I kept the computer plugged in all night to charge as I normally do.

This morning I pulled the plug and watched for messages. Within half a minute or so the power monitor reported about 5 minutes of battery life remained. Less than a minute after that it reported the battery was critically low. No more than half a minute later it shut down.

The power monitor now reports (correctly) that it is running on AC power and the battery is charging (6.3%). This is about 20 minutes after the shut down.

I can not specifically recall running on battery since the upgrade to 9.04 about 2 weeks ago. Yesterday may have been the first time.

Could the battery actually be charged and the power monitor is not reporting correctly? This sounds better than a harware failure.:)

---

### Post by thomasaaron on 2009-05-22
Well, there is a power reporting problem on the Pangolin, but I don't *think* it is related to what you are experiencing (simply because there are tons of these machines out there, and I've not heard of this being a symptom of the problem). For more info on the bug I'm speaking of, see...

[http://ubuntuforums.org/showthread.php?t=1155641&highlight=pangolin+battery](http://ubuntuforums.org/showthread.php?t=1155641&highlight=pangolin+battery)

I've got some things for you to try on this, like re-setting your cmos. So, if you don't mind, I'd like to give you instructions via email. support(at)system76(dot)com.

---

### Post by earrame on 2009-05-22
I did the first step in the email. Pulling the battery & AC adapter for 30 minutes.

I'm getting ready to do the second step. I just wanted to note that after four hours of charging the power monitor reports only 16% battery life.

---

### Post by earrame on 2009-05-22
Ok, confirming the first step did not work. Computer tanked about 2 minutes after pulling the AC adapter.

Going to do step 2 in the email now.

update; about 2 hours since I last update. The battery got up to about 12% and is going to shut down in a moment. Just a couple minutes after I pulled the AC adapter.

I'll keep an eye on it over the weekend to see if any new information becomes available.

---

### Post by earrame on 2009-05-25
After runing both procedures in your email I did the following over the weekend;

1. I left the AC adapter in. After about 12 hours the battery reached 27% charge. After 24 hours it was 100% charged.

2. A couple days later, with the power monitor reporting 100% charge and 1:40 of battery time, I unplugged the AC adapter.

3. Within 1 minute the power monitor reported 44.8% charge and 35 minutes of battery time remaining. (I did not use the computer after I unplugged the AC adapter. No apps were running.)

4. 20 minutes later I got the 'Critically Low' message with 5 minutes and 7% battery life remaining. It shut down a few seconds after that.

---

### Post by Lee_Machine on 2009-05-26
This just sounds like the holding capacity of your battery is down to nill. Try this: left click your battery applet, and then left click laptop battery.

Under Capacity: What does it say?

Like mine says 81% (fair)

---

### Post by PatrickVogeli on 2009-05-26
Do you usually let your laptop plugged into AC with the battery in place for long times?

---

### Post by earrame on 2009-05-26
Lee_Machine; I'll check that this evening when I am home.

PatrickVogeli; Yes

---

### Post by earrame on 2009-05-26
> **Lee_Machine said:**
> This just sounds like the holding capacity of your battery is down to nill. Try this: left click your battery applet, and then left click laptop battery.

Under Capacity: What does it say?

Like mine says 81% (fair)

Mine says:

Charge time: 1 hour 31 minutes
Capacity: 88% (Fair)

After running the test last night I have left it plugged in since then. It is still charging and only up to 68.8%

---

### Post by thomasaaron on 2009-05-27
That sounds like a worn out battery, as opposed to actual broken hardware. If you leave it plugged into AC all the time or run it down to zero a lot, it will decrease the capacity.

---

### Post by earrame on 2009-05-27
That's what it seems like. Would the capacity at 88% reflect a worn out battery?

It still strikes me as curious that this appeared shortly after the upgrade to Jaunty.

---

### Post by jdb on 2009-05-27
> **earrame said:**
> That's what it seems like. Would the capacity at 88% reflect a worn out battery?

It still strikes me as curious that this appeared shortly after the upgrade to Jaunty.

Yeah, that's the way the brain works, it loves to look for patterns & usually it's right.
Coincidences always throw me off the trail :)

jdb

---

### Post by thomasaaron on 2009-05-27
```
Would the capacity at 88% reflect a worn out battery?
```

It would at least reflect a battery that is *wearing* out.

> It still strikes me as curious that this appeared shortly after the upgrade to Jaunty. 

Perhaps, but I'm not seeing this issue on other computers after upgrading to Jaunty.

---

### Post by earrame on 2009-05-27
> **thomasaaron said:**
> [CODE]It would at least reflect a battery that is *wearing* out.

Perhaps, but I'm not seeing this issue on other computers after upgrading to Jaunty.


Still, we're looking at a sudden change in battery behavior shortly after the upgrade to Jaunty. It reeks of coincidence but I need to come up with some options. It doesn't seem to me that an 88% battery should be an issue. I would expect to see 20% battery life with the type of behavior my battery is displaying. Maybe I'll boot an Intrepid CD and see if anything changes.

I've never seen nor heard of anyone yanking their laptop battery every time when using AC. Is that normal? I'm asking because I honestly don't know. This Pangolin is the first notebook computer I have owned. I thought battery chargers were designed to not allow harm to the battery once 100% charge was reached. I know some of the cheaper AA/AAA chargers don't protect the battery this way.

I appreciate all the assistance. :)

---

### Post by jdb on 2009-05-27
> **earrame said:**
> Still, we're looking at a sudden change in battery behavior shortly after the upgrade to Jaunty. It reeks of coincidence but I need to come up with some options. It doesn't seem to me that an 88% battery should be an issue. I would expect to see 20% battery life with the type of behavior my battery is displaying. Maybe I'll boot an Intrepid CD and see if anything changes.

I've never seen nor heard of anyone yanking their laptop battery every time when using AC. Is that normal? I'm asking because I honestly don't know. This Pangolin is the first notebook computer I have owned. I thought battery chargers were designed to not allow harm to the battery once 100% charge was reached. I know some of the cheaper AA/AAA chargers don't protect the battery this way.

I appreciate all the assistance. :)

I bought my Daru2 in January of 2008 & whenever it's on my desk, which is most of the time, it's plugged in with the battery in it.
It still gets close to 3 1/2 hours on a fully charged battery & I don't dim the screen or do anything else to baby the battery.

When it's on the charger & fully charged the battery is cool to the touch.
There is a chip on board an LI battery pack that controls charging.
I've heard that storing LI batteries with a partial charge is better for them than storing them with a full charge, but I don't think it makes a significant difference.

jdb

---

### Post by thomasaaron on 2009-05-28
> I've never seen nor heard of anyone yanking their laptop battery every time when using AC. Is that normal?

That would not be normal. But that's not really what I'm trying to say. 

If you leave your battery in while having your ac plugged in ALL THE TIME, it can reduce the battery life (according to everything I've read on the subject). 

Also, if you CONSTANTLY run your battery all the way down to zero, it will eventually reduce your capacity (according to everything I've read on the subject).

---

### Post by earrame on 2009-05-28
Thanks jdb. That is some decent battery time. I didn't go for something with high bettery life because the extra cost really isn't neccessary for my home use. Perhaps down the road with Pangolin's successor (which will undoubtably be from System76) I will go for higher battery life.

My battery didn't really feel warm to the touch or anything but I wasn't paying particular attention to that. I will next time I am using it.

I read something about temperature monitoring on these forums that I want to relocate and study. My Pangolin feels very warm, perhaps even hot right under the fan. I started imagining that it feels hotter recently than it did months ago but that could just be the paranoia talking. :D

Off topic while I'm thinking about it; Tom, I got the bluetooth module in the mail a while back and I want to start using it. Do you have an instruction page for installing it or should I call you about it?

---

### Post by earrame on 2009-05-28
Thanks Tom, that is good info. I am seeking for knowledge on what I should be doing. I have no problem yanking the battery when I am going to be on AC for long periods of time. I know there is a limit to how many times a battery can be charged.

When I run on batttery, which on average is less than once a week, I usually run it down to zero. Since I've had the Pangolin (last August) I've probably run on battery down to zero somewhere in the neighborhood of two dozen times.

Just seeking answers and I appreciate all the help. At this point I'm not sure I see a solid reason for my battery to have tanked. Unless it is from the amount of time it spends on AC at 100% charge. But, the battery status info seems to belie a physical battery problem.

---

### Post by earrame on 2009-06-05
I just made another observation that I wanted to note here.

When I am running on battery power the Power Manager reads "Computer is running on AC power". So something (perhaps irrelevant) is wrong with the Power Manager.

Would any of the graphs in the power history be useful?

---

### Post by miniyak on 2009-06-05
i've been yanking the battery at full charge from the get go based on what the user manual said. This is allot less inconvenient then one would think it would be. i do kinda worry about exposed pins though, would dust be an issue here?

The manual gave me the impression that draining the completely battery was ok for some reason (i'll look at it again). Completely draining is something i do allot, just about every day in fact. If i change my habits what percentage should i plug in at?

---

### Post by PatrickVogeli on 2009-06-06
just in case it's useful: my girlfriend also leaves the battery in place always, and nearly always her laptop runs on AC power. Now, her battery will show nearly 90% capacity, bull won't last more than 20 minutes. Her battery hasn't really lost capacity, but it is unable to hold charge.

And costing something less than 300$, it isn't really affordable to exchange..

---

### Post by earrame on 2009-06-08
That sounds like an identical situation to mine.

It is very curous to me why there doens't appear to be any visible evidence of this. I would think the battery stats in the Power Manager would show it in the form of reduced capacity or something.

It is starting to appear that laptop battery chargers continue blasting the battery with a charge signal even when the battery is full. If that is in fact the case I would be pretty shocked to learn that laptops don't incorporate smart charging like a $40 AA/AAA charger.

---

### Post by earrame on 2009-06-16
> **PatrickVogeli said:**
> And costing something less than 300$, it isn't really affordable to exchange..

I took a quick look around and found this battery for $86. I'll probably replace it next Winter.

I would like to dig deeper into understanding the power manager but I don't really have time in the near future. Besides, I honestly don't care about little quirks and what not that don't really cause real issues. My enjoyment of Ubuntu and System76 is unblemished.

---

