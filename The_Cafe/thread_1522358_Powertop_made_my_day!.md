---
title: "Powertop made my day!"
date: 2010-07-02
forum: The Cafe
---

### Post by NightwishFan on 2010-07-02
[QUOTE='From Wikipedia']PowerTOP is a software utility designed to measure, explain and minimise a computer's electrical power consumption. It was released by Intel in 2007 under the GPLv2 license. It works for Intel, AMD and ARM processors.

PowerTOP analyzes the programs, device drivers, and kernel options running on a computer based on the Linux and Solaris operating systems, and estimates the power consumption resulting from their use. This information may be used to pinpoint software that results in excessive power use. Many open source and free software programs, such as Mozilla Firefox [1][2], have been patched to reduce their power consumption since the release of PowerTOP. This is particularly useful for laptop computer users who wish to prolong battery life, and data center operators, for whom electrical and cooling costs are a major expenditure.[/QUOTE]

[To Install Powertop Click Here]("apt://powertop")

I decided to use powertop just now to see what was causing my laptop (should get around 4hrs) to get between 1h30 and 2h. When idle, it normally says I should get around 2h 55m, but it is never idle. :)

Well anyway, I ran the test, and I got a few interesting results:

[LIST]
[*]USB devices (such as webcam) were not set to auto-suspend.
[*]Audio device was on 100% of the time.
[*]Network device was not set to use less power.
[*]Disk was not set to use a lower power mode.
[/LIST]

Powertop told me to push various key shortcuts upon discovering these, and I did so. I was at full charge, so I did the inevitable and pulled the power cord. It said right away I had 4hrs remaining, which normally read 2h 55m. In about 5-10mins of use it told me 5hrs remaining.

I know that the estimate is dynamic and not exactly accurate, but I have never been told I had this much juice. I know that some folks may not get the same good results but this is always a good utility to keep around. I hope progress continues with it.

My only question is do these tweaks remain after reboot? Or will I need to apply them every time I want to use battery?

---

### Post by Concrete Pants on 2010-07-02
I had to try this out to see if I could bring back some of my battery life (seems to be running out faster and faster) I only managed to save about half hour though...

One of the options was to enable auto shutoff of non-input usb devices (something like that) and this made my mouse unresponsive until I gave it a wiggle. However, after a restart this did not happen anymore. Also when i ran powertop again, it gave me all the same choices. So it appears that yes, you do need to redo the steps on every restart. 

I'm guessing there would probably be a way to find these options and enable/disable them manually though?

---

### Post by NightwishFan on 2010-07-02
Seems so, it tells you how to do some. I will have to wait for an expert to get back to me. Thanks for the response I will keep you posted. For now it is not too bad to have to run it again.

---

### Post by Glenn nl on 2010-07-02
How do I undo the usb powersafe mode?

EDIT

Did a reboot... worked.

---

### Post by ubunterooster on 2010-07-02
Yet another reason to never reboot...I like my powertop settings

---

### Post by NightwishFan on 2010-07-02
I think in some cases it still has the tweaks enabled. Next time I log on ill report if I get good power savings on a fresh boot.

---

### Post by KdotJ on 2010-07-02
I'm going to have to try this out, my laptop battery life is bad. My netbook battery life however is an absolute joke :-( maybe powertop will show some light

---

### Post by NightwishFan on 2010-07-02
It was pretty dramatic here, even if I have to rerun it all the time.

---

### Post by steveneddy on 2010-07-03
[http://ubuntuforums.org/showthread.php?t=716293](http://ubuntuforums.org/showthread.php?t=716293)

---

### Post by NightwishFan on 2010-07-03
Thanks for the link, I am getting closer. The /etc/acpi/battery.d/ does not exist for me, but there are links to scripts in that same folder. The only thing I can think of is that I would have to add commands in one of these scripts (after making a backup). However, I would also have to reset them in the "counter script" (ie: one for battery and one for plugging back into ac). This seems equivalent to running power-top each time I am on battery though, so it is progress.

---

### Post by Yes on 2010-07-03
A lot of the suggestions PowerTOP makes are the commands listed [here](http://wiki.archlinux.org/index.php/Laptop#Suggestions_for_saving_power) and [here](http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption).  I've got a bash script that runs on bootup that checks whether I'm using battery or AC power, and runs the commands accordingly.  I use acpid to run the same script when I unplug or plug in the laptop after it's booted.

---

### Post by NightwishFan on 2010-07-03
That sounds like the solution I am playing with right now. Could you post the script? Is it any different than installing the full "laptop mode tools"? Thanks for the links.

---

### Post by steveneddy on 2010-07-03
> **Yes said:**
> A lot of the suggestions PowerTOP makes are the commands listed [here](http://wiki.archlinux.org/index.php/Laptop#Suggestions_for_saving_power) and [here](http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption).  I've got a bash script that runs on bootup that checks whether I'm using battery or AC power, and runs the commands accordingly.  I use acpid to run the same script when I unplug or plug in the laptop after it's booted.

I have used PowerTop before and I knew it could be done.

Let us know how that works - I may be interested in using PowerTop again.

---

### Post by KdotJ on 2010-07-03
Well I'm testing powertop out on my netbook, along with using xfce instead of gnome.My netbook has never actually gave me a time remaining, just a percentage. I'll see how it goes...

---

### Post by madjr on 2010-07-03
the papercut guys may find this useful and include this tweaks by default

check my sign

---

### Post by KdotJ on 2010-07-03
Well I've been on here for about an hour and a half and my battery says 30% remaining, whereas before my netbook would be dead by now haha.

So definitely works :-)

---

### Post by steveneddy on 2010-07-03
> **KdotJ said:**
> Well I've been on here for about an hour and a half and my battery says 30% remaining, whereas before my netbook would be dead by now haha.

So definitely works :-)

Post your config file.

---

### Post by Yes on 2010-07-03
Here's my /etc/acpi/handler.sh script, which is run by acpid when it detects a change in something (like switching from AC to battery power).  Please note, this isn't at all what any other handler.sh scripts I've seen look like, but those scripts didn't work with my laptop, so after much messing around this is what I came up with:

```
#!/bin/sh
# Default acpi script that takes an entry for all actions

# NOTE: This is a 2.6-centric script.  If you use 2.4.x, you'll have to
#       modify it to not use /sys

minspeed=`cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq`
maxspeed=`cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq`
setspeed="/sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed"

set $*

case "$1" in
    button/power)
        #echo "PowerButton pressed!">/dev/tty5
        case "$2" in
            PWRF)   logger "PowerButton pressed: $2" ;;
            *)      logger "ACPI action undefined: $2" ;;
        esac
        ;;
    button/sleep)
        case "$2" in
            SLPB)   echo -n mem >/sys/power/state ;;
            *)      logger "ACPI action undefined: $2" ;;
        esac
        ;;
    ac_adapter)
        case "$2" in
            AC)
                case "$4" in
                    00000000)
			;;
                    00000001)
			;;
                esac
                ;;
            *)  power_source=`acpi -a`
		ac_source='Adapter 0: on-line'
		if [ "$power_source" = "Adapter 0: on-line" ]
		then
			echo 100 > /proc/acpi/video/VGA/LCD/brightness
                        #cpufreq-set -g performance
			echo "performance" >/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
			/etc/rc.d/cpufreqd restart
			hal-disable-polling --enable-polling --device /dev/sr0
			echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
                        echo 0 > /sys/devices/system/cpu/sched_smt_power_savings
			echo 0 > /proc/sys/vm/laptop_mode
			echo 500 > /proc/sys/vm/dirty_writeback_centisecs
			echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
			echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy
			#echo -n $maxspeed >$setspeed
		else
			echo 23 > /proc/acpi/video/VGA/LCD/brightness
                        #cpufreq-set -g ondemand		
			echo "ondemand" >/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
			echo 50 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
			/etc/rc.d/cpufreqd restart
			hal-disable-polling --device /dev/sr0
			echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
                        echo 1 > /sys/devices/system/cpu/sched_smt_power_savings
			echo 5 > /proc/sys/vm/laptop_mode
			echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
			hciconfig hkci0 down
			echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
			echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
			#echo -n $minspeed >$setspeed
		fi
			
		logger "ACPI action undefined: $2" ;;
        esac
        ;;
    battery)
        case "$2" in
            BAT0)
                case "$4" in
                    00000000)   #echo "offline" >/dev/tty5
                    ;;
                    00000001)   #echo "online"  >/dev/tty5
                    ;;
                esac
                ;;
            CPU0)	
                ;;
            *)  logger "ACPI action undefined: $2" ;;
        esac
        ;;
    button/lid)
        #echo -n mem >/sys/power/state
	/usr/sbin/pm-suspend
        ;;
    *)
        logger "ACPI group/action undefined: $1 / $2"
        ;;
esac
```

You might have to change the values you put into the brightness file, check that file for the different brightness settings your screen has.  If my script doesn't work, you can try [this](http://wiki.archlinux.org/index.php/Cpufrequtils#Interaction_with_ACPI_events), which is the "proper" way of doing stuff when switching power source.

---

### Post by NightwishFan on 2010-07-03
Thanks for the replies all. So far I got my laptop lasting longer than Windows, so it IS possible. :)

---

### Post by Cason on 2010-07-03
> **NightwishFan said:**
> Thanks for the replies all. So far I got my laptop lasting longer than Windows, so it IS possible. :)

Yes, it most certainly is! I only got 4 hours of battery life yesterday on my netbook before my battery hit critical. But after reading this thread and testing PowerTOP out, I got more than 7 1/2 hours today, which is almost an hour more than I ever got with all the tweaking I did in Windows. And that's not just idling either; I was using the computer the whole time, browsing, listening to music, playing games, etc. :D

As for the irritation from rebooting, I solved that by simply creating a "shortcut" to run PowerTOP from my programs menu. That was enough for me. Besides, I don't necessarily always want to have my netbook in lower-power mode anyway. ;)

Anyway, thanks much for the hookup!

---

### Post by NightwishFan on 2010-07-03
Is there any effort in Ubuntu to integrate better power management. I found a few things on launchpad but it was not entirely clear on how I should post ideas or reports.

---

### Post by steveneddy on 2010-07-04
> **NightwishFan said:**
> Thanks for the replies all. So far I got my laptop lasting longer than Windows, so it IS possible. :)

How much longer than before?

How does your config file differ from Yes' config file?

Or did you use a stock config file?

Haven't done this yet - spent all day getting my mouse side scroll buttons working on my mouse.

---

### Post by NightwishFan on 2010-07-04
I haven't played with the config files much. Though Windows 7 on this model gets around 3-3 1/2 hours. I get 4-4 1/2 on Ubuntu. I may try on Debian later because it gets more battery life usually. (for me)

---

### Post by dragos240 on 2010-07-04
Wow. It went from 26m to 59m. Cool!

---

### Post by KdotJ on 2010-07-04
> **steveneddy said:**
> Post your config file.

which?

---

### Post by NightwishFan on 2010-07-04
> **dragos240 said:**
> Wow. It went from 26m to 59m. Cool!

Not much battery eh? That is a lot more though. :)

---

### Post by rottentree on 2010-07-05
Not entirely related but you could also try Jupiter (from fewt) if you are not afraid of mono. It was designed for eeepcs with a gnome environment in mind but it supposedly works with every laptop, desktop, or netbook  computer.

[http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html](http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html)
[]("http://www.webupd8.org/2010/06/jupiter-take-advantage-of-asus-super.html#disqus_thread")

---

### Post by dragos240 on 2010-07-05
> **NightwishFan said:**
> Not much battery eh? That is a lot more though. :)

It was at 30% :p

---

### Post by beavis5551 on 2010-07-05
for me the increase was pretty good.

Notebook before powertop: 2 1/2 - 3 hours (wireless enabled)
Notebook after powertop: 3 1/2 - 4 hours (wireless enabled)

Netbook before powertop: ~ 4 hours (wireless enabled)
Netbook after powertop: 7 hours (wireless enabled)

guess that rocks :)

---

### Post by NightwishFan on 2010-07-05
Sorry I have been neglecting this thread I have been too busy to study the power management scripts. If possible I will provide a detailed explanation of them.

---

