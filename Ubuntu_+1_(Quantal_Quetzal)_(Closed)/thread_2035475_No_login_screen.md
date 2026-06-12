---
title: "No login screen"
date: 2012-07-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kiwited on 2012-07-30
My start sequence stops at a command line login prompt.
1. Starting with the normal (non-recovery mode) goes to login prompt. after login to user "sudo startx" series of messages (19 in total) similar to "(WW) fglrx: No matching Device section for instance (Bus ID PCI :0@0:9:2:0) found"
The last group of numbers changes.
Further on "Segmentation fault at address 0x10
Caught signal 11 (segmentation fault) . Server aborting"
Thence back to command line prompt.
So:
"sudo start lightdm"
Messages starting lots of services but stops at "*Starting CUPS printing spooler/printer"
Restart into recovery mode
Run in failsafe graphics mode leads to a fatal error no screens found message
Resume goes to command line login and the problems above.
64 bit AMD X6 Radeon 

Theo

Theo

---

### Post by effenberg0x0 on 2012-07-30
As a side note, you should use the command "service" to control services. So instead of directly executing startx or lightdm, you can use the following:
```

sudo service lightdm stop
sudo service lightdm start

```To me, a normal boot stopping before lightdm suggests no VGA driver/kernel module installed, VGA kernel module not loaded, incorrect driver/module set (versions) or a wrong /etc/X11/xorg.conf.

I'm no ATI specialist, but I'm gonna pick the last one. You should have a proper "BusID" value in the device section. You can get this value using lspci.
```
 
[19:23:39] ahsl@AL-DESK01:[~]: lspci | grep -i vga
**01:00.0** VGA compatible controller: NVIDIA Corporation GF106 [GeForce GTS 450] (rev a1)

```So, if you boot normally (not in recovery mode), switch to a VT (Ctrl+Alt+F1 to F6), edit /etc/X11/xorg.conf (sudo nano /etc/X11/xorg.conf) you can check what you have for BusID. In my case, I have:
```

BusID    "PCI:**1:0:0**"

```Also: I *think* you can simply remove /etc/X11/xorg.conf with ATI...
```

sudo service lightdm stop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo service lightdm start

```...and you can also run the ATI config tool. I guess it creates whatever you need in config (again, ATI is not my area of expertise):
```

sudo aticonfig --initial

```OBS: I'm not sure if one needs to run aticonfig with or without X. I think I would stop lightdm service before, run the tool, start lightdm service after.

---

### Post by kiwited on 2012-07-30
Code

 lspci | grep -i vga
05:00.0 VGA compatible controller:Advanced Micro Devices [AMD] nee ATI RV670 [Radeon HD 3870]

Editing xorg.conf
BusID    "PCI:5:0:0"
 
Adding the word service to the command caused an error message and the command did not run

The aticonfig command firstly made the response that something was not initialised then ran. Subsequently the command just ran.

In the end, though, there has been no changes and the login screen does not start.

Many thanks for you help,

Theo

---

### Post by effenberg0x0 on 2012-07-30
Ok, so at first you had:
```
"(WW) fglrx: No matching Device section for instance (Bus ID PCI :0@0:9:2:0) found"

```
I found that PCI weird, which is why I suggested lspci and fixing BusID on /etc/X11/xorg.conf. I think this was a correct step - the BusID was wrong, now it is right. But I have no information about the messages and/or errors you got after fixing that, so I cannot try to help you in a more efficient way.

Try renaming, moving or deleting xorg.conf altogether, as I suggested as a possible alternative in my previous post: Maybe there's more stuff wrong in xorg.conf and I'm pretty sure we don't need a xorg.conf anymore in ATI too. 

Regards,
Effenberg

---

### Post by nutscracker.ua on 2012-07-31
Hello, I have a same problem. No login screen, and same segmentation fault. I removed xorg.conf, becose its not needed. Xorg log says that. BusID PCI setted wrong. And i cant change that id somehow. End then xorg set device with no busId as primary divice. And all this stuff happen to me after last upgrade.

---

### Post by nutscracker.ua on 2012-07-31
I have removed  fglrx driver, and this, i hope, fix busID problem becose no warnings in my xorg log file. I still cant see my login screen. But when i star X from console, type sudo startx, i see message "Failed to load session "ubuntu""

---

