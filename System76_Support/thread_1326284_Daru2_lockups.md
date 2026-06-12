---
title: "Daru2 lockups"
date: 2009-11-14
forum: System76 Support
---

### Post by williumbillium on 2009-11-14
I'm experiencing system lock ups on my Darter Ultra 2 on a daily basis.  When it happens I can still move the mouse but there's no response to mouse clicks or key presses.  I've tried leaving it for up to half an hour and the system never comes back.

At the moment I'm having to do a hard poweroff by holding down the power button.  This is happening on a daily basis :(

I have this in /var/log/messages every time it hangs:

```
Nov 14 09:37:28 koe kernel: [  163.797836] CE: hpet increasing min_delta_ns to 15000 nsec
Nov 14 09:40:44 koe kernel: [  359.691261] CE: hpet increasing min_delta_ns to 22500 nsec
Nov 14 09:47:32 koe kernel: [  768.414291] CE: hpet increasing min_delta_ns to 33750 nsec
```

This leads me to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798)

Which has been open for over a year and people are still experiencing on Karmic.

Is anyone else experiencing this problem and has any kind of workaround?

I did notice the same error in the logs of someone else with a Daru2 who was experiencing touchpad issues:

[http://ubuntuforums.org/showthread.php?p=6951730&highlight=hpet#post6951730](http://ubuntuforums.org/showthread.php?p=6951730&highlight=hpet#post6951730)

I'm running Jaunty with 2.6.28-11-generic.

Let me know if you need any more info. Thanks.

---

### Post by williumbillium on 2009-11-14
I tried adding clocksource=jiffies as suggested in the bug report but X would not start.

---

### Post by williumbillium on 2009-11-14
now trying with hpet=disable which seems to make it use acpi_pm:

```
$ cat /sys/devices/system/clocksource/clocksource0/current_clocksource 
acpi_pm
```

will report back on what happens.

---

### Post by thomasaaron on 2009-11-16
There is a power management issue on the DarU2 that requires acpi=noirq as a kernel option, but there are no pre-existing freeze issues on the DarU2 that require kernel options.

Please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

---

### Post by ackey on 2009-11-17
> I did notice the same error in the logs of someone else with a Daru2 who was experiencing touchpad issues:

I can happily report that my touchpad issues are gone with a hardware replacement.  I *do* still see the error messages you are talking about.  I seem to have lost the acpi=noirq option - upgrading to grub2 and fixing that is on my to do list.

While I do see the messages, I don't have any problematic hang ups.  I believe I see a momentary "pause" in system response, but it is brief enough to appear like a hiccup in the mouse movement.  My system gets used about 10 hours a day - if there is a certain min_delta_ns that is triggering it, I might not be getting there.

From my dmesg (7 hours uptime currently)
```

[  665.588059] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1589.659938] CE: hpet increasing min_delta_ns to 22500 nsec
[25249.957067] CE: hpet increasing min_delta_ns to 33750 nsec

```

---

### Post by williumbillium on 2009-11-24
> **thomasaaron said:**
> There is a power management issue on the DarU2 that requires acpi=noirq as a kernel option, but there are no pre-existing freeze issues on the DarU2 that require kernel options.

Please go to System > Administration > System76 Driver > Support (tab) > Create (button). This will create an archive called logs.tar in your home directory. Please attach that archive to this thread.

I'll have a look at it and see what I can figure out.

Hi Tom.  I've attached my logs.  The latest lock ups were on Nov 24th at around 8:15 AM and then again at around 8:35 AM both after an hour of uptime or less.

hpet=disable didn't help at all and I still got lockups consistently.  I didn't initially have the acpi=noirq option (I didn't think it was still necessary), adding it back in didn't make any difference to this problem.

Thanks for any help.

---

### Post by thomasaaron on 2009-11-24
Have a look at this bug...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798)

This is the offending error message...
```
CE: hpet increasing min_delta_ns to 33750 nsec
```

Does that sound like the symptoms you're seeing? Do any of the workarounds therein work for you?

---

### Post by williumbillium on 2009-11-25
> **thomasaaron said:**
> Have a look at this bug...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798)

This is the offending error message...
```
CE: hpet increasing min_delta_ns to 33750 nsec
```

Does that sound like the symptoms you're seeing? Do any of the workarounds therein work for you?

I agree that that sounds like what I'm experiencing.  However the system doesn't recover from the lockups for me and I have to hold down the power button to turn of the computer.

I tried adding clocksource=jiffies as a kernel parameter as suggested in the bug report but X would not start.

I also tried with hpet=disable which seems to make it use acpi_pm instead.  I still got the lockups, and the "hpet increasing..." message was not present in my logs.

---

### Post by thomasaaron on 2009-11-25
Let's rule out a memory problem. Please run memtest86 on your system.

> Reboot your computer. When you see the grub countdown menu, press the 'Esc' key. When you see the grub menu, press your 'down' arrow until Memtest86 is highlighted. Then press 'Enter' to start testing.

Please start Ubuntu in the evening before going to bed and let it run all night long. Memory card problems can be subtle, and sometimes they will not show up until the cards start heating up. Often it will take several passes before errors appear.

Please email us the results of your testing.   

---

### Post by williumbillium on 2009-12-10
Just a quick update to say that Memtest86 didn't find any errors.

I decided to install karmic last weekend and haven't had any lockups so far.

---

### Post by pveurshout on 2009-12-27
I had the same problem with Jaunty, although it was somehow dependent on the kernel version used. 2.6.28-15 and -17 worked fine, but -14 and -16 (and perhaps -11, -12 and -13 too - never really used those) resulted in random, complete freezes. In [this]("http://ubuntuforums.org/showthread.php?t=1135055&page=74") thread there were a lot of positive experiences with Karmic (only after a clean install - don't upgrade from Jaunty!) from people who had Jaunty freeze on them all the time. How's Karmic working out for you? :)

---

