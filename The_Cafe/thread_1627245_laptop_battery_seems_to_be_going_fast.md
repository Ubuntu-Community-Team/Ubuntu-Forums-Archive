---
title: "laptop battery seems to be going fast"
date: 2010-11-21
forum: The Cafe
---

### Post by markp1989 on 2010-11-21
I have had this laptop since late August, and im already starting to see the battery life decrease ( i have lost about 500 mAh already), Im looking for tips to slow this down, because at this rate im going to have nothing left in a year. 


```
mark@mark-Aspire-3810TZ:~$ cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         5600 mAh
last full capacity:      5138 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 0 mAh
design capacity low:     0 mAh
cycle count:		  0
capacity granularity 1:  100 mAh
capacity granularity 2:  0 mAh
model number:            AS09D36
serial number:           C625
battery type:            LION
OEM info:                SSANY
mark@mark-Aspire-3810TZ:~$ 

```

my basic usage pattern is that I use the laptop downstairs in the evening till ubuntu auto shuts down, then after that I will go up stairs and put it on charge, I leave it plugged in most nights to make sure i have a full battery for uni in the morning. 
 
looking for tips to stop the battery diminishing any more as I have already lost about 8% capacity 

Thanks for reading Mark

---

### Post by Lucradia on 2010-11-21
It's often not the battery itself that is the cause. For example, some netbooks and laptops from Toshiba have an issue where the battery will still drain after being shut off when using linux, but not windows.

This is because Windows has the ability to turn off all the hardware, but Linux can't. Some hardware that may be on even when shut off: Ethernet, Wireless, USB.

You may have had a similar problem.

---

### Post by madjr on 2010-11-21
oops double post//

---

### Post by madjr on 2010-11-21
its never good to go below 15 - 25% every day.

here's some info about the charge / discharge cycle:
[http://www.mpoweruk.com/life.htm](http://www.mpoweruk.com/life.htm)

having 2 batteries is the ideal situation and can extend the life of both of them dramatically.

you may also try this app (if your laptop supports it):
[http://www.webupd8.org/2010/11/granola-improves-your-netbooklaptop.html](http://www.webupd8.org/2010/11/granola-improves-your-netbooklaptop.html)

---

### Post by madjr on 2010-11-21
> **Lucradia said:**
> It's often not the battery itself that is the cause. For example, some netbooks and laptops from Toshiba have an issue where the battery will still drain after being shut off when using linux, but not windows.

This is because Windows has the ability to turn off all the hardware, but Linux can't. Some hardware that may be on even when shut off: Ethernet, Wireless, USB.

You may have had a similar problem.

huh?
sources?

well his laptop seems to be an acer, not a toshiba

---

### Post by aeronutt on 2010-11-21
I learn something everytime I poke around here; didn't know this file existed. /proc/acpi/battery/BAT0/info 

Thanks!


FYI, I had noticed my battery having less capacity after a full charge too, so this file reveals

design capacity:         5200 mAh
last full capacity:      3883 mAh

But my battery is more than 2 years old.

---

### Post by aeronutt on 2010-11-21
> **Lucradia said:**
> It's often not the battery itself that is the cause. For example, some netbooks and laptops from Toshiba have an issue where the battery will still drain after being shut off when using linux, but not windows.

This is because Windows has the ability to turn off all the hardware, but Linux can't. Some hardware that may be on even when shut off: Ethernet, Wireless, USB.

You may have had a similar problem.

That's an interesting comment. Come to think of it, my Dell has a 'wifi finder' button that when pushed with computer off, it flashes if it finds a wifi signal. Wonder if it uses any power when the computer is off?

---

### Post by Lucradia on 2010-11-21
> **madjr said:**
> huh?
sources?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784)

Have fun reading it.

---

### Post by madjr on 2010-11-21
also a tip if your battery doesnt want to re-charge completely (lets say it stays at: 90 - 98%)

it that happens to you, just unplug it a few minutes and plug it back in, till it starts to fill the gap.

if it gets stuck again, repeat the unplugin / plugin back.

---

### Post by madjr on 2010-11-21
> **Lucradia said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784)

Have fun reading it.

thx, i wont be buying a toshiba now

---

### Post by markp1989 on 2010-11-21
Thanks for getting back to me :) 

I do have an issue with ubuntu, it warns be about the battery way before the hardware lights come on, it warns me at about 20% remaining, considering this laptop has a 8hour battery 20% is still over an hour left, so i have gotten in to the habit of ignoring ubuntus battery warnings, if i could remember how to change the warning threshold on the gnome battery monitor to match the hardware battery light, i would pay more attention to ubuntus warnings.

the day i got the laptop, i did time the battery life to see how long it would last when web browsing, and i got about 8:10 out of it, I dont know how long i would get now as i have never timed it. 

i just installed Granola, seems like an interesting program, im not sure if its actually doing anything, I will have to check it properly later on.


@ madjr : thanks for the tip, I will try that when i get home to see if i can get any of the lost capacity back :)

---

