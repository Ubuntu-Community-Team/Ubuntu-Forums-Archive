---
title: "MIR issues 14.04.  VIRTUAL BOX"
date: 2013-11-18
forum: Ubuntu Development Version
---

### Post by ryanvade on 2013-11-18
Hello everyone.  

I know that both 14.04 and MIR are HIGHLY in development but I have to try anyway.  ;) I have 14.04 installed in a VM (Virtual Box). I am trying to run MIR natively following this guide:
[http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)

However I keep getting this error:
[IMG]http://i1251.photobucket.com/albums/hh555/ryanvade/mir_error_zps44c90269.png[/IMG]

Is this because of the software being alphas or maybe being run in a VM?

---

### Post by grahammechanical on 2013-11-18
Try installing it through the software centre. Look for unity-system-compositor. I have no time to add anything else. Sorry.

Regards.

---

### Post by ryanvade on 2013-11-18
I didn't want to mess with compiling in a VM.  Installed through apt-get...no changes.  Thanks though.

---

### Post by Mateusz Stachowski on 2013-11-19
Mir and XMir aren't supported by VirtualBox or VMware. You have to run those directly on your hardware. 

VMware is probably working on support for Mir because two of theirs developers posted some questions on Mir-devel mailing list.
[URL="https://lists.ubuntu.com/archives/mir-devel/2013-November/"]
https://lists.ubuntu.com/archives/mir-devel/2013-November/[/URL]

---

### Post by grahammechanical on 2013-11-19
Some of us have been checking out Xmir/Mir since the days of the Saucy Salamander cycle. I did not find the instructions in the wiki page to be much good.

[http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)

I found more useful information in a blog by Olli Ries.

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

But even that is now outdated. The last time I installed Xmir on Trusty I did it using these commands

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install unity-system-compositor
sudo restart lightdm
```

Now, I notice that unity-system-compositor is in the Trusty Software Centre. How do we know that we are running on Xmir? some commands to try.

```
grep -i xmir /var/log/Xorg.0.log
grep -i LoadModule /var/log/Xorg.0.log
```

There are others. If the xmir module is loaded then we will be running on it. Interestingly, on this install of Trusty without unity-system-compositor installed I get this message when I run the first of those commands to search for xmir in the log files,

> grep -i xmir /var/log/Xorg.0.log
[    27.561] (WW) "xmir" is not to be loaded by default. Skipping.

What does it mean? apart from the obvious, that is.

Regards.

---

