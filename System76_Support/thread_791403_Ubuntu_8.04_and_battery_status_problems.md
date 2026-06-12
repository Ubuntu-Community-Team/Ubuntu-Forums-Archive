---
title: "Ubuntu 8.04 and battery status problems"
date: 2008-05-12
forum: System76 Support
---

### Post by izquierdista on 2008-05-12
Hello,
I just updated to Ubuntu 8.04 on my Daru2. The install went well. The first problem that I have noticed even after installing the System 76 drivers is that the power notification is not working properly.

So far the icon stays on the AC power state and does not change back and forth whenever the AC power cord is disconnected. Is system 76 working on this?

---

### Post by badbull on 2008-05-12
There are some other threads on this problem. take a look at this [http://ubuntuforums.org/showthread.php?t=772722](http://ubuntuforums.org/showthread.php?t=772722) and this [http://sudan.ubuntuforums.com/showthread.php?t=609722&page=15](http://sudan.ubuntuforums.com/showthread.php?t=609722&page=15)

System76 is still working on this problem. I'm currently using a selfbuild kernel, which enables the acpi polling mode. this fixes the battery status problem, but not the suspend problems.

---

### Post by thomasaaron on 2008-05-12
If you download and run the latest System76 driver (version 2.2.1) from planet76.com/repositories, it will cure the battery status problem. Unfortunately it will also mess up your brightness function keys.

We are working on a better solution to this -- and a solution to the suspend problem.

---

### Post by laserline on 2008-05-12
Hi Tom,

I installed the latest driver (2.2.1) -- That means I can stop passing 'acpi=noirq' at grub (I didn't want to manually change menu.lst because I thought the fix would come quick)

Thanks,
Idan.

---

### Post by laserline on 2008-05-13
Hi Tom,

I would like to report that the new driver does NOT fix the battery status.

The battery keeps getting lost, and sometimes the acpi reports i'm working with AC cable, even when it's off.

My system is a 'daru2'.

Please take a better look at this, as the driver only fixes the alsa and installes the led fix (which I don't think is necessary)

Thanks,
Idan

---

### Post by thomasaaron on 2008-05-13
OK. I'm sorry to ask this. But, alas, I must...

Did you *run* the driver? System > Admin > System76 Driver > Install Tab > Install Button...

...and then reboot?

---

### Post by laserline on 2008-05-13
Hi Tom,

Of Course I did that :)

Look at the file 'driverscontrol.py' the daru2 only calls alsa and the led fix...
And if we are looking inside the drivers, when choosing the 'restore' option, the 'gsynaptics' is automaticaly installed on 'daru2', but the xorg.conf file isn't updated, so when trying to start 'gsynaptics', the SHM error comes up....

Idan.

---

### Post by ctsdownloads on 2008-05-13
> **thomasaaron said:**
> OK. I'm sorry to ask this. But, alas, I must...

Did you *run* the driver? System > Admin > System76 Driver > Install Tab > Install Button...

...and then reboot?

Been here before. I once downloaded and installed the driver. But then totally forgot to actually goto the menu, select it and run that sucker. I can relate to this moment on another issue. :oops:

---

### Post by thomasaaron on 2008-05-13
Hmmm...

Could you please post the output of...
cat /boot/grub/menu.lst

Let's have a look under the hood. Thanks for your patience. I hate asking questions like that. But it often pays off. :lolflag:

---

### Post by thomasaaron on 2008-05-13
I was just looking at an earlier post.
The driver should insert that kernel option. You should not take it back out -- if that's what you did.

---

### Post by laserline on 2008-05-13
Tom, it's ok :)

Attached is my menu.lst file.
It's the default file shipped with hardy. I manually start by adding 'acpi=noirq' to fix the battery issue.
As fas as I see, the system76 driver doesn't touch menu.lst

Thanks,
Idan

---

### Post by laserline on 2008-05-14
> **thomasaaron said:**
> I was just looking at an earlier post.
The driver should insert that kernel option. You should not take it back out -- if that's what you did.

Hi Tom,

1. What was the post you were looking at ?

2. As I said earlier, I never touched 'menu.lst' -- I was waiting for the official fix.
The easiest part for me was to add it to the default area  and run 'update- grub'.

3. Can you point me to the place where the Driver is supposed to add that kernel option ?

4. When there will be a fix for the suspend and battery monitor by the system76-driver, I'm going to wipe and re-install the whole system (again!) -- that will give you guys some extra testing.

Idan

---

### Post by thomasaaron on 2008-05-14
> 1. What was the post you were looking at ?

This post confused me as to what you were attempting.

```
Hi Tom,

I installed the latest driver (2.2.1) -- That means I can stop passing 'acpi=noirq' at grub (I didn't want to manually change menu.lst because I thought the fix would come quick)

Thanks,
Idan.
```
> 
3. Can you point me to the place where the Driver is supposed to add that kernel option ?

My mistake. I was wrong. At any rate, you will continue to need that option in /boot/grub/menu.lst for now to keep the battery indicator from being flaky.

> 4. When there will be a fix for the suspend and battery monitor by the system76-driver, I'm going to wipe and re-install the whole system (again!) -- that will give you guys some extra testing.

The battery monitor workaround is adding the kernel option. As for an ETA on a permanent fix, I don't know for sure. They are still holed up working on it.

---

### Post by laserline on 2008-05-14
Thanks for your reply,

I really hope you get that fixed.

On Gutsy, the 'ec_intr=0' was responsible for the battery to work or the suspend feature (or both?)

Thanks,

Idan.

---

### Post by thomasaaron on 2008-05-14
That kernel option only fixes the battery monitor. If you need Suspend to work, you will have to run Ubuntu 7.10 64-bit for the time being.

---

### Post by laserline on 2008-05-14
I'll keep my breath with Hardy :-)

BTW, The 'daru2' is an MSI laptop, do you have other MSI products / Laptops that have the same problems ?

Thanks,
Idan.

---

### Post by zombiepig on 2008-05-15
Mike Trim found a fix for this that worked with my msi s271 - see
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/218094](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/218094)

Basically, if I add msi-laptop to the /etc/modprobe.d/blacklist file then reboot, my battery status works fine. 

Hope that helps someone!

---

### Post by badbull on 2008-05-15
i don't think this will work for the daru2 or msi pr200 (but i didn't test it). as workaround they blacklisted the msi-laptop module. on my system this module isn't loaded and not loadable. so this cannot cause the problems on the daru2.

---

### Post by bkloppenborg on 2009-02-25
For those of you following this forum, there is a kernel patch that has proven to be quite promising.  With the patch installed, you no longer need the specify any ACPI-related kernel parameters no do you need any special scripts.  

At the moment, I have been running with the patch, without any kernel parameters, and have yet to lose my battery's status once in the last four days (uptime ~14 hours per day).


For more information see [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/323823](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/323823)

---

