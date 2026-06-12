---
title: "Lemur Battery Life"
date: 2010-03-19
forum: System76 Support
---

### Post by thomasaaron on 2010-03-19
The Lemur was introduced right about when Karmic was released. Our initial testing indicated it got about 4+ hours of battery life.

Right now, we're getting more like 3+ hours of battery life. We're not really sure why yet, but it could be that some updates have had an effect on power management. We're also trying to figure out if having 2GB vs. 4GB of RAM have an effect.

But for now, if you're looking to purchase a Lemur, our official estimate is 3 hours.

---

### Post by PatrickVogeli on 2010-03-20
thomas, have you considered shipping the Lemur with power management tweaks on?

In my machine, SU4100 powered, I have a script in /etc/pm/power.d/15_saving and a symlink to sleep.d with the following:

```

#!/bin/sh

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then

  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds.  By default this is 5 but, I prefer to reduce the disk
  # activity a bit.
  mount -o remount,commit=30,atime,diratime /
  mount -o remount,commit=30,atime,diratime /home

  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo max_performance > $foo;
  done

  # Manually set the wifi driver to no power savings.
  iwconfig wlan0 power off

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 600 > /proc/sys/vm/dirty_writeback_centisecs 

  echo N > /sys/module/snd_hda_intel/parameters/power_save_controller
else # Save power
 
  # Change the ext3 commit times to 10 minutes.  This reduces disk
  # activity
  mount -o remount,commit=600,noatime,nodiratime /
  mount -o remount,commit=600,noatime,nodiratime /home
  
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo min_power > $foo;
  done

  # Manually set the iwl3945 driver to power savings.
  iwconfig wlan0 power on

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
fi

```

Actually I have a few other things, like undervolting, disable wake on lan and some tweaks hardware related, but that's it. 

Maybe it's worth a try. It should be quite easy to setup a script that does install those files or remove them if they are present.

---

### Post by satsujinka on 2010-03-20
Power management tweaks would probably help. For example, you could set cpufreq to powersave (I get a little under 3 hours on my 6 cell battery, and about 6 hours on my 9 cell that way, btw the computer I have is just a regular old intel cpu [specifically a T5250.]) Though if you don't want to have the cpu clocked at its lowest setting (which is what powersave does) you could set it to ondemand, which should give you fairly decent battery life as well.

---

### Post by Paul Stone on 2010-03-23
I don't know if this will help:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1309882](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1309882)

> for dell studios try running metacity only and not compiz.

as my 9 cell with compiz gave 90 minutes and with metacity is giving me nearly 6 hrs, and the same is what i get in windows 7


--------------------


Alternatively, could it be related to this (alleged) Debian bug?

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=571161](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=571161)

> Package: devicekit-power
Version: 014-3
Severity: normal

Now that gnome-power-manager uses this, I have noticed a situation
where it falsely thinks my battery is about to run out, and suspends
the laptop.

I can reproduce this reliably, as follows. The attached log
of devkit-power --monitor-detail was taken while doing this:

1. Charge battery to full.
2. Run on battery until it's fairly low. 15% in the log.
3. Replug and let battery charge until it's nearly full. 72% in the log.
4. Unplug again.
5. Immediatly, the time to empty is a bogus value (1.1 minutes in log).
   (Possibly, this is because the energy-rate is a very bogus value of > 1000 W)
   The laptop is suspended.
6. Resume from sleep.
7. Now the time to empty is a reasonable value (2.8 hours),
   and I can leave the laptop off AC for hours without
   it suspending again.
8. But if at any point, I plug it in, even for a minute, and
   unplug, GOTO 5.
9. To get it out of this state, I have to charge the battery all
   the way up to full. After it's reached full I can unplug and plug
   without bogus suspends.


---

### Post by Paul Stone on 2010-03-23
A recent post discusses high power consumption on Kubuntu (with no resolution):

[http://alexandervanloon.nl/english/?p=395](http://alexandervanloon.nl/english/?p=395)

---

### Post by thomasaaron on 2010-03-29
Someone just tested the Lemur for us with Windows 7. With the power option on Power Saver, display brightness dimmed and 10% CPU usage, the battery can run about 3 hours.

And we're getting about that in Ubuntu.

---

### Post by PatrickVogeli on 2010-03-31
If windows 7 in powersave mode and a standard ubuntu both get 3 hours, may I suggest you to try the powersaving tips? Of course, if you want, you can ship a Lemur to Spain and I'll be glad to test it :D

Now, seriously, if a standard ubuntu install gets 3 hours, the powersaving tips should improve that. Every machine is different, but I'm quite confident using some powersaving tips would give you about 30 minutes extra. I believe it's worth a try.

---

### Post by urlwolf on 2010-04-10
There was a test somewhere that shows ubuntu as a poor battery performer:
[http://www.dvhardware.net/article38069.html](http://www.dvhardware.net/article38069.html)

Not having a lappy with ubuntu right now, I cannot say...

---

### Post by jml on 2010-04-10
Battery life with Ubuntu, or any Linux distro is a bit of an Achilles heel compared to either Windows or OS 10.  Windows has the advantage of market share so computer manufacturers have an interest in optimising battery life.  OS 10 simply represents the advantage of a company that closely controls both hardware and software.  I'd love to have my laptop get seven hours of battery life.

The one thing I find interesting is the observation that power management and therefore battery life seems to vary from distro to distro, and between different versions of the same distro.  Why did battery life fall by an hour with the move from Ubuntu 9.04 to 9.10 in the Lemur?  If anything, I would think that things should improve over time, not get worse.  Just my two cents.

Joe

---

### Post by satsujinka on 2010-04-12
I think you're confusing power management with standards compliance. Most computer manufacturers don't fully comply with acpi and other standards. As a result, O.S.s that are heavily compliant suffer. Since vendors provide drivers that know about this, there isn't a problem when you use their drivers. The problem with linux is that we don't get vendor support.

But I maintain that I never got anywhere near as good of battery life on my laptop in Windows as I currently get with Arch Linux. I recall only getting about 2 hours in Windows, as opposed to the 3+ hours I get currently. So I can assure you that linux power management isn't the problem. It's non-compliant hardware, poor implementation, and using buggy, resource intensive programs.

---

### Post by jml on 2010-04-12
Good points.  Thanks for your perspective.

Joe

---

### Post by eapache on 2010-04-30
Have there been any further developments on this front, perhaps the battery is better with lucid?

---

### Post by thomasaaron on 2010-04-30
Still about 3 hours on our test Lemur.

---

### Post by msrinath80 on 2010-04-30
Has the Lemur been tested with Lucid yet? Is the Webcam functional? Also what about suspend/hibernate and the function keys?? Do they work without issues? Sorry too many questions!

Thanks,
Srinath

Update: Out of the box, Webcam does not work. Cheese hangs. Neither do the brightness keys. All other keys are ok. Sound, video, wireless and eth0 are fine, as is suspend (which seems to work with Fn+F4). That's about all I could test with a Live USB startup disk of 10.04 AMD64.

Update2: Internal mic also works (actually without having to turn up the slider too much!). Also, for some reason, torcs gives better FPS in Lucid than in Karmic. Seems like the 4500MHD is better supported in Lucid.

---

### Post by thomasaaron on 2010-05-03
Install and run the System76 Driver for webcam support on the Lemur.

---

### Post by msrinath80 on 2010-05-03
Thanks Tom!

What about the brightness hotkeys. Do they work on your Lemur?

---

### Post by thomasaaron on 2010-05-03
Our Lemur is out of the office until tomorrow. I've made a note on [**_task_**]("http://thomasaaron.wordpress.com/2010/04/22/a-cool-task-management-cli-application/") to check it out then.

---

### Post by msrinath80 on 2010-05-03
Thanks Tom :)

---

### Post by thomasaaron on 2010-05-03
OK, the latest System76 Driver fixes the brightness hot keys and the webcam.

---

### Post by msrinath80 on 2010-05-03
That's great news Tom :) Thanks!

---

### Post by seanlano on 2011-02-15
I presume this is with the standard 31WH battery? What about with the 62WH battery? Logically it would be six hours, but is this confirmed? 

Also, is it possible to upgrade the default battery rather than buying an extra one?

---

### Post by isantop on 2011-02-15
We're seeing about two hours on the Standard (31 Wh) battery, and around four on the extended (62 Wh) battery.

---

