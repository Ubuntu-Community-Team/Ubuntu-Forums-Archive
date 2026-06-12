---
title: "Ubuntu HP laptop Overheating problem solved"
date: 2008-10-18
forum: The Cafe
---

### Post by mstipic on 2008-10-18
Hello,
I dont know if ther is any active thread but i'd like to tell that i solved HP (CQ 6820) overheating problem. 
I found that many users have this problem.
I tried to lower ati power state trough aticonfig. But that didn't work. Well laptop is not old and the temperatures of cores were about 45-50 degrees in Win Vista.

Before mod the temperatures of cores were about 60 degrees with no active programs running.
So I moded a configuration file in /etc/modules. I added these lines:
battery
ac
processor
thermal
acpi-cpufreq
cpufreq-userspace

Then I installed tool kpowersave, enabled it at startup and set dynamic processor usage.
The result was temperature about 44-48 degrees which is even lower then in Vista.
(my new issue now is blinkink screen of opengl application in dekstop mode.)
good luck

---

### Post by xarte on 2009-01-17
so do I just add the text exactly as you've written? At the top or the bottom of the file?

I just tried adding some lines to X11.conf (think that was it...) for a different overheating fix (video card settings) and it wouldn't boot and had to go back to default settings.

I don't know what I'm doing but need to get this fixed. My laptop is about to cook itself, and it's so frustrating that so many threads on this topic say 'clean the fan' or 'shut down xyz' - I don't think installing a different distro suddenly dirtied my fan - it was running fine before - and I don't want to have to shut down graphics or flash or whatever - that's pointless. I should be able to run loads of stuff without overheating.

sorry for starting to rant!

anyway. Could you just rephrase your solution for complete idiots so I don't break anything when trying to apply it? Thanks!

---

### Post by wyth on 2009-02-15
Yep, add it as written, but don't mess with your X-files.  Add them to /etc/modules.

If you look in /etc, you'll see a file called modules.  You'll need to open it as root.  At the command line, sudo nano /etc/modules, or use gedit, or vim, or whatever knocks your socks off.

---

### Post by Reaper29 on 2009-03-03
how do i add kpowersave to start-up?

---

### Post by shibbz on 2009-07-13
Hi,

I know this thread is a little old but..

I tried this on Ubuntu 9.04, on an HP dv6411ej.

My problem is the same. I boot up with nothing running but default ubuntu settings, and my temp reaches 87c.  

I tried using your solution, but yacpi indicates the same temp. Nothing has changed.

Is there anything you changed and did add to your post?

Thanks.

---

### Post by Firestem4 on 2009-07-13
Personally I am beginning to believe this problem lies in HP's manufacturing. I have an HP Dv9600 that i run ARCH and Vista on (Predominantly Vista.) Over the two years ive had it the heat issues have grown and the overheating has actually warped the keyboard.

The laptop just keeps getting warmer and warmer under idle power too (Linux or Windows)..

Many other people seem to have HP problems with heat too..so blah =(

---

### Post by Ecsthetic on 2009-09-20
> **Reaper29 said:**
> how do i add kpowersave to start-up?

once you downloaded the kpowersave, there will be a gui configuration.

---

### Post by jelliott1963 on 2011-02-27
> **mstipic said:**
> Hello,
I dont know if ther is any active thread but i'd like to tell that i solved HP (CQ 6820) overheating problem. 
I found that many users have this problem.
I tried to lower ati power state trough aticonfig. But that didn't work. Well laptop is not old and the temperatures of cores were about 45-50 degrees in Win Vista.

Before mod the temperatures of cores were about 60 degrees with no active programs running.
So I moded a configuration file in /etc/modules. I added these lines:
battery
ac
processor
thermal
acpi-cpufreq
cpufreq-userspace

Then I installed tool kpowersave, enabled it at startup and set dynamic processor usage.
The result was temperature about 44-48 degrees which is even lower then in Vista.
(my new issue now is blinkink screen of opengl application in dekstop mode.)
good luck



I am having the same problem but I am somewhat uninformed to the technical aspects as depicted above. Can you tell me how you resolved this issue?

---

### Post by jelliott1963 on 2011-02-27
> **jelliott1963 said:**
> I am having the same problem but I am somewhat uninformed to the technical aspects as depicted above. Can you tell me how you resolved this issue?
Hello: 
I am having the same problem but I am somewhat uninformed to the  technical aspects as depicted in your message from October of 2008. Can you tell me how you resolved  this issue? My HP g60 started shutting down a few months ago due to over heating. HP has not been much help. I do not want to send the laptop away and not get it back for a month as has been my past experience.
HELP! Thanks JOHN

---

### Post by cariboo on 2011-02-27
THis is an old thread, and some of the solutions may not work any more, jelliott1963, I would suggest you start a new thread in [Hardware & Laptops]("http://ubuntuforums.org/forumdisplay.php?f=332").

This thread is closed.

---

