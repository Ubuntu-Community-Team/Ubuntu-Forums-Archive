---
title: "Radeon HD 4570: Unsure if I have graphics card drivers in Ubuntu 14.04"
date: 2014-05-16
forum: System76 Support
---

### Post by belandil on 2014-05-16
I have a Pangolin Performan with an ATI Mobility Radeon HD 4570 Graphics with 512MB GD.  Finally upgraded to Ubuntu 14.04, but I'm not sure my graphics card driver was installed properly.  I installed the System76 driver following instructions found at [http://knowledge76.com/index.php/Version_Upgrade](http://knowledge76.com/index.php/Version_Upgrade) but I don't see any evidence of a graphics driver installation.  Nothing comes up under when running 'Additional Drivers.'  Is there a way I can check to see if I have the driver installed?

---

### Post by grahammechanical on 2014-05-20
I do not have a System 76 machine but I do know that Additional Drivers does need to be allowed time to work. You can also try either or both of these commands. Again we must wait for the commands to work.

```
ubuntu-drivers list
ubuntu-drivers devices
```

If the system76 driver is in the list then in should be installed. You could also try running the install system76-driver command again. The terminal should tell you if you already have it installed. If it is installed then it will be activated.

Regards.

---

### Post by MoebusNet on 2014-05-20
This should show what is currently in use:

```
lspci -nnk | grep -iA2 vga
```

I found this at: [http://ubuntuforums.org/showthread.php?t=2068195](http://ubuntuforums.org/showthread.php?t=2068195)

---

### Post by MoebusNet on 2014-05-20
> **belandil said:**
> I have a Pangolin Performan with an ATI Mobility Radeon HD 4570 Graphics with 512MB GD.  Finally upgraded to Ubuntu 14.04, but I'm not sure my graphics card driver was installed properly.  I installed the System76 driver following instructions found at [http://knowledge76.com/index.php/Version_Upgrade](http://knowledge76.com/index.php/Version_Upgrade) but I don't see any evidence of a graphics driver installation.  Nothing comes up under when running 'Additional Drivers.'  Is there a way I can check to see if I have the driver installed?

One other thing; the instructions state that you must reboot your computer for the drivers to complete installation. I can confirm that this is the case; my NVIDIA drivers did not take effect until after I shut completely down and did a cold boot. If you haven't done this yet, it is definitely worth a try.

Hope this helps.

---

### Post by belandil on 2014-06-01
```

belandil@europa: ubuntu-drivers list

belandil@europa: ubuntu-drivers devices
belandil@europa: lspci -nnk | grep -iA2 vga
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4530/4570/545v] [1002:9553]
    Subsystem: CLEVO/KAPOK Computer Device [1558:0770]
    Kernel driver in use: radeon
belandil@europa: sudo apt-get install system76-driver
[sudo] password for belandil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
system76-driver is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

```

Since "Kernel driver in use: radeon" shows up, I think I have the driver installed.  Marking this solved.  Thanks!

---

