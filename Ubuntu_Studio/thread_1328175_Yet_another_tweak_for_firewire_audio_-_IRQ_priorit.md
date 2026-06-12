---
title: "Yet another tweak for firewire audio - IRQ priorities"
date: 2009-11-16
forum: Ubuntu Studio
---

### Post by trulan on 2009-11-16
[B]The rtirq script in the Karmic repositories is out of date and does not work properly.
[/B]It is essential for real-time patched kernels 2.6.31 or newer to update the rtirq script, as detailed in post 5 of this thread.

In poking around as I am inclined to do, I came across some interesting information.  It was all new to me and I thought I'd pass it along.

With the RT kernel comes some added abilities in the area of IRQ priorities, especially with Karmic's kernel.  Ubuntu Studio by default comes with a program called rtirq installed, and it is assigned the task of getting these priorities the way we want them.  By default, it is configured to give Alsa devices a very high priority, with USB devices right behind.  1394 firewire devices are left to fend for themselves.  We want to change that:

```
sudo gedit /etc/default/rtirq
```The line we are interested in is RTIRQ_NAME_LIST.  By default it reads:

```
RTIRQ_NAME_LIST="rtc snd usb i8042"
```Add ohci1394 second in the list, so it looks like this:

```
RTIRQ_NAME_LIST="rtc ohci1394 snd usb i8042"
```And when you reboot, your firewire card will have top priority!
 Unless you're using something like a PC-Card, where a card controller is involved. In that case, the card controller's device name needs to be in front of ohci1394 in the list.

For better performance, add it to this line as well:
[code]RTIRQ_NON_THREADED="rtc ohci1394 snd"

 For a more detailed explanation, and for more IRQ tweaks, read this very informative page:
[http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)

---

### Post by AutoStatic on 2009-11-16
[http://www.youtube.com/watch?v=futxIzHLcuM](http://www.youtube.com/watch?v=futxIzHLcuM)

Sorry, first thing that popped up in my mind :-\"
Going to test it on my 9.10 installation asap :)

---

### Post by trulan on 2009-11-17
```
RTIRQ_NAME_LIST="rtc ohci1394 snd usb i8042"
```It seems than the real time clock (rtc) actually gets missed with the default settings.  It is supposed to be set to 90, the highest of IRQ priorities.  It shows up as rtc0 when I check the IRQ priorities in a terminal (using a command on the ffado wiki page I posted above).  I need to do more research but I think this may actually be a bug.  If I change it to rtc0 like this:
```
RTIRQ_NAME_LIST="rtc0 ohci1394 snd usb i8042"
```then it gets prioritized properly.  I'd like some feedback from experienced users, because like I said, I think this is a bug.

Edit: it indeed is a bug.  It has been corrected by the developer but the update hasn't made it into the Ubuntu reposiroties yet.  Update your script as outlined in post 5.

Also, on another note, I think I get better performance by adding ohci1394 to the unthreaded list in rtirq.  Again, more research is needed.

---

### Post by trulan on 2009-11-18
And here's the settings portion of /etc/default/rtirq, as I am using it currently:

```
# IRQ thread service names
# (space separated list, from higher to lower priority).
RTIRQ_NAME_LIST="rtc0 ohci1394 snd usb i8042"

# Highest priority.
RTIRQ_PRIO_HIGH=90

# Priority decrease step.
RTIRQ_PRIO_DECR=2

# Whether to reset all IRQ threads to SCHED_OTHER.
RTIRQ_RESET_ALL=1

# On kernel configurations that support it,
# which services should be NOT threaded 
# (space separated list).
RTIRQ_NON_THREADED="rtc0 snd ohci1394"

# Process names which will be forced to the
# highest realtime priority range (99-91)
# (space separated list, from highest to lower priority).
# RTIRQ_HIGH_LIST="timer"
```

Note the changes of rtc to rtc0, and the presence of ohci1394 in the 'non-threaded' list.

Also, the ffado wiki page (linked in my first post) recommends setting a higher priority for the softirq-tasklet threads (one for each cpu).  As of yet there seems to be no way to do this with rtirq.  I'm not sure how much difference these make, but my system is running as never before!

---

### Post by trulan on 2009-11-19
I asked about the problem with rtc vs. rtc0 here:
[http://www.rncbc.org/drupal/node/107](http://www.rncbc.org/drupal/node/107)
and he said I should update my script, this has been fixed some time ago.  So I filed a bug about it here:
[https://bugs.launchpad.net/ubuntu/+source/rtirq/+bug/485262](https://bugs.launchpad.net/ubuntu/+source/rtirq/+bug/485262)

Until the rtirq package is updated, you can get the latest version of rtirq here:
[http://www.rncbc.org/jack/](http://www.rncbc.org/jack/)
Unfortunately for us Ubuntu guys, he does rpm's, not deb's.  I'll attempt to update though - we'll see how it goes.

Edit:  I was trying to make that too hard.  There's no 'building' involved - it's just a file or two to copy, since we already have the script installed.

To update your script, download the tar.gz and extract it.  In a terminal, from the newly extracted directory, run:
```
sudo cp rtirq.sh /etc/init.d/rtirq
```
The settings file hasn't changed, but you can copy the new one into place as well if you like:
```
sudo cp rtirq.conf /etc/default/rtirq
```Then, of course, add ohci1394 to the NAMES_LIST line and the UNTHREADED line.

Now we are getting somewhere!

---

### Post by kinta on 2009-11-22
Doing this helps with the sirq-tasklet priority as is said in [http://subversion.ffado.org/wiki/IrqPriorities:](http://subversion.ffado.org/wiki/IrqPriorities:)
```
# ps -eLo pid,cmd | grep tasklet| awk '{ system("chrt -f -p 78 " $1)}'
```

---

### Post by trulan on 2009-11-23
OK I got it.  I had to add 'sudo' in the middle, like this:
```
ps -eLo pid,cmd | grep tasklet| sudo awk '{ system("chrt -f -p 78 " $1)}'
```
Otherwise I got an 'operation not permitted' error.

Of course you could change the 78 to whatever priority you want to assign to your tasklet threads.

---

### Post by kinta on 2009-11-24
You can read that there's a "#" before the command and not a "$", this means that the command is executed as root.  
And that's true, minor xruns or skip cycle errors after changing the priority.

Also can be helpful to put your cpus in performance mode to avoid scaling cpu ( [http://www.mail-archive.com/64studio-devel@64studio.com/msg01427.html](http://www.mail-archive.com/64studio-devel@64studio.com/msg01427.html) ): 
```

sudo su

```and then:
```

for cpu in ` seq  0 $(lscpu | grep "CPU(s)" | awk '{ print $2-1 }' )`
do 
    echo  performance > /sys/devices/system/cpu/cpu$cpu/cpufreq/scaling_governor;
done

```(note: If you have a Laptop consider extracting the battery if you can plug it on the wall! or the battery will be a brick in few months... the previous commands tells to cpus to work at full perfromance all the time! )


I wrote a bash script that I run before starting my rt production studio in /usr/local/bin/startstudio :
```

#!/usr/bin/env bash
#run it with SUDO or AS ROOT
TASKLETPR=78
#avoid cpu scaling
for cpu in ` seq  0 $(lscpu | grep "CPU(s)" | awk '{ print $2-1 }' )`
do
    echo  performance > /sys/devices/system/cpu/cpu$cpu/cpufreq/scaling_governor;
done
#give sirq-tasklet priority
ps -eLo pid,cmd | grep tasklet| grep -v grep | awk '{ system("chrt -f -p '$TASKLETPR' " $1)}'


```And then:
run it with
```

sudo startstudio

```or tell qjackctl to run it before starting jack with kdesudo startstudio or gksudo startstudio.
And If you need to work with audio you may consider if you need visual effects like compiz. When you're in a digital audio workspace you need a lot of windows running: jack control, ardour, hydrogen, rosegarden jack rack, qsampler... Switching between these windows  with desktop effects may suppose a 30% of cpu without these it will be around 7~10% CPU.
and hungry graphics drivers, in my case switching from nvidia to nouveau improves a little (this also makes your studio free as in freedom ;) ).

and so on if you don't need network you can turn off the network switch.

---

### Post by trulan on 2009-11-24
> **kinta said:**
> You can read that there's a "#" before the command and not a "$", this means that the command is executed as root.
Wow.  I never knew that.  I wondered why people put those at the beginning...but putting 'sudo' in front as I usually do to run commands as root doesn't work, it has to be in the middle, as I posted above.

> I wrote a bash script that I run before starting my rt production studio...tell qjackctl to run it before starting jack with kdesudo startstudio or gksudo startstudio.VERY nice.  That saves a lot of trouble.  I have your startstudio script running with qjackctl.  Thank you very much!

---

### Post by trulan on 2009-11-24
For some reason the 'performance' cpu governor setting does not stick - it reverts to 'ondemand' after a few minutes.  I think it's a Karmic issue (or is it a feature?)  At any rate, I was experimenting with your script.  (I know basically nothing about scripts).

First, I tried calling cpufreq-selector with the script and assigning my maximum cpu speed that way.  But for some reason, cpufreq-selector freezes for a full 30 seconds after the cpu speed is set.  It did this for each cpu, so when I ran the script from qjackctl, it froze for a full minute while it waited for the cpu scaling to be complete.

So, I came up with this solution:  Since the governor settings don't stick, how about using the minimum scaling setting to force the cpu to the maximum frequency?  And it works!  It's probably not the best way to do things, but it's simple and it works.

So here's my startstudio script:
```
#!/usr/bin/env bash
#run it with SUDO or AS ROOT
TASKLETPR=78
#avoid cpu scaling
for cpu in ` seq  0 $(lscpu | grep "CPU(s)" | awk '{ print $2-1 }' )`
do
     cp  /sys/devices/system/cpu/cpu$cpu/cpufreq/cpuinfo_max_freq /sys/devices/system/cpu/cpu$cpu/cpufreq/scaling_min_freq;
done
#give sirq-tasklet priority
ps -eLo pid,cmd | grep tasklet| grep -v grep | awk '{ system("chrt -f -p '$TASKLETPR' " $1)}'
```I also made another script, called stopstudio:
```
#!/usr/bin/env bash
#run it with SUDO or AS ROOT
#return cpu scaling to normal
for cpu in ` seq  0 $(lscpu | grep "CPU(s)" | awk '{ print $2-1 }' )`
do
     cp /sys/devices/system/cpu/cpu$cpu/cpufreq/cpuinfo_min_freq /sys/devices/system/cpu/cpu$cpu/cpufreq/scaling_min_freq;
done
```I have qjackctl set to run 'gksudo startstudio' when Jack is started, and 'gksudo stopstudio' when jack is stopped.

Anyway, I have learned a lot through doing this.  Thank you again.

---

### Post by trulan on 2009-11-25
I attatched the startstudio and stopstudio scripts I am currently using.  I put them in /usr/local/bin/ and set qjackctl to run gksudo startstudio when starting Jack and gksudo stopstudio when stopping Jack.  It's a nifty setup, makes one less thing to forget when setting up to record.

---

### Post by bluesscream on 2009-11-26
Heavy stuff Trulan, this seems to be really important for rt-audio performance improvement. For maximizing cpu frequency by default I try another way over configuring rt.local and sysfsutils. But for setting rtirq priorities I don't really understand this code with ps, tasklet, awk and the language in which they are used. 
The link kinta (thank you) gave - needs to be corrected by deleting colons at the end - does not help me understand setting sirq. Can someone enlighten me?

---

### Post by trulan on 2009-11-26
> **kinta said:**
> Doing this helps with the sirq-tasklet priority as is said in [http://subversion.ffado.org/wiki/IrqPriorities:](http://subversion.ffado.org/wiki/IrqPriorities:)
```
# ps -eLo pid,cmd | grep tasklet| awk '{ system("chrt -f -p 78 " $1)}'
```
I don't understand the how the code works either.  But I know what this line does - it sets the softirq-tasklet threads to rt priority 78.  The way it uses grep and awk allows it to work on multi-core processors - there will be one tasklet for each core, and it will set the priority of each one..

The ffado wiki mentions upping the priorities of the tasklets for better performance.
[http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)

The script just combines this and cpu scaling.

It's deep, you're right - way over my head for sure ;)

---

### Post by bluesscream on 2009-11-27
Tx trulan, this helps me to understand what this code line does.
At least I want to have a clue where I poke around  ;)
Indeed binding this script to jack start makes sense.
I found a startup script etc/init.d/ondemand. It has a line with a sleep 60 command to give desktop login time before system is set to governor ondemand. This was the reason my first rc.local edits failed, system took my commands at start up but little later all was reset to ondemand. After removing it's xbit my rt.local governor settings run

---

### Post by kinta on 2009-11-29
For cpu scaling maybe your troubles with cpu scaling are in gnome power applet or another application that manage the power ( in kde powerdevil did it... ), I am using Kde most of the time and the kde power manager applet let's me put my cpu at performance mode.
With the script you made you are not changing the governor, therefore the cpu keeps working on demand. I suggest to you my script... And investigate which is the app that is changing the governor to ondemand. 

One more thing, for pragmatic issues I recommend you to put your scripts in /usr/local/bin, it's  a way to organize your self-made scripts / compilations  and keep it away from the deb installation system (if a deb package contains a file called startstudio which needs to be in /usr/bin/ it will delete your script...). And so on if you need to reinstall the whole system and you want to save your scripts you only have to take a look in /usr/local/...

---

### Post by trulan on 2009-11-29
Before you posted your script, I had been using the Gnome panel cpu scaler applets.  I had the same result, setting the CPU to performance would not stick, but setting a specific value did.  Other Gnome users have reported the same issue.  Setting the cpu as I am doing now is rather backwards, I realize, but it does reliably set the cpu to run at its maximum speed, which is what performance mode is supposed to do anyway.  Although the governor says 'ondemand', the minimum speed it will allow gets set to the CPU maximum speed.  Still, doing things the right way would be better.

I didn't think I had a /usr/local/bin/ directory, which is why I put it in /usr/bin/.  I'll move them, that makes sense.

---

### Post by kinta on 2009-11-29
Trulan, can you post the bug link of cpufreq-applet (if any...). To help users to decide which script to use in relation with the possibility to stick the cpu mode. 
So, I think that we can make the statement that if a user is using gnome (until bug is fixed), has to use your script , if not use mine.

---

### Post by trulan on 2009-11-30
I haven't been able to trace down what was setting the cpu governor back to on-demand.  What's more, today it is working properly - the setting will stay on performance.  Last week it wouldn't stay set to performance for more than three minutes.  Until we can track down what is sometimes causing the governor to revert to default, I would recommend that people running gnome use the cpu scaling panel applet, so they can easily see if the cpu is being scaled properly.  If it is working, use kinta's script.  If it keeps reverting back to on-demand, either use my script or try to figure out what is going on.

There were many bugs against cpu-scaling but I didn't find any that referred to governor settings not sticking.  The only thing I found was that in Karmic, it will boot up with the cpu set to performance, then change to on-demand after 60 seconds.  That's not a bug, it's a feature.

---

### Post by bluesscream on 2009-12-02
This is my solution for setting highest rt performance automatically at boot time -  further on I have  access to modify cpufreqency by clicking the applets - 
1. prohibit system to set back cpufreq to ondemand after 60 seconds: ```
sudo chmod -x /etc/init.d/ondemand
```
2. optional, if one wants to modify cpu freq without entering password: ```
sudo gedit /usr/share/polkit-1/actions/org.gnome.cpufreqselector.policy
``` go to the end of the file and edit line     <allow_active>[COLOR="Red"]blablabla[/COLOR]</allow_active> as follows   <allow_active>[COLOR="Red"]yes[/COLOR]</allow_active>
3. set highest frequency:
```
sudo aptget install sysfsutils
```
4. my /etc/sysfs.conf:
```
#
# /etc/sysfs.conf - Configuration file for setting sysfs attributes.
#
# The sysfs mount directory is automatically prepended to the attribute paths.
#
# Syntax:
# attribute = value
# mode attribute = 0600 # (any valid argument for chmod)
# owner attribute = root:wheel # (any valid argument for chown)
#

# Always use the userspace CPU frequency governor
devices/system/cpu/cpu0/cpufreq/scaling_governor = userspace
devices/system/cpu/cpu1/cpufreq/scaling_governor = userspace
# 
# Use userspace CPU frequency governor and set initial speed
devices/system/cpu/cpu0/cpufreq/scaling_governor = 2300000
devices/system/cpu/cpu1/cpufreq/scaling_setspeed = 2300000
#
# Set permissions of suspend control file 
# mode power/state = 0660
# owner power/state = root:power
```
  
4. Set taskletpr:
/etc/rc.local: 
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# echo 20 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
# echo 20 > /sys/devices/system/cpu/cpu1/cpufreq/ondemand/up_threshold

TASKLETPR=78
ps -eLo pid,cmd | grep tasklet| grep -v grep | awk '{ system("chrt -f -p '$TASKLETPR' " $1)}'

exit 0
```

Plz understand this as example and modify for your own configuration.
Guess its self-evident for non kamikazes to write down such changes for being able to restore if something fails. For me it's working stable with highest audio performance.
I did not invent nothing, all these stuff you'll find better explained around these forums or by asking google.

---

### Post by AutoStatic on 2009-12-11
Woohoo! Installed rtirq, replaced the /etc/init.d/rtirq with the more recent one, added the ohci1394 module to /etc/default/rtirq, disabled my wireless device and ran the script to change the priority of the sirq-tasklet and YES, my Focusrite fires up flawlessly and runs smoothly (listening to a recording with about 20 tracks and some MIDI stuff now)! Thanks guys! Now I can use my Focusrite with my notebook too, that's kind of a relief, at least I have a good backup now :)

For the record, the Focusrite refused to run well on my notebook, it kept spitting out the following error:
```
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
```
I don't see those anymore, good riddance :)

---

### Post by AutoStatic on 2009-12-18
FYI, rtirq also works nicely on my netbook to prioritize the HDA Intel chipset. The netbooks runs really stable now with low latencies. The two lines in /etc/default/rtirq that matter:
```
RTIRQ_NAME_LIST="rtc 'HDA Intel' snd usb i8042"
RTIRQ_NON_THREADED="rtc 'HDA Intel' snd"
```

---

### Post by nutjob on 2009-12-21
trulan,

your notes inspired me to register for this forum so I can say THANK YOU, and maybe I'll get more engaged here now that I'm STOKED to be making music!

I have a PreSonus Firebox, getting tons of clicks and pops but no xruns (well, maybe every minute or two would get one), even when dragging out the latency pretty high. I'm running on a Dell Latitude D630 laptop, so no special hard disk or other optimized hardware except for the presonus firebox. Running Ubuntu Studio 9.10 from DVD fresh install, no custom compiled stuff yet.

Immediately after adjusting the rtirq stuff with ohci1394, the clicks and pops are totally gone. I made my first linux-based recording of my classical guitar through an SM-57 mic, and recorded another track while playing it back via Ardour a minute later, and all looks good!

Except, still have a half-second drop-out in the middle of the recording... I'll take a look at the other optimizations tomorrow. But thanks for the folks who care about documenting their trials and tribulations for the benefit of others. I've done that a lot with Asterisk PBX stuff in the past, maybe will do it more with this audio stuff as I get myself sorted out.

---

### Post by sub_acoustic on 2010-05-23
Thanks so much trulan and everyone else.  I finally have a working system with my firebox on Puredyne!  Only a few rare xruns under intensive cpu use, but I guess that's to be expected...
Because I'm also using an expresscard, I inserted the bits below in bold in the  /etc/default/rtirq as below...as I'm using a Startech Expresscard (as recommended by Presonus) I also put raw1394 in there before the ohci1394...with my technical knowledge i go by guesswork rather than understanding things completely...there are probably ways in which i could finetune the system but in the meantime i can finally make some sound with my Firebox!

Thanks ffado developers for making this possible! you rock!  and all the people with helpful advice on lists like this, I take back what I said about the Firebox being an expensive paperweight...

# IRQ thread service names
# (space separated list, from higher to lower priority).
RTIRQ_NAME_LIST="rtc0 **raw1394 ohci1394** snd usb i8042"

# On kernel configurations that support it,
# which services should be NOT threaded
# (space separated list).
RTIRQ_NON_THREADED="rtc0 snd **raw1394 ohci1394**"

---

### Post by sub_acoustic on 2012-03-12
So Ardour inexplicably stopped working in Puredyne 9.11 so I've upgraded to Ubuntu Studio 11.10 - my firebox is working with the same changes as above (with the generic kernel).  

Although when I start ffado-dbus-server (it works) but I get the following error message

>  Discovering devices...
02315920162: Warning (ieee1394service.cpp)[ 375] initialize: Could not set SPLIT_TIMEOUT to min requested (1000000)
02315920228: Warning (ieee1394service.cpp)[ 379] initialize: Set SPLIT_TIMEOUT to min requested (1000000) did not succeed
DBUS service running
press ctrl-c to stop it & exit


perhaps this can be finetuned somehow

---

