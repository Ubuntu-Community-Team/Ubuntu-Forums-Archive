---
title: "Fails to boot properly after updating to 14.04"
date: 2014-05-17
forum: Server Platforms
---

### Post by LugnutsK on 2014-05-17
[SIZE=7]The problem went away by itself, some time in late 2014, after some updates. I don't know what the problem was, but it's gone now.[/SIZE]



-----


(similar, also with no solution yet: [http://ubuntuforums.org/showthread.php?t=1585439](http://ubuntuforums.org/showthread.php?t=1585439) )

After updating to 14.04, my server no longer boots. Here is what happens:
From GRUB, if I choose the normal "Ubuntu" option, it appears to be booting normally until it outputs something like:
```

init: plymouth-upstart-bridge main process (398) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (398) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge main process (398) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
init: plymouth-upstart-bridge respawning too fast, stopped
Adding swap on /dev/sda2. ...

```
***See below**

The console then stops for a few moments, then the screen falls asleep, then I see my motherboard logo (BIOS) indicating the computer is restarting. It is very similar as discussed in [http://ubuntuforums.org/showthread.php?t=2218100](http://ubuntuforums.org/showthread.php?t=2218100) , but the problem described there doesn't actually crash the server.

-------

From GRUB, if I choose "Advanced options for Ubunutu" there are 4 options:
[LIST]
[*]Ubuntu w/ Linux 3.13 
[*]Ubuntu w/ Linux 3.13 (recovery mode) 
[*]Ubuntu w/ Linux 3.11 
[*]Ubuntu w/ Linux 3.11 (recovery mode) 
[/LIST]
When I boot with either of the recovery modes, selecting "resume normal boot" will continue booting a be successful.
Booting with 3.13 has the same issue as in the beginning of this post.
Booting with 3.11, interestingly, will display the same messages as above, but will continue to boot successfully. The same pause and screen-sleeping occurs, but the console comes back afterwards (in a different screen resolution too). ***This leads me to believe that neither this plymouth thing nor swap is causing the problem.**

One more thing, twice when I have tried booting it, (after crashing) instead of showing the motherboard logo, the BIOS says:
```
All settings were reset to default values.
The previous overclock settings have failed, system has been restored to its default settings.
Press F1 to run setup.
Press F2 to load default values and run setup.
```The only settings I have changed was to set the ram clock speed to the manufacturer's default, 1600, and to underclock the CPU a bit. Sure enough, these settings were reset. This could indicated a hardware problem, but I have run memcheck, and it did not detect any errors. I have also tried booting without any OC adjustments, and the problem persists.

Any help is appreciated!

---

### Post by Tadaen_Sylvermane on 2014-05-17
Similar problem except mine doesn't reboot. It just sits there until I turn it off manually and go back to my trusty Debian. It boots directly to a recovery though. Tons of stuff scrolling by the screen when it boots until it just hangs there around or just at mounting swap.

AMD 5350 Kabini
AsRock AM1H-ITX
4gb Gskill
120 GB Samsung Evo
1TB WD HDD

---

### Post by LugnutsK on 2014-07-16
I am still having the same problem.
From Ubuntu advanced options in GRUB:
```

Ubuntu, with Linux 3.13.0-30-generic - does not boot
Ubuntu, with Linux 3.13.0-30-generic (recovery mode) - boots after "resume normal boot"
Ubuntu, with Linux 3.13.0-24-generic - does not boot
Ubuntu, with Linux 3.13.0-24-generic (recovery mode) - boots after "resume normal boot"
Ubuntu, with Linux 3.11.0-20-generic - boots
Ubuntu, with Linux 3.11.0-20-generic (recovery mode) - boots after "resume normal boot"

```

---

