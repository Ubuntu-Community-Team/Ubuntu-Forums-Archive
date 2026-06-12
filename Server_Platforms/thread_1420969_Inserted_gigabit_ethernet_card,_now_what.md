---
title: "Inserted gigabit ethernet card, now what?"
date: 2010-03-03
forum: Server Platforms
---

### Post by Hathadar on 2010-03-03
I installed ubuntu server 9.10.  During the install the onboard 10/100 land card was automatically installed and was used for updating packages.

I just put in a DGE-530T gigabit ethernet card.
I can see it recognized under lspci.
[INDENT]01:07.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
[/INDENT]
It does not show up under ifconfig.

The CD came with linux drivers.  The readme talked about recompiling the kernal and a whole bunch of other stuff.  Google was equally confusing.

What do I do?

---

### Post by Hathadar on 2010-03-03
I have gotten this far.

I extracted the .tar file.
[INDENT]tar xfjv install-8_3523.tar.bz2[/INDENT]
I tried executing
[INDENT]sudo ./install.sh[/INDENT]
It was giving me a syntax error.
Google had me edit the file and replace #!/bin/sh with #!/bin/bash.
This enabled the installer to start.
After selecting installation from the menu this is what I happened.
[INDENT]Create tmp dir (/tmp/Sk98IgClDiIjdpQCIKAfiYrlR)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.31-14-generic-pae)                         [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (1)                                             [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (not found)                                           [ failed ]
./install.sh: line 504: inst_failed: command not found
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check archive file (sk98lin)                                         [   OK   ]
Check kernel gcc version (4.4.1) (Kernel:4.4.1 != gcc:729:)          [ failed ]
There is a version mismatch between the compiler that was used
to build the current running kernel and the compiler which you
intend to compile the kernel module with. In most of the cases,
this is no problem, but there are cases in which this compiler-
mismatch leads to unexpected system crashes

If you know what you are doing and want to override this
check, you can do so by setting IGNORE_CC_MISMATCH system
variable:
    Example: export IGNORE_CC_MISMATCH=1
Installation of sk98lin driver module failed.
[/INDENT]

What do I do now?

---

### Post by FuturePilot on 2010-03-03
This driver should already be in the kernel. Try ```
sudo modprobe skge
```

---

### Post by Hathadar on 2010-03-03
It accepted the command.  No output.
Rebooted.
Device still does not show up in ifconfig.

---

### Post by FuturePilot on 2010-03-03
Try deleting /etc/udev/rules.d/70-persistent-net.rules and reboot. It will get regenerated on reboot. IIRC I had to do that when I added a NIC card to my server.

---

### Post by Hathadar on 2010-03-03
Ok, I tried that.  It broke my network on the box.
Restored original.
Any other suggestions?

---

### Post by Hathadar on 2010-03-03
I got it working.
I followed the instructions via [https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html").
It had me add a new line to /etc/network/interfaces.

auto eth1
iface eth1 inet dhcp

---

### Post by samosamo on 2010-03-03
> **Hathadar said:**
> I got it working.
I followed the instructions via [https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html").
It had me add a new line to /etc/network/interfaces.

auto eth1
iface eth1 inet dhcp

That's all you needed to do in the first place.  The drivers were unnecessary.

---

