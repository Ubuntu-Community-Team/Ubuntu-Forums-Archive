---
title: "cpu frequency scaling"
date: 2007-08-30
forum: System76 Support
---

### Post by ncappel1 on 2007-08-30
Hello, I was wondering how I can find out if cpu frequency scaling is supported on my Gazelle Performance gazp3. it has a 2.0 Ghz dual core processor. 

when I add the cpu freq. scaling monitor to the panel, i get a little message saying that it is unsupported, is this because the system doesn't support it, or because i need to install something?

I tried following the steps here first: [http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

the ubuntugeek howto didn't work, so I thought I'd just ask the forum before I tried to follow the steps in the feisty guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

---

### Post by thomasaaron on 2007-08-30
It should work.
The second how-to you listed is what most people use to get it going.
What CPU do you have (cat /proc/cpuinfo)?

---

### Post by voidmage on 2007-08-30
I got my cpu scaling to work with:

sudo modprobe acpi_cpufreq

---

### Post by tedrampart on 2007-08-30
> **voidmage said:**
> I got my cpu scaling to work with:

sudo modprobe acpi_cpufreq

same here..

there's also another thread somewhere in this forum that explains how to get it to work.. just too tired right now to go back and look it up..

EDIT - here's the thread [http://ubuntuforums.org/showthread.php?t=497191](http://ubuntuforums.org/showthread.php?t=497191)

---

### Post by ncappel1 on 2007-08-31
everything seemed to work well, except that when I entered "sudo modprobe speedstep-centrino"  i got the following error: FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

I then tried the previous posters' suggestion of acpi-cpufreq
 and everything worked. except that later on a new boot, it stopped working! I double checked the steps, here is my /etc/modules
[HTML]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
acpi-cpufreq[/HTML]

any ideas? :-k

---

### Post by thomasaaron on 2007-08-31
Can you tell, after the boot is completed, if it actually DID load?
Try: lsmod

---

### Post by tedrampart on 2007-09-01
I found that when I added it to etc/modules after adding the applets for cpu frequency to the panel, I had to remove and re-add them for some reason.

but now I just use powernowd

it might be worth it, to try removing and re-adding the applets to see if that has any affect, now that acpi_cpufreq is added to etc/modules

---

### Post by ncappel1 on 2007-09-01
tom, don't know if it is still relevant, but I attached my /proc/cpuinfo

on a fresh boot, lsmod doesn't show acpi_cpufreq at all (though cpufreq_userspace, cpufreq_stats, etc are there). if I run sudo modprobe acpi-cpufreq manually everything works fine.

does it make a difference if in etc/modules i put acpi_cpufreq or acpi-cpufreq? I tried both and neither worked.

tedrampart- closing and reloading the applets doesn't have an effect!

---

### Post by tedrampart on 2007-09-03
you have the same cpu info that I have on my gazp3.. so it should be working..

what happens when you run "sudo powernowd"  I use it for cpu scaling, and added it to my etc/rc.local

if that works, then you can atleast tell if scaling works or doesn't work.

---

### Post by ncappel1 on 2007-09-03
I should clarify that the cpu scaling **does** work. However, I need to run modprobe acpi-cpufreq at each fresh boot, even though i put it in /etc/modules.

I also removed powernowd and cpudyn (step two of feistyguide howto posted above)

---

### Post by thomasaaron on 2007-09-04
Have you tried writing a little script to add the module, and inserting the script into sessions or init.d?

---

### Post by ncappel1 on 2007-09-04
no, I havn't, i don't know very much about scripts. would it be loaded for all the users on the machine? or just mine?

from what I understand, adding the module to /etc/modules should have made it load at each boot...

---

### Post by thomasaaron on 2007-09-04
Yeah, that's what you would think.
But a sure way to do it would be to write a script and add it to your sessions. It would only be for whatever user account you wanted it to run in.

If you want it to run for every account, you can put the script into init.d.

Let me know which one you'd like to try and I'll help you with the proper scripts and commands tomorrow. (I've got to pick up my kids right now!)

Take care.
Tom

---

### Post by ncappel1 on 2007-09-06
It would be most helpful if the script would run for every account.

:)

thanks for the help,
n

---

### Post by thomasaaron on 2007-09-06
Create a text file like this:

```
#!/bin/sh
modprobe acpi-cpufreq
```

Save it on your Desktop as cpuScaling.sh

Now enter these commands one at a time:

sudo mv ~/Desktop/cpuScaling.sh /etc/init.d
cd /etc/init.d
sudo chmod a+x cpuScaling.sh
update-rc.d cpuScaling.sh defaults

That should work (should being the key word, here.)

---

### Post by ncappel1 on 2007-09-07
Tom, you are a wizard. it worked perfectly. thanks a million!
n

edit: I even learned a little bit about shell scripts, I tried the same steps (different file name, of course) with the following: 

#!/bin/sh
pon dsl-provider

and now my dsl connection starts up at boot too! yay

just for curiosity, to remove a script we added to init.d can we just delete it from the folder? or does something else have to happen too?

---

### Post by thomasaaron on 2007-09-07
In the past, I've just deleted the script from /etc/init.d, and that has done the trick.

It seems like you might run the update command again, but since you don't have a filename anymore...  I'll have to look that one up.

---

### Post by thomasaaron on 2007-09-07
Here's a good how-to on boot scripts.
It doesn't mention removing scripts, but it does mention de-activating them.

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

