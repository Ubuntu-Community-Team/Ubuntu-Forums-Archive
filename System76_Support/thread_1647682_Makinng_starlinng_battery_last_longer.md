---
title: "Makinng starlinng battery last longer"
date: 2010-12-17
forum: System76 Support
---

### Post by tc101 on 2010-12-17
Is it true that if you keep your starling plugged in to a power source all the time that the battery will not last as long as if you let it discharge some times by running without being connected.

If this is true, how often and how much should you let the battery discharge for maximum life?

---

### Post by isantop on 2010-12-17
Leaving the battery plugged in for extended periods of time will gradually degrade battery life, but we're talking in the area of around 15-30% per year. Basically, the charge level and elevated heat accelerate the natural performance degradation of the battery. The best way to store a Li-Ion battery is at about 40% charged at about 20 degrees C. However, under these conditions, you'll still loose about 5% of the maximum capacity per year.

---

### Post by tc101 on 2010-12-17
Thanks.  I notice that if I just unplug the charger, I can not see the battery level.  To see the battery icon on the tool bar I have to unplug the power and then restart the computer.  Is there another way to see the battery level?

---

### Post by Dave_L on 2010-12-18
> Is there another way to see the battery level?

Install "acpi", and use the shell command:

acpi -b

---

### Post by tc101 on 2010-12-18
> Install "acpi", and use the shell command:
acpi -b

That works.  Thanks.  I also installed something called batmon but it doesn't give the same info as the shell script and I think it is probably wrong.  I installed battery charge graph, but I'll have to wait a few hours to see what it does.

The  shell script works fine, but are there any other GUI utilities you would recommend?

---

### Post by Dave_L on 2010-12-19
> **tc101 said:**
> The  shell script works fine, but are there any other GUI utilities you would recommend?

I haven't tried any other utilities.  There are some other topics discussing the bug:

[http://ubuntuforums.org/showthread.php?t=1599148](http://ubuntuforums.org/showthread.php?t=1599148)
[http://ubuntuforums.org/showthread.php?t=1576111](http://ubuntuforums.org/showthread.php?t=1576111)

---

### Post by Eyore15 on 2010-12-19
> **tc101 said:**
> That works.  Thanks.  I also installed something called batmon but it doesn't give the same info as the shell script and I think it is probably wrong.  I installed battery charge graph, but I'll have to wait a few hours to see what it does.

The  shell script works fine, but are there any other GUI utilities you would recommend?

My Starling isn't working at the moment, so I can't test this, but could you make a custom application launcher with the acpi -b command?  It's not a gui interface, but it keeps you from having to go the command line.

---

### Post by tc101 on 2010-12-20
When you need a new battery, how much does it cost and how much trouble is it to replace?

---

### Post by isantop on 2010-12-21
As of now, the batteries cost $69 for the 3-cell and $99 for the 6-cell. That may change in the future, but I imagine it won't fluctuate too much.

To replace them, there are a couple of clips on the bottom of the computer; one is spring loaded. Simply slide the clips to the side and pull the battery out.

---

### Post by tc101 on 2010-12-23
> Leaving the battery plugged in for extended periods of time will gradually degrade battery life

Wouldn't it be pretty easy to write an app that unplugged power to the battery after it is at 100% power for over an hour, then let it discharge to about 70%, then let charge back up and so on?  If this would extend battery life I am surprised no one has created one, or maybe they have.

---

