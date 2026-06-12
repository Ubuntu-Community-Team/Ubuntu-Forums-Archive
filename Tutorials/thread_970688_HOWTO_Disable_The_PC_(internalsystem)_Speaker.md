---
title: "HOWTO: Disable The PC (internal/system) Speaker"
date: 2008-11-04
forum: Tutorials
---

### Post by steveydoteu on 2008-11-04
**[SIZE="3"]Preamble[/SIZE]**

This may also be referred to as the system beep. Ubuntu utilizes this function found on the majority of computers rather a lot, and it can, for some become an irritation.

A guide does already exist, but on reading seems tailored to laptop users: [http://ubuntuforums.org/showthread.php?t=126746](http://ubuntuforums.org/showthread.php?t=126746)

You may find suggestions else where that instruct you on how to remove the module, or indeed disable the terminal bell. For the purposes of this guide though we will be blacklisting the module as it is the more elegant means of disabling the internal speaker. The module will not even be loaded at boot time.

This has been tested and verified under the following, if you have success in other releases, please let me know and I can add to the list:

[LIST]
[*]**[COLOR="RoyalBlue"]Karmic (9.10)[/COLOR]**
[*]**[COLOR="YellowGreen"]Intrepid (Beta, RC and 8.10)[/COLOR]**
[*]**[COLOR="SandyBrown"]Hardy (8.04 and also 8.04.1)[/COLOR]**
[/LIST]

**[SIZE="3"]Blacklisting the module[/SIZE]**

This method requires basic knowledge of the terminal, but is still very simple.

Fire up a terminal session (Applications > Accessories > Terminal) and proceed with the following command:

```
sudo gedit /etc/modprobe.d/blacklist
```

Enter your password when prompted, it will not display any input.

At the very bottom of the file that is now open in Gedit append the following:

```
blacklist pcspkr
```

Save and close. Next boot, the module will not be loaded and your annoyance ceases.

If you do not want to reboot to initiate the effects of the file, you can manually disable the module using:

```
sudo modprobe -r pcspkr
```

Bare in mind that this piece of code will only disable the module until next boot, if you do not use the above blacklisting method.
[I]
To reverse the process follow the same steps as above, but remove the line you added to the blacklist file.[/I][COLOR="RoyalBlue"][/COLOR]

---

### Post by rossjman1 on 2008-11-15
Worked perfectly. Thanks.

---

### Post by steveydoteu on 2008-11-16
> **rossjman1 said:**
> Worked perfectly. Thanks.

What version are you running may I ask?

---

### Post by roccivic on 2008-12-15
Worked perfect, many thanks.

I'm on Hardy.
```
roccivic@roccivic-office-pc:~$ uname --all
Linux roccivic-office-pc 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

```

---

### Post by Greyed on 2008-12-15
Huh.  My method is a tad simpler, really.

```

Pop case.
Yank cable.

```

Done.  Even works for Windows!  :D

---

### Post by PinkFloyd102489 on 2008-12-15
> **Greyed said:**
> Huh.  My method is a tad simpler, really.

```

Pop case.
Yank cable.

```

Done.  Even works for Windows!  :D


Not in a laptop.

---

### Post by ubername on 2009-01-16
This works for  2.6.27-9-generic Release 8.10 (Intrepid) on Dell 4200

---

### Post by Bachstelze on 2009-01-16
And if you want to avoid a reboot, just unload the module manually:

```
sudo modprobe -r pcspkr
```

---

### Post by lallalla on 2009-11-05
THANKS steveydoteu. after updating to 9.10 the beep started but fortunately it has been banned now....

---

### Post by GiveLove on 2010-01-04
Thank you steveydoteu! :D

This worked under Ubuntu 9.04

GiveLove

---

### Post by wiz561 on 2010-12-10
Doesn't work on Lucid.  :(

---

### Post by LogansRun22 on 2011-11-08
I've tried this on an Acer Iconia W500 running Natty and it doesn't work. The beep happens when I plug in or unplug the power cord, and it also happened in the Windows 7 that came pre-loaded. The BIOS settings have no option to enable or disable the beep either.

---

