---
title: "any special instructions for 12.10 upgrade?"
date: 2012-10-17
forum: System76 Support
---

### Post by b7j0c on 2012-10-17
I am the proud owner of a Gazelle laptop. I presume I will be able to upgrade 12.04 to 12.10 like anyone using stock ubuntu, but I do recall when I first purchased it, having to do some minor tweaks to route around a bug in the kernel with respect to Intel video (freezes). 

Are there any special instructions from System76 or may we proceed with a standard upgrade?

---

### Post by isantop on 2012-10-18
> **b7j0c said:**
> I am the proud owner of a Gazelle laptop. I presume I will be able to upgrade 12.04 to 12.10 like anyone using stock ubuntu, but I do recall when I first purchased it, having to do some minor tweaks to route around a bug in the kernel with respect to Intel video (freezes). 

Are there any special instructions from System76 or may we proceed with a standard upgrade?

Watch This Space...

---

### Post by isantop on 2012-10-18
Done!

[http://ubuntuforums.org/showthread.php?t=2072824](http://ubuntuforums.org/showthread.php?t=2072824)

---

### Post by philbert on 2012-10-22
Last Saturday, I upgraded the Gazelle I bought in July and updated the System 76 drivers a few minutes ago.   I have not seen any problems yet.
Also, thanks to isantop for the reminder  on the sticky post to download the drivers.

---

### Post by oakhilltop on 2012-10-23
Hmmm, I feel silly. I open the update manager but don't see the message that there is a new release available.

I'm on a Lemur running 12.04
This is my first attempt at an ubuntu upgrade.

---

### Post by oakhilltop on 2012-10-23
Never mind. I found a setting in the upgrade manager that controls when it notifies of new versions. I adjusted that and now I see the message

---

### Post by oakhilltop on 2012-10-25
I started the upgrade and get this warning in the middle of it.

Could not install 'libjbig0'
no package named `libjbig0' is installed, cannot configure

It says the upgrade will continue.

Is this normal? Does it have something to do with cinnamon being installed?

---

### Post by elopio on 2012-10-25
I installed Quantal from scratch. It works fine, but it started using the nouveau drivers. I would prefer to use them because they are free, but after a while the system crashes.
So I switched to the nvidia drivers, and after log in, I only see the desktop. No unity bars, no window bars. I can open a terminal and do stuff from there, but I want my unity back.

Does this happen to you?

My system has a GForce GT430. And I installed the system76 drivers too.

---

### Post by isantop on 2012-10-25
> **elopio said:**
> I installed Quantal from scratch. It works fine, but it started using the nouveau drivers. I would prefer to use them because they are free, but after a while the system crashes.
So I switched to the nvidia drivers, and after log in, I only see the desktop. No unity bars, no window bars. I can open a terminal and do stuff from there, but I want my unity back.

Does this happen to you?

My system has a GForce GT430. And I installed the system76 drivers too.

Which version of the System76 driver did you install? We just released an update which should fix this issue. 

You may need to reinstall. Once you have, install the System76 Driver and run the restore. Then, reboot, and update. Then, install the Nvidia driver. You should be good to go after that.

---

### Post by jjonesjr on 2012-10-29
Why do the installation instructions (linked here: [http://knowledge76.com/index.php/QuantalUpgrade](http://knowledge76.com/index.php/QuantalUpgrade)) suggest a "System Restore" during the "upgrade" process.  At worst, that's a bad naming job, at best that may not be doing what I want it to (whatever if i've customized my system, will it blow away my changes? etc).

---

### Post by rawrmonster on 2012-11-02
> **jjonesjr said:**
> Why do the installation instructions (linked here: [http://knowledge76.com/index.php/QuantalUpgrade](http://knowledge76.com/index.php/QuantalUpgrade)) suggest a "System Restore" during the "upgrade" process.  At worst, that's a bad naming job, at best that may not be doing what I want it to (whatever if i've customized my system, will it blow away my changes? etc).

I was wondering the same thing...

---

### Post by isantop on 2012-11-02
> **rawrmonster said:**
> I was wondering the same thing...

I actually wrote the new driver/UI. :)

When I did that button I suggested changing the naming to something else. However, when I ran it by the higher ups, they said no. 

That said, I'll play around with the wording and design a bit to see if I can come up with something clearer and less confusing. If I can, and the change is approved, then we can roll it out a little larger.

Thanks for the feedback!

---

