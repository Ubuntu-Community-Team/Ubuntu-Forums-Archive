---
title: "Bionic Beaver Randomly freezes....any idea how to debug?"
date: 2018-04-07
forum: Ubuntu Development Version
---

### Post by cybermono on 2018-04-07
Hi all,

**The setup**
Running Bionic Beaver - with all the latest updates - tried various  desktops (MATE, Cinnamon, Unity) and kernels (14.5, 14,6 {low latency  and normal} ).  The box it is running on is a Ryzen2400G with 16GB of  RAM.  Virtualbox is running with servers.

**The problem:**

At random the desktop  locks up (freezes) and a reboot is needed.  The  problem is random, but is guaranteed to occur within a few hours (if the  box is left on overnight, 99% it will be locked in the morning - with a  black screen when the monitor is powered on ).

On reboot it may take several retries before it will start, otherwise it hangs in a black screen of death..

Any ideas on how to debug this will be appreciate!

---

### Post by dino99 on 2018-04-07
As you have mixed several desktops, even if only one is still active (others have been erased), that let zomby files/settings that usually disturb/brake the system.
So if you want to test something new, then set a new related partition instead of mixing Desktops for example.
You can try cleaning your actual system via 'gtkorphan' & 'bleachbit' as root, but carefully select the options.
And the best place to find warnings/errors is to run: 'journalctl -b' into a terminal. Warnings are the 'highlighted lines, Errors are the red ones.

---

### Post by cybermono on 2018-04-07
Hi dino99,

Appreciate the response....I only started switching desktops when I noticed Bionic Beaver  randomly freezing - so I do not think that is root cause (pun intended!)

Hope the following info is of some use ...

**From journalctrl here are the last lines at the time the box crashed the last 2 times ...I am not seeing anything in common**

[I]Crash 1
[/I]
```
Apr 07 04:17:01 cybermono01 CRON[5537]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 07 04:17:01 cybermono01 CRON[5538]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 07 04:17:01 cybermono01 CRON[5537]: pam_unix(cron:session): session closed for user root

```
[I]Crash 2
[/I]
```
Apr 07 10:31:23 cybermono01 dbus-daemon[1007]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostnam
Apr 07 10:31:23 cybermono01 systemd[1]: Starting Hostname Service...
Apr 07 10:31:23 cybermono01 dbus-daemon[1007]: [system] Successfully activated service 'org.freedesktop.hostname1'
Apr 07 10:31:23 cybermono01 systemd[1]: Started Hostname Service.
```

**As a matter of interest Header from a boot and some errors along the way**

```
Apr 07 08:34:18 cybermono01 kernel: Linux version 4.16.0-041600-lowlatency (kernel@kathleen) (gcc version 7.2.0 (Ubuntu 7.2.0-8ubuntu3.2)) #201804012230 SM
Apr 07 08:34:18 cybermono01 kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.16.0-041600-lowlatency root=UUID=78e914e5-672c-4cda-aad8-13d02db08230 ro quiet
Apr 07 08:34:18 cybermono01 kernel: KERNEL supported cpus:
Apr 07 08:34:18 cybermono01 kernel:   Intel GenuineIntel
Apr 07 08:34:18 cybermono01 kernel:   AMD AuthenticAMD
Apr 07 08:34:18 cybermono01 kernel:   Centaur CentaurHauls
Apr 07 08:34:18 cybermono01 kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
Apr 07 08:34:18 cybermono01 kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
Apr 07 08:34:18 cybermono01 kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
Apr 07 08:34:18 cybermono01 kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Apr 07 08:34:18 cybermono01 kernel: x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'compacted' format.
Apr 07 08:34:18 cybermono01 kernel: e820: BIOS-provided physical RAM map:

```
**And some errors at boot time - but the system still came up**

```
pr 07 08:34:18 cybermono01 kernel: ACPI BIOS Error (bug): Failure creating [\_SB.SMIC], AE_ALREADY_EXISTS (20180105/dswload-380)
Apr 07 08:34:18 cybermono01 kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180105/psobject-252)
Apr 07 08:34:18 cybermono01 kernel: ACPI Error: AE_ALREADY_EXISTS, (SSDT:  AMD PT) while loading table (20180105/tbxfload-228)
Apr 07 08:34:18 cybermono01 kernel: ACPI Error: 1 table load failures, 7 successful (20180105/tbxfload-246)
...
Apr 07 08:34:18 cybermono01 kernel: ACPI BIOS Error (bug): Failure looking up [\PTOS], AE_NOT_FOUND (20180105/psargs-364)
Apr 07 08:34:18 cybermono01 kernel: No Local Variables are initialized for Method ["\" ]
Apr 07 08:34:18 cybermono01 kernel: No Arguments are initialized for method ["\" ]
Apr 07 08:34:18 cybermono01 kernel: ACPI Error: Method parse/execution failed \, AE_NOT_FOUND (20180105/psparse-550)
....
Apr 07 08:34:18 cybermono01 kernel: AMD-Vi: Unable to write to IOMMU perf counter.
Apr 07 08:34:18 cybermono01 kernel: pci 0000:00:00.2: can't derive routing for PCI INT A
Apr 07 08:34:18 cybermono01 kernel: pci 0000:00:00.2: PCI INT A: not connected
....
Apr 07 08:34:18 cybermono01 kernel: AMD-Vi: Unable to write to IOMMU perf counter.
Apr 07 08:34:18 cybermono01 kernel: pci 0000:00:00.2: can't derive routing for PCI INT A
Apr 07 08:34:18 cybermono01 kernel: pci 0000:00:00.2: PCI INT A: not connected
```

---

### Post by cybermono on 2018-04-07
**And the box just crashed again - last lines recorded in journalctl**

```
Apr 07 14:01:25 cybermono01 systemd[1]: Started Run anacron jobs.
Apr 07 14:01:25 cybermono01 anacron[6774]: Anacron 2.3 started on 2018-04-07
Apr 07 14:01:25 cybermono01 anacron[6774]: Normal exit (0 jobs run)
Apr 07 14:05:46 cybermono01 kernel: logitech-hidpp-device 0003:046D:2008.0005: u´
```

And similar boot errors as earlier post on startup ...

---

### Post by slickymaster on 2018-04-09
@cybermono:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output because when it's posted as plain text it loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by mrosrios on 2018-04-09
[COLOR=#212121][FONT=arial]I have the same problem as cybermono[/FONT][/COLOR]

---

### Post by cybermono on 2018-04-11
I still have this problem in most cases the magic reboot key sequence works - which proves the kernel is still running - but I can not restart the graphics system from the keyboard.  I consider this a graphics driver bug with Raven Ridge chips.

---

### Post by tim1aust on 2018-04-15
Me too.  I am new to kubuntu, switching from long-time centos use in attempt to get my new Ryzen 5 2400G rig going with latest.. hence I loaded 18.04 beta.  I was happy to see my video recognized and (sometimes) working well.  However, after light desktop use (mozilla browsing, and most recently when watching an H.264 video with Plex) the desktop freezes. Rebooting is a crap shoot, more times than not (say 70% of the time), it locks up when mode switching. nomodeset avoids this, but that's not what I'm here for :-) Anyway, I captured lspci and dmesg output, will append that as soon as I figure out how.
--tim

---

### Post by tim1aust on 2018-04-15
I had to compress the dmesg due to filesize limit.

I hope this helps to debug the AMD Vega graphics issue.  I am willing to do some testing if that will help.  Thanks!
--tim

---

### Post by mc4man on 2018-04-15
As I don't have this hw (not even close..) only gave a quick glance to this extended thread, seems related, maybe some info of use?
[https://forum.manjaro.org/t/any-support-for-the-ryzen-2200g-and-2400g-for-linux/38079/161](https://forum.manjaro.org/t/any-support-for-the-ryzen-2200g-and-2400g-for-linux/38079/161)

---

### Post by tim1aust on 2018-04-16
Thanks, definitely more things to try.. perhaps best one: "You all should probably just wait until 4.16 has stabilized, mesa 18 has been released, ..."

I'm impressed with kubuntu, may just switch from centos, esp. if things stabilize on this new hardware.
--tim

---

### Post by cybermono on 2018-04-19
OK, quick update - I am still having this issue.  The latest Bionic Beaver builds (the last 2 or 3 days) with Kernel 4.15 generic seems much more stable than 4.16 (which is counter intuitive as 4.16 is supposed to have more fixes  ).  I can often get 9 hours plus without a freeze!  Which is still not good...might have to go with MS Server for a few months :-(

---

### Post by mrosrios on 2018-04-20
[COLOR=#212121][FONT=inherit]Ubuntu 18.04 freezes very often. System freezes completely[/FONT][/COLOR]

[COLOR=#212121][FONT=inherit]Ubuntu 18.04 freezes every so often and does not allow you to do anything or respond to any combination of roofs, it only remains to turn off the computer with the switch.[/FONT][/COLOR]
[COLOR=#212121][FONT=inherit]I have not been able to relate it to any particular application, it does it randomly, it only seems that when the graphic card has more work there is also a better chance of the computer freezing.[/FONT][/COLOR]


[COLOR=#212121][FONT=inherit]My computer is an Acer Extensa-2508[/FONT][/COLOR]
[COLOR=#212121][FONT=inherit]Processor: Intel® Pentium (R) CPU N3540 @ 2.16GHz × 4 - 64 bits[/FONT][/COLOR]
[COLOR=#212121][FONT=inherit]Graphics card: Intel® Bay Trail[/FONT][/COLOR]
[COLOR=#212121][FONT=inherit]Solid disk of 240 GB[/FONT][/COLOR]
[COLOR=#212121][FONT=inherit]500GB data hard drive[/FONT][/COLOR]
[COLOR=#212121][FONT=inherit]Dual boot with Windows 10[/FONT][/COLOR]

[COLOR=#212121][FONT=inherit]I think it must be kernell or the drivers of the graphic card.[/FONT][/COLOR]
[COLOR=#212121][FONT=inherit]Is there any way to check it?[/FONT][/COLOR]

---

### Post by pqwoerituytrueiwoq on 2018-04-21
install [openssh-server]("apt:openssh-server") and see if you can login via ssh after it freezes
I *may* have managed to get this to happen on some much older hardware, in my case i was able to use ssh to login and found the cpu had soft-locked [https://ubuntuforums.org/showthread.php?t=2389818](https://ubuntuforums.org/showthread.php?t=2389818)
Trying to rule out hardware failure as a possibility now

---

