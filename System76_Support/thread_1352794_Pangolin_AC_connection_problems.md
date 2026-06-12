---
title: "Pangolin AC connection problems"
date: 2009-12-12
forum: System76 Support
---

### Post by exodus_ms on 2009-12-12
I'm using a Pangolin Performance with Karmic installed.

Has anyone else experienced any problems with their AC cord adapter? More specifically the connection from the cord to the laptop. When my laptop is running on AC, I will get the "Battery Discharging" from the notification applet, and the screen will dim. Then, the screen will brighten back up, and the laptop will resume running off AC. This will happen a few times within a couple of seconds. It is very annoying to have the screen dim and brighten back up several times within a few seconds.

If I move the laptop it will lose it's AC connection and again the screen will dim, notification applet alerts "Battery Discharging"... To get the AC connection to work again, I have to move the cord (the plug that plugs into the laptop) around until the screen brightens back up and the laptop resumes running on AC.

I purchased another AC adapter thinking the problem was with the cord itself. I experience the same behavior with the new cord. I have noticed that the cord where it plugs into the laptop becomes extremely hot, the male end that plugs into the laptop is too hot to touch.

The only way that I can describe this is, it's almost like the part on the laptop where the cord plugs into is slightly too big, just enough to cause the plug to not fit tightly.

**I have a couple of questions:**

A. Will this rapid and constant changing from AC to BAT damage my system?

B. Should the metal plug on the AC adapter that plugs into the laptop become so hot that it cannot be touched?

C. Is it possible that there is a problem (hardware) that needs to be fixed to correct this behavior?

I would appreciate any help you all could provide. I'm having a hard time explaining this but if anyone has any ideas I would really appreciate it.

_**SYSTEM:**_
Processor: 2x Intel(R) Core(TM)2 Duo CPU T6400 @ 2.00GHz
Memory: 4025MB
OS Ubuntu: 9.10
Kernel: Linux 2.6.31-16-generic (x86_64)
Distribution: Ubuntu 9.10

_**BATTERY INFO**_
/proc/acpi/battery/BAT0/info

present:                 yes
design capacity:         4400 mAh
last full capacity:      4256 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            M740TX
serial number:            
battery type:            LION
OEM info:                Clevo CO.

---

### Post by jdb on 2009-12-12
> **exodus_ms said:**
> I'm using a Pangolin Performance with Karmic installed.

Has anyone else experienced any problems with their AC cord adapter? More specifically the connection from the cord to the laptop. When my laptop is running on AC, I will get the "Battery Discharging" from the notification applet, and the screen will dim. Then, the screen will brighten back up, and the laptop will resume running off AC. This will happen a few times within a couple of seconds. It is very annoying to have the screen dim and brighten back up several times within a few seconds.

If I move the laptop it will lose it's AC connection and again the screen will dim, notification applet alerts "Battery Discharging"... To get the AC connection to work again, I have to move the cord (the plug that plugs into the laptop) around until the screen brightens back up and the laptop resumes running on AC.

I purchased another AC adapter thinking the problem was with the cord itself. I experience the same behavior with the new cord. I have noticed that the cord where it plugs into the laptop becomes extremely hot, the male end that plugs into the laptop is too hot to touch.

The only way that I can describe this is, it's almost like the part on the laptop where the cord plugs into is slightly too big, just enough to cause the plug to not fit tightly.

**I have a couple of questions:**

A. Will this rapid and constant changing from AC to BAT damage my system?

B. Should the metal plug on the AC adapter that plugs into the laptop become so hot that it cannot be touched?

C. Is it possible that there is a problem (hardware) that needs to be fixed to correct this behavior?

I would appreciate any help you all could provide. I'm having a hard time explaining this but if anyone has any ideas I would really appreciate it.

_**SYSTEM:**_
Processor: 2x Intel(R) Core(TM)2 Duo CPU T6400 @ 2.00GHz
Memory: 4025MB
OS Ubuntu: 9.10
Kernel: Linux 2.6.31-16-generic (x86_64)
Distribution: Ubuntu 9.10

_**BATTERY INFO**_
/proc/acpi/battery/BAT0/info

present:                 yes
design capacity:         4400 mAh
last full capacity:      4256 mAh
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
capacity granularity 1:  64 mAh
capacity granularity 2:  64 mAh
model number:            M740TX
serial number:            
battery type:            LION
OEM info:                Clevo CO.

You definitely have a bad connection.
That's what's making it hot, power is being dropped
on resistance in the connection.
Worse case is it could catch on fire, it needs to be fixed.

jdb

---

### Post by exodus_ms on 2009-12-12
> **jdb said:**
> You definitely have a bad connection.
That's what's making it hot, power is being dropped
on resistance in the connection.
Worse case is it could catch on fire, it needs to be fixed.

jdb
[B]jdb,

[/B] Thanks for the reply. I guess I should contact system76 about this issue. Man, this sucks.

---

### Post by miniyak on 2009-12-13
i just got a hold of a hp tc4400 that has this issue, the problem seems to be with the socket and not the plug. In the case that it is the socket sometimes the solder points have be broken or the contact point that hug the plug have lost their resiliency. In the first case you can possibly de-solder then resolder back but that is something you should probably have experience doing before attempting. In the second case its pretty much the same deal accept you have to replace the socket which you probably find online somewhere.

I think the bottom line is that this type of issue really is a pain. If you can get help from s76 that would probably be the best line of action. 

Lucky for me I going to get a docking station for the HP tablet and i won't have to mess with it

as far as the pangolin ac adapter goes, i think that it get plenty hot regardless of malfunction.

---

### Post by exodus_ms on 2009-12-14
Thanks for all the replies. I have found something that works.

[IMG]http://lh4.ggpht.com/_xugXSvvju-U/SyZ_-oFbQMI/AAAAAAAABG4/Wkz1n3IFK-U/s144/ac-jack.jpeg[/IMG]

In the picture above you will notice that I have placed a piece of paper (folded several times) in between the plug and the jack. This makes the connection very tight and secure. I have also noticed that since I have done this, the AC adapter box and the plug itself are not as hot as they were before. They are significantly cooler.

The problem is with the jack itself. It appears it is slightly too big for the connector. This could have happened over time (within 6 months) maybe. Or like **miniyak** suggested "the contact point that hug the plug have lost their resiliency". Whatever the reason I do know that everything related to the input connection and the cord itself are significantly cooler. When the connection wasn't secured, everything became very hot.

Padding the area around the the plug and the jack is not my ideal resolution, but it works.

---

### Post by miniyak on 2009-12-14
ha ha, DIY ftw!

I would air on the side of caution though, just as jdb pointed out, this could be a fire hazard.  

I kind of surprised this happened though, the socket seems to be fairly rugged on my panp5. Do you have a panp5 or 4? I wonder if the two sockets are different

---

### Post by exodus_ms on 2009-12-14
**miniyak**,

I have a panp5 as well, I have had it ~6 months. I wish there was a way to get the power history info from right-clicking on my battery icon in the panel, there doesnt seem to be a way to generate a report from there. 

exodus@s76:/proc/acpi$ ls --group-directories-first 
ac_adapter  battery  button  embedded_controller  fan  power_resource  processor  thermal_zone  video  dsdt  event  fadt  info  sleep  wakeup

Not the info I wanted from ac_adapter or battery. I'll post a screen shot of what I'm talking about.

**History**

[IMG]http://lh3.ggpht.com/_xugXSvvju-U/SyaHvh3qBgI/AAAAAAAABHA/xkL9nNphr4I/s800/history.png[/IMG]

**Stats**

_[IMG]http://lh4.ggpht.com/_xugXSvvju-U/SyaHvcvIklI/AAAAAAAABG8/hpD4qwwkjDU/s800/stats.png[/IMG]_

---

### Post by miniyak on 2009-12-14
what desktop manager are you using? that looks like E11... right?

In gnome you can get your power history with a right click but still i think it has a hard time estimating discharge times or logging multiple sessions. 

Logging multiple session and comparing to actual time/date vs. backtracked time would definitely help you see when your droping AC power

---

### Post by exodus_ms on 2009-12-14
I'm using Gnome. I have the top panel hidden. Other than that it's just conky for the stuff on the right, and cairo-dock on the bottom. Compiz also, but you cant see that :P

Those screen-shots above are from right-clicking on the battery applet in the notification area.

The 1st one is the power history for the past week.
The 2nd one is the stats from the past week. Notice how the connection factor shows a rapid fluctuation.

---

