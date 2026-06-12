---
title: "Gazelle Professional Boot Time"
date: 2013-01-27
forum: System76 Support
---

### Post by nmg49 on 2013-01-27
I just purchase a System 76 Gazelle Professional laptop around a month ago and so far, I've been extremely satisfied with it. My one complaint however, is with the boot time. When I start my machine up, it shows a blank purple screen for about 10 second, before it starts showing the Ubuntu loading symbol. I wonder if its actually loading something in this time, or if its just stuck on something. Is there any way to fix this? I just think its kind of lame that my old HP Computer (which was running a Core 2 Duo) can boot Ubuntu faster than my Gazelle (which has a 3rd gen i7). Thanks.

---

### Post by tgalati4 on 2013-01-27
Try turning kernel modesetting (kms) off, there are tutorials on how to do it.

---

### Post by isantop on 2013-01-28
> **tgalati4 said:**
> Try turning kernel modesetting (kms) off, there are tutorials on how to do it.

We'd recommend against this, as it breaks some other system functionality that's particularly useful to laptops.

In general, the boot time represents a very small amount of time spent on the computer, and shaving the ten seconds in half doesn't represent a significant increase in usage time. If the system is booted five times per day (which is pretty excessive with suspend/resume), then you'd save a total of twenty five seconds per day.

---

### Post by nmg49 on 2013-01-31
I don't want to do anything that could harm my computer... Any other ideas?

---

### Post by isantop on 2013-02-01
> **nmg49 said:**
> I don't want to do anything that could harm my computer... Any other ideas?

Unfortunately, this is the time it takes to get Ubuntu loaded into memory initially, then get it up and running. It can't really be safely reduced. It isn't stuck, and is acutally performing system operations during this time.

---

### Post by lolwtfhax on 2013-02-04
You could compile a custom kernel and strip out anything that is not needed. You can usually shave a few seconds off this way.

Also, I've been using Arch Linux for the last few years and have just recently decided to try out Ubuntu again so I'm not too familiar with its' boot process anymore. I'm sure it has changed quite a bit. But I'm sure there are some services starting up that aren't necessarily needed at boot time. There are probably some things you can disable. As soon as I get some time I'll dig around and see what I can find because I obsess over my laptop's boot time as well.

---

### Post by isantop on 2013-02-05
> **lolwtfhax said:**
> You could compile a custom kernel and strip out anything that is not needed. You can usually shave a few seconds off this way.

Also, I've been using Arch Linux for the last few years and have just recently decided to try out Ubuntu again so I'm not too familiar with its' boot process anymore. I'm sure it has changed quite a bit. But I'm sure there are some services starting up that aren't necessarily needed at boot time. There are probably some things you can disable. As soon as I get some time I'll dig around and see what I can find because I obsess over my laptop's boot time as well.

These, however, are extremely technical steps, and we don't recommend end-users take them since it's very easy to wind up with a system that doesn't boot.

---

### Post by nmg49 on 2013-02-07
So I decided to test my boot time. I timed my system 3 times, and it averaged around 45 seconds to get to log-in screen from the point Ubuntu started loading (adding in the BIOS, the figure is about 55 seconds). Is this normal for the Gazelle-professional? And if so, why then did my 5 year old HP Computer (which had a core 2 Duo) boot Ubuntu faster?

I'm considering re-installing Ubuntu to see if there’s any performance difference, mostly out of curiosity... Any thoughts on this?

---

### Post by lolwtfhax on 2013-02-07
I held shift after turning on my laptop to pause at the grub menu. Then hit enter while at the same time starting a timer. It took about 23 seconds to reach the login screen. 55 seconds is a bit long even counting the bios screen.
Make sure you have this line in your /etc/init.d/rc file:
CONCURRENCY=makefile

If it says "none" instead of "makefile", change it. It makes a big difference on multicore machines.

And yes, a custom kernel can render your OS unbootable if you do something wrong. So be careful if you go that route. If you do, do not replace your existing kernel and initramfs. Create a separate entry for it on the grub menu.

As far as disabling services during boot, I have a fairly clean install and do not see much that can be disabled that would make any significant difference. There's a program called bootup-manager that can disable stuff. But be very careful as this could also render your OS unbootable:
sudo apt-get install bum

Another way to slightly decrease boot time is to disable extra virtual terminals that are loaded during boot. -- the consoles you access by pressing ctrl+alt+F1 - through F6
By default 6 are loaded. You probably don't need that many. If you want to disable all but 3, delete or rename the following files:
/etc/init/tty4.conf
/etc/init/tty5.conf
/etc/init/tty6.conf
Though on a Core i7, this may not make much impact.

---

