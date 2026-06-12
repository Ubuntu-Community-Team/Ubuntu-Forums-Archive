---
title: "Systemd discussion - during the W cycle"
date: 2015-05-08
forum: Ubuntu Development Version
---

### Post by slickymaster on 2015-05-08
Previous discussions during the V cycle are [here]("http://ubuntuforums.org/showthread.php?t=2249915")

---

### Post by dino99 on 2015-05-08
from the latest UOS (published on phoronix):

> Ubuntu developers are working on replacing ifupdown with systemd-networkd for Ubuntu Snappy, Ubuntu Cloud, and Ubuntu Server. The switch is happened to go ahead of Ubuntu 16.04 LTS. This change wouldn't affect the Ubuntu desktop or Touch versions.

Networkd is becoming great for handling networking on servers, particularly clouds, and coming out better than the current Ubuntu Server network support. However, as it hasn't reached feature parity on the desktop nor can work with NetworkManager, the change wouldn't happen there for now. 

---

### Post by Cavsfan on 2015-05-08
Good info dino99!

I went with Ubuntu with Unity this d cycle and I was using systemd every time I logged in but am now seeing what others were complaining about. 

Firefox was eating up a lot of cpu and it was very slow scrolling down. I mean it would hesitate as I tried to scroll down the page.
So, thankful to have upstart back. It's seems to be doing well. 

On Vivid I went with Mate which had no upstart.

---

### Post by zika on 2015-05-08
Well: [http://ubuntuforums.org/showthread.php?t=2249915&p=13281385#post13281385](http://ubuntuforums.org/showthread.php?t=2249915&p=13281385#post13281385) not all... ;)
There might be a slim differnce in speed but there is much bigger gain in some other fields.

---

### Post by fjgaude on 2015-05-08
In 15.10 the boot time difference between systemd and upstart for my system is 32 versus 6 seconds... a huge difference!

---

### Post by QIII on 2015-05-08
I'm not seeing crazy boot times like that on Fedora, so it might be an implementation issue in WW.

---

### Post by cariboo on 2015-05-08
Systemd boot has steadily gotten slower through the Vivid development cycle. Check the boot plot I created in October 2014, last week just before Vivid was released I was getting boot times in the 30 second range. Today it has gone back down to 11 seconds:

```
systemd-analyze
Startup finished in 2.412s (kernel) + 9.038s (userspace) = 11.450s
```

---

### Post by fjgaude on 2015-05-08
> **cariboo said:**
> Systemd boot has steadily gotten slower through the Vivid development cycle. Check the boot plot I created in October 2014, last week just before Vivid was released I was getting boot times in the 30 second range. Today it has gone back down to 11 seconds:

```
systemd-analyze
Startup finished in 2.412s (kernel) + 9.038s (userspace) = 11.450s
```

I'm downloading the new iso for 15.10 right now and will fresh install it and see what my boot times are.

---

### Post by ventrical on 2015-05-09
SystemD is now performing excellently on one of my older machines with single core Celeron D at high overclock. All verbose reporting during boot process  are no longer there.

 Although it reports it is taking longer to boot it actually appears faster.

```

ventrical@ventrical-System-Product-Name:~$ systemd -analyze
systemd: invalid option -- 'a'
ventrical@ventrical-System-Product-Name:~$ systemd-analyze
Startup finished in 2.064s (kernel) + 34.358s (userspace) = 36.423s
ventrical@ventrical-System-Product-Name:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.267 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 1034 requests (1034 known processed) with 0 events remaining.
ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.59 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.61 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.59 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.20 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +22.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +25.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:   +6.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +42.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +2.0°C)
                       (emerg = +110.0°C, hyst = +10.0°C)

ventrical@ventrical-System-Product-Name:~$ inxi -b
System:    Host: ventrical-System-Product-Name Kernel: 3.19.0-16-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5AD2-E-Deluxe v: Rev 1.xx
           Bios: American Megatrends v: 1005.002 date: 01/19/2006
CPU:       Single core Intel Celeron D (-UP-) speed: 5051 MHz (max)
Graphics:  Card: NVIDIA G98 [GeForce 8400 GS Rev. 2]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NV98 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Marvell 88E8053 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 160.0GB (4.5% used)
Info:      Processes: 159 Uptime: 4 min Memory: 376.2/2000.6MB
           Client: Shell (bash) inxi: 2.2.16 

```

and look how cool it is running :)

Regards..

---

### Post by fjgaude on 2015-05-09
Well, after a clean, fresh install, 15.10 systemd analyze gave 16 seconds to boot. It was the same after installing all my usual apps including VerticalBox and huge database files. So... I wait to see if it gets in the range of upstart at 6 seconds. At the last test of 15.04, the boot time was 32 seconds under systemd. <smile>

---

### Post by Cavsfan on 2015-05-09
```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.227s (kernel) + 17.966s (userspace) = 22.194s
```

That command ran fast but, I'd have to agree on the slowing down part. I think it did actually boot faster than that command says though.
Now that I've got upstart to compare it to that is.

---

### Post by pixelro on 2015-05-09
systemd-analyze
Startup finished in 5.193s (kernel) + 1min 11.014s (userspace) = 1min 16.208s

:-|

---

### Post by harry332 on 2015-05-10
Systemd works excellently on my setup. I have completely purged all upstart and related packages (like cgmanager and systemd-shim).

This is the result:

> 
harry@Sabertooth:~$ systemd-analyze
Startup finished in 1.112s (kernel) + 1.032s (userspace) = 2.144s


---

### Post by P-I H on 2015-05-10
These are my values after change of timeout in /lib/systemd/system/NetworkManager-wait-online.service to 2.

```
p-i@pi-GA-MA770-UD3-SSD:~$ inxi -b
System:    Host: pi-GA-MA770-UD3-SSD Kernel: 3.19.0-16-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: Gigabyte model: GA-MA770-UD3 v: x.x
           Bios: Award v: FKb date: 07/08/2010
CPU:       Quad core AMD Athlon II X4 620 (-MCP-) speed: 2999 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Turks XT [Radeon HD 6670/7670]
           Display Server: X.Org 1.17.1 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1680x1050@60.0hz
           GLX Renderer: Gallium 0.4 on AMD TURKS GLX Version: 3.0 Mesa 10.5.2
Network:   Card-1: Qualcomm Atheros AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express)
           driver: ath9k
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 760.2GB (1.8% used)
Info:      Processes: 214 Uptime: 8 min Memory: 1151.8/3948.7MB
           Client: Shell (bash) inxi: 2.2.16 
p-i@pi-GA-MA770-UD3-SSD:~$ systemd-analyze
Startup finished in 4.613s (kernel) + 7.579s (userspace) = 12.192s
p-i@pi-GA-MA770-UD3-SSD:~$ 

```

---

### Post by grahammechanical on 2015-05-10
Has anyone noticed the variation in userspace times in the results being posted here? It must be a reflection of differences between our systems. One factor could be the number of partitions. Other possible factors?

Regards.

---

### Post by sgage on 2015-05-10
> **grahammechanical said:**
> Has anyone noticed the variation in userspace times in the results being posted here? It must be a reflection of differences between our systems. One factor could be the number of partitions. Other possible factors?

Regards.

Some ideas:

Booting from SSD vs. old-timey spinning platter.

Speed of SATA connection, general HD parameters.

Processor/RAM speed.

Numbers/types of devices that may need to have drivers/etc. started up at boot.

I have a 2008-vintage 2 GHz Pentium dual-core, and a 250 GB hard disk, and relatively slow RAM for this day and age. My boot looks like this:

```
Startup finished in 6.057s (kernel) + 27.208s (userspace) = 33.266s
```

Usually it comes up in the 20's. It seems different every time. This is a fresh installation made yesterday, so maybe systemd is still trying to figure things out...

---

### Post by Cavsfan on 2015-05-10
System differences definitely account for the different startup times.

An SSD boots up in like 2 seconds on Windows 8 I've been told. I'd imagine the same for Ubuntu like harry332 reported.

My vintage 2009 system with a quad core is slow but not too slow.

```
cavsfan@cavsfan-MS-7529:~$ systemd-analyze
Startup finished in 4.271s (kernel) + 18.778s (userspace) = 23.050s
```

The slowest part which is not included in that is when it first comes up and finds the attached Phantom USB drive. That adds about 10-15 seconds before it even gets to the grub screen.
I see the bios screen for that long. If I turn it off I do not even see the bios screen. But that would not be included in systemd boot time of course.

---

### Post by fjgaude on 2015-05-10
I boot from an SSD, have another SSD and a HDD online... 

frank@flash:~$ sudo systemd-analyze
Startup finished in 960ms (kernel) + 25.061s (userspace) = 26.021s

Just updated the fresh install. It takes longer than the first day of the iso. In upstart it still takes only 6 seconds to boot. Notice how fast the kernel loads. Ah well!

---

### Post by Elfy on 2015-05-10
booting from an ssd I get similar times, I'm more annoyed with the shutdown issue I've got atm - "a stop job is running for session c2" takes 90seconds

---

### Post by fjgaude on 2015-05-10
Hmmm... I don't think I have any issues with shutdown, it's normal. But the next time I'll pay attention.

---

### Post by Elfy on 2015-05-10
> **fjgaude said:**
> Hmmm... I don't think I have any issues with shutdown, it's normal. But the next time I'll pay attention.

You'd notice 90 seconds I guess :)

---

### Post by P-I H on 2015-05-10
My system shuts down immediately, max 3 sec.

---

### Post by Elfy on 2015-05-10
> **Elfy said:**
> booting from an ssd I get similar times, I'm more annoyed with the shutdown issue I've got atm - "a stop job is running for session c2" takes 90seconds

something awry then - definitely only affecting wolfy - the old vampire returns to it's crypt when told to 

boot with upstart and restart or shutdown sends me to the login screen

---

### Post by rrnbtter on 2015-05-10
Greetings,
Systemctl poweroff will delay for "installing unattended updates". If there are no unattended updates it will go straight to "off". When the delay occurs, if you CTRL ALT DEL one time it should show the "installing unattended updates" at the bottom (last line) of the terminal. Yep! it is a good long delay depending on what it has in que.

PS 
if you CTRL ALT DEL seven times it should go through it.

---

### Post by Elfy on 2015-05-10
> **rrnbtter said:**
> Greetings,
Systemctl poweroff will delay for "installing unattended updates". If there are no unattended updates it will go straight to "off". When the delay occurs, if you CTRL ALT DEL one time it should show the "installing unattended updates" at the bottom (last line) of the terminal. Yep! it is a good long delay depending on what it has in que.

PS 
if you CTRL ALT DEL seven times it should go through it.

testing that then ...

---

### Post by Elfy on 2015-05-10
> **Elfy said:**
> testing that then ...

...

So - tried that.

It did say something about "installing unattended updates" even though there are none.

Totally ignored it - and it went back to counting down to 90 seconds :p

---

### Post by Elfy on 2015-05-11
So - this is stubbornly refusing to do anything but annoy me :lol:

---

### Post by rrnbtter on 2015-05-11
Greetings,
> **Elfy said:**
> ...
So - tried that.
It did say something about "installing unattended updates" even though there are none.
Totally ignored it - and it went back to counting down to 90 seconds :p

I take a cautionary issue with your "even though there are none." statement. The poweroff process lists the shutdown processes but doesn't show the script that is being run and its results, hence the blind wait state. In my opinion (which is where the word cautionary derives) if the poweroff is stopping at the unattended updates process then "it is" doing something. I think this because if there is nothing at all to do, it will rush directly to shutdown. I also believe this process is run at shutdown to reduce or eliminate the prospect of a no boot situation due to the incomplete installation of an update. If the update is run from the old fashioned "wait til reboot method" the system may not be able to reboot due to the failed process. So it makes sense to me to handle that (finishing updates) at shutdown so as to ready the system for reboot.  As much as I have come to enjoy reinstalling my OS I think I can live with out that prospect if I only need to be patient every so often for a short process to run at shutdown. There is a much preoccupation with startup and shutdown speed with regard to systemd vs upstart in this section when in my opinion the whole feel of the OS is much more robust and enjoyable in between those two points (startup and shutdown) then it was from Karmic to Utopic. This systemd business was accepted by Canonical to further their server aspirations and desktop is just reaping the benefits IMHO.  I'm sure others may disagree and I can accept that.

---

### Post by Elfy on 2015-05-11
> startup and shutdown speed with regard to systemd vs upstart in this section when in my opinion the whole feel of the OS is much more robust and enjoyable in between those two points (startup and shutdown)

Personally I rarely care how fast the machine boots - I'm usually in the kitchen waiting for the kettle.

The reason's the shutdown is annoying me - a)it doesn't do so in the vivid install, so something must have changed in the meantime b) I'm more often rebooting checking things out :)

Ftr - there's no reference to unattended upgrades now btw, still 90 second wait - could be waiting for user session or sound card state - not sure.

Once the release schedule is up and Canonical bods are properlly Wilying - I'll catch one or two people I know and try and get to the bottom of it.

---

### Post by ventrical on 2015-05-11
> **Elfy said:**
> Personally I rarely care how fast the machine boots - I'm usually in the kitchen waiting for the kettle.

The reason's the shutdown is annoying me - a)it doesn't do so in the vivid install, so something must have changed in the meantime b) I'm more often rebooting checking things out :)

Ftr - there's no reference to unattended upgrades now btw, still 90 second wait - could be waiting for user session or sound card state - not sure.

Once the release schedule is up and Canonical bods are properlly Wilying - I'll catch one or two people I know and try and get to the bottom of it.

I had some of these problems on a few of my machines with VV but not with xubuntu. Those were solved and at last reboot/shutdown with xubuntu 15.10 I did not have a problem with systemd. Just updated and will try again.

Regards..

edit:

2 and 1/2 second shutdown :)

```

ventrical@ventrical-P5QL-PRO:~$ inxi -b
System:    Host: ventrical-P5QL-PRO Kernel: 3.19.0-16-generic x86_64 (64 bit)
           Desktop: Xfce 4.12.0 Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 4005 MHz (max)
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NVA8 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 120.0GB (9.3% used)
Info:      Processes: 176 Uptime: 0 min Memory: 381.4/2000.4MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-P5QL-PRO:~$ systemd-analyze
Startup finished in 1.696s (kernel) + 9.435s (userspace) = 11.131s
ventrical@ventrical-P5QL-PRO:~$ 


```

---

### Post by rrnbtter on 2015-05-11
Greetings,
> **Elfy said:**
> 
Once the release schedule is up and Canonical bods are properlly Wilying - I'll catch one or two people I know and try and get to the bottom of it.

Thanks, I could stand some first hand information on this myself. Your efforts are appreciated. I just want to emphasize that we already have a really great OS to use with more to come around the corner. I'm not going to beat it up over a shutdown script regardless the intentions. I find these to be exciting times. Can't wait for my snappy apps!

---

### Post by rrnbtter on 2015-05-11
Greetings,
@Elfy
Just for the fun of it .....
sudo leafpad /usr/lib/systemd/user/systemd-exit.service

Add the following after the last line.
WorkingDirectory=/

Interested in your results regarding the shutdown delay.

---

### Post by Elfy on 2015-05-11
> **rrnbtter said:**
> Greetings,
@Elfy
Just for the fun of it .....
sudo leafpad /usr/lib/systemd/user/systemd-exit.service

Add the following after the last line.
WorkingDirectory=/

Interested in your results regarding the shutdown delay.

Stop job for user session c2 of user hob (1s of 1 minute 30s)
bunch of Ctrl+Alt+Dels leads to 

Failed to start StoreSouncCard State

Then I wondered about nvidia not being installed yet - so I did, reboot just hung ... 

I'll catch up with someone in irc in the next few days probably

---

### Post by ventrical on 2015-05-11
Here is what I have with systemd-exit.service

```

#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.

[Unit]
Description=Exit the Session
Documentation=man:systemd.special(7)
DefaultDependencies=no
Requires=shutdown.target
After=shutdown.target

[Service]
Type=oneshot
ExecStart=/bin/kill -s 58 $MANAGERPID

```

Regards..

---

### Post by grahammechanical on 2015-05-11
As I booted just now after coming home from shopping it occurred to me that the startup times we have been recording could be inaccurate from a certain point of view. In another thread on this topic someone said that systemd is still doing its stuff even by the time we have reached the desktop.

Tonight I noticed that sound was muted (red mute icon) at the login screen. Then after logging in to the desktop sound was un-muted. Normally I see boot time defined as the time from Grub to the login screen or the desktop if automatic login is set.

I think systemd-analyze as measuring the full time that systemd does its stuff.

Regards

---

### Post by fjgaude on 2015-05-11
Yes, yes, but from the Grub menu to desktop it is easy time the seconds, and what I've been reporting is pretty much the way it is.

---

### Post by grahammechanical on 2015-05-11
Oh, I do not disagree. As I pointed out in an earlier post kernel times are similar on our different machines. SSD, are in a league of their own. It is the userspace times that vary and they will include the time systemd takes to start services after we have reached the login screen. So, from that point of view the systemd-analyze results although an accurate measure in themselves are not what we normally consider as a boot time.

---

### Post by rrnbtter on 2015-05-12
Greetings,
This is what my systemd-exit.service looks like. I have not had a delayed shutdown since I added the last line. I am using systemctl poweroff from a script to power off just to save a few key strokes. 
po(~/bin) 
#!/bin/bash
systemctl poweroff

The information I am getting is that there is various fixes and each does not work in every case for some reason.

#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.

[Unit]
Description=Exit the Session
Documentation=man:systemd.special(7)
DefaultDependencies=no
Requires=shutdown.target
After=shutdown.target

[Service]
Type=oneshot
ExecStart=/bin/kill -s 58 $MANAGERPID
WorkingDirectory=/

---

### Post by dino99 on 2015-05-12
That report wish for modification (related to previous posts)  [lpbug]1451797[/lpbug]

---

### Post by rrnbtter on 2015-05-12
Greetings,
@dino99, Thanks! that fixed it! The normal shutdown even works. Evidently unattended-upgrades can't find a network.

Solution
sudo leafpad /lib/systemd/system/rc-local.service

comment out "After=network.target"
add these two lines
Wants=network-online.target
After=network-online.target

Should look like my file below.

#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.

# This unit gets pulled automatically into multi-user.target by
# systemd-rc-local-generator if /etc/rc.local is executable.
[Unit]
Description=/etc/rc.local Compatibility
ConditionFileIsExecutable=/etc/rc.local
# After=network.target
Wants=network-online.target
After=network-online.target

[Service]
Type=forking
ExecStart=/etc/rc.local start
TimeoutSec=0
RemainAfterExit=yes

---

### Post by dino99 on 2015-05-12
> **rrnbtter said:**
> Greetings,
@dino99, Thanks! that fixed it! The normal shutdown even works. 

Great :p got a better karma then :lolflag:

---

### Post by rrnbtter on 2015-05-12
Greetings,
> **dino99 said:**
> Great :p got a better karma then :lolflag:

Definitely! It is also a good example of the flexibility of Systemd. There is a lot to learn here but I'm on-board.

---

### Post by Elfy on 2015-05-13
> **Elfy said:**
> Stop job for user session c2 of user hob (1s of 1 minute 30s)
bunch of Ctrl+Alt+Dels leads to 

Failed to start StoreSouncCard State

Then I wondered about nvidia not being installed yet - so I did, reboot just hung ... 

I'll catch up with someone in irc in the next few days probably

Fixed it.

MUCH too early in cycle to be worrying about things - clean install did the job ;)

Edit - back again with a 90s shutdown - better placed to see why now ...

Edit edit - and I have found what was playing up ... [Serviio]("http://serviio.org/") - grab java8 - set that up with it's 2 files starting with desktop - back to 90s shutdown.

Edit edit edit - run the 2scripts from a terminal - reboots properly, put them in session startup - 90s wait.

---

### Post by Cavsfan on 2015-05-14
Did the recent update to systemd fix the 90 second delay problem? I believe it did for me.

> systemd (219-9ubuntu1) wily; urgency=medium

  * Merge with Debian experimental branch. Remaining Ubuntu changes:
    - Hack to support system-image read-only /etc, and modify files in
      /etc/writable/ instead.
    - Keep our much simpler udev maintainer scripts (all platforms must
      support udev, no debconf).
    - initramfs init-top: Drop $ROOTDELAY, we do that in a more sensible way
      with wait-for-root. Will get applicable to Debian once Debian gets
      wait-for-root in initramfs-tools.
    - initramfs init-bottom: If LVM is installed, settle udev,
      otherwise we get missing LV symlinks. Workaround for LP #1185394.
    - Add debian/udev.lvm2.init: Dummy SysV init script to satisfy insserv
      dependencies to "lvm2" which is handled with udev rules in Ubuntu.
    - Add debian/udev.lvm2.service to avoid running the dummy lvm2 init
      script.
    - Provide shutdown fallback for upstart. (LP: #1370329)
    - debian/extra/ifup@.service: Additionally run for "auto" class. We don't
      really support "allow-hotplug" in Ubuntu at the moment, so we need to
      deal with "auto" devices appearing after "/etc/init.d/networking start"
      already ran. (LP: #1374521) Also, check if devices are actually defined
      in /etc/network/interfaces as we don't use Debian's net.agent.
      Also run ifup in the background during boot, to avoid blocking
      network.target. (LP: #1425376)
    - ifup@.service: Drop dependency on networking.service (i. e.
      /etc/init.d/networking), and merely ensure that /run/network exists.
      This avoids unnecessary dependencies/waiting during boot and dependency
      cycles if hooks wait for other interfaces to come up (like ifenslave
      with bonding interfaces). (LP: #1414544)
    - Add Get-RTC-is-in-local-time-setting-from-etc-default-rc.patch: In
      Ubuntu we currently keep the setting whether the RTC is in local or UTC
      time in /etc/default/rcS "UTC=yes|no", instead of /etc/adjtime.
      (LP: #1377258)
    - Put session scopes into all cgroup controllers. This makes unprivileged
      user LXC containers work under systemd. (LP: #1346734)
    - systemctl: Don't forward telinit u to upstart. This works around
      upstart's Restart() always reexec'ing /sbin/init on Restart(), even if
      that changes to point to systemd during the upgrade. This avoids running
      systemd during a dist-upgrade. (LP: #1430479)
    - Drop hwdb-update dependency from udev-trigger.service, which got
      introduced in v219-stable. This causes udev and plymouth to start too
      late and isn't really needed in Ubuntu yet as we don't support stateless
      systems yet and handle hwdb.bin updates through dpkg triggers. This can
      be dropped again with initramfs-tools 0.117.
    - Lower Breaks: to plymouth version which has the udev inotify fix in
      Ubuntu.
    - Lower libappamor dep to the Ubuntu version where it moved to /lib.
    - Lower apparmor Breaks: to the Ubuntu version that dropped $remote_fs.
    - Change systemd-sysv's conflicts to upstart-sysv. (LP: #1422681)
    - Make failure of boot-and-services NSpawn.test_boot non-fatal for now.
      This currently fails when being triggered by Jenkins, but is totally
      unreproducible when running this manually on the exact same machine.

    Upgrade fixes, keep until 16.04 LTS release:
    - systemd Conflicts/Replaces/Provides systemd-services.
    - Remove obsolete systemd-logind upstart job.
    - Clean up obsolete /etc/udev/rules.d/README.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Wed, 13 May 2015 14:14:35 +0200


---

### Post by fjgaude on 2015-05-14
Well, I got my desktop in about 7 seconds, instead of 26, but it took about 20 more seconds to get a mouse, for a total of 28. I have no issues with shut downs!

---

### Post by Elfy on 2015-05-14
> **Cavsfan said:**
> Did the recent update to systemd fix the 90 second delay problem? I believe it did for me.

No - but I didn't expect it to. 

Once I've got some semblance of order,now I know what's causing it, I ,might start a seperate thread.

---

### Post by cariboo on 2015-05-14
I did a fresh UEFI install yesterday, just because I could. :) I really did it to see if boot times are any different using systemd. There was so little difference, I might convert my just convert my Trusty->Utopic->Vivid->Wily install to UEFI and continue using it.

---

### Post by rrnbtter on 2015-05-15
Greetings,
For those that still need a solution for the shutdown delay I have been able to eliminate it on my system and this has held up for the last several days. If you want to give it a try here it is. 

Add this "TimeoutStopSec = 5" at the end of the [Service] section of the following. Remove the quotes of course!

EDIT:
[SIZE=3][COLOR=#000000][FONT=Calibri]leafpad /lib/systemd/system/systemd-shutdownd.service[/FONT][/COLOR][/SIZE]
[SIZE=3][COLOR=#000000][FONT=Calibri]leafpad /lib/systemd/system/unattended-upgrades.service
[/FONT][/COLOR][/SIZE]
If you have the teamviewer delay bug add the same line to the end of the [service] section of the following.
leafpad /etc/systemd/system/teamviewerd.service

I can't remember if I had to reboot for it to take effect.

PS you guys can add any kind of sudo at the beginning of those command lines that suits your fancy. Have at it! The default is good enough for me.

---

### Post by Cavsfan on 2015-05-15
> **rrnbtter said:**
> Greetings,
For those that still need a solution for the shutdown delay I have been able to eliminate it on my system and this has held up for the last several days. If you want to give it a try here it is. 

Add this "TimeoutStopSec = 5" at the end of the [Service] section of the following. Remove the quotes of course!

sudo leafpad /lib/systemd/system/unattended-upgrade-shutdown.service
sudo leafpad /lib/systemd/system/systemd-shutdownd.service

If you have the teamviewer delay bug add the same line to the end of the [service] section of the following.
sudo leafpad /etc/systemd/system/teamviewerd.service

I can't remember if I had to reboot for it to take effect.

Don't intend to denigrate your most excellent solution, which I plan to implement but shouldn't that be gksu or gksudo instead of sudo since leafpad is a GUI app?

EDIT: Also I have a file called /lib/systemd/system/unattended-upgrades.service but not /lib/systemd/system/unattended-upgrade-shutdown.service

---

### Post by zika on 2015-05-15
> **rrnbtter said:**
> Greetings,
For those that still need a solution for the shutdown delay I have been able to eliminate it on my system and this has held up for the last several days. If you want to give it a try here it is. 
Add this "TimeoutStopSec = 5" at the end of the [Service] section of the following. Remove the quotes of course!
```
[COLOR=#add8e6]sudoedit[/COLOR] /lib/systemd/system/unattended-upgrade-shutdown.service
[COLOR=#add8e6]sudoedit[/COLOR] /lib/systemd/system/systemd-shutdownd.service

```If you have the teamviewer delay bug add the same line to the end of the [service] section of the following.
```
[COLOR=#add8e6]sudoedit [/COLOR]/etc/systemd/system/teamviewerd.service
```
I can't remember if I had to reboot for it to take effect.Is it not easier to disable/mask unattended-upgrades.service?
> **Cavsfan said:**
> Don't intend to denigrate your most excellent solution, which I plan to implement but shouldn't that be gksu or gksudo instead of sudo since leafpad is a GUI app?Even though it seems that I gave up giving warnings about that (gk)sudo error the truth is that I grew stronger in preventing myself from doing that. I've edited code up/above and I thank You for keeping that fire alive.

---

### Post by Cavsfan on 2015-05-15
> **zika said:**
> Is it not easier to disable/mask unattended-upgrades.service?

I do not have an existing /lib/systemd/system/unattended-upgrade-shutdown.service file.
I edited /lib/systemd/system/unattended-upgrades.service since I don't have the other one. It seemed appropriate... 

But, if disabling/masking it is better I could do that.

> **zika said:**
> I thank You for keeping that fire alive. 

You are welcome! :)

---

### Post by zika on 2015-05-15
> **Cavsfan said:**
> I do not have an existing /lib/systemd/system/unattended-upgrade-shutdown.service file.
I edited /lib/systemd/system/unattended-upgrades.service since I don't have the other one. It seemed appropriate... You've picked the right file, there was an error in proposed solution. I did not want to correct that in my quote... ;)
> **Cavsfan said:**
> But, if disabling/masking it is better I could do that.Better is an elusive property when metric is not well defined... ;)
> **Cavsfan said:**
> You are welcome! :)[img]http://www.4smileys.com/smileys/wave-smileys/wave_smiley10.gif[/img]

---

### Post by Cavsfan on 2015-05-15
It must have worked without restarting because when I did restart it did it in 2 seconds.

I'm in Mate now and no need to do anything; all it has is systemd and it always just works.

[IMG]http://www.4smileys.com/smileys/wave-smileys/wave_smiley10.gif[/IMG]

---

### Post by rrnbtter on 2015-05-15
Greetings,
Sorry about the use of sudo guys (bad habit). I edited my post for that one. Regarding the systemd shutdown file you are missing I will check on that when I get home. The reason I put the timeout in both files is so that shutdown and poweroff both would work. I may have typed it the wrong file on the second one. Like I said I have been testing this for a few days and lost track of my changes. I used cut and paste from the terminal memory and may have chosen the wrong one. I will fix this when I get home from work. 
But please to see that it is working. My previous fix in the earlier post worked also but wasn't persistant. It reverted back to it's original state. Could be because the edit wasn't under the [service] unit.

---

### Post by Cavsfan on 2015-05-20
Suddenly my Mate install of Wiley starts going into the 90 second wait with systemd and the fix on this thread will not fix it.

So I google how to to install upstart and I feel like such an idiot that I hadn't discovered this before.

Simply installing *upstart-sysv* gets Init as PID 1 and makes Upstart default and systemd as the alternate.

Plus it has shutdown, restart and logoff all available. :rolleyes:

---

### Post by Cavsfan on 2015-05-21
So....... installing *upstart-sysv* on flavors that do not come with anything but systemd is a most excellent solution IMO.

---

### Post by zika on 2015-05-22
[http://lists.freedesktop.org/archives/systemd-devel/2015-May/032147.html](http://lists.freedesktop.org/archives/systemd-devel/2015-May/032147.html)
> [COLOR=#000000]CHANGES WITH 220:[/COLOR]
        * The gudev library has been extracted into a separate repository
          available at: [https://git.gnome.org/browse/libgudev/](https://git.gnome.org/browse/libgudev/)
          It is now managed as part of the Gnome project. Distributions
          are recommended to pass --disable-gudev to systemd and use
          gudev from the Gnome project instead. gudev is still included
          in systemd, for now. It will be removed soon, though. Please
          also see the announcement-thread on systemd-devel:
          [http://lists.freedesktop.org/archives/systemd-devel/2015-May/032070.html](http://lists.freedesktop.org/archives/systemd-devel/2015-May/032070.html)

        * systemd now exposes a CPUUsageNSec= property for each
          service unit on the bus, that contains the overall consumed
          CPU time of a service (the sum of what each process of the
          service consumed). This value is only available if
          CPUAccounting= is turned on for a service, and is then shown
          in the "systemctl status" output.

        * Support for configuring alternative mappings of the old SysV
          runlevels to systemd targets has been removed. They are now
          hardcoded in a way that runlevels 2, 3, 4 all map to
          multi-user.target and 5 to graphical.target (which
          previously was already the default behaviour).

        * The auto-mounter logic gained support for mount point
          expiry, using a new TimeoutIdleSec= setting in .automount
          units. (Also available as x-systemd.idle-timeout= in /etc/fstab).

        * The EFI System Partition (ESP) as mounted to /boot by
          systemd-efi-boot-generator will now be unmounted
          automatically after 2 minutes of not being used. This should
          minimize the risk of ESP corruptions.

        * New /etc/fstab options x-systemd.requires= and
          x-systemd.requires-mounts-for= are now supported to express
          additional dependencies for mounts. This is useful for
          journalling file systems that support external journal
          devices or overlay file systems that require underlying file
          systems to be mounted.

        * systemd does not support direct live-upgrades (via systemctl
          daemon-reexec) from versions older than v44 anymore. As no
          distribution we are aware of shipped such old versions in a
          stable release this should not be problematic.

        * When systemd forks off a new per-connection service instance
          it will now set the $REMOTE_ADDR environment variable to the
          remote IP address, and $REMOTE_PORT environment variable to
          the remote IP port. This behaviour is similar to the
          corresponding environment variables defined by CGI.

        * systemd-networkd gained support for uplink failure
          detection. The BindCarrier= option allows binding interface
          configuration dynamically to the link sense of other
          interfaces. This is useful to achieve behaviour like in
          network switches.

        * systemd-networkd gained support for configuring the DHCP
          client identifier to use when requesting leases.

        * systemd-networkd now has a per-network UseNTP= option to
          configure whether NTP server information acquired via DHCP
          is passed on to services like systemd-timesyncd.

        * systemd-networkd gained support for vti6 tunnels.

        * Note that systemd-networkd manages the sysctl variable
          /proc/sys/net/ipv[46]/conf/*/forwarding for each interface
          it is configured for since v219. The variable controls IP
          forwarding, and is a per-interface alternative to the global
          /proc/sys/net/ipv[46]/ip_forward. This setting is
          configurable in the IPForward= option, which defaults to
          "no". This means if networkd is used for an interface it is
          no longer sufficient to set the global sysctl option to turn
          on IP forwarding! Instead, the .network file option
          IPForward= needs to be turned on! Note that the
          implementation of this behaviour was broken in v219 and has
          been fixed in v220.

        * Many bonding and vxlan options are now configurable in
          systemd-networkd.

        * systemd-nspawn gained a new --property= setting to set unit
          properties for the container scope. This is useful for
          setting resource parameters (e.g "CPUShares=500") on
          containers started from the command line.

        * systemd-nspawn gained a new --private-users= switch to make
          use of user namespacing available on recent Linux kernels.

        * systemd-nspawn may now be called as part of a shell pipeline
          in which case the pipes used for stdin and stdout are passed
          directly to the process invoked in the container, without
          indirection via a pseudo tty.

        * systemd-nspawn gained a new switch to control the UNIX
          signal to use when killing the init process of the container
          when shutting down.

        * systemd-nspawn gained a new --overlay= switch for mounting
          overlay file systems into the container using the new kernel
          overlayfs support.

        * When a container image is imported via systemd-importd and
          the host file system is not btrfs, a loopback block device
          file is created in /var/lib/machines.raw with a btrfs file
          system inside. It is then mounted to /var/lib/machines to
          enable btrfs features for container management. The loopback
          file and btrfs file system is grown as needed when container
          images are imported via systemd-importd.

        * systemd-machined/systemd-importd gained support for btrfs
          quota, to enforce container disk space limits on disk. This
          is exposed in "machinectl set-limit".

        * systemd-importd now can import containers from local .tar,
          .raw and .qcow2 images, and export them to .tar and .raw. It
          can also import dkr v2 images now from the network (on top
          of v1 as before).

        * systemd-importd gained support for verifying downloaded
          images with gpg2 (previously only gpg1 was supported).

        * systemd-machined, systemd-logind, systemd: most bus calls
          are now accessible to unprivileged processes via
          PolicyKit. Also, systemd-logind will now allow users to kill
          their own sessions without further privileges or
          authorization.

        * systemd-shutdownd has been removed. This service was
          previously responsible for implementing scheduled shutdowns
          as exposed in /usr/bin/shutdown's time parameter. This
          functionality has now been moved into systemd-logind and is
          accessible via a bus interface.

        * "systemctl reboot" gained a new switch --firmware-setup that
          can be used to reboot into the EFI firmware setup, if that
          is available. systemd-logind now exposes an API on the bus
          to trigger such reboots, in case graphical desktop UIs want
          to cover this functionality.

        * "systemctl enable", "systemctl disable" and "systemctl mask"
          now support a new "--now" switch. If specified the units
          that are enabled will also be started, and the ones
          disabled/masked also stopped.

        * The Gummiboot EFI boot loader tool has been merged into
          systemd, and renamed to "systemd-boot". The bootctl tool has been
          updated to support systemd-boot.

        * An EFI kernel stub has been added that may be used to create
          kernel EFI binaries that contain not only the actual kernel,
          but also an initrd, boot splash, command line and OS release
          information. This combined binary can then be signed as a
          single image, so that the firmware can verify it all in one
          step. systemd-boot has special support for EFI binaries created
          like this and can extract OS release information from them
          and show them in the boot menu. This functionality is useful
          to implement cryptographically verified boot schemes.

        * Optional support has been added to systemd-fsck to pass
          fsck's progress report to an AF_UNIX socket in the file
          system.

        * udev will no longer create device symlinks for all block
          devices by default. A blacklist for excluding special block
          devices from this logic has been turned into a whitelist
          that requires picking block devices explicitly that require
          device symlinks.

        * A new (currently still internal) API sd-device.h has been
          added to libsystemd. This modernized API is supposed to
          replace libudev eventually. In fact, already much of libudev
          is now just a wrapper around sd-device.h.

        * A new hwdb database for storing metadata about pointing
          stick devices has been added.

        * systemd-tmpfiles gained support for setting file attributes
          similar to the "chattr" tool with new 'h' and 'H' lines.

        * systemd-journald will no longer unconditionally set the
          btrfs NOCOW flag on new journal files. This is instead done
          with tmpfiles snippet using the new 'h' line type. This
          allows easy disabling of this logic, by masking the
          journal-nocow.conf tmpfiles file.

        * systemd-journald will now translate audit message types to
          human readable identifiers when writing them to the
          journal. This should improve readability of audit messages.

        * The LUKS logic gained support for the offset= and skip=
          options in /etc/crypttab, as previously implemented by
          Debian.

        * /usr/lib/os-release gained a new optional field VARIANT= for
          distributions that support multiple variants (such as a
          desktop edition, a server edition, ...)

        Contributions from: Aaro Koskinen, Adam Goode, Alban Crequy,
        Alberto Fanjul Alonso, Alexander Sverdlin, Alex Puchades, Alin
        Rauta, Alison Chaiken, Andrew Jones, Arend van Spriel,
        Benedikt Morbach, Benjamin Franzke, Benjamin Tissoires, Bla&#382;
        Toma&#382;i&#269;, Chris Morgan, Chris Morin, Colin Walters, Cristian
        Rodríguez, Daniel Buch, Daniel Drake, Daniele Medri, Daniel
        Mack, Daniel Mustieles, daurnimator, Davide Bettio, David
        Herrmann, David Strauss, Didier Roche, Dimitri John Ledkov,
        Eric Cook, Gavin Li, Goffredo Baroncelli, Hannes Reinecke,
        Hans de Goede, Hans-Peter Deifel, Harald Hoyer, Iago López
        Galeiras, Ivan Shapovalov, Jan Engelhardt, Jan Janssen, Jan
        Pazdziora, Jan Synacek, Jasper St. Pierre, Jay Faulkner, John
        Paul Adrian Glaubitz, Jonathon Gilbert, Karel Zak, Kay
        Sievers, Koen Kooi, Lennart Poettering, Lubomir Rintel, Lucas
        De Marchi, Lukas Nykryn, Lukas Rusak, Lukasz Skalski, &#321;ukasz
        Stelmach, Mantas Mikul&#279;nas, Marc-Antoine Perennou, Marcel
        Holtmann, Martin Pitt, Mathieu Chevrier, Matthew Garrett,
        Michael Biebl, Michael Marineau, Michael Olbrich, Michal
        Schmidt, Michal Sekletar, Mirco Tischler, Nir Soffer, Patrik
        Flykt, Pavel Odvody, Peter Hutterer, Peter Lemenkov, Peter
        Waller, Piotr Dr&#261;g, Raul Gutierrez S, Richard Maw, Ronny
        Chevalier, Ross Burton, Sebastian Rasmussen, Sergey Ptashnick,
        Seth Jennings, Shawn Landden, Simon Farnsworth, Stefan Junker,
        Stephen Gallagher, Susant Sahani, Sylvain Plantefève, Thomas
        Haller, Thomas Hindoe Paaboel Andersen, Tobias Hunger, Tom
        Gundersen, Torstein Husebø, Umut Tezduyar Lindskog, Will
        Woods, Zachary Cook, Zbigniew J&#281;drzejewski-Szmek

        -- Berlin, 2015-05-22

Lennart

-- 
Lennart Poettering, Red Hat

Update: 220 just came (main parts) today via upgrade... ;)

---

### Post by Cavsfan on 2015-06-11
I do believe the days of the 90 second wait while systemd restarts/shuts down are a thing of the past.

I seen an update to 220 in systemd and decided to try it again and it's better now. 

Just curious when the normal Wiley 4.2 kernel is going to hit the repos. At least that is what I read Wiley will use. (not trying to get off topic of course)

Cheerios.

---

