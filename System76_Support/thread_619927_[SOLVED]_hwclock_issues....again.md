---
title: "[SOLVED] hwclock issues....again"
date: 2007-11-22
forum: System76 Support
---

### Post by steveneddy on 2007-11-22
I'm having excessively long boot times (over 6 minutes) and I believe hwclock is the issue for some reason.

Here is the output of **hwclock**

```

 hwclock --debug
hwclock from util-linux-ng 2.13
hwclock: Open of /dev/rtc failed, errno=16: Device or resource busy.
No usable clock interface found.
Cannot access the Hardware Clock via any known method.


```

Help?......

---

### Post by steveneddy on 2007-11-23
I think I fixed this problem by going to the BIOS and selecting the defaults at the last screen and then saving and restarting.

Is this a battery issue or maybe a software issue?

I hardly ever run on the battery alone. It's always plugged in, so I can't see why the battery would be bad already.

Any guesses?

I have installed the linux-rt kernel, but I'm not sure if that was the problem.

Can the clock be set wrong if the machine is on a Windows open network some of the time?

---

### Post by thomasaaron on 2007-11-23
Well, that's an interesting question. I guess it might be possible. I know that when the computers are originally configured, we choose the UTC clock option. I believe this syncs the clock with an online source. Maybe your Windows network is messing that up?

---

### Post by steveneddy on 2007-11-24
It's kinda weird. I received an update for **tzdata** Wednesday at work and it started acting screwy then. After I got home and booted up again, I noticed the problem.

It's just weird that I have has a **hwclock** issue twice is less than 3-4 months time.

Is there anything else that I need to be checking?

---

### Post by thomasaaron on 2007-11-26
Did you re-image the machine?
If so, did you choose the UTC option?
And what OS are you running? Ubuntu 32? 64?

---

### Post by steveneddy on 2007-12-02
> **thomasaaron said:**
> Did you re-image the machine?
If so, did you choose the UTC option?
And what OS are you running? Ubuntu 32? 64?

I'm on 64 bit version, and the RT kernel.

I was looking through my notes from last year when this happened and it looks like I was running the RT kernel then, also.

I was noticing that when the machine is on for longer than 12 hours, or coming up on a 12 hour work cycle that it gets a little buggy with this kernel. Still trying to put my finger on it though. Sometimes it gets non-responsive and others it will loose the window manager. I'm still trying to get a feel for what is really going on here.

BTW - had to do a complete reinstall recently and I didn't have to use any on the System76 driver stuff. I just installed from a new Ubuntu produced CD, 64 bit, and all of the hardware worked perfectly. Is there any reason for me to use the System76 driver for a Serval Performance Type 1?

---

### Post by thomasaaron on 2007-12-03
If everything works, then no.

---

### Post by steveneddy on 2007-12-22
Having hwclock issues again this week - all week. I have left my laptop at work all week just to try and get the clock to do something.

It looks like the hwclock is just stopped.

Boot time is in the 10 minute range. After startup, everything works well. But this clock issue is driving me insane!

Is anyone else having these issues?

---

### Post by thomasaaron on 2007-12-24
I remember you had these problems before. What I don't remember is whether or not you were running 64-bit then.

HOWEVER, google this:
ubuntu 64-bit hwclock

Looks like it might be a 64-bit bug.

---

### Post by steveneddy on 2007-12-28
From[ another pos]("http://ubuntuforums.org/showthread.php?t=595544")t.

```

I have tried this to try and repair the hwclock.

Anyone think this is a battery problem?

I have even thought about going back to Feisty until Heron is released.

I wonder about getting a new battery for the MB and installing it myself.

Thoughts?

Maybe I need to go back to a 32 bit OS?

Banging my head against the counter.

Other than this and suspend stopped working again, everything seems to be working well.

Serval Type 1, Core 2 Duo, Gutsy 64 bit.

```

---

### Post by thomasaaron on 2007-12-28
steveneddy,

I think it is a 64-bit bug. Look here:
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/158849](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/158849)

There are some workaround listed in that post. Are those the ones you tried?
Also, did this problem ever occur under 32-bit? Or just with 64-bit?

Best,
Tom

---

### Post by steveneddy on 2007-12-29
> **thomasaaron said:**
> steveneddy,

I think it is a 64-bit bug. Look here:
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/158849](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/158849)

There are some workaround listed in that post. Are those the ones you tried?
Also, did this problem ever occur under 32-bit? Or just with 64-bit?

Best,
Tom

Tom - Is the Serval Performance Type 1 based on the HP laptop in this bug report?

---

### Post by steveneddy on 2007-12-30
OK - here's the scoop. I followed the advice, against what i thought may be right, and found the package** util-linux** on packages.ubuntu.com.

I downloaded the i386.deb file and saved it to my /home folder.

I then opened a terminal and used this command to execute the installation of this 32 bit software on my 64 bit machine.

```

sudo dpkg --force-architecture -i util-linux_2.13-8ubuntu1_i386.deb

```

I then restarted the machine and checked the hardware clock in my BIOS to set it correctly and noticed that it was now ticking while viewing the BIOS when before it wasn't even ticking (the seconds were incrementing sequentially on a regular tick).

The GRUB menu clicked off and I didn't have to hit the ESC key and select the kernel that I wanted to boot into. So far so good.

My boot time is now the 12 second boot time that I had to com to know and love.

**PROBLEM:**

Now the auto update manager was going wild telling me that I had to update. Hmmm - ran the update manager and it told me that I had broken packages.

I ran this command

```

suto apt-get install -f

```

and it removed util-linux, ubuntu-minimal and util-linux-locales. 

I reboot. Cool - fast boot times, everything looks good. 

I test the system by moving a small text file from my /home folder to my ~/Desktop via the terminal command

```

mv scripts ~/Desktop

```

"scripts" was the name of the file that I moved to the Desktop.

Worked great.

Util-linux is the base of the Ubuntu system that has the basic UNIX commands and features that we use and may not know it through moving, deleting and creating files and installing software. 

**Synopsis:**

Installing the 32 bit version of hwclock by using the util-linux software package from packages.ubuntu.com solved my issues with slow boot times due to the system looking for a way to set the hwclock during the boot process.

This is a 64 bit bug that may not affect all PC's running 64 bit software. 

This worked for me on a System76 Serval Performance Type 1 laptop running a Core 2 Duo processor, 2 Ghz, 2 Gig of RAM and nVidia graphics card and the nVidia drivers from the repos.

I am on Ubuntu Gutsy 7.10 as of this date and the laptop seems to be running fine.

The laptop ran great before this "repair" after it was fully booted up. The issue was that there was an almost 10 minute boot and shutdown cycle that made it unbearable to use or transport the machine until it was fully booted or shutdown.

Now to tackle the suspend issue.

**EDIT:**

This was also affecting the suspend capabilities of this laptop. After this "repair" the suspend issues are now solved. The laptop now suspends correctly and wakes up in about 5 seconds.

**Thanks Tom for making me look somewhere other than these forums for an answer. I went into this kicking and screaming not knowing for sure if this was going to work correctly, which it did. **

This was the fix I was looking for.

---

### Post by steveneddy on 2007-12-30
Maybe this is one for a new thread, but now auto updates wants to upgrade **util-linux** because the version I installed isn't showing up in Synaptic.

Anyone know how to fix this?

---

### Post by thomasaaron on 2007-12-31
Right on.

No the SerP1 is not based on that HP. My understanding is that the bug is primarily an OS bug. But you're right, it does seem to effect some models and leave others alone.

Good work, by the way.

---

### Post by steveneddy on 2007-12-31
> **thomasaaron said:**
> Right on.


Good work, by the way.

Thanks - any idea how to get Synaptic to ignore the 64 bit package so it will stop asking me to install it?

---

### Post by thomasaaron on 2007-12-31
Other than installing 32-bit Ubuntu? Nope.:-k

---

### Post by SteffJay on 2008-01-01
I have a hwclock issue, perhaps you can solve for me please. I am using Dapper Drake v6.06 (with all updates included), no packages are broken and the mobo is an Asus A7n8X-E deluxe with an AMD 3.0 Ghz processor 32 bit. 3 Gb of ram. The instalation is done, primarily as a server for Apache2, MySQL, PHP5 etc. The problem i am having is that the clock (using UTC) is racing. For example, over a 24 hour period it gains about 19 minutes. I have tried everything to get this to work properly but to no avail. I am also running Firestarter but it is not showing me any connection using UTC. I have to reset the clock manualy which is most frustrating which also causes a problem with Macromedia Flash Server (FMS) when the time is changed, then i have to restart for the settings to take effect. :mad: Any halp on this subject would be greatly appreciated. Thanks in advance.

---

### Post by steveneddy on 2008-01-01
> **SteffJay said:**
> I have a hwclock issue, perhaps you can solve for me please. I am using Dapper Drake v6.06 (with all updates included), no packages are broken and the mobo is an Asus A7n8X-E deluxe with an AMD 3.0 Ghz processor 32 bit. 3 Gb of ram. The instalation is done, primarily as a server for Apache2, MySQL, PHP5 etc. The problem i am having is that the clock (using UTC) is racing. For example, over a 24 hour period it gains about 19 minutes. I have tried everything to get this to work properly but to no avail. I am also running Firestarter but it is not showing me any connection using UTC. I have to reset the clock manualy which is most frustrating which also causes a problem with Macromedia Flash Server (FMS) when the time is changed, then i have to restart for the settings to take effect. :mad: Any halp on this subject would be greatly appreciated. Thanks in advance.

OK - so is the clock in the BIOS running fast or is it the clock in the software that is gaining time?

These are sometimes two totally different issues.

One thing that you might try is this:

Open this file - /etc/default/rcS - with this method:

I assume that you have a Gnome desktop. Otherwise, if you have KDE, use Kate or your favorite text editor, like vi.

```

sudo gedit /etc/default/rcS

```

it will look like this, or close to it.

```

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no

```

and change the **UTC=yes** to **UTC=no**

reboot and see what happens.

---

### Post by SteffJay on 2008-01-01
> **steveneddy said:**
> OK - so is the clock in the BIOS running fast or is it the clock in the software that is gaining time?

These are sometimes two totally different issues.

One thing that you might try is this:

Open this file - /etc/default/rcS - with this method:

I assume that you have a Gnome desktop. Otherwise, if you have KDE, use Kate or your favorite text editor, like vi.

```

sudo gedit /etc/default/rcS

```

it will look like this, or close to it.

```

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no

```

and change the **UTC=yes** to **UTC=no**

reboot and see what happens.



Ok steveneddy. I'll give that a bash and get back to you in a day or so.. Thanks for the quick reply....  :)

---

### Post by riseringseeker on 2008-01-02
> **steveneddy said:**
> Maybe this is one for a new thread, but now auto updates wants to upgrade **util-linux** because the version I installed isn't showing up in Synaptic.

Anyone know how to fix this?

Sure, just lock the version you have in synaptic and it won't show in the update manager any longer.  You will have to unlock it if you do decide to upgrade though.

Open synaptic, locate and highlight the package in question, then click package and lock.

---

### Post by steveneddy on 2008-01-03
I was just going over old posts and this problem started when I went to 64 bit.

I didn't believe tom, but it seems that I have had this bug for a while and the machine dealt with it somehow until recently.

This fix worked and the machine has been stable all week.

I find it a little humorous that my laptop boots up and down much faster that my boss' 6 month old laptop with vista installed.

My boot time was clocked from cold at 48 seconds and shut down is in the 30 second range.

The vista box takes 5-10 minutes to boot fully and shutdown, I laugh thinking about it, he carries the lappie out of the case through the office waiting for it to shut down. sometimes it takes 15 minutes.

Thanks, Tom, again for all of the help.

---

### Post by SteffJay on 2008-01-04
Hello **steveneddy**. After following your advice with inputting NO for the UTC, i t seems that, that has done the trick :) Thanks for the up. Happy New Year m8 !!

---

### Post by steveneddy on 2008-01-04
> **SteffJay said:**
> Hello **steveneddy**. After following your advice with inputting NO for the UTC, i t seems that, that has done the trick :) Thanks for the up. Happy New Year m8 !!

You are very welcome and I'm glad that I could help.

If you want to could you hit the "Thanks" button?

:popcorn:

---

