---
title: "Best battery life within S76?  (non netbook)"
date: 2009-04-30
forum: System76 Support
---

### Post by abulluck on 2009-04-30
Ok, I may get the opportunity to purchase my work PC on my own and I would like to consider a system76.  Something that is important to me is battery life.

I have a pangolin at home, and I wouldn't be able to live with its battery life at work. So, that would probably leave me with the darter or gazelle.  

Between the two, which gets the best batter life, and you can consider the larger battery option as I would probably go that route anyway.

And for the larger batteries, how much do they stick out (Picutres anyone?).

Oh and the types of things I would need to do on this laptop are typical office applications, database work, and a lot of work in sharepoint (I will be running xp in virtualbox for this).  

Thanks
Andy

---

### Post by thomasaaron on 2009-04-30
The Gazelle and Darter are going to be pretty close. The Gazelle may have the edge due to the LED backlit screen.

The Gazelle comes with a 4-cell battery, and you can order an additional 8-cell battery.

The 4-cell gets approximately 1.5-2 hours, and the 8-cell gets approximately 3-4 hours. Usage is largely dependent on usage.

We also provide a tutorial for maximizing battery life.

(It is not possible to order the larger battery *instead* of the smaller one. The chassis comes to us with the smaller battery, and we actually have to order the larger one separately. So, we only provide the larger battery as an extra.)

---

### Post by abulluck on 2009-04-30
Thanks Thomas.

No problem on the 4 cell coming standard.  I knew that, and I would want both anyway.

Those times are in my range, so the decision will be easy.

I hope this option comes through with my company, as I will be happy as can be working on a S76 Gazelle at work running ubuntu.

---

### Post by miniyak on 2009-05-01
Sorry, i only did a quick search, where is the tutorial located?
I'm thinking of getting the pangolin, is under clocking/cpu throttling possible?

---

### Post by thomasaaron on 2009-05-01
Voila.

> Battery life is largely dependent on how you are using your computer. If you typically use programs that tax your cpu, your battery will be used up more quickly than it will if you are using lighter programs. For example, playing a DVD will use your battery much more quickly than, say, a word processing program.

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

5. CPU Scaling
Right click on your upper panel and select "Add to Panel." Scroll down and select the "CPU Frequency Scaling Monitor" and then click the add button. Now you should have an applet on your upper panel that gives you various options for throttling your CUP.   

...frequency scaling does work.

---

### Post by miniyak on 2009-05-01
thanks Tom, now that you mention it i think i remember seeing the scaling options on my own rig when i was messing the panel.

would Xfce make a difference in regard to power consumption? 

say i was only using firefox with all of the recommended power saving solutions presented. Do you think the pangolin would run more then 2 hours? if so, how much longer?

---

### Post by 3Miro on 2009-05-01
I get about 1:30 - 1:45 on my pangolin with compiz running and not all the options of the tutorial selected.

To toss an idea, if you will be using the laptop on battery for long, then you might consider getting a second battery and then Hibernate (not suspend) -> Swap Battery -> Resume. Nuisance, but might be worth it.

---

### Post by miniyak on 2009-05-02
i was thinking of a getting a second battery. but im going to try without first just to see if the base life suits my needs and like 3Miro noted, battery switching seems like sort of a nuisance. dose anyone have experience with this? Is it practical?

If i want the extra later, there seems to be an option to order the battery separately.

---

### Post by thomasaaron on 2009-05-02
Yeah, I change batteries all the time. It's no big deal. Shut down, change the battery, reboot. I guess it's a little bit of a nuisance, but not enough to worry about.

---

