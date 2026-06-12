---
title: "Mobile Users Beware: Linux Has Major Power Regression"
date: 2011-04-23
forum: The Cafe
---

### Post by sffvba[e0rt on 2011-04-23
> For those that follow [my personal  Twitter feed]("http://twitter.com/michaellarabel") will know that for the past week I've been closely testing Ubuntu  11.04 and all Ubuntu releases going back to Ubuntu 8.04 on many mobile devices  in the office. The overall system performance, power consumption, and boot performance  have been the principal targets. However, late this week I discovered a glaring  regression: Ubuntu 11.04 is viciously going through power. Compared to Ubuntu  10.10, the power consumption on Ubuntu 11.04 for mobile devices is up about 10%  on average but under some workloads, I am seeing the power consumption up by nearly  30%. This is happening on many mobile systems spanning multiple generations of  Intel CPUs and with Intel / ATI / NVIDIA graphics. This issue has been tracked  down to a frightening kernel regression in the mainline tree that is still not  addressed.

[Source]("http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1")

I have been very skeptical about things coming from phoronix (Still waiting for native Steam support in Linux)... however, if this is true it is a bit of a concern, especially if Unity is targeting tablet devices and such as battery life is of paramount importance... (and on a personal note my aging laptop already doesn't have brilliant battery life, this will just make it so much worse :()


404

---

### Post by NightwishFan on 2011-04-23
I have been using 2.6.38 and if anything my battery life is better than ever. Even using 1000hz.

---

### Post by sffvba[e0rt on 2011-04-23
> **NightwishFan said:**
> I have been using 2.6.38 and if anything my battery life is better than ever. Even using 1000hz.

Well clearly your delusional, but using Debian for an extended period of time will do that to you :P

OR

You are the exception that proves the rule :P


404

PS - :P

---

### Post by NightwishFan on 2011-04-23
There has been a lot of device power saving code since 2.6.32 I believe.

---

### Post by sffvba[e0rt on 2011-04-23
> **NightwishFan said:**
> There has been a lot of device power saving code since 2.6.32 I believe.

I know... but an average regression of 10% is pretty bad since .38 ...

---

### Post by Hyporeal on 2011-04-23
> **not found said:**
> I have been very skeptical about things coming from phoronix (Still waiting for native Steam support in Linux)...

That is wise. The methodology commonly seen at Phoronix makes it a somewhat interesting site to read, but not a reliable source of news. Stick with the more journalistic sites (such as arstechnica.com) for your tech news.

---

### Post by fuduntu on 2011-04-23
I tend to stay pretty close to kernel changes that alter battery life (because of Jupiter, and my other netbook related efforts), and I haven't seen this.  It could be a device specific regression.

---

### Post by Bölvaður on 2011-04-23
Actually even if there was a major problem with battery life, having many devices on it would make things better, as one of the makers of such a device might patch it. The more linux will be used the more it will be fixed.

---

### Post by nathan28 on 2011-04-23
> **Bölvaður said:**
> Actually even if there was a major problem with battery life, having many devices on it would make things better, as one of the makers of such a device might patch it. The more linux will be used the more it will be fixed.

I've never had a laptop battery that could hold a charge longer than 45 minutes after a few months' use, so I'm not sure I trust this Fauxronix benchmark. But even so.

???? How is a kernel regression ever a good thing? Unless something has changed with the actual hardware, it's a problem that didn't exist and now needs to be fixed thereby taking time away from other problems. Especially something crucial like power mgmt.

IOW, if you're busying hacking the kernel to repair the issue, that's time you aren't running folding@home... that 3. GHz quad-core could be curing cancer... Or it could be doing empty quatraterabagoogle-flops while you stare at vi.

And if you're burning through batteries, that's more toxic waste someone in Africa ends up burning to extract the gold and silver from.

Like I said I don't trust the 'benchmark' here, but I already feel like I need to get a tiny SSD/Atom netbook to make the dedicated Facebook + youtube machine and keep all the bloated megahardware (seriously, the oldest laptop I have still running has almost two orders of magnitude more processing power than the one I used to dial the library catalog BBS in the '90s) running something folding@home or turned off and sitting in a refrigerator.

Apologies for the moral outrage, after a month of "OMG GNOME Shell sucks" this seems a little more real than some ugly-*** css colors.

---

### Post by fuduntu on 2011-04-23
> **nathan28 said:**
> I've never had a laptop battery that could hold a charge longer than 45 minutes after a few months' use, so I'm not sure I trust this Fauxronix benchmark. But even so.

Interesting, I have a couple of machines some of which are over 3 years old that still hold 90% or more of their charge.

My old 1000HE still lasts over 8 hours on a charge, and it's almost 3 itself.

> **nathan28 said:**
> Apologies for the moral outrage, after a month of "OMG GNOME Shell sucks" this seems a little more real than some ugly-*** css colors.

I still believe that it's only that one model that's impacted.  I just tested 2.6.38.4 on my 1015PEM, and it drops to 7 watts on battery (dual core Atom N550) as expected.

A fair study would have tested the effect across several models, all using fresh installations with no added configuration or software.

---

### Post by phoronix on 2011-04-23
> **fuduntu said:**
> A fair study would have tested the effect across several models, all using fresh installations with no added configuration or software.

That's what was done: [http://www.phoronix.com/vr.php?view=15935](http://www.phoronix.com/vr.php?view=15935)
There's also completely independent reports of power issues now if you do some digging. There was also this bug report from a few days ago - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

---

### Post by fuduntu on 2011-04-23
> **phoronix said:**
> That's what was done: [http://www.phoronix.com/vr.php?view=15935](http://www.phoronix.com/vr.php?view=15935)
There's also completely independent reports of power issues now if you do some digging. There was also this bug report from a few days ago - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

I was focusing on this article though - [http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1) - not the later article that tests various versions of Ubuntu.

Do you have the same result testing with Fedora, Debian, Arch or another distribution that isn't an Ubuntu derivative?  It's possible that it's something in Ubuntu itself.

Also, I would say to use something like Ubuntu and Fedora across all of the different hardware that you have to see if it is specific to the T60 like I think it may be.

I wonder if Jupiter masks the issue.  I really don't see it anywhere (I'm about to test on my T400).

---

### Post by phoronix on 2011-04-23
> **fuduntu said:**
> I was focusing on this article though - [http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1) - not the later article that tests various versions of Ubuntu.

That was just a quick one thrown together on Friday.

> **fuduntu said:**
> Do you have the same result testing with Fedora, Debian, Arch or another distribution that isn't an Ubuntu derivative?  It's possible that it's something in Ubuntu itself.

Also, I would say to use something like Ubuntu and Fedora across all of the different hardware that you have to see if it is specific to the T60 like I think it may be.

I wonder if Jupiter masks the issue.  I really don't see it anywhere (I'm about to test on my T400).

What looks to be causing the regression after bisecting it out, is not device-specific or a user-space interaction problem, so could be reproduced with any distribution and - with the right workload - any x86/x86_64 and potentially IA64 system. More details will be announced tomorrow or Monday.

---

### Post by fuduntu on 2011-04-23
> **phoronix said:**
> That was just a quick one thrown together on Friday.



What looks to be causing the regression after bisecting it out, is not device-specific or a user-space interaction problem, so could be reproduced with any distribution and - with the right workload - any x86/x86_64 and potentially IA64 system. More details will be announced tomorrow or Monday.

Lenovo T400
Fuduntu 14.9 (64bit)
Kernel 2.6.38.4
Completely idle on battery for ~15 minutes.

[[img]http://ompldr.org/tOGU1Mw[/img]](http://ompldr.org/vOGU1Mw)

---

### Post by fuduntu on 2011-04-23
Asus Eee PC 1015PEM
Fuduntu 14.9 (32bit)
Kernel 2.6.38.4
Completely idle on battery (as before)

[[img]http://ompldr.org/tOGU1OA[/img]](http://ompldr.org/vOGU1OA)

---

### Post by fuduntu on 2011-04-23
> **phoronix said:**
> What looks to be causing the regression after bisecting it out, is not device-specific or a user-space interaction problem, so could be reproduced with any distribution and - with the right workload - any x86/x86_64 and potentially IA64 system. More details will be announced tomorrow or Monday.

I'm looking forward to reading about it, though I'm still highly skeptical.  We did find in testing 2.6.38 that we needed to disable NMI watchdog when on battery, which I added to Jupiter 0.0.50.  I wonder if that's what you are seeing.

---

### Post by sffvba[e0rt on 2011-04-23
I like it that there are some people with their own proven results... always the best!


404

---

### Post by leviathan8 on 2011-04-23
This may, or not may be related, but I would like to ask something.
I have a Dell N5010 laptop with a 15,6" screen. The battery doesn't last any longer than 2 hours. I have a minimal environment, no fancy effects, brightness always on 0%, very few applications and services running on startup. Is this normal? Is there a way to prolong my battery life?

This is what acpi reports at the moment:

```
mono@mono-laptop:~$ acpi -V
Battery 0: Discharging, 85%, 02:49:31 remaining
Battery 0: design capacity 4444 mAh, last full capacity 4144 mAh = 93%
Adapter 0: off-line
Thermal 0: ok, 41.5 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 87.0 degrees C
Cooling 0: LCD 15 of 15
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10

```

I have an integrated Intel HD Graphics card, and the fan is constantly running after 5 minutes of usage. I do not have any proprietary drivers available, just the one for WiFi. Again, is this as it should be? The kernel is  2.6.32-31-generic.

---

