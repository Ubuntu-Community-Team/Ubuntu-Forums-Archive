---
title: "Gutsy and battery life"
date: 2007-12-08
forum: System76 Support
---

### Post by perce on 2007-12-08
My white Darter's battery life dropped from something like 3h40 on Feisty (with Beryl) to 2h55 on Gutsy, and this after performing pretty much all operations suggested by powertop. Is anybody experiencing something similar? any ideas how to fix it?

---

### Post by bigdidz on 2007-12-09
My laptop does the exact same thing.  I do not know what to do.

---

### Post by thomasaaron on 2007-12-10
Question for both of you: Did the actual time you can use your computer on battery change, or just the report you get from the battery icon.

I read somewhere that Gutsy changed its "power estimator." 

On a fully-charged 9-cell, the battery indicator says I have 3hr 15min remaining.
Running acpi from the command line tells me 4hr 17min.

Even that is a little low, but I'm pretty sure this thing will go longer than either of those estimates on my 9-cell.

---

### Post by perce on 2007-12-10
Both times I unplugged the computer and I waited until it told me "less than five minutes remaining". Both times I had the same programs on: Skype, Pidgin, Firefox and Xemacs.

A side question: do you still sell 9 cells batteries for the white Darter? how bigger and heavier is it?

---

### Post by thomasaaron on 2007-12-10
I think we have about three 9-cells left. It's about an inch wider. It might be 4 or 5 ounces heavier.

---

### Post by perce on 2007-12-10
Thank you, I've just sent you an email about the battery.

Now back on topic: I forgot to mention in the original post that gutsy seems to operate at a higher temperature than feisty: my computer often reaches 50C, and it almost never arrived at that temperature before the upgrade.

---

### Post by thomasaaron on 2007-12-10
Mine is running at 62C.
50C is definitely not a problem.

That said, Mine used to run at 57C, so you may be right on that.

In fact, check out this post -- both problems in one fell swoop:
[http://ubuntuforums.org/showthread.php?p=3817043](http://ubuntuforums.org/showthread.php?p=3817043)

I did what this form suggested:
sudo apt-get install powertop
sudo powertop

It reports my cpu at 53C! Maybe Gutsy's acpi is just all screwed up.
It looks like firefox-bin and my wirless card is sucking up the most power.

---

### Post by riseringseeker on 2007-12-13
> **thomasaaron said:**
> Mine is running at 62C.
50C is definitely not a problem.

That said, Mine used to run at 57C, so you may be right on that.

How do I find the temp of my white darter?  

> In fact, check out this post -- both problems in one fell swoop:
[http://ubuntuforums.org/showthread.php?p=3817043](http://ubuntuforums.org/showthread.php?p=3817043)

I did what this form suggested:
sudo apt-get install powertop
sudo powertop

It reports my cpu at 53C! Maybe Gutsy's acpi is just all screwed up.
It looks like firefox-bin and my wirless card is sucking up the most power.

powertop does not give me a temperature at all, and though 7.04 would show battery life of 3:30+ when fully charged (depending on what I had open/running), 7.10 now says a fully charged battery is only good for 2:20.  (powertop and the battery icon mostly agree - within 20 minutes or so.)

I do not know if CPU scaling is enabled or not, but would like to try to do whatever I can to increase my battery life.  Being only a little more than 6 months old, I wouldn't think the battery is that weak - at least I would hope not!

---

### Post by thomasaaron on 2007-12-13
> How do I find the temp of my white darter? 

acpi -t

> powertop does not give me a temperature at all

powertop gives you a run-down of what is sucking up power on your computer. And it gives you suggestions about what you might do to kill some unnecessary services.

> I do not know if CPU scaling is enabled or not,

Try creating a cpu scaling monitor on your upper panel. (right click the panel, add applet, cpu scaling monitor). Then right click on the monitor, click on preferences, and see if you can choose both cores of your cpu. Or you can put two monitors on your panel and set one to CPU0 and the other to CPU1. If that works, CPU scaling should be enabled.

---

### Post by rrwo on 2007-12-19
The power usage estimate on my laptop halved when upgrading to Gutsy. Before, I could use 4.5 hours-- and actually did.  Now it says I have 2.5 hours, and will try and shut the system down if I have very little left.  So even if their estimate is wrong, it affects the practical usage time.

---

### Post by gobbles414 on 2007-12-21
rrwo,

If you are using the GNOME version of Gusty, you should be able to disable the automatic shutdown in the *On Battery Power tab* in *Power Management*.

Your battery has a sort of memory. Resetting this memory can increase the amount of time your battery will work on a single charge. By starting with a fully charged battery and then letting it drain completely, you begin to reset the battery's memory. Your BIOS may also contain a utility for doing all of this outside of Ubuntu, thus minimizing the risk of damage to your operating system. But I have allowed my battery to drain completely while in Ubuntu without anything bad happening. **Here's a procedure that you can use to simultaneously measure and reset your battery's charge from within Ubuntu:**

<1> Charge your computer overnight.

<2> Be sure to disable the automatic sleep and shutdown functions in Power Management.

<3> If you usually do a lot of audio and video stuff on your laptop, use your favorite video application to play a video file. Set the application to "loop" the playback so that the file is always playing. **OR**, if you do mostly office stuff on your laptop, open OpenOffice and Firefox instead.

<4> Unplug your laptop from external power. EDIT: Let the battery drain completely. Your computer will turn off without doing a shutdown routine.

<5> Allow the battery to completely recharge back to 100%. IMPORTANT: The recharge needs to be done all at once. DO NOT interrupt the recharging process.

<6> Repeat steps 2 through 4. This time, make a note of when you unplug your computer and when it runs out of power. The difference will be your computer's average runtime on a single charge.

<7> Once again, allow your battery to fully recharge all at once.

<8> Re-enter your desired settings into the Power Manager.

EDIT: It is also worth considering that batteries simply lose the ability to hold a charge as well over time. So the drop in efficiency you have noticed may very will be a sign that your battery is no longer able to hold a charge very well. We use laptops a lot in my house. The longest a that a laptop battery has lasted for us before needing to be replaced is about 18 months.

---

### Post by rrwo on 2007-12-22
I've already tried draining my battery and re-charging it. It hasn't fixed a thing, but then again, that's not the problem.

The problem is that as soon as I upgraded from Feisty to Ubuntu, it lost two hours of battery life.  It's too much of a coincidence to assert that there's a problem with my battery, particularly when a lot of other people with similar laptops are having the same problem.

---

### Post by gobbles414 on 2007-12-23
rrwo,

Well, that is very interesting indeed. A friend of mine just purchased a new laptop from System76. It has Ubuntu 7.10 pre-installed, and I will be configuring the machine for her. Once it arrives, I will let you know what kind of battery performance I am able to get from the unit. FYI: My laptop -- an Asus G1 running 32-bit Ubuntu 7.10 (non Santa Rosa) -- reports 2 hours and 40 minutes capacity on what I believe is a heavily used 8 cell battery. This is similar to the performance I used to get on the G1 under Windows Vista (yuck).

---

### Post by harrisupstate on 2008-01-02
Just an FYI -- my white Darter has the same symptom.  It tends to show that it'll run approximately 2.5 hours, when it used to show 3.5 to 4.

Please share the fix when it's out there!

Thanks.

---

### Post by harrisupstate on 2008-01-12
Any updates on this apparent problem?  I haven't actually done any detailed testing of the situation, but I've definitely observed a precipitous drop in the levels of available power when running on battery.  I also have to say that the heat exhaust seems to be pumping out a lot more heat these days, although I'm not as sure about this as I am about the indicated battery life. 

TIA

---

### Post by perce on 2008-01-12
> **harrisupstate said:**
> Any updates on this apparent problem?  I haven't actually done any detailed testing of the situation, but I've definitely observed a precipitous drop in the levels of available power when running on battery.  I also have to say that the heat exhaust seems to be pumping out a lot more heat these days, although I'm not as sure about this as I am about the indicated battery life. 

TIA

After upgrading to Gutsy my sensors applet reports 50C quite often, and it never reached that temperature with feisty, so you're right. For the temperature, however, I noticed that if I close firefox it drops to about 46C, which was the same I usually had in Feisty.

---

### Post by thomasaaron on 2008-01-14
Just a note on temperature. My DarU1 ran CONSISTENTLY at 54C on Feisty.
It does seem to run a little hotter on Gutsy (I'm at home today with a different computer, so I can't acpi -t, but I think it is about 60C). But 50C is not hot at all for a laptop, according to my research.

---

### Post by perce on 2008-01-14
> **thomasaaron said:**
> Just a note on temperature. My DarU1 ran CONSISTENTLY at 54C on Feisty.
It does seem to run a little hotter on Gutsy (I'm at home today with a different computer, so I can't acpi -t, but I think it is about 60C). But 50C is not hot at all for a laptop, according to my research.

I'm not worried about the possible damage temperature can do, I'm worried about the waste of energy that a rise of temperature means.
In fact I'm well aware that a Darter is cooler that most of the my friends' laptops.

---

