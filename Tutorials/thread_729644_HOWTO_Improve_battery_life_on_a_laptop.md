---
title: "HOWTO: Improve battery life on a laptop"
date: 2008-03-20
forum: Tutorials
---

### Post by sdennie on 2008-03-20
By default Gutsy/Hardy is reasonable on laptop battery life but, with very little work, it's not difficult to dramatically increase battery life.  Some of this information is from lesswatts.org or straight out of the powertop tool however, neither of them (that I've seen) give you a way to automate the switch between AC power and battery.

Essentially the idea is to create a script that plugs into the acpi system that should properly handle events like switching to/from battery as well as resuming from suspend.  It's possible to do some of these things via the laptop-mode tool but, I prefer this method because it gives a more fine grained control over what settings you use.

The basic script looks like this:

```

#!/bin/bash
if on_ac_power; then
# Reset back to normal settings
else
# Turn on aggressive power savings
fi

```

The commands that will populate the two sections of that script will differ from laptop to laptop but, the information that the powertop tool provides and the tips at [http://www.lesswatts.org/tips/](http://www.lesswatts.org/tips/) are good places to start.  Some of the things are fairly generic however and so a script closer to this is a reasonable starting point:

```

#!/bin/bash
if on_ac_power; then
# Reset back to normal settings
  echo 0 > /proc/sys/vm/laptop_mode
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
else
# Turn on aggressive power savings
  echo 5 > /proc/sys/vm/laptop_mode
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 10 > /proc/sys/vm/dirty_background_ratio
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
fi

```

The first set of settings should be similar to the default Ubuntu settings and are what will be used when on AC power.  The second set of settings should help to save power.  These settings should work on any modern laptop with a SATA disk but, in practice there are actually many more power saving features that you can use depending on your hardware (sound card, wifi, bluetooth, etc...).  The links above to lesswatts.org should get you going in the right direction as far as what more to add.

For users of nvidia laptop cards, you can also save some power by adding

```

    Option      "OnDemandVBlankInterrupts" "True"

```

to /etc/X11/xorg.conf.  You'll want to add that to the section in that file that contains 'Driver  "nvidia"'.  If you are using compiz (Desktop effects) you will either need to disable sync to vblank (not actually enabled by default) or add the following to the script above:

```

for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"

        if on_ac_power; then
            su $user -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 1"
        else
            su $user -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 0"
        fi
    fi
done

```

This will toggle compiz sync to vblank depending on whether or not you are on battery power.

(Note: The compiz/nvidia solution doesn't work on Hardy.  I'm working on a solution for it.)

Finally, you'll need to install the script.  You will want to name the script something like 99-save_power.sh and then to install it, you can use a command like this:

For Hardy:
```

$ sudo install 99-save_power.sh /etc/pm/power.d
$ sudo install 99-save_power.sh /etc/pm/sleep.d

```

For Gutsy:
```

$ sudo install 99-save_power.sh /etc/acpi/ac.d
$ sudo install 99-save_power.sh /etc/acpi/battery.d
$ sudo install 99-save_power.sh /etc/acpi/resume.d
$ sudo install 99-save_power.sh /etc/acpi/start.d

```


This should make the script run whenever you start the machine, resume it from suspend or plugin/unplug the power cable.

The script(s) as written above may not save you huge amounts of power but, the idea is more to provide a general harness for adding power saving options and reverting those options when on AC power.  Once you have the basic scripts in place, things like lesswatts.org or the powertop tool should be able to help guide you in further power savings.

For a machine specific example of how I use this script on a Dell XPS m1330, see: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

---

### Post by calraith on 2008-04-05
I've got a riddle for you -- a conundrum, if you will.  What do you do when "on_ac_power" returns true no matter whether the laptop is plugged in or not?  How does gnome-power-manager know whether the laptop is on battery or on AC?  In other words, is there some sort of something in /proc or /dev that gnome-power-manager reads to know whether to display a battery or a plug in the tray?  Is there something I could grep to determine whether my script should call either the fullBlast or the powerSave function, rather than calling on_ac_power, which is apparently lying?

---

### Post by sdennie on 2008-04-05
Actually, on_ac_power is just a script in /usr/bin that checks /proc/acpi/ac_adapter/state (or status).  You could look at that as a start or you could probably do something like:

```

grep discharging /proc/acpi/battery/BAT0/state

```

If neither of those things properly display ac/battery changes, it's possible that it's a BIOS problem and you may want to check if your laptop/motherboard has any BIOS updates.

---

### Post by ethanay on 2008-05-14
how would you install the above script for use by pm-utils in 8.04 hardy?

---

### Post by sdennie on 2008-05-14
Updated first post for pm-utils in Hardy.

---

### Post by ethanay on 2008-05-15
another question:  how do these settings relate to/interact with what exists in /usr/lib/pm-utils/power.d/laptop-tools ?  and also the ones in laptop-mode-tools if laptop-mode is enabled?  it is all very confusing to have so many different places where a single parameter can be set, or perhaps be in conflict or be overridden...

---

### Post by sdennie on 2008-05-15
Yes, it's quite confusing and worse in Hardy with the inclusion of /usr/lib/pm-utils.  However, one nice things is that all these ".d" directories should be looking at the numbers at the beginning of the filename and executing them in order so, "99-foo.sh" will get executed after "50-bar.sh".  I think if you name your personal settings "99-whatever.sh", you can essentially override any other setting that has come before it.

---

### Post by smsmith050 on 2008-05-16
I am using 8.04 x86-64 on a HP6715b with a Turion TL60. I know the processor supports C1E but I never see the processor in any state but C0. 
Does anyone else see the "power management:        yes"
in the processor info?
I would like to enable C1E in linux to improve battery life.



:/proc/acpi/processor/C000$ more info
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        no
throttling control:      yes
limit interface:         yes

:/proc/acpi/processor/C000$ more power
active state:            C0
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 8000 usec
states:
    C1:                  type[C1] promotion[--] demotion[--] latency[000] usage[00000000] duration[00000000000000000000]

thanks

---

### Post by sdennie on 2008-05-17
smsmith050, I've never used an AMD CPU before.  Have you used powertop to check the C and P states of the CPU?  I'm not sure if it works with AMD CPUs but, it's possible that /proc/acpi is simply wrong and that powertop can give you more accurate information.

---

### Post by smsmith050 on 2008-05-17
The Intel powertop app is not able to identify the AMD Turion. 

For C1E not working I suspect something is wrong with the BIOS. C1E does work with windows.... I have the latest BIOS

During C1E the hyper-transport link is stopped, the memory is in self-refresh, and the processor clocks are divided down. It saves a good amount of power.

S

     PowerTOP version 1.9       (C) 2007 Intel Corporation

                                      P-states (frequencies)
                                        2.00 Ghz     0.0%
                                        1.80 Ghz     0.0%
                                        1.60 Ghz     0.0%
                                         800 Mhz   100.0%
< Detailed C-state information is only available on Mobile CPUs (laptops) >

---

### Post by mizu12 on 2008-05-17
Hi,

I updated Hardy to the latest laptop-mode-tools ([http://samwel.tk/laptop_mode/]("http://samwel.tk/laptop_mode/")) and changed in */etc/default/acpi-support* ENABLE_LAPTOP_MODE to true.

The latest version is quite configurable with many-many options and powermanagement modules. It works well on my HP 6910p.

---

### Post by ethanay on 2008-05-17
> Interesting how-to. Some people say that Windows manage battery life better than Ubuntu. 

I believe this is currently true by default.  Windows offers more default options that are easier to access and understand via a GUI.  Linux power management may be more powerful in terms of all the parameters available to tweak, but the adjustments are more difficult to make and it is not always clear (to me) what they are intended to do.

---

### Post by ethanay on 2008-05-17
Does anyone know whether Hardy can take advantage of SATA cd hardware notification yet, as explained at [lesswatts.org]("http://www.lesswatts.org/tips/disks.php")??  Configuring as such will allow permanent disabling of hal drive polling, which causes frequent wakeups and extra power consumption.

If so, we should figure out how and add that to this (already very good) thread :)

If not, we should add the following options to the scripts for people

battery power, no plans to use cd/dvd drive:
```
hal-disable-polling --device /dev/scd0
``` 

ac power:
```
hal-disable-polling --enable --device /dev/scd0
```

(insert actual name of your drive as appropriate)

---

### Post by sdennie on 2008-05-18
I used to have the hal-disable-polling commands in my scripts but (at least on Gutsy), hal-disable-polling didn't always work right and sometimes you would have to tell it to disable polling to re-enable it.  I'll try it out on Hardy for a while and, if it's fixed, add that to the first post.

I'm also working on a gtk based program that detects all the stuff mentioned at lesswatts.org and generates a proper power savings script for you.  I will post the link when it's ready for use (it will likely be a while).

---

### Post by ethanay on 2008-05-19
that sounds like a very useful program that many laptop users would be happy to have :)  

Are there plans to include an autocheck to ensure that 1) settings are properly applied and recognized by the system and 2) are permanent across restarts, power off/on, and suspend/resume?  For some reason I see that as a potential problem area, but my concerns may be unjustified...

I'm not thinking about a daemon that is always running, more like a temporary "setup mode" daemon that the user agrees to run while executing the various commands above to ensure that all's well.  Then generates a report for the user afterward to show either all's well or detail instances where the settings are reset or lost or improperly applied, etc.

I think something like that would be useful for debugging not just the program but power management in Ubuntu.

But for the time being I am just very thankful that people are working hard on laptop power management issues :D

---

### Post by sdennie on 2008-05-19
What it currently does is read a bunch of "power saving modules" that can detect if a certain power saving feature is availabe on that machine.  Then it generates and installs a script exactly like in the first post.  I may not actually make a gui for it and instead just have it prompt on the command line like, "Enable wireless power savings [Y/n]".  It will depend on how lazy I get...

---

### Post by ethanay on 2008-05-19
my personal opinion from my experience as a "normal" (non-programming) computer user, text ui's can often be just as or even more user friendly than gui's.  depends on the language (jargon), information provided about choices and their effects (e.g., this setting does [x], select it if [y]), and how well the program detects and recommends choices. 3-d buttons are over-rated.

sounds great -- please post as soon as a beta is available for testing!

---

### Post by ethanay on 2008-05-22
theoretically, setting swappiness (/proc/sys/vm/swappiness) to a lower value (e.g., 10 from 60) while on battery should help increase the burstiness of hdd usage.

i haven't explored whether this is actually true.  i think it depends on what variable(s) swappiness is assessing in order to determine swap activity level.

---

### Post by sdennie on 2008-05-22
Possibly, ethanay but, my only laptop has 4G of RAM so it's hard to test that.  I did test default swappiness on a friends laptop with 1G of RAM and it was REALLY hard to get it to actually swap to disk (I opened almost every app on the system and it still wasn't using swap).  There are settings to improve battery usage but, if you are actually concerned about it, you won't use the machine in a way that makes swap relevant.  (You also won't use VM's, gmail in a firefox tab (yup, it's a battery drainer) or anything else that powertop complains about).

---

### Post by ethanay on 2008-05-23
yup, i'm experiencing the same and it does seem like small potatoes with no noticeable gain.  one more question:

doesn't pm-utils in hardy currently handle changes in power state from ac to battery, or shouldn't it?  

/etc/pm/power.d/
/usr/lib/pm-utils/power.d/

I can confirm that modifying /usr/lib/pm-utils/power.d/laptop-tools does make changes to my system configuration.

Does pm-utils still rely on /etc/acpi/ac.d and /battery.d in order to know when to implement changes in power state?

---

### Post by sdennie on 2008-05-23
In Hardy, /etc/acpi/ac.d and /etc/acpi/battery.d still seem to work just fine.  If you are willing to try it out, I would be *VERY* interested if you could do the following: [http://ubuntuforums.org/showpost.php?p=5016005&postcount=139](http://ubuntuforums.org/showpost.php?p=5016005&postcount=139)

There has been some confusion as to what is actually working with the inclusion of pm-utils in Hardy and, though I have tested this in a VM and on my own machine I'd love to have more feedback.

---

### Post by ethanay on 2008-05-23
I am in the middle of getting a dual-boot system set up for low-latency audio work.  If I can get a handle on that, I will then go back to optimizing my main boot setup for powersaving and will include your inquiry.

Tho I seem to remember some bugs...do these possibly relate:
[bug 89269]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/89269")
[bug 229693]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/229693")

regardless, I will do the test once I can regain focus and certainly report back

---

### Post by smsmith050 on 2008-05-25
I ran some idle power experiments on my 6715b laptop. 
Using the AMD 64b kernel uses the most power ~21W.
Using the i686 32b kernel and the ati fglrx driver uses the least power ~15.5W.
Using Vista Business 32b uses ~14W.

Probing the LDTSTOP# signal I do not see it asserted with the 64b kernel. With the 32b kernel LDTSTOP# is asserted 3% of the time. 
With the 32b kernel and fglrx driver LDTSTOP# is asserted 60% of the time. 

Additional power (~0.5W) maybe saved by sudo aticonfig --set-powerstate=1

I don't ever see the processor in C1. I expected C1 (HALT) to be entered on both cores before LDTSTOP# was asserted. 
cat /proc/acpi/processor/C001/power always shows C0. 
Is anyone else with an AMD Turion CPU seeing C1?

---

### Post by fishfillet on 2008-05-30
I am still a newbie on this.. I am using a Lenovo 3000 G400.

Wont the line "hdparm -B 128 -S 12 /dev/sda" trigger too many hard disk spin downs?

Its my first to use Ubuntu on a laptop, and honestly I am quite paranoid about this "BUG"

---

### Post by sdennie on 2008-05-30
> **fishfillet said:**
> I am still a newbie on this.. I am using a Lenovo 3000 G400.

Wont the line "hdparm -B 128 -S 12 /dev/sda" trigger too many hard disk spin downs?

Its my first to use Ubuntu on a laptop, and honestly I am quite paranoid about this "BUG"

It shouldn't cause any problems because that part only gets executed when on battery power.  Because you can only spend a limited amount of time per day on battery power, it's essentially impossible to noticeably shorten the life of the disk (unless you have something that amounts to an infinite amount of batteries).  

Even still, if you are worried about the -B 128, you are welcome to change it to 254 or 255.  The power savings of using -B 128 and -S 12 is probably negligible unless you increase the ext3 journal commit time to something much larger and probably the dirty_writeback_centisecs to something much higher.  As I've written it, without further tweaks, it's really to just put the disk into a mode where it's probably less vulnerable to bumps and drops (which is more likely when it's unplugged).

---

### Post by fishfillet on 2008-06-03
> **vor said:**
> It shouldn't cause any problems because that part only gets executed when on battery power.  Because you can only spend a limited amount of time per day on battery power, it's essentially impossible to noticeably shorten the life of the disk (unless you have something that amounts to an infinite amount of batteries).  

Even still, if you are worried about the -B 128, you are welcome to change it to 254 or 255.  The power savings of using -B 128 and -S 12 is probably negligible unless you increase the ext3 journal commit time to something much larger and probably the dirty_writeback_centisecs to something much higher.  As I've written it, without further tweaks, it's really to just put the disk into a mode where it's probably less vulnerable to bumps and drops (which is more likely when it's unplugged).

Thank you.  I guess its a choice between battery life and HD life. :)

At least now I am more confident to suggest your script to my friends.

Again, heaps of gratitude!

I am btw using reiserfs

---

### Post by fishfillet on 2008-06-03
How about laptop mode?  Won't there be any problems with load_cycle_count on that?

---

### Post by sdennie on 2008-06-03
I would research Load_Cycle_Count stuff if you are worried about it.  laptop_mode probably won't hurt the disk (and, in fact, is probably better than the Ubuntu default).

---

### Post by ethanay on 2008-06-08
> **vor said:**
> In Hardy, /etc/acpi/ac.d and /etc/acpi/battery.d still seem to work just fine.  If you are willing to try it out, I would be *VERY* interested if you could do the following: [http://ubuntuforums.org/showpost.php?p=5016005&postcount=139](http://ubuntuforums.org/showpost.php?p=5016005&postcount=139)

There has been some confusion as to what is actually working with the inclusion of pm-utils in Hardy and, though I have tested this in a VM and on my own machine I'd love to have more feedback.

Hi Vor,

have you gotten feedback with this yet from others?  If you need more and it will be helpful, I can try to do it.

ethanay

---

### Post by ethanay on 2008-06-10
> **vor said:**
> In Hardy, /etc/acpi/ac.d and /etc/acpi/battery.d still seem to work just fine.  If you are willing to try it out, I would be *VERY* interested if you could do the following: [http://ubuntuforums.org/showpost.php?p=5016005&postcount=139](http://ubuntuforums.org/showpost.php?p=5016005&postcount=139)

There has been some confusion as to what is actually working with the inclusion of pm-utils in Hardy and, though I have tested this in a VM and on my own machine I'd love to have more feedback.

after following your directions in the above link:
acpi: no
pm-utils result: yes, it-ran present in /tmp

(sorry it took so long...!)

---

### Post by sdennie on 2008-06-10
@ethany: Thanks.  That's what I figured.

Also, I've updated the first post a bit.  It looks like /etc/pm/sleep.d and /etc/pm/power.d can be used instead of /usr/lib/pm-utils.

---

### Post by fishfillet on 2008-06-14
On my Lenovo 3000 G400 where Hardy is installed... I don't have this line:   /sys/class/scsi_host/host0/link_power_management_policy

Can you please help me on how I can have it?

---

### Post by sdennie on 2008-06-15
> **fishfillet said:**
> On my Lenovo 3000 G400 where Hardy is installed... I don't have this line:   /sys/class/scsi_host/host0/link_power_management_policy

Can you please help me on how I can have it?

If you are using an older laptop that doesn't have a SATA disk, you probably won't have that option.  It's perfectly fine to not use that option in that case.

---

### Post by ubunutukid on 2008-08-03
Im running Kubuntu and gnome on my acer 3680. The battery back to say is seriously sad! 
The laptop turns off the moment I unplug the power supply and I get a weird error that the battery is broken and always shows 0% even while connected to the power supply and charging. 

This laptop came with Vista and the battery seemed to work perfectly fine... I really dont understand the problem here. 
Please advise on the right course of action.

---

### Post by ethanay on 2008-08-05
Ubuntukid:  welcome to Ubuntu forums.

the best way to get an answer to your question(s) is to
1) first search the forum for keywords relating to your problem, to see if anyone else has encountered/solved the problem
2) post to a *new* thread if you can't find any pre-existing threads relating exactly to your problem

otherwise, your questions will be less visible to those who are able to be helpful, and it also muddies up the thread with multiple topics and makes finding info from the forums more difficult in the future.

cheers,
ethanay

---

### Post by peppoj on 2008-08-13
I ******* love you man!! You got my poor laptop battery from 1h 20min to 3h 10min.

---

### Post by sdennie on 2008-08-13
> **peppoj said:**
> I ******* love you man!! You got my poor laptop battery from 1h 20min to 3h 10min.

I've used this on two laptops now and generally see a 50% increase in battery but, those numbers are very impressive.  I'm glad it worked for you.

---

### Post by philandstuff on 2008-08-16
Great tutorial. I have a problem to do with the ordering of execution of various scripts.

I have put the file in /etc/pm/power.d/99powersave.sh and I also have /usr/lib/pm-utils/power.d/laptop-tools but there seems to be a third thing interfering.

When I remove the power, /proc/sys/vm/laptop_mode changes to 2 (pm-utils) and then to 5 (99powersave.sh). However, about 5 seconds later it then changes back to 2. (This was reported by tail -f.) I have confirmed by adding "echo `date` >>/tmp/<logfile>" to each script that each script only runs once. Any advice for where to search next for whatever is fiddling with the settings?

Things like this make linux very frustrating :confused:

---

### Post by sdennie on 2008-08-16
> **philandstuff said:**
> Great tutorial. I have a problem to do with the ordering of execution of various scripts.

I have put the file in /etc/pm/power.d/99powersave.sh and I also have /usr/lib/pm-utils/power.d/laptop-tools but there seems to be a third thing interfering.

When I remove the power, /proc/sys/vm/laptop_mode changes to 2 (pm-utils) and then to 5 (99powersave.sh). However, about 5 seconds later it then changes back to 2. (This was reported by tail -f.) I have confirmed by adding "echo `date` >>/tmp/<logfile>" to each script that each script only runs once. Any advice for where to search next for whatever is fiddling with the settings?

Things like this make linux very frustrating :confused:

Have you enabled the laptop-mode utility via /etc/default/acpi-support ENABLE_LAPTOP_MODE?  That's the only other thing I can think of that would be involved when changing power state.

---

### Post by philandstuff on 2008-08-16
> **vor said:**
> Have you enabled the laptop-mode utility via /etc/default/acpi-support ENABLE_LAPTOP_MODE?  That's the only other thing I can think of that would be involved when changing power state.

Yes, that was it. Thank you very much!

---

### Post by jpittack on 2008-09-22
> I don't ever see the processor in C1. I expected C1 (HALT) to be entered on both cores before LDTSTOP# was asserted.
cat /proc/acpi/processor/C001/power always shows C0.
Is anyone else with an AMD Turion CPU seeing C1?

There are two issues that stop the c1 state (and thus the c1e state) from being entered.  The first is an issue with dynticks and lacpi.  I think it will be fixed soon.  The next you will need to fix yourself.  The issue is your dsdt processor section.  Mine is blank, and yours will probably be too.  This is found in the BIOS.  You must program in the states and how they transtion from one to the other.  I have already submitted a bug report on the issue.  No I don't know how to fix it, and can't find anything or anyone that can help me try and program it.

---

### Post by Kuroyume on 2008-09-30
I tried using this script, but i think my laptop doesn't know when it is unplugged... not only is the script not executed, but Ubuntu doesn't apply the "on battery" settings i set up on the power management config.Is there a way for me to find out if it knows it is unplugged?

I have a sony vaio vgn-c240fe... Core 2 Duo T5500, intel 3945 wireless, intel 945GM chipset, running a fresh, up to date install of 8.04.1.

---

### Post by ferossan on 2008-10-08
Very interesting.
I did apply the script but I'm not sure if it is working well.
Using PowerTop it still keeps me recommending two things:

> Suggestion: Disable 'hal' from polling your cdrom with:
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a window if you plug in a CD but disables SATA power saving from kicking in.

Suggestion: Enable SATA ALPM link power management via:
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
or press the S key.

Is it normal?

PowerTop keeps more or less this way (after following the suggestions):
---------------------------------------------------------
     PowerTOP version 1.9       (C) 2007 Intel Corporation

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 3.5%)         2.11 Ghz     1.7%
C1                0.0ms ( 0.0%)         2.10 Ghz     0.0%
C2                0.6ms ( 2.6%)         1.60 Ghz     0.0%
C3                4.7ms (94.0%)          800 Mhz    98.3%


Wakeups-from-idle per second : 244.2    interval: 10.0s
Power usage (ACPI estimate): 16.0W (0.9 hours) (long term: 17.5W,/0.9h)

Top causes for wakeups:
  33.0% ( 96.9)      <kernel IPI> : Rescheduling interrupts 
  27.2% ( 79.9)       <interrupt> : uhci_hcd:usb3, yenta, i915@pci:0000:00:02.0 
  19.6% ( 57.6)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   6.2% ( 18.2)       <interrupt> : extra timer interrupt 
   4.1% ( 12.0)       compiz.real : schedule_timeout (process_timeout) 
   3.6% ( 10.7)       <interrupt> : iwl3945 
---------------------------------------------------------

I'm using a Lenovo Thinkpad T61
Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
2Gb RAM
Ubuntu 8.04.1
GNOME 2.22.3 (Ubuntu 2008-07-09)
Linux 2.6.24-19-generic

Thanks a lot.

---

### Post by ndennen on 2008-10-22
Vor,

Your other thread about decreasing disk activity disables laptop-mode by making it non-executeable.  

How does this script work then and should we use it or the disk activity one?   Thanks!

-Nate

Toshiba Tecra M7, 2.0 Ghz Core Duo, 2 GB ram, 320 GB HD, Ubuntu 8.04

---

### Post by conjunctivitis on 2008-11-30
Is there a way to check if the script is functioning?  I have an Acer Extensa 4420 with AMD Athlon 64 x2 and can't get below 21 watts even with display on it's minimum brightness and wireless off after installing the scripts...

Thanks.

---

### Post by jastonas on 2008-12-16
my average consumption is 24-26 watts. Isnt that too much?

---

### Post by melat0nin on 2009-02-28
Is it possible to implement this script in Intrepid?  I have just got my hands on a netbook (Advent 4211/MSI Wind) and I'd like to improve its battery life as much as possible before investing in a bigger battery.

---

### Post by toyonut on 2009-02-28
How would you go about scripting the aticonfig utility to change power state automatically?
command line is
aticonfig --set-powerstate=1 for low power
aticonfig --set-powerstate=2 for normal power.

But I dont know how to impliment this in a script.

Thanks
Paul

---

### Post by betty320 on 2009-04-03
A new battery usually maintains a discharged condition with very low capacity. It is highly recommended to fully charge new battery packs before using. You can refer to the users' guide of your electronic device for charging instructions. 
A new battery pack needs to be circled (fully discharged and recharged) three to five times to reach its optimum performance. 
Rechargeable battery will undergo self-discharging when left unused for a long period of time. Thus, it should always be stored in a fully charged state and kept in a cool, dry and clean place. 
To maintain the optimum performance of a battery pack, it is highly recommended to circle (fully discharging and recharging) it at least once a month. 
It is normal if a new battery gets warm when being charged or used. However, please pay special attention if the battery pack becomes excessively hot. This may indicate there is a problem with the charging circuit of the electronic device. Please consult a qualified technician if necessary. 
New batteries are hard to be charged. Sometimes, your electronic device may indicate a fully charged condition about 10 to 15 minutes when the new battery pack is being charged for the first time. When this happens, remove the battery pack and let it cool down for about 10 to 15 minutes then repeat the charging procedure. Sometimes, a new battery will suddenly refuse to be charged. If this happens, a suggested solution is trying to remove the battery from the device and insert it again. 
 
detail info:
[http://www.diggingshop.com](http://www.diggingshop.com)

---

### Post by lincen on 2009-05-05
Generally the LI ion material is nucleus in the laptop battery inside, It with suited manage power supply electrocircuit make up of laptop battery. It’s encase in the laptop inside charge and use.  result in because high temperature condition work on long time. But the LI ion battery apply use condition temperature 25-30&#8451; confine. Therefore at laptop host computer temperature high attain 40&#8451; usually, so have existence blast or combustion latency safety problem and shorten use life the battery.
That has be dead against use front happen problem and LI ion battery trait., when charge battery must take out use, has insure up to snuff on room temperature charge , as well as can avert happen blast or combustion or life reduce problem. simultaneity can let it is accomplish normally charge and discharge process the battery , It’s activation state urge LI ion battery inside is longtime. Can prolong use life the battery.

That has be dead against use two species battery voltage parameter at laptop IT trade, the product have setup switch switchover voltage, insure apply two species different voltage laptop battery charge,  any more introduced commutator model the product DC output plug, can use different variety, let use charger electricize for laptop battery is safety and set one's heart at rest. And that can prolong use life the battery, best economize expenses which needless for the peoples.
A new product---laptop battery charger
AC input&#65306;100-240V  50/60HZ
DC input&#65306;12-24V
H switch output&#65306;16.8V 2.5A
L switch output&#65306;12.6V 2.5A
Charge time&#65306;3-5h
Size&#65306;107*62*31mm
Color&#65306;black
Linkman: lincen
Mobile:86-13751018213
skype:lincen18213
TEL:86-755-61573100
FAX:86-755-61573100
[http://www.myspace.cn/a18213](http://www.myspace.cn/a18213)

---

### Post by golem3 on 2009-05-06
Does this stuff work on 9.04 as well?

---

### Post by davbren on 2009-05-07
I would like to know this also. 

Ok, all this sounds all good a well. However, is it possible to make all of these changes in a nice graphical format. I know from personal experience that terminal and text editor aren't bad at all. But, I and I would imagine many others will want big ol' buttons to press.

Just a thought.

---

### Post by Fzang on 2009-05-11
Yes please. I'm sure there's a lot of GUI whores who wants to save some power as well (I'm one of them!) :p

---

### Post by zubin71 on 2009-05-20
> **sdennie said:**
> By default Gutsy/Hardy is reasonable on laptop battery life but, with very little work, it's not difficult to dramatically increase battery life.  Some of this information is from lesswatts.org or straight out of the powertop tool however, neither of them (that I've seen) give you a way to automate the switch between AC power and battery.

Essentially the idea is to create a script that plugs into the acpi system that should properly handle events like switching to/from battery as well as resuming from suspend.  It's possible to do some of these things via the laptop-mode tool but, I prefer this method because it gives a more fine grained control over what settings you use.

The basic script looks like this:

```

#!/bin/bash
if on_ac_power; then
# Reset back to normal settings
else
# Turn on aggressive power savings
fi

```

The commands that will populate the two sections of that script will differ from laptop to laptop but, the information that the powertop tool provides and the tips at [http://www.lesswatts.org/tips/](http://www.lesswatts.org/tips/) are good places to start.  Some of the things are fairly generic however and so a script closer to this is a reasonable starting point:

```

#!/bin/bash
if on_ac_power; then
# Reset back to normal settings
  echo 0 > /proc/sys/vm/laptop_mode
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
else
# Turn on aggressive power savings
  echo 5 > /proc/sys/vm/laptop_mode
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 10 > /proc/sys/vm/dirty_background_ratio
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
fi

```

The first set of settings should be similar to the default Ubuntu settings and are what will be used when on AC power.  The second set of settings should help to save power.  These settings should work on any modern laptop with a SATA disk but, in practice there are actually many more power saving features that you can use depending on your hardware (sound card, wifi, bluetooth, etc...).  The links above to lesswatts.org should get you going in the right direction as far as what more to add.

For users of nvidia laptop cards, you can also save some power by adding

```

    Option      "OnDemandVBlankInterrupts" "True"

```

to /etc/X11/xorg.conf.  You'll want to add that to the section in that file that contains 'Driver  "nvidia"'.  If you are using compiz (Desktop effects) you will either need to disable sync to vblank (not actually enabled by default) or add the following to the script above:

```

for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"

        if on_ac_power; then
            su $user -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 1"
        else
            su $user -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 0"
        fi
    fi
done

```

This will toggle compiz sync to vblank depending on whether or not you are on battery power.

(Note: The compiz/nvidia solution doesn't work on Hardy.  I'm working on a solution for it.)

Finally, you'll need to install the script.  You will want to name the script something like 99-save_power.sh and then to install it, you can use a command like this:

For Hardy:
```

$ sudo install 99-save_power.sh /etc/pm/power.d
$ sudo install 99-save_power.sh /etc/pm/sleep.d

```

For Gutsy:
```

$ sudo install 99-save_power.sh /etc/acpi/ac.d
$ sudo install 99-save_power.sh /etc/acpi/battery.d
$ sudo install 99-save_power.sh /etc/acpi/resume.d
$ sudo install 99-save_power.sh /etc/acpi/start.d

```


This should make the script run whenever you start the machine, resume it from suspend or plugin/unplug the power cable.

The script(s) as written above may not save you huge amounts of power but, the idea is more to provide a general harness for adding power saving options and reverting those options when on AC power.  Once you have the basic scripts in place, things like lesswatts.org or the powertop tool should be able to help guide you in further power savings.

For a machine specific example of how I use this script on a Dell XPS m1330, see: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

based on the above info and the information from the site [http://www.lesswatts.org](http://www.lesswatts.org), ive made a app using python which could help you change between performance and powersave mode.. details of what im doing are at [http://zubin71.wordpress.com/2009/05/20/battery-life-ubuntu-9-04/](http://zubin71.wordpress.com/2009/05/20/battery-life-ubuntu-9-04/) and the updates are available on the same site too. my projects hosted on sourceforge... more details @ my blog; 

`n im open to learning... ;-) all comments are welcome.. :-)

---

### Post by Ostien on 2009-06-29
I have a similar script running at startup via /etc/pm/power.d/ (/etc/acpi/start.d and resume.d do not execute when they are supposed to as bootup is handled by pm-utils [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/244839](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/244839)), changing power states work via /etc/acpi/ac.d and battery.d

I'm not sure about resume though.

I know these scripts execute but files such as /proc/sys/vm/dirty_writeback_centisecs are reset apparently after the script executes.

I'm running 9.04.

---

### Post by myacer on 2009-06-30
very very confusing,any simple ways?

---

### Post by Shikaku2 on 2009-07-02
[http://ubuntuforums.org/showthread.php?p=7548627#post7548627](http://ubuntuforums.org/showthread.php?p=7548627#post7548627)

I made a neat little script to disable Compiz when you are running off the battery for very high battery life.

Any suggestions or any questions are welcome!

---

### Post by Qwertman on 2009-07-29
This thread seems to be slowly dying but I thought I'd give a stab at getting some answers. Sdennie, how'd that program work out, did you ever finish it? I plan on trying out these scripts on my EeePC although I don't think they're suited for me as is since I've got an SSD. I will check out those websites to see what they say about the matter.

Has anyone confirmed these work on 9.04? Let me know if there ere any tweaks you had to make.

---

### Post by X1R1 on 2009-10-05
nice info but lots of work to do, Im on 9.04 and would also like to know if this works as well.

---

### Post by parrimin on 2009-11-08
Hi!
Im trying to install the script in karmic, but not getting on, can anybody explain how to run a script automatically every time a plug/unplug the battery charger or when login in karmic?
It should be great, because i can say since i have discovered powertop, my battery length has increased a while, but more interesting would be running the same commands when needed automatically...

---

### Post by ceramicm on 2009-11-08
[QUOTE=parrimin]can anybody explain how to run a script automatically every time a plug/unplug the battery charger or when login in karmic?[/QUOTE]

One way to run a script at login:
1. Go to System, Preferences, Startup Applications.

2. On the Startup Programs tab, click the "Add" button (on the right).

3. Type a name for the script, and then paste the location (something like /home/parrimin/Desktop/powersave-script.sh) in the "Command:" field.

4. Click the "Add" button to save, and then close the Startup Applications window.

The script should be run the next time you log in. (Make sure it is executable, of course.) As for running when the laptop is plugged/unplugged from power, I don't know, sorry.

---

### Post by diskotek on 2009-11-09
this can be also useful for eeepc netbook with 9.10 ubuntu (not a netbook remix)?

---

### Post by parrimin on 2009-11-17
> **ceramicm said:**
>  As for running when the laptop is plugged/unplugged from power, I don't know, sorry.

Thanks, It was so easy to run it on login... For more months i use ubuntu, more i dont know to make the easy things! :D

Sooo, now the last question, how to launch on plug/unplug power?

---

### Post by Rinzwind on 2009-11-28
Heya. Excellent topic this.

I got myself a new battery (the other one started to die and ended up on 25 minutes at full power :X and was looking for ways to start my new battery off with a look at getting more from it.

I started powertop and it came back with some suggestions.
laptop mode enabled
disable hal from something to cd-rom

But now I get a ...

A USB device is active 100.0% of the time:
USB device  3-2 : BCM2045B2 (Broadcom)


and the option to set "  U - Enable USB suspend"

After I did the this notice comes back again.
Sooooo I guess it does not work? 

Oh and how can I check all the settings and see if any of them is picked up? :D Just look at the battery indicator and see if it shows a better max time? Or...


Oh and I also found this topic and a reply by camel1cz:
[http://ubuntuforums.org/showthread.php?t=644978](http://ubuntuforums.org/showthread.php?t=644978)
> 
Hi, on my system I found several autosuspend files in the /sys directory tree (under usb)... they seem to have default value of 2 and powertop changes it to 1... so some simple scripting can do the trick:

Code:

#!/bin/bash

for i in `find /sys -name autosuspend -exec echo {} \;` ; do echo "1" > $i ; done

I'm not sure it it's all (cause powertop still offers to turn it on) but in seems to have positive impact anyhow...


Is this save to execute? :X 
IE. it is from 2008 so... basically old...

HA I am getting into it.

$locate autosuspend
/etc/laptop-mode/conf.d/usb-autosuspend.conf
/usr/share/laptop-mode-tools/modules/usb-autosuspend


$ cat /etc/laptop-mode/conf.d/usb-autosuspend.conf
```
# Configuration file for Laptop Mode Tools module usb-autosuspend.
#
# For more information, consult the laptop-mode.conf(8) manual page.
#


###############################################################################
# USB autosuspend settings
# ------------------------
#
# If you enable this setting, laptop mode tools will automatically enable the
# USB autosuspend feature for all devices.
#
###############################################################################

# Enable USB autosuspend feature?
CONTROL_USB_AUTOSUSPEND=0

```



NOW THE BIG QUESTON: what numbers are considered BAD/GOOD/EXCELLENT when using powertop.
I get this with FF + powertop running:
```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 9.3%)         2.51 Ghz     3.3%
polling           0.0ms ( 0.0%)         2.50 Ghz     0.1%
C1 mwait          0.0ms ( 0.0%)         2.00 Ghz     0.7%
C2 mwait          0.3ms ( 0.2%)         1.60 Ghz     0.2%
C4 mwait          2.3ms (90.5%)          800 Mhz    95.7%

Wakeups-from-idle per second : 407.9    interval: 10.0s
Power usage (ACPI estimate): 21.7W (1.9 hours)

Top causes for wakeups:
  26.9% (160.6)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  17.9% (106.9)           firefox : hrtimer_start_range_ns (hrtimer_wakeup) 
  17.8% (106.4)      <kernel IPI> : Rescheduling interrupts 
  14.8% ( 88.4)     <kernel core> : hrtimer_start_range_ns (tick_sched_timer) 
  12.2% ( 72.8)       <interrupt> : extra timer interrupt 
   2.0% ( 12.2)          smplayer : hrtimer_start_range_ns (hrtimer_wakeup) 

A USB device is active 100.0% of the time:
USB device  3-2 : BCM2045B2 (Broadcom)

```

---

### Post by cong06 on 2009-12-28
> **parrimin said:**
> Thanks, It was so easy to run it on login... For more months i use ubuntu, more i dont know to make the easy things! :D

Sooo, now the last question, how to launch on plug/unplug power?

I was also having problems with this in 9.10. I'm wondering if there's a bug in one of the files, or a depencency that isn't mentioned. 

I commended out all the lines in the file "/etc/acpi/power.sh" except for the "pm-powersave $*" line, and my script started working (in /etc/pm/power.d)

(thanks to [PatrickVogeli](http://ubuntuforums.org/showpost.php?p=8565482&postcount=32))

[http://ubuntuforums.org/showpost.php?p=8569808&postcount=33](http://ubuntuforums.org/showpost.php?p=8569808&postcount=33)

Edit: On a clean reinstall of 9.10, everything seems to be working.

---

### Post by X1R1 on 2010-03-14
What about AMD processors and ATI video cards? any advice on saving battery for that setup?

I want to improve battery life on my hp Pavilion dv4-2013la

regards

---

### Post by Sadoon on 2010-04-03
hi,
I have a thinkpad sl 400. im having a very bad experience with ubuntu regarding battery performance. Usually in windows 7 it supports close to 4.5 hours but in ubuntu it hardly goes more than 2 hours. Rite now im using the new 10.04.  I tried Many things its not working. if anyone have a suggestion please let me know.
regards 
sadoon mohiuddin

---

### Post by finite9 on 2010-04-21
Sadoon: Im experiencing the same thing.  Brand new intel only laptop (video/wifi/CPU) running 10.04 beta2.

Seems like there are a number of bugs in gnome-power-manager:

Battery time left can fluctuate wildly and sometmies show 16hrs left.

applet may say 4hrs left but 10 minutes later with some light browsing says 2.5 hrs left.

Battery is not charging to 100%, but stopping at 82% for some reason.

In WIndows7 (before I wiped the disc) it was saying 6.5 hrs.  Now in Ubuntu 10.04 im getting max 5 hrs according to gnome-power-manager applet but in reality about 2-2.5 hrs.

Ive implemented many Powertop suggestions in /etc/rc.local and disabled compiz completely, but it's not making much of a dent in my Powertop rating (wakeups from idle) nor my battery time.

---

### Post by finite9 on 2010-05-07
> **parrimin said:**
> 
Sooo, now the last question, how to launch on plug/unplug power?

You can make a script run when the power cable is plugged into or unplugged from your laptop by following the instructions in the first post of this thread: namely:

create a scripts called 99_powersave for example and then type in a terminal:

# script will run when power cable plugged in
sudo install 99_powersave /etc/pm/power.d

# script will run when power cable unplugged
sudo install 99_powersave /etc/pm/sleep.d

# script will run when computer booted, whether plugged in or not
sudo install 99_powersave /etc/pm/config.d

If you create the script with an if then else clause for on_ac_power and install the same script in all three folders then your power saving script will run perfectly no matter what state you boot the computer in or whether you are on battery or otherwise.

EDIT:

Err, yeah, so I was playing around with this and realised what a dumbass I was... Ignore what I just said:

Putting a script in /etc/pm/power.d seems to get run every time the power status of the system changes, and if you have an if/then/else cluse in your script it works more or less as it should.

I now _assume_ that scripts put in /etc/pm/sleep.d only get run when the computer goes into standby or comes out of standby?  Does anyone know?

I thought that putting the script in /etc/pm/config.d was like an initial place where scripts got run when pm was started, but im no longer sure if this is the case.  I can say for sure however that it doesn't currently work if this is the intention:  I start my laptop on battery and my script to do powersaving is in the config.d directory but it does not get run.  I have a little script to check all the settings that I change in my power save script and they are all on ac power setting even if I boot with just battery.  If I plug in the ac, then unplug it again, _then_ things start working as expected.

Apologies for the confusion.

---

### Post by areskz on 2010-05-10
Guys, could you please help me?
I've been trying to improve power saving with PowerTOP, and I enabled 'USB Suspend' during that.

I should have enabled this for all USB devices but mouse. So I don't need this feature for mouse (it turns off if it's idle for 1 or 2 seconds), how can I get my mouse to it's previous condition? :)

---

### Post by yatara on 2012-01-19
I have a blank...I've look quite a bit
From memory i use to _ _ _tool to select the power mode i wanted.
 
Alternatives: powerTop and pm-config.
 
If I remember correctly they where 5 modes possible from airplane to aggressive.
Fill in the blank _ _ _tool in console.
 
Would someone know the command I'm refering to.
 
Many thanks.

---

### Post by ilmkidunya on 2012-01-20
It may harm the system or run properly any one have idea about that

---

### Post by tumutanzi.com on 2012-05-19
I would like to keep the default setting. To use Ubuntu, it is to make life easy and lazy.

---

