---
title: "[SOLVED] Windows keeps rebooting"
date: 2008-11-12
forum: Windows
---

### Post by Jackp90 on 2008-11-12
There is this computer at out school that keeps giving us the safe mode screen and when we select any of the options it instantly reboots and shows us the same screen again.

Any help would be very much appreated. 

Thanks

---

### Post by caljohnsmith on 2008-11-12
Do you have a Windows Install CD? If you have that, I would begin by booting that, going to the recovery console, and doing:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. If that doesn't fix the problem, I might then simply do a "Windows Repair" from the Install CD; you can do that by first choosing the option to install Windows, and then when the CD finds your current installation, it should give you the option to repair it. Good luck and let me know how it goes.

---

### Post by prshah on 2008-11-12
> **Jackp90 said:**
> There is this computer at out school that keeps giving us the safe mode screen and when we select any of the options it instantly reboots and shows us the same screen again.


You need to see why Windows is (instantly) restarting; you can do this in two ways:

1) Immediately after selecting the Windows option in GRUB, keep tapping F8 to get the startup options menu.

== OR ==

2) From Ubuntu (installed or liveCD), edit the MSDOS.SYS file in your Windows partition, and add the below line to the [Options] section:
```

BootMenu=1

```

(if there is no [options] section or if the msdos.sys file is blank, then use
```

[Options]
BootMenu=1

```

Now, when you boot Windows, the startup options menu will appear automatically, without the need to tap F8.

==

Then, from the boot menu, choose the "Disable Automatic Restart on Failure" option. Then let windows boot normally; near the end of the process, you will get a blue screen which will state the cause of the error; post back the error message and details, and we can see how to resolve it easily.

Most likely the error will be similar to "Cannot find NTLDR/System.Dat/User.Dat/SAM/SECURITY" etc. In this case, it's quite easy to resolve, depending on the actual file (area) affected.

---

### Post by pdescham49 on 2008-11-12
What is this windows 98.. groan.

---

### Post by pdescham49 on 2008-11-12
Oh it's NT isn't it ;) "new technology" 

*"Computers are like air conditioners, when you open WINDOWS they stop working."*

---

### Post by Jackp90 on 2008-11-12
> **pdescham49 said:**
> What is this windows 98.. groan.

Sorry I wasn't specific its a hp dc5000 uT running XP

---

### Post by Jackp90 on 2008-11-12
> **caljohnsmith said:**
> Do you have a Windows Install CD? If you have that, I would begin by booting that, going to the recovery console, and doing:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. If that doesn't fix the problem, I might then simply do a "Windows Repair" from the Install CD; you can do that by first choosing the option to install Windows, and then when the CD finds your current installation, it should give you the option to repair it. Good luck and let me know how it goes.

Thanks that worked beautifully and my teacher is surprised that people on Ubuntu forums helped . . . still trying to get him to try Linux though . . .

---

