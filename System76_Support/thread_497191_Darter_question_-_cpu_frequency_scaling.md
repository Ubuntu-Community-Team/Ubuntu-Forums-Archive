---
title: "Darter question - cpu frequency scaling"
date: 2007-07-09
forum: System76 Support
---

### Post by PatrickMay16 on 2007-07-09
Hello everyone.

I have an Asus Z35FM, which I didn't buy from shafetech... but I can see that it is the same model as your 'Darter' laptop, so you might be able to answer some questions I have.

Does this laptop support CPU frequency scaling?

And, where can one find the most recent bios? And how does one update the bios?

Sorry for asking these questions without actually being a system76 customer.

---

### Post by tedrampart on 2007-07-10
you could add the applet "CPU frequency scaling monitor" to see if its already enabled..

I don't see why it wouldn't have cpu scaling.  but if not you could try:

sudo modprobe acpi-cpufreq

you might have to add it to /etc/modules

as far as upgrading the bios, if it ain't broke, don't fix it.  if everything works, then you shouldn't worry about upgrading the bios.

if you do want to upgrade, you can probably find the bios on the asus website, in the downloads section.

---

### Post by PatrickMay16 on 2007-07-10
Thanks, 

When I add the cpu frequency scaling monitor applet, it says that cpu frequency scaling is not supported. Loading the module 'acpi-cpufreq' returns a 'no such device' message. 

I was thinking of updating the bios in case that would help with this problem.

Any help would be appreciated.

---

### Post by thomasaaron on 2007-07-10
I second that -- regarding doing a BIOS upgrade.
But you're probably on the most current version anyway (I think it is 305).

If you have a core 2 duo processor, it should support frequency scaling.

---

### Post by digitalbenji on 2007-07-10
I have this model laptop, and it takes some module loading to enable cpu frequency scaling, but I use it, usually with the on-demand governor.  It will depend on which cpu you have, but I have the Pentium M version, so it uses the p4_clockmod module I believe.  I have a Pentium M Celeron 410 1.46GHz . By using insmod p4_clockmod I have been able to get cpu frequency scaling working. However, I notice that sometimes the network connection goes down (and won't come back up).  I believe this happens if you allow the CPU to scale down too low, so I never let it go below 1ghz.

---

### Post by digitalbenji on 2007-07-10
I got the latest bios from the system76 launchpad site, you'll need to browse into the bugs, it's attached to one of the darter brightness related bugs as I recall.

---

### Post by PatrickMay16 on 2007-07-10
OH MAN yeeeeeeeeaaaaaaaaaahhhhhhhh. Thanks guys. Loading the 'p4_clockmod' module enables the cpu frequency scaling fine. 

Just for future reference, Digitalbenji, how do you control the scaling so it doesn't go under 1GHz?

---

### Post by digitalbenji on 2007-07-20
I forget the exact location at the moment, but I think if you do a man on the cpu frequency scaling packages you can figure it out.  I'm sorry I didn't get back to you sooner, and this response it pretty lame.  If you PM me or e-mail [email]go@digitalbenji.com[/email] a reminder I'll get you that answer...

too busy for Friday :(

---

### Post by tedrampart on 2007-07-22
I think the command is cpufreq-selector (as root) ..example ```
sudo cpufreq-selector -c 0 -g ondemand
``` .. but I think the applet lets you choose.  (I've been using powernowd for awhile now, so I can't remember exactly...)

if its not, would someone post it here so there's a reference to it?

also, is it better to use powernowd or cpufreq-selector for system76 laptops?  I've been using powernowd and it seems to work, but after a resume from suspend one cpu seems to get stuck.

---

### Post by Offoffoff on 2007-07-23
Is there any kind of *.conf file for cpu-freqselector? How to fix governor "ondemand" forever? I know about rc.local, but maybe there is a better light way.

---

