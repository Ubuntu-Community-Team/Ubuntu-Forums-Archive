---
title: "Having power issue with Serp4"
date: 2009-01-20
forum: System76 Support
---

### Post by bodam on 2009-01-20
I'm having an unusual problem with a Serp4 system that I bought within the last year.  Over the last month or so, on 4 separate occasions i experience a complete power loss.  I do not mean a graceful shutdown but it behaves just like a desktop when a power cable is pulled.  Afterward, even pushing the power button has no effect.  I seem to have to unplug the power supply to get it to start up again.  I'm at a loss.  Any ideas?

---

### Post by thomasaaron on 2009-01-20
Does it do this on battery-only? AC-only? Battery and AC?
Does your battery charge up OK?
If you wiggle your ac jack (both at the computer and at the brick) does your the battery monitor applet switch back and forth from ac to battery?

---

### Post by bodam on 2009-01-20
> **thomasaaron said:**
> Does it do this on battery-only? AC-only? Battery and AC?
Does your battery charge up OK?
If you wiggle your ac jack (both at the computer and at the brick) does your the battery monitor applet switch back and forth from ac to battery?

I run 90% of the time plugged in so it hasn't happened on battery power.

The battery charges up fine.  It was at 100% right after a failure (i checked)  and no, the power cable is not loose.

---

### Post by thomasaaron on 2009-01-21
OK, thanks.

Does it do this following a suspend/hibernate / resume cycle? Or does it do it from a fresh start-up as well?

And are you running 32-bit or 64-bit Ubuntu?

Finally, the next time it happens, please go to System > Admin > System76 Driver > Support > Create and attach the logs.tar file that it creates in your home directory. Also, please make careful note of the time of the crash if you can. That will make it easier to identify the problem in your logs.

---

### Post by jbelmonte on 2009-01-21
FWIW, I have a laptop (non-System76) that exhibited the same behavior. It turned out that moving the laptop around had unseated the battery just enough to cause an occassional total shutdown. All I had to do to correct the problem was 1) turn off the laptop; 2) unplug the laptop; 3) remove the laptop battery; 4) reseat the battery making sure it was secure and the locking tabs were closed. After I did that, I just plugged it in, turn it on and I haven't had a total shutdown since. I hope your issues can be addressed as easily.

---

### Post by thomasaaron on 2009-01-21
Good point. I didn't think of that.

---

### Post by bodam on 2009-01-23
Sometime over last night, it did it again.  I have tried to remove and reconnect the battery but it still happens.  As suggested I've created a tar of the system logs and attached them here.  Any help would be appreciated.

---

### Post by thomasaaron on 2009-01-23
Please clarify something...

When it shuts down, do all LEDs and everything go *off*? Or do you just get a black screen with a couple of LEDs on, or blinking LEDs?

---

### Post by bodam on 2009-01-23
> **thomasaaron said:**
> Please clarify something...

When it shuts down, do all LEDs and everything go *off*? Or do you just get a black screen with a couple of LEDs on, or blinking LEDs?

It's a complete power loss.  No lights, no nothing.  It is like pulling the power cord out of a desktop.  Even pressing the power button sometimes does not work right away.  I'm suspecting a hardware issue.

---

### Post by thomasaaron on 2009-01-23
Sounds like it.

Please run memtest86 and see if it reports any errors. Instructions below...

> Reboot your computer. When you see the grub countdown menu, press the 'Esc' key. When you see the grub menu, press your 'down' arrow until Memtest86 is highlighted. Then press 'Enter' to start testing.

Please start Ubuntu in the evening before going to bed and let it run all night long. Memory card problems can be subtle, and sometimes they will not show up until the cards start heating up. Often it will take several passes before errors appear.

---

### Post by bodam on 2009-02-04
> **thomasaaron said:**
> Sounds like it.

Please run memtest86 and see if it reports any errors. Instructions below...

I did as suggested and during one of the passes it powered off.

Also on another note, originally I was running 8.04 and was having some issues anyways so I upgraded to 8.10 but the upgrade did not go particularly well so I completely reimaged.  On a whim I have loaded Kubuntu 8.10 ( I wanted to play with KDE 4.2 to see what the fuss was about) and for a week or so, I did not experience any issues.  But it seems that when I really start to push the system a little (for example, using Kino to do video rendering for DVD) it powered itself off on two occasions within a few minutes of each other.

I realize that Kubuntu is not supported but given that it has even done this during the memtest, I'm pretty sure that it's hardware related.  So what are my next steps?

---

### Post by thomasaaron on 2009-02-04
It sounds to me like it is either a memory problem or a overheating problem. Either of these could cause a shutdown when you really push the computer.

First, remove the panel that houses the CPU. Make sure you don't have any dust bunnies living in there. Blow it all out (especially the fan housing) with some canned air.

Also, can you hear the fan running? There was a problem with the SerP4 running 32-bit Ubuntu, where after resuming from suspend or hibernate, the CPU fan would not throttle. You are running 64-bit, right?

Second, since you couldn't get through memtest with the memory cards, there's a chance that one of them is bad. To check, remove one of them and run the machine with the other. Can you crash it? If you can, remove that card and put in the other card. Can you crash it? The idea is to see if just one of the cards is causing a problem. If so, we can replace it.

If this fails, let's bring it in.

---

### Post by zacinator on 2009-02-04
I am having a similar problem with the SERP 4.  My battery is only charging to 1 hour 25 minutes.  I don't know if an update started that or not, but it has been happening for about a week.  I removed Beagle which was running at 100 %.  I also killed npviewer which in the past ate my battery alive.  

It also randomly shuts down, but mostly when I am watching videos on battery.  

Another issue I have always had is that my fingerprint reader could melt wax it gets so hot.  Is there a way to turn it off or to cool that down?  If you accidentally touch it with your wrist it burns!

---

### Post by thomasaaron on 2009-02-05
> My battery is only charging to 1 hour 25 minutes.

What does that mean? Do you mean it charges to 100%, but you only get 1hr 25min of battery life? Or do you mean that it never reaches 100% charge no matter how long you leave it plugged in?

> my fingerprint reader could melt wax it gets so hot

I've never heard that before. If it's really getting that hot, it might represent an electrical problem of some kind (and it could explain low battery life -- if it has a short of some kind).

Instructions for un-installing the software for that component are here...
[http://ubuntuforums.org/showthread.php?t=860681&page=5&highlight=fingerprint](http://ubuntuforums.org/showthread.php?t=860681&page=5&highlight=fingerprint)

---

### Post by zacinator on 2009-02-05
> **thomasaaron said:**
> What does that mean? Do you mean it charges to 100%, but you only get 1hr 25min of battery life? Or do you mean that it never reaches 100% charge no matter how long you leave it plugged in?


It means that fully charged it says:
Laptop Battery 1 hour 25 minutes remaining (100%)

It used to get nearly 3 hours.  The fingerprint thing has always been that way for as far back as I can remember so I don't think it is the culprit.

---

### Post by betrunkenaffe on 2009-02-05
Are you using the tooltip information for how long it'll last? It's glitched, you need to open the battery device information and it will give you the correct information.

Currently tooltip is telling me 25 minutes but if I open the battery it says 31 minutes. I've been testing it quite a bit and the tooltip is always wrong.

Also, how long have you had the battery, if it's lithium ion, it could be partially due to time. [http://en.wikipedia.org/wiki/Lithium_ion_battery]("http://en.wikipedia.org/wiki/Lithium_ion_battery")

---

### Post by thomasaaron on 2009-02-05
Also, batteries loose their capacity with time, particularly if you run them all the way down frequently.

---

### Post by zacinator on 2009-02-05
> **thomasaaron said:**
> Also, batteries loose their capacity with time, particularly if you run them all the way down frequently.

I have had this laptop less than a year.  Can batteries go that quickly?  This just started happening last week.  

> **betrunkenaffe said:**
> Are you using the tooltip information for how long it'll last? It's glitched, you need to open the battery device information and it will give you the correct information.

Whether it is spot on or not, it still lasts at most an hour and 20 minutes.  I can't find anything that is using additional battery power.  The fact that it is only charging to max 1 hr 25 min makes me think either a setting is way off or my battery is dying.

---

### Post by thomasaaron on 2009-02-05
If you always drain it down to zero, it can happen that fast.

---

### Post by zacinator on 2009-02-05
> **thomasaaron said:**
> If you always drain it down to zero, it can happen that fast.

Do you think I should get another battery? I would hate to spend the money and have it be a system issue.  I do have a bad habit of letting it dwindle down to the warning.

---

### Post by thomasaaron on 2009-02-05
Try one more thing first.

Run the battery almost all the way down. Take it out. Let it cool down to room temperature (maybe 30 minutes?). Then put it back in and charge it back up.

That sometimes works to calibrate it. If that doesn't fix it though, I'm 98.3% sure it's the battery.

---

### Post by betrunkenaffe on 2009-02-05
One of the things I understood about Li-on batteries were that they didn't have a memory issue. What would be the best way to optimize the battery life? I was under the impression that running down to 40% and keeping it around there would be best.

---

### Post by thomasaaron on 2009-02-06
That is my understanding too. Either way, the battery will eventually wear down. But the lest rigorous your usage of it, the longer it will last -- kind of like anything.

---

