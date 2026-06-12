---
title: "Pangolin Battery Life :-("
date: 2008-12-29
forum: System76 Support
---

### Post by abulluck on 2008-12-29
I will be writing up a full review of my new Pangolin soon (want to get more time with it), but I wanted to address my biggest issue here so as not to clutter up my review (which will be very positive).

I will preface this by saying that I was fully aware of the battery limitations of the pangolin when I got it.

However; it would be nice to collect some info on what folks have done to improve it.  I already bring down my brightness to well below 50%, and I am supprised with the display's readability at that setting.

So, what are some suggestions to get this thing at least over 2 hours?

And what happened to the talk about a larger batter for the pangolin?

Thanks
Andy

---

### Post by Lee_Machine on 2008-12-29
For my Pangolin I run the program Laptop_Mode which spins down the hard drive when not in use. I also use the frequency applet in gnome to down clock the CPU.

With those and the brightness turned down I get around 1 hour 50 minutes. With normal load of web browsing or watching a movie.

I would like a 9 cell battery though, and one that is the same size.

---

### Post by thomasaaron on 2008-12-29
As for a larger battery, I'm not sure when/if one will be released. As for increasing battery life...

Battery life is largely dependent on how you are using your computer. If you typically use programs that tax your cpu, your battery will be used up more quickly than it will if you are using lighter programs. For example, playing a DVD will use your battery much more quickly than, say, a word processing program.

Here are a few things I know of that can maximize your battery life.

1. SCREEN BRIGHTNESS
Go to System > Preferences > Power Management. Under the AC tab, set your brightness. Under the Battery Tab, select the checkboxes labled: "Dim Display When Idle" and "Reduce Backlight Brightness."

2. POWERTOP
Go to a terminal (Applications > Accessories > Terminal) and install powertop by running this command: sudo apt-get install powertop
Then start powertop by running this command: sudo powertop
Powertop will present you with opportunities to press keys that will kill un-needed services. You must leave the terminal open to keep powertop running, but you can minimize the terminal so that it isn't visible.

3. STARTUP PROGRAMS
Go to System > Preferences > Sessions > (Startup Programs Tab) and uncheck any startup sessions you do not need. It is not a good idea to uncheck startup programs unless you are sure you really do not need them. Some that are generally safe to remove are: Bluetooth Manger, Evolution Alarm Notifier, Remote Desktop, Tracker, Tracker Applet, and Visual Assistance.

4. SEARCHING AND INDEXING
Go to System > Preferences > Searching and Indexing and select the checkboxes labled: "Disable All Indexing When on Battery" and "Disable Initial Index Sweep When On Battery."

---

### Post by Peebles on 2009-02-05
I'm considering buying a new Pangolin, but battery life is an absolute deal-breaker for me. Is it still around two hours under normal usage, or has there been some improvement on this front?

---

### Post by betrunkenaffe on 2009-02-05
Battery life really is the only complaint I have about the Pangolin, it seems odd that there isn't even an option for at least 9 cell. That being said I get around 1.5 hours - 2.5 hours depending on usage. If I barely touch it, it's around 2.5 hours. I'll try that powertop app and see if that helps.

---

### Post by axel_2078 on 2009-02-06
Wow, the battery life is really that short? That kind of sucks. I was thinking about ordering one of these soon. Why isn't there an option for a 9-cell battery? How much more time could you squeeze out of a 9-cell (roughly; I know this is just an estimate)?

---

### Post by finite9 on 2009-02-06
im thinking of a gazelle, and im really concerned about battery time.

on a Thinkpad T61, I got 5.5 hrs when it was new...whilst actually working.

My HP dv9297 now gets maybe 45mins to 1hr during use after 2 yrs.  When new, it probably got 2-2.5hrs during use.  My Acer WLMI 5201 went the same way... 2 hrs when new.  I think these are both 4 cell batteries.

LiIon sucks.  They die quickly.  When new, they get manufacturers spec for usage, but this decreases *rapidly* during the first year.  After 2 yrs you're looking at a new battery.  Unfortunately, LiIon is the only choice.

Becuase of my experience, I want at least 5hrs according to manufacturer spec.  Only an 8 cell battery will give you this.  A 4 cell will only give about 2 hrs.

So im looking at the gazelle with the 8 cell battery, but Apple Macbook gives 5 hrs on their standard battery... tough choice.

Of course, powernowd, laptop_mode and hdparm to spin down the discs is a give.

---

### Post by betrunkenaffe on 2009-02-06
For those that are concerned about the life of the Lithium Ion batteries (and Lithium Polymer [Apple's new battery] which have same characteristics), you should read up on how to treat/extend the life of them.

[http://www.batteryuniversity.com/partone-12.htm]("http://www.batteryuniversity.com/partone-12.htm")

There are other resources on it but that's one. First thing to note is if you aren't charging or using the battery (like I currently am doing, I'm plugged in on table) then you should charge to 40% or so and remove. Keeping around that point will keep it alive longer as well as prevent the gauge from screwing up as quickly. Secondly, try not to fully drain the battery unless you have to, as Thomas Aaron said, it's bad for them. Finally, don't buy spares unless you REALLY need to have a back up battery, they lose charge the same as your regular battery will.

I'll charge the battery back to 100% when I know I'm going to possibly be in a situation that I won't have power access and drain it/charge it to 40% once done with it. It'll be rather rare that I don't have a power source.

From a quick google search it appears 9 cell batteries give 33% more battery life than 6 cell batteries. If someone can please verify this, that would be nice.

I'm curious as to how much work/research has gone into the idea of switching to lithium-ion polymer batteries for the notebooks, I know I'd be interested in getting more life out of my laptop (especially if it would either minimize or eliminate the "stick out" effect). I knew I wouldn't get the battery life I wanted out of the Pangolin, but I have my hopes and dreams :)

There also seems to be some room for improvement with the power management options as my screen auto drops to 50% when on battery when I'd prefer it to go to 25% and back to 100% once on AC again. With that being said, I'm hoping that there'll be some software improvements within the next few months which will bring the battery life up.

---

### Post by formol on 2009-02-08
yeah, battery, the only bad thing about my pangolin.  so, I always got the ac adapter with me.

to save battery power, we can also turn off the wireless.  wireless constantly search for network, and it take power.

---

