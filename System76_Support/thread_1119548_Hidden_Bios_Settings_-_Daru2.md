---
title: "Hidden Bios Settings - Daru2"
date: 2009-04-08
forum: System76 Support
---

### Post by laserline on 2009-04-08
Hello,

I've just found this website that claims that the MSI-PR200 which is exactly the same as the Daru2 (MS-1221) have a Hidden Bios Menu.

The site tested this on BIOS versions 1.48 - But my guess is that it will also show-up on older bioses.

One particular setting that interests me (and I don't have a clue about what it says) is: "ENE EC BACK DOOR IO DECODE -> Disabled/Enabled"

Because I won't be near my Daru2 in the upcoming week, would anyone care to try launching this menu (w/o saving there bios settings) just to see this really works ?

To access the hidden bios menu, just press Alt+Ins when inside the bios (meaning after pressing DEL at boot time).

In addition, does anyone know what this settings mean ? as for me, when I hear the term EC and the Daru2 I smell trouble/solution/bugs/fixes/etc...

Well, thought to share this,

Thanks in advance,
Idan.

---

### Post by madverb on 2009-04-08
Lots of motherboards have hidden BIOS settings.

---

### Post by laserline on 2009-04-08
> **madverb said:**
> Lots of motherboards have hidden BIOS settings.

Right, but I'm interested if this hidden setting can help fix/understand the Daru2 ACPI and EC bugs.

---

### Post by thomasaaron on 2009-04-08
Our shop DarU2 is running BIOS version 2.61, and there doesn't appear to be a hidden BIOS setting (at least not via Alt-Ins).

---

### Post by laserline on 2009-04-08
Version 2.61 ? Wierd.

Aren't these suppose to be the same numbers (atleast) as the PR200 ?

I've just checked MSI's website and the latest bios for the PR200 is 1.50 and 3.50 (Vista/XP respectivly).

Idan.

---

### Post by thomasaaron on 2009-04-08
The manufacturing facility updates the BIOS before imaging and shipping. So, there are a lot of different BIOSes out there on the DarU2.

---

### Post by williumbillium on 2009-04-09
I just checked on my Daru2 with v3.3 BIOS.  The ALT-INS didn't seem to do anything (i could be wrong) but I noticed the same, ENE EC BACK DOOR IO DECODE, option under an advanced tab.

I've enabled it (it was previously disabled) and I'm now running an unpatched kernel without the acpi=noirq boot parameter.  Will report back with what happens.

---

### Post by loomsen on 2009-04-09
You may want to use [color=red]dmidecode[/color] to view your BIOS' features/capabilities/version and a lot more.

[color=red]sudo apt-get install dmidecode[/color] 

Then run it as root

sudo dmidecode  | more

[color=green]( | more ) is probably a good idea too [/color]

---

### Post by williumbillium on 2009-04-09
Thanks for the tip.  Just for the record, nothing is mentioned about the hidden option in the output from dmidecode.

Also, I was wrong above, the ALT-INS combination is required for the ENE EC BACK DOOR IO DECODE option to be displayed.

---

### Post by williumbillium on 2009-04-09
```
cat /proc/acpi/battery/BAT1/state 
present:                 no
```

Broke after 20 minutes. Oh well, it was worth a try.  (Just for the record I tried this with an Arch kernel.)

---

### Post by laserline on 2009-04-09
Hi, thanks for testing this.

From the name of this option, I would guess it's something that might provide more information and not really fix the problem.

Maybe, this 'backdoor' was designed for debugging or something else, but to access it's information one needs instructions.

Tom, would it be a possibility that System76 contact MSI and ask what this setting is all about? And if relevent, how to use it.

I think this is worth a shot.

Thanks,
Idan.

---

### Post by jdb on 2009-04-09
> **williumbillium said:**
> ```
cat /proc/acpi/battery/BAT1/state 
present:                 no
```

Broke after 20 minutes. Oh well, it was worth a try.  (Just for the record I tried this with an Arch kernel.)

I'm running the Arch kernel on a Daru-2 and the bug is completely fixed on 2.6.29

Edit: I've been running 2.6.29-1 from testing but I just noticed that 2.6.29-3 was moved to core yesterday.

jdb

---

### Post by williumbillium on 2009-04-09
> **jdb said:**
> I'm running the Arch kernel on a Daru-2 and the bug is completely fixed on 2.6.29

Edit: I've been running 2.6.29-1 from testing but I just noticed that 2.6.29-3 was moved to core yesterday.

jdb

I was testing with a stock 2.6.28 kernel since it exhibits the problem.  I figured that would be a good way to see if the bios option had any effect.

I agree with laserline though that the option should still be looked into further.

---

### Post by thomasaaron on 2009-04-09
OK. Email sent. I'll report back when they respond.

I did some googling on it, but I found nothing of interest.

---

### Post by thomasaaron on 2009-04-09
This is what I got back from MSI...

> It has to do with an internal test module....not for the enduser, so just leave it on the default setting.

Not overly informative, I know. But it sounds like something pertaining to one of their testing procedures, not a fix for anything.

---

### Post by laserline on 2009-04-09
Thanks a lot for looking in to this.

Can you please tell us where is the Standby (suspend) and the Daru2 stands ?

I relly would like to know what caused the regressing on this, because as far as I remember, Ubuntu 7.10 was able to suspend.

Thanks again,
Idan.

---

### Post by thomasaaron on 2009-04-09
Yes, the last time it worked was in Gutsy 64-bit. We've never been able to find the regression. After Gutsy, they started making the kernels tickless.

We've still been unable to fix the problem despite more man-hours than we've probably spent on all the rest of our machines combined. We've also sent computers to devs and have yet to see a fix.

When we get to the daru2 with Jaunty testing, we will examine the kernel options and see if maybe there's something in there to fix it.

---

### Post by jdb on 2009-04-09
> **thomasaaron said:**
> Yes, the last time it worked was in Gutsy 64-bit. We've never been able to find the regression. After Gutsy, they started making the kernels tickless.

We've still been unable to fix the problem despite more man-hours than we've probably spent on all the rest of our machines combined. We've also sent computers to devs and have yet to see a fix.

When we get to the daru2 with Jaunty testing, we will examine the kernel options and see if maybe there's something in there to fix it.

I've gone nuts trying to figure this one out, at least I'm in good company :lolflag:

jdb

---

### Post by thomasaaron on 2009-04-09
Thanks for being good-natured about it, JDB. This one has just been an absolute monster. Definitely the most difficult linux problem I've had the pleasure of working on.

---

### Post by laserline on 2009-04-10
Yeah, it is hell.

I remember going over all the changelogs of the kernels from Gutsy to Intrepid inorder to try and map what might caused the regression - That didn't help.

If I recall correctly, there were more laptops suffering from such regression (I'm not sure from which make) - I wonder what's the scoop on those.

---

