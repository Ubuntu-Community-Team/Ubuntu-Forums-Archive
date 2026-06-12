---
title: "ubuntu_studio Freezes in a samsng S9"
date: 2013-08-29
forum: Ubuntu Studio
---

### Post by chava2 on 2013-08-29
Hi all,

I've got a Samsumg s9 (RAM: 4gig, I5, solid state hard drive). And it is just amazing. I just installed ubuntu studio 12.04 LTS. And for some reason every once in a while it freezes completely (I can't even use the ctrl+alt + F* terminals) and I have to do a hard reboot. As you can understand this is very frustrating  since I cannot rely on my laptop. 

Can anyone please help me ?

Thanks,
Chava.

---

### Post by dhunt84971 on 2013-08-29
When you say it "freezes" do you mean that it is completely unresponsive to the keyboard and mouse and the screen is simply stuck showing the same thing regardless of what you do and you subsequently need to hold the power button until it turns off?

If the answer is yes, this may be a hardware issue.  You may want to check that it is not overheating.  Try running:

sensors

If you have this installed it may tell you the temperature of your cpu.  If you do not have it installed it is available under lm-sensors in the Ubuntu Software Center.

---

### Post by chava2 on 2013-08-30
DEar[COLOR=#000000] dhunt84971,
[/COLOR]
By freezes I meant [COLOR=#000000]it is completely unresponsive to the keyboard and mouse and the screen is simply stuck showing the same thing regardless of what you do and you subsequently need to hold the power button until it turns off.
[/COLOR]
The output of the sensors command is the following:

chava@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +41.0°C  (crit = +106.0°C)
temp2:        +29.8°C  (crit = +106.0°C)

The output may not be very helpfull since my ubuntu is not freezed at the time I issued it. So everything may seem normal. 

If there is more data you need me to collect, kindly let me know.

Thanks!.

---

### Post by su:bhatta on 2013-08-31
Try running 'top' from the terminal once your system freezes(if you can) and see if it gives you any idea!

Also, what Graphics card are you using, are you running proprietory drivers for it?

If it is a case of overheating using proprietory drivers help.

---

### Post by chava2 on 2013-09-08
Hi all, 

I did this in order to find if the temperature was an issue and because of that it was geting hanged:

  while ((1)); do echo `sensors` >> Escritorio/temps; sleep 0.5;  done

And by the time it got freezed the temp was:

acpitz-virtual-0 Adapter: Virtual device temp1: +55.0°C (crit = +106.0°C) temp2: +29.8°C (crit = +106.0°C)

As you can see the temp is ok.... So ubuntu studio 12.04 LTS is getting hanged for another reason.

If it is not the temp, what could it be ??? 

I'm looking forward of getting your answear.

Thanks,
Chava.

---

### Post by su:bhatta on 2013-09-11
try running

```
top
```

to see if something is keeping the system overly engaged.

---

### Post by chava2 on 2013-09-19
When the lap top frezes I can not even get a ctr + alt + f1 to get a terminal and use the command top or any command. 

It completely freezes, no keyboard nor mouse is active.

Please help me, I really need help.

Thanks,
Chava.

---

### Post by jejeman on 2013-09-19
If this is a new hardware, try the latest Ubuntu version.

---

### Post by su:bhatta on 2013-09-20
> **jejeman said:**
> If this is a new hardware, try the latest Ubuntu version.

+1, 

try Ubuntu 13.04 or the Beta of 13.10 maybe a newer Kernel version is going to suit that Hardware.

---

