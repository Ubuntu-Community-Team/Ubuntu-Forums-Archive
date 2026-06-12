---
title: "loaded updates: now starling locks up at password window"
date: 2010-02-04
forum: System76 Support
---

### Post by eljayski on 2010-02-04
and i get a message that the gnome power manager is not properly configured.

advice appreciated!  eljayski

---

### Post by thomasaaron on 2010-02-04
If you're running 9.10, please try this...

> This is a new bug we've recently encountered. There is a package called winbind that, as far as we can tell, is breaking HAL (the hardware abstraction layer), which provides an interface to your keyboard and mouse.

Here is the fix...

1. Establish a wired (Ethernet) Internet connection.

2. Boot into recovery mode.
Right after the System76 Splash Page, you will see the word "Grub" in the upper left corner of your LCD. The moment you see it, quickly press "Shift." This should get you to a list of available kernels. Choose the first kernel that has "Recovery Mode" in its title. You will then be prompted to select a particular recovery mode functionality. Select Netroot (or "boot into a root prompt with networking").

3. Once you're in recovery mode, run the following commands. (In some instances, the letters typed are not echoed to the screen, but they are being entered.)

dpkg --configure -a
apt-get remove winbind
apt-get install winbind
apt-get --reinstall install hal
apt-get update
apt-get dist-upgrade
reboot -h now


---

### Post by eljayski on 2010-02-04
thank you, thomas!  i'll try the fix when i get home this evening.  for my info, is it advisable to download updates with a hardwire internet connection?  many thanks, eljayski

---

### Post by thomasaaron on 2010-02-04
It's often faster than a wireless connection. But technically, it doesn't really matter.

For the above procedure, though, a wired connection is definitely necessary.

---

### Post by Wildbill1 on 2010-02-04
Tried your fix, but to no avail.  The problem was that I could not follow what was happening on screen.  Don't know whether I missed something as the screen was totaly unreadable.  Third times a charm!  No way, could not connect to planet76.com, although, I could read the screen up to this point.  Anyway, will try again in the morning before I board my flight, that I can't use my Starling, for the second time due to upgrade breaks.

---

### Post by nealaustin on 2010-02-05
It seems right now that planet76 is down and without the planet 76 repository any upgrade or this fix keeps timing out. Right now I'm without wireless until my Starling can reconect

---

### Post by Thepookster on 2010-02-05
Had the same problem, first day with my starling no less lol.

Would try this now but seems like the 76 domain is down, hopefully it will be up when I get home.

Question, assuming this fixes the issue, are we safe to once again run the system updates?  Was this a system76 specific update or was it a generic Ubuntu update?

Good thing I love Ubuntu enough to forgive its occasional follies ;)

Thanks for your hard work and quick response Tom.

---

### Post by thomasaaron on 2010-02-05
I wouldn't run any updates just yet.

Our web hosting service is experiencing a data center-wide outage. We are currently transferring our site to other servers and expect this process to take a couple of days.

While we will be unable to take orders while the site is down, we are still available via forums, phone and email to answer any sales or support questions you have.

This will also keep the System76 Driver from running, as it pings our website to determine that there is an Internet connection. We're sorry for this inconvenience.

Please see...
[http://ubuntuforums.org/showthread.php?t=1399130](http://ubuntuforums.org/showthread.php?t=1399130)
...for further updates on our website.

Tom Aaron
[email]support@system76.com[/email]
720-226-9269

---

### Post by Thepookster on 2010-02-05
> **thomasaaron said:**
> I wouldn't run any updates just yet.

Our web hosting service is experiencing a data center-wide outage. We are currently transferring our site to other servers and expect this process to take a couple of days.

Ouch! Well when it rains it pours I guess.

So does this mean for us Starling owners there is not much we can do atm?

---

### Post by thomasaaron on 2010-02-05
Well, the above commands don't require the System76 Driver, so they shouldn't be a problem.

But if you have to re-image or run the driver, then, yes.

---

### Post by nealaustin on 2010-02-05
> **nealaustin said:**
> It seems right now that planet76 is down and without the planet 76 repository any upgrade or this fix keeps timing out. Right now I'm without wireless until my Starling can reconect

I was able to resolve this by using sudo gedit then in ect/modeprobe.d/rtl8187 then adding the # in front of blacklist rtl8187 and then saving. After the reboot all is well. I wonder if just removing the rtl8187 file would keep this problem from reappearing in the future?

---

### Post by thomasaaron on 2010-02-05
OK, basically what you've done is keep the system from blacklisting the rtl8187 driver (which is the driver that we have replaced via the System76 Driver). 

In other words, for proper wireless range, you *need* to have that driver blacklisted.

But, if that works, you can establish a wired Internet connection, open a terminal and run the commands I gave you earlier. You need to preface all of them with "sudo" though.

Then, try removing the # from the rtl8187 module and rebooting. Did that fix it.

---

### Post by nealaustin on 2010-02-05
> **thomasaaron said:**
> OK, basically what you've done is keep the system from blacklisting the rtl8187 driver (which is the driver that we have replaced via the System76 Driver). 

In other words, for proper wireless range, you *need* to have that driver blacklisted.

But, if that works, you can establish a wired Internet connection, open a terminal and run the commands I gave you earlier. You need to preface all of them with "sudo" though.

Then, try removing the # from the rtl8187 module and rebooting. Did that fix it. 
That fix hung up trying to connect to planet 76. I'm ok for now so I will redo it when the site is back up and running.
Thanks , I'll keep you updated when I do.

---

### Post by Thepookster on 2010-02-05
im having same problem, it just keeps trying to connect to the planet76 domain and timing out over and over.

I was able to get a few of the commands to go through but its still freezing at the logon screen, is there anything I can do just to get back in to the OS?  is there a way to revert back to a previous state before the updates fubar'd everything?

---

### Post by thomasaaron on 2010-02-08
OK, the website is back up, now. So it should connect to planet76.

---

### Post by Wildbill1 on 2010-02-12
Finally got back from my trip.  Tried to run the fix but my system still returns me to the log in window after logging in.  Any other suggestion?

---

### Post by thomasaaron on 2010-02-12
Hi, Wildbill.

I responded a few minutes ago to your email. I'll await your reply there.

---

