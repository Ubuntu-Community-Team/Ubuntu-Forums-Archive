---
title: "VMWare Server with Win2K won't register some keys"
date: 2009-12-05
forum: Virtualisation
---

### Post by sethtriggs on 2009-12-05
I have a bizarre problem with my VMWare Server. After upgrading to Ubuntu 8.10, which was a painful process no thanks to my ATI card, I noticed that certain keys do not work when in VMWare Server. These keys function perfectly fine in Ubuntu, but when I load the virtual machine, all of a sudden they either do not respond, or they provide an odd behavior.

Essentially, all of the standard type keys and the function keys work - essentially, the entire left side of the keyboard (which is a Microsoft Media Pro Keyboard). Note that this keyboard is plugged into the PS/2 port since my machine will not boot with a keyboard connected via USB.

It gets very odd to the right side. None of the keys like Delete, Insert, Page up or Down work; neither do the arrow keys. The numbers on the numeric keypad work, as do the special symbols (and Num Lock works too) - yet the Enter key doesn't work (it seems to function like a tab key)! Very annoying and bizarre to say the least.

I'm running VMWare Server 2.0.2, installed from the tar.gz. The guest OS is Windows 2000. What I've tried already, since I cannot find keyboard settings in the virtual machine config:

* Tried checking for a keyboard layout setting in Windows, got nowhere with locating that (and this should not have changed anyway since the machine was identical to before I upgraded to 8.10).
* I installed Microsoft Intellitype for Windows. This seems to not recognize the keyboard anyway. Perhaps this would've only worked via USB? I don't know. Because if that's the case, I'll have a system that will not start.

Has anyone had this happen? Thank you all very much for your help, in advance.

-Seth

---

### Post by sethtriggs on 2009-12-06
This was solved by following the instructions in this thread:

[http://ubuntuforums.org/showpost.php?p=8248408&postcount=13](http://ubuntuforums.org/showpost.php?p=8248408&postcount=13)

The instruction:

```

Edit the file: /etc/vmware/config

Add the line:
xkeymap.nokeycodeMap = "TRUE"

```
from sdowney717

-Seth

---

