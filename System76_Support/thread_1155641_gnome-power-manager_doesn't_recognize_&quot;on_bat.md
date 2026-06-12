---
title: "gnome-power-manager doesn't recognize &quot;on battery&quot;"
date: 2009-05-11
forum: System76 Support
---

### Post by justin.waters on 2009-05-11
I have a Pangolin (model panp5) running 64-bit Jaunty.  When I unplug the AC power supply, the gnome-power-manager still reports "The computer is running on AC Power", although it does recognize that the battery is discharging.  This has a number of side effects:

* The remaining life of the battery is not displayed; instead, it reports that "Battery discharge time is unknown"
* The screen does not automatically dim when unplugged, even though I have the "Reduce backlight brightness" selected for "On battery".  In fact, it looks like none of the "On battery" settings are being used.
* The graphs for "Discharge time profile" and "Discharge time accuracy profile" under Power History are always 0.

If I click the applet, and select the battery, the "Device Information" box displays the correct information, including discharge time.

I do not experience this issue in a fresh install of 32-bit Jaunty on my Toshiba A105 laptop.

Is anybody else having any issues like this?  I was able to find references to similar bugs on Ubuntu's launchpad, although none seemed to affect Jaunty.

EDIT: I also tried to reproduce the issue on my work laptop, a Compaq nx6325 with a fresh install of 64-bit Jaunty, but I was unable to.  It doesn't look like it's a 32- vs 64-bit issue.

---

### Post by thomasaaron on 2009-05-11
This definitely is not a known problem in Jaunty. Could be a hosed upgrade from Intrepid.

Please boot from a live CD and see if the problem occurs there.

---

### Post by justin.waters on 2009-05-11
I'll try when I get home from work today.

However, I just received the computer on Friday from System76, with Jaunty pre-installed.  I suppose it's possible that it was upgraded from Intrepid to Jaunty at the Factory, though, so I'll still give it a shot.

---

### Post by thomasaaron on 2009-05-11
They put a fresh Jaunty image on it at the factory. So that rules out a hosed upgrade.

Is there a suspend/resume cycle involved? Or does it do this after a fresh boot.

If there is a suspend/resume cycle involved, you may have found a bug. If not, we can try re-setting your cmos. That usually fixes such quirks. Send me an email, though, for instructions. support@system76...

---

### Post by justin.waters on 2009-05-11
I noticed that I wasn't getting a battery life estimate right out of the box, although I didn't investigate further until I noticed my severely reduced battery life (due to the screen not dimming).  I don't typically use Suspend (I turned off suspend when the screen is closed after the first time it happened), so I'm leaning more towards the CMOS issue.  I'll send you an e-mail.

---

### Post by Guille Damke on 2009-05-15
Hi,

I did a clean install of 9.04 amd64 a couple of weeks ago and I have exactly the same issue with the power-manager in a panp4n. I did 2 tests, I booted using a LiveCD to 9.04 and the problem was still there when pluging/unpluging the power cord. Then, I used a LiveCD for 8.10 and it could recognize when it was running on AC or battery power. 
Any ideas? Are more users experiencing this problem? 
I found a couple of users in the main forum with asking the same question, but nobody has answered yet.

---

### Post by thomasaaron on 2009-05-16
We've confirmed it on our shop PanP4n/5. It's definitely a gnome-power-manager bug.

---

### Post by Guille Damke on 2009-05-16
> **thomasaaron said:**
> We've confirmed it on our shop PanP4n/5. It's definitely a gnome-power-manager bug.

Thank you for confirming it. Have you s76 guys filled any bug report about this? Do you have any idea when we can expect a fix? Or is it possible to temporally go back to an older version of gnome-power-manager which used to work in 8.10 until this is fixed?

---

### Post by thomasaaron on 2009-05-16
We are looking into this. There are some similar bug reports, but none of them quite hit the mark, and some are quite old, dating back to Edgy (although people are chiming in again after upgrading to Jaunty).

I don't know that I'd try to revert to a previous version, as I think you would have to actually compile Intrepids gnome-power-manage. Not sure what you might run into doing that.

---

### Post by lnxguit on 2009-05-16
I noticed my brand-new Pangolin wasn't aware when it was running on battery. I guess I'm glad I'm not the only one, but it's small comfort.
So, do we just track this thread in hopes of a fix?

---

### Post by Scotty Bones on 2009-05-17
I have the same issue too, but my pan's power management seems to work the way it should when unplugged. This will most likely need to be solved on the package maintainers end.  I haven't checked to see if any bugs have been reported against the package yet, but hopefully an update will come soon that resolves the issue.

---

### Post by dda on 2009-05-19
Also have the same problem on Russian "DEPO 9510" laptop (seems to be Clevo M860TU). I found this bug: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/118492](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/118492) - should a clone be created?

---

### Post by thomasaaron on 2009-05-19
I don't think that's the same problem.

The Applet, in our case, does indicate whether or not the computer is on AC or battery. It's the rest of the detailed information that doesn't register correctly.

---

### Post by justin.waters on 2009-05-19
Thomas,

This is a regression from 8.10, correct?  Looking at the sources from Intrepid and Jaunty's GPM, it looks like the code isn't terribly different.  I'll happily help to hunt down and fix the problem.  I would have started looking by now, but playoff hockey and bike-friendly weather have made it difficult to do any serious work on it.

I'd appreciate any info that you could send to me from the guys working on it internally.

---

### Post by thomasaaron on 2009-05-19
I'm pretty sure it is a regression. I definitely heard nothing about it under Intrepid. I'll load a machine and double-check, though.

---

### Post by Guille Damke on 2009-05-19
I checked 8.10 64 using a live CD and the power-manager-applet seemed to work fine, obviously it could not estimate the discharge time because it was the first time discharging, but it did recognize the battery/ac-power status.

---

### Post by justin.waters on 2009-05-19
Okay, so it looks like gnome-power-manager isn't the problem.  I booted the Jaunty file system with an Intrepid kernel (2.6.27-11) and everything works fine.  I wouldn't recommend this as a fix, since it breaks a bunch of other things (such as the NVidia driver).  However, it looks like we can rule out GPM as the bad guy.

The biggest difference that I noticed is that it doesn't look like the 2.6.28 kernel recognizes the AC power supply; the directory /sys/class/power_supply/ADP0 does not exist in 2.6.28, but *does* in 2.6.27.  I'm going to do some more research, but if anybody has any insight into this, let me know!

EDIT:  Neat- check out dmesg for 2.6.28:

```
[    1.452775] ACPI Error (psargs-0358): [\_PR_.CPU0._PPC] Namespace lookup failure, AE_NOT_FOUND
[    1.452780] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.ADP0.ADJP] (Node ffff88013f81a580), AE_NOT_FOUND
[    1.452828] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.ADP0._PSR] (Node ffff88013f81a540), AE_NOT_FOUND
[    1.452856] ACPI Exception (ac-0135): AE_NOT_FOUND, Error reading AC Adapter state [20080926]
```

---

### Post by justin.waters on 2009-05-19
Okay, so I found this thread:

[http://ubuntuforums.org/showthread.php?t=968713](http://ubuntuforums.org/showthread.php?t=968713)

It looks like this problem has existed for a while, but only appears whenever the AC adapter driver is built into the kernel instead of as a module.

[LIST]
[*] In Ubuntu 8.10, ac was built as a module (CONFIG_ACPI_AC=m), so the power manager works.
[*] In Ubuntu 9.04, ac is built in to the kernel (CONFIG_ACPI_AC=y), and the power manager was broken.
[/LIST]

The Gentoo user probably had a kernel with that driver built in, hence he found the issue.  I'm going to rebuild the kernel with ac as a module just to verify that this is the case.

EDIT: Yup, setting CONFIG_ACPI_AC=m fixed it.  At least we know it's not a regression, but a bug that's been around for quite some time.

---

### Post by lnxguit on 2009-05-21
So what's needed is a custom kernel that has the AC adapter driver load as a module?

---

### Post by Guille Damke on 2009-05-21
Hi,

I am also interested on a solution for this problem. If building a custom kernel is a solution, can people of system76 try this on their shop machines, which also have this problem, and post a "how to"?

---

### Post by lnxguit on 2009-05-22
I downloaded the debian lenny amd64 live CD from [http://mirrors.usc.edu/pub/linux/distributions/debian-cd/current-live/amd64/iso-cd/](http://mirrors.usc.edu/pub/linux/distributions/debian-cd/current-live/amd64/iso-cd/)
The gnome-power-manager works properly with this distro.

---

### Post by lnxguit on 2009-05-22
removed repost

---

### Post by Guille Damke on 2009-05-26
Hi people,

Could someone  tell us how to fix this battery power issue? I do not know how to fix the kernel and load "CONFIG_ACPI_AC=m", and I am sure that more people around does not either. A sort of how_to/guide would be perfect.

Thanks.

---

### Post by thomasaaron on 2009-05-27
Removed Post.

Posted to wrong thread!

---

### Post by thomasaaron on 2009-05-27
We're looking into this. It is probably something that will need to be fixed by the Ubuntu developers and will come down as an update.

---

### Post by lnxguit on 2009-06-12
I notice the next version (Karmic Koala/9.10) of Ubuntu has a functioning Power Manager.

---

### Post by Derath on 2009-06-13
I also noticed one other thing, I did a fresh install (see dying hard-drive post) and installed kde as well, and while the screen and all dims when unpluged, both the gnome and kde's power management applet doesn't recognize that it's been unplugged.

Also I have configured both apps to only blank and lock the screen when the lid is closed and ac plugged in; unfortunately when I close the lid while the ac is still plugged it is being put into sleep mode.

While not a big issue, this is a problem for when I am at home (will close lid but still access files from other pcs/laptops through network.

If anyone knows of an answer to that one as well, I'm all ears!

Thanks!
Jordan

---

### Post by miniyak on 2009-06-14
I know this may confuse more then help but my panp5 seem to be recognizing power as on battery correctly. Even after resuming from suspend to disk, not sure bout plain suspend/stand-by though. However this was before my applet disappeared (another problem for a different thread)

Discharge time estimate in the power history never worked though

---

### Post by jii on 2009-06-15
I have this problem also on my brand new Gazelle (gazu1, arrived 6/11/09, Jaunty preinstalled). The battery is always designated as running on AC power, whether it's charging or discharging. It's never designated as "on battery." The AC powered actions are always in effect, so it powers off when the battery runs out, with no option to hibernate. The discharge time is always unknown.

If the problem is Jaunty having the AC adapter driver built into the kernel instead of as a module, then this bug should be affecting everyone with preinstalled Jaunty, right? So to add to Guille Damke's questions, is there a bug report filed, is there a how to guide underway for fixing manually, should we send a support email to try resetting CMOS first, etc?

---

### Post by shusai on 2009-06-17
> **justin.waters said:**
> EDIT: Yup, setting CONFIG_ACPI_AC=m fixed it.  At least we know it's not a regression, but a bug that's been around for quite some time.

How and where can I set CONFIG_ACPI_AC=m?

Thanks!

---

### Post by elboeufx on 2009-06-18
Hi--

I'm not sure if this is the place to post this. I've been having similar problems, though not exactly the same. Basically, my laptop (Sony Vaio TT) only automatically suspends (I'm on 9.04, using Gnome Power Manager 2.24) when it's plugged in. When I unplug it from AC, the computer seems to recognize it, the screen brightness dims to 50%, and the applet tells me I'm on battery power. However, it won't automatically suspend. The screen goes dark but the computer stays on, and within a few hours the battery is drained. I went into gconf-editor, and changed the settings on the "apps" pertaining to power management, but they don't seem to take effect. Specifically, under "actions" I set the "sleep_type_battery" to suspend, and also under "backlight" set "brightness_battery" to 70, but it still comes out at 50% when AC is disconnected. Is there something I'm missing?

Thanks,
Elboeufx

---

### Post by lnxguit on 2009-06-18
Cool - the latest kernel update solved the gnome-power-manager issue on my Pangolin!!!

---

### Post by shusai on 2009-06-19
> **lnxguit said:**
> Cool - the latest kernel update solved the gnome-power-manager issue on my Pangolin!!!

Same here on my Panasonic - everything OK now!

---

### Post by Lee_Machine on 2009-06-19
Which kernel? 

The newest stable release .30 or just backports to .28? 

As far as official kernels go I'm running .28-13, and the problem still persist. As does it in .29, and .30

---

### Post by jii on 2009-06-24
I just installed a kernel update via the update manager, restarted, and nothing has changed. Still broken on gazu1 (Gazelle Ultra, Jaunty preinstalled). 
Still awaiting a response from the [S]support team[/S] community. (lol, sorry). ):P

---

### Post by Dawei87 on 2009-07-30
just curious as to whether or not anyone found a how to for compiling the kernal with this? i dont know anything about that kinda stuff. if someone could atleast point me in the right direction that would be great

---

### Post by Scotty Bones on 2009-07-30
If you want to mess around with the kernel, here are some resources.

[Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158")  This is the place to ask about all things related to the kernel. It's a very active thread.
[KernelCheck Project]("http://kcheck.sourceforge.net/")  This is an application created by Master_Kernel to automate the kernel building process via GUI.


I haven't messed around too much with kernelcheck, but just a note: when it asks about compiling the nVidia driver into the kernel, just say no.

---

### Post by jtappin on 2009-07-30
I think this is the same problem as [http://ubuntuforums.org/showthread.php?t=1213976]("http://ubuntuforums.org/showthread.php?t=1213976"), but with different symptoms due to the Gnome & KDE power managers flagging off different things.

Has anyone tried the kernel backports from [http://ppa.launchpad.net/a7x/kbp/ubuntu](http://ppa.launchpad.net/a7x/kbp/ubuntu) on a pangolin?

---

### Post by jii on 2009-11-01
To bring closure to the thread, upgrade to 9.10 Karmic to fix the power manager problem.

---

### Post by jii on 2009-11-16
> **jii said:**
> To bring closure to the thread, upgrade to 9.10 Karmic to fix the power manager problem.

Well, scratch that. I still have problems, and if you're reading this, you probably do too. Sorry.

---

### Post by hamselv on 2010-04-12
Excat same problem on newly installed and updated 9.10 on Dell Studio 1737 w radeon 3650 video.

Icon shows AC even when charger is unplugged.
The command:

cat /proc/acpi/ac_adapter/ADP1/state 

Does show the the correct state, but somehow gnome power manager does not subscribe to that,

Here is a little more information which might be of use,
please let me now if I can supply more.
## on AC
[FONT=Courier New] peter@red:log> cat /proc/acpi/ac_adapter/ADP1/state 
state:                   on-line
## AC removed
peter@red:log> cat /proc/acpi/ac_adapter/ADP1/state 
state:                   off-line
peter@red:log> ps -eaf | egrep '(hal|acpi|dbus)'
root        19     2  0 17:47 ?        00:00:00 [kacpid]
root        20     2  0 17:47 ?        00:00:00 [kacpi_notify]
root        21     2  0 17:47 ?        00:00:00 [kacpi_hotplug]
102        856     1  0 17:47 ?        00:00:00 dbus-daemon --system --fork
107        868     1  0 17:47 ?        00:00:00 hald --daemon=yes
root       958   868  0 17:47 ?        00:00:00 hald-runner
root      1061     1  0 17:47 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1203   958  0 17:47 ?        00:00:00 /usr/lib/hal/hald-addon-rfkill-killswitch
root      1220   958  0 17:47 ?        00:00:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1234   958  0 17:47 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
107       1235   958  0 17:47 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      1237   958  0 17:47 ?        00:00:00 hald-addon-input: Listening on /dev/input/event11 /dev/input/event12 /dev/input/event3 /dev/input/event0 /dev/input/event6 /dev/input/event5 /dev/input/event1 /dev/input/event8 /dev/input/event7 /dev/input/event2
peter     1856  1811  0 17:47 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
peter     1859     1  0 17:47 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
peter     1860     1  0 17:47 ?        00:00:00 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
peter     4682  3818  0 18:12 pts/0    00:00:00 egrep (hal|acpi|dbus)
peter@red:log>

==========

Well I did some further testing, startet up on battery, and now the Icon will change
when I switch to AC - there is however a 20 second delay 

But what is really strange is that now I tried again booting up on AC, and first time it seems to work
(less than 2 seconds delay) I changed a few times back and forth.

After I wrote the above I tried again starting on AC and removing/adding AC and now it takes
around 25 seconds before it ripples through. - I am certain that it would not change at all before

But why should it take 25 seconds, when I run this

while true;do cat /proc/acpi/ac_adapter/ADP1/state ;sleep 1;done

the data is available immediately

=============
Third update

After 30 minuttes I tried again unplugging AC, and have now waited 10 minuttes for the icon to change to battery. uptime is 40 miuttes
so I was got going crazy after all

=============
After 2 hours and 21 minutes uptime and almost 2 hours on battery the icon is still showin the AC icon (with the plug but not the yellow dot)
[/FONT][FONT=Courier New] [/FONT]

---

### Post by jii on 2010-04-13
Hey, hamselv, this forum is for specific hardware, System76 laptops and computers only. Sorry.

---

