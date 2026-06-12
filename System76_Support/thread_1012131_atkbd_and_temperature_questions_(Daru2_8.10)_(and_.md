---
title: "atkbd and temperature questions (Daru2 8.10) (and a ton of thanks!)"
date: 2008-12-15
forum: System76 Support
---

### Post by ackey on 2008-12-15
I reformatted my Daru2 and did a fresh install of Intrepid.  I was previously running Gutsy.  I was having touchpad, optical drive, and overheating problems - all of which have gone away with the upgrade.  A *huge* thank you to everyone who spent the past months fighting through the bugs and everyone at System76.  This is the best functioning system I have ever had!  :D

Two questions:
Is it reasonable that my Daru2 is running 10-15 degrees cooler (C) in Intrepid as it was in Gutsy?  I was having problems with the system hitting critical trip temperatures while playing videos, etc.  I'm using sensors-applet with lm-sensors, as I was in Gutsy.  It occasionally hits ~80 now, so I want to make sure that I can trust the sensors, rather than the temperature *actually* being 95.  I couldn't find a way to check the temp in BIOS on startup.

My dmesg fills with atkbd complaints.  I saw this sometimes in Gutsy - it is either worse now in Intrepid or everything else is gone so it is more noticeable:
```
[76098.935602] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[76098.935615] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[76098.936864] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[76098.936869] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[76265.077745] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[76265.077760] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[76265.078991] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[76265.079003] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[76265.092075] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[76265.092090] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[76265.093403] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[76265.093416] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[76265.094188] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[76265.094200] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[76265.095528] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[76265.095541] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[76490.666566] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[76490.666582] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[76490.667815] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[76490.667822] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[76490.680684] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).

```
I'm not actually hitting any keys during this.  The solutions I have found so far seem system-specific and aren't clear.  I don't think any problem exists other than useful information in log files being hard to find due to the adkbd output, so I didn't want to hose my system modifying config.d files I don't understand. 
   
Again, a huge thank you to everyone here who makes Ubuntu and system76 machines such a joy to use.

-Nicole

---

### Post by thomasaaron on 2008-12-15
Hi, Nicole.

Please run your system76 driver and reboot and see if the problem stops. That's a pretty weird message, but it could be related to the DarU2's power management bug.

---

### Post by ackey on 2008-12-15
I ran the driver and restarted (I have done it at least twice since the install of 8.10).

I see the atkbd message during part of all of the start-up log message.  I didn't see it for a good 30 minutes or so after, but then I unplugged my laptop and got:
```
[ 2582.277582] atkbd.c: Unknown key pressed (translated set 2, code 0xf2 on isa0060/serio0).
[ 2582.277598] atkbd.c: Use 'setkeycodes e072 <keycode>' to make it known.
[ 2582.278839] atkbd.c: Unknown key released (translated set 2, code 0xf2 on isa0060/serio0).
[ 2582.278847] atkbd.c: Use 'setkeycodes e072 <keycode>' to make it known.
[ 2582.354321] CPU0 attaching NULL sched-domain.
[ 2582.354329] CPU1 attaching NULL sched-domain.
[ 2582.356382] CPU0 attaching sched-domain:
[ 2582.356387]  domain 0: span 0-1 level MC
[ 2582.356390]   groups: 0 1
[ 2582.356395]   domain 1: span 0-1 level CPU
[ 2582.356398]    groups: 0-1
[ 2582.356403] CPU1 attaching sched-domain:
[ 2582.356405]  domain 0: span 0-1 level MC
[ 2582.356408]   groups: 1 0
[ 2582.356411]   domain 1: span 0-1 level CPU
[ 2582.356414]    groups: 0-1
[ 2582.660932] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[ 2582.660939] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[ 2582.662192] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[ 2582.662196] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[ 2582.791299] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[ 2582.791306] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[ 2582.792578] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[ 2582.792584] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[ 2582.812631] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[ 2582.812638] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[ 2582.813889] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[ 2582.813894] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[ 2582.824457] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[ 2582.824466] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[ 2582.825719] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[ 2582.825725] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.

```

The batter monitor seems to work 80% of the time for me.  Right now it can't be read.  Your idea seems likely - every time I plug it in or unplug it a different hex code shows up in the error.  Perhaps when the battery is being properly read the output is frequent...

---

### Post by thomasaaron on 2008-12-15
What version of the driver are you using? System > Admin > System76 Driver > About.

Please post the output of...
```
cat /boot/grub/menu.lst
```

---

### Post by ackey on 2008-12-15
Driver: version 2.2.7

menu.lst 
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7c364b84-efec-46ef-aa1b-09ec1924441c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7c364b84-efec-46ef-aa1b-09ec1924441c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		7c364b84-efec-46ef-aa1b-09ec1924441c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7c364b84-efec-46ef-aa1b-09ec1924441c ro splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		7c364b84-efec-46ef-aa1b-09ec1924441c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7c364b84-efec-46ef-aa1b-09ec1924441c ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7c364b84-efec-46ef-aa1b-09ec1924441c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7c364b84-efec-46ef-aa1b-09ec1924441c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7c364b84-efec-46ef-aa1b-09ec1924441c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7c364b84-efec-46ef-aa1b-09ec1924441c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7c364b84-efec-46ef-aa1b-09ec1924441c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



```

Thank you, as always, for your prompt and excellent help!

---

### Post by thomasaaron on 2008-12-15
That's missing an important kernel option.

Follow these instructions...

> To install the System76 Driver, navigate to [http://planet76.com/repositories](http://planet76.com/repositories) and download the latest .deb package. It will be the one closest to the bottom of the page. Save the package to your Desktop and, when it has finished downloading, double-click it to launch the Gdebi installer. Then, click the install button.

Once the package has installed, you can open the System76 driver by going to System > Administration > System76 Driver. To install the drivers for your machine, Click the "Install" tab and the "Install" button. If you are restoring your machine to factory settings, Click the "Restore" tab and the "Restore" button.

When the driver has finished running, reboot your computer.


...and then re-post your menu.lst.

---

### Post by ackey on 2008-12-15
Ok, I downloaded it - verified the version is 2.2.9 - hit the restore button, then restarted my system.  It doesn't look like my menu.lst has changed - either from the modification date - or from looking at it, but here it is.

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7c364b84-efec-46ef-aa1b-09ec1924441c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7c364b84-efec-46ef-aa1b-09ec1924441c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		7c364b84-efec-46ef-aa1b-09ec1924441c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7c364b84-efec-46ef-aa1b-09ec1924441c ro splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		7c364b84-efec-46ef-aa1b-09ec1924441c
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=7c364b84-efec-46ef-aa1b-09ec1924441c ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7c364b84-efec-46ef-aa1b-09ec1924441c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7c364b84-efec-46ef-aa1b-09ec1924441c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7c364b84-efec-46ef-aa1b-09ec1924441c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7c364b84-efec-46ef-aa1b-09ec1924441c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7c364b84-efec-46ef-aa1b-09ec1924441c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

So assuming that something *should* have changed... the only thing I can think of I might have done wrong is that I edited menu.lst right after the initial install to remove the quiet option.  I removed it from the kernel list, rather than modifying the defoptions or anything.  I am still getting the atkbd output in dmesg, as well.

---

### Post by thomasaaron on 2008-12-15
You need to add this kernel option and reboot...

acpi=noirq

---

### Post by ackey on 2008-12-15
ok, added it.  It looks like the battery monitor is behaving better.

Didn't fix the atkbd issue at all.  I seem to be only getting e071 and e072 when plugging/unplugging the AC, so I'm going to set those scancodes to be keycode 120 - I found people with similar problems saying that 120 isn't used for anything.  Is this going to do anything horrible?    I'm sure my naive fiddling is part of the reason my previous installation was working so poorly...

---

### Post by thomasaaron on 2008-12-16
That might work. Give it a try.

---

### Post by ackey on 2008-12-16
Suddenly things aren't working...   I'm getting bizarre mouse and keyboard behavior.  The dmesg output:

```
[ 1360.518913] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[ 1362.902455] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1363.019268] psmouse.c: resync failed, issuing reconnect request
[ 1364.870362] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1364.881197] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[ 1364.881217] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.THRM._TMP] (Node f70146a8), AE_TIME
[ 1365.068562] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1365.836156] Unable to query Synaptics hardware.
[ 1369.433507] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[ 1369.433523] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.THRM._TMP] (Node f70146a8), AE_TIME
[ 1371.481695] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[ 1371.481725] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1.UPBS] (Node f7015108), AE_TIME
[ 1371.481829] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._BST] (Node f70150a8), AE_TIME
[ 1371.481922] ACPI Exception (battery-0360): AE_TIME, Evaluating _BST [20080609]
[ 1373.533829] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[ 1373.533850] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1.UPBS] (Node f7015108), AE_TIME
[ 1373.533920] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._BST] (Node f70150a8), AE_TIME
[ 1373.533983] ACPI Exception (battery-0360): AE_TIME, Evaluating _BST [20080609]
[ 1375.077403] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[ 1375.077435] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1.UPBS] (Node f7015108), AE_TIME
[ 1375.077541] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._BST] (Node f70150a8), AE_TIME
[ 1375.077635] ACPI Exception (battery-0360): AE_TIME, Evaluating _BST [20080609]
[ 1375.615573] input: PS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input17
[ 1376.150727] psmouse.c: Failed to enable mouse on isa0060/serio4
[ 1381.329326] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[ 1382.115761] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[ 1382.145742] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input18

```

I restarted and the touchpad wouldn't work at all.  I restarted again and it immediately was prolematic:
```

[  120.774981] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  120.775808] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  120.776743] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  120.777712] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  120.778619] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  120.778625] psmouse.c: issuing reconnect request
[  121.604138] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[  121.643964] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[  121.968772] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  121.969669] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  121.970602] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  121.971572] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  121.972504] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  121.972511] psmouse.c: issuing reconnect request
[  123.238738] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[  123.270856] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[  125.846723] wlan0: deauthenticated
[  125.846772] wlan0: authenticate with AP 00:18:74:48:d2:00
[  125.848804] wlan0: authenticated
[  125.848814] wlan0: associate with AP 00:18:74:48:d2:00
[  125.850681] wlan0: RX ReassocResp from 00:18:74:48:d2:00 (capab=0x421 status=0 aid=254)
[  125.850690] wlan0: associated
[  127.570268] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  127.571189] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  127.572099] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  127.573040] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  127.573974] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  127.573980] psmouse.c: issuing reconnect request
[  130.360086] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[  130.360108] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.THRM._TMP] (Node f70146a8), AE_TIME
[  136.968381] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  139.109032] Unable to query Synaptics hardware.
[  139.936442] input: PS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input12
[  154.779341] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 2 bytes away.
[  158.110564] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[  191.020141] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[  197.183184] NET: Registered protocol family 10
[  197.184972] lo: Disabled Privacy Extensions
[  197.186652] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  199.040511] usb 1-1: new low speed USB device using uhci_hcd and address 4
[  199.232577] usb 1-1: configuration #1 chosen from 1 choice
[  199.350919] usbcore: registered new interface driver hiddev
[  199.363445] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0/input/input13
[  199.364851] input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1a.0-1
[  199.364879] usbcore: registered new interface driver usbhid
[  199.364882] usbhid: v2.6:USB HID core driver
[  207.432137] wlan0: no IPv6 routers present
[  219.788559] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[  223.392154] psmouse.c: failed to re-enable mouse on isa0060/serio4
[  223.392170] psmouse.c: resync failed, issuing reconnect request
[  239.118314] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  239.877510] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[  239.928074] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input14
[  240.011596] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  240.012527] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  240.013460] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  240.014402] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  240.015334] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  240.015347] psmouse.c: issuing reconnect request
[  240.776594] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[  241.601063] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[  241.634518] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input15


```

The battery monitor stopped working and one of my temp sensors went crazy.  The ACPI errors are new, but I used to see these psmouse.c errors in Gutsy.

I didn't have any of these problems Friday through today.  The only difference is that I came to work.  I plugged in an external USB mouse - could that have started to cause the psmouse issues?

I think it is using the acpi=noirq boot option.  Before I added that I saw (at least once) " psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away." but I didn't notice strange mouse behavior.  Now it has a life of its own and I get bizarre messages about F7 turning caret behavior on or something.  My keyboard is occasionally not responding at all.  This is now worse than it was under Gutsy, and I had hope the upgrade would make it go away... which it had, for a few days.

Any guesses?

---

### Post by thomasaaron on 2008-12-16
Oops. I think I've seen this before. Let's verify your touchpad isn't failing before looking at configs...

Boot from a live CD and see if the problem occurs (you probably should add the acpi=noirq while booting into the cd. There's a function key you will need to press for it (don't remember for sure which one... maybe F4).

---

### Post by ackey on 2008-12-16
How long should I look for the problem?  I didn't have it behave this badly for a few days - including some time running off a live cd.

---

### Post by thomasaaron on 2008-12-16
Not sure how long. Intermittent problems are difficult to figure out some time. But I've definitely seen this...
> 
[  120.778619] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  120.778625] psmouse.c: issuing reconnect request

...before on several occasions. I'm not trying to freak you out, but it was usually a faulty touchpad. If so, it will get progressively worse and show up on a live CD. If it doesn't show up on a live CD, it could just be some glitch with the psmouse module that a re-install might fix. A fresh install might would fix it. You might also try running from a previous kernel.

---

### Post by ackey on 2008-12-16
Running on the live cd (without the acpi option) definitely results in the same problem.  I rebooted and added the acpi=noirq option and it took longer, but also occurred.

It seems like the problem might be worse in 2.6.27.9 than 2.6.27.7, but it is intermittent enough to make it difficult to tell.  I haven't found a combination in which it doesn't happen.

It looks like my optimism didn't pay off...

---

### Post by thomasaaron on 2008-12-17
Please fill out this form...

[http://system76.com/article_info.php?articles_id=39](http://system76.com/article_info.php?articles_id=39)

It will be sent directly to my inbox, and I'll have a look at your warranty status and see what your options are.

---

### Post by ackey on 2008-12-17
Submitted at least one - computed crashed the first time, so resubmitted.

Thanks for your help!

---

