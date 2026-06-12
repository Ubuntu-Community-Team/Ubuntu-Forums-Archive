---
title: "Battery Not Found"
date: 2007-05-07
forum: System76 Support
---

### Post by logical_thought on 2007-05-07
I recently purchased a gazelle value, and I'm loving it. Unfortunately after installing some software and attempting to suspend I am unable to monitor battery power. When the laptop is plugged up it doesn't recognize that there is a battery, and when running on battery power it doesn't poll how much charge is left.

While looking at dmesg this seemed significant:

```
[   19.552000] ALSA /opt/system76/system76-driver/src/sys76-alsa-1.0.14rc3/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:556: hda_intel: azx_get_response timeout, switching to polling mode...

[   20.500000] NET: Registered protocol family 17

[   21.068000] Asus Laptop ACPI Extras version 0.30

[   21.068000]   unsupported model Z62FM, trying default values

[   21.068000]   send /proc/acpi/dsdt to the developers

[   21.092000] ACPI: AC Adapter [AC0] (off-line)

[   21.168000] ACPI Exception (exoparg2-0442): AE_AML_BUFFER_LIMIT, Index (000000080) is beyond end of object [20060707]

[   21.168000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_.BIF9] (Node df80aae0), AE_AML_BUFFER_LIMIT

[   21.168000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.BAT0._BIF] (Node df80a2d4), AE_AML_BUFFER_LIMIT

[   21.168000] ACPI Exception (acpi_battery-0148): AE_AML_BUFFER_LIMIT, Evaluating _BIF [20060707]

[   21.188000] input: Power Button (FF) as /class/input/input4

[   21.188000] ACPI: Power Button (FF) [PWRF]

[   21.188000] input: Lid Switch as /class/input/input5

[   21.188000] ACPI: Lid Switch [LID]

[   21.188000] input: Power Button (CM) as /class/input/input6

[   21.188000] ACPI: Power Button (CM) [PWRB]

[   21.188000] input: Sleep Button (CM) as /class/input/input7

[   21.188000] ACPI: Sleep Button (CM) [SLPB]

[   21.328000] No dock devices found.

[   21.352000] Using specific hotkey driver

[   21.436000] ibm_acpi: ec object not found

[   21.512000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

[   21.568000] pcc_acpi: loading...

[   21.872000] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFD) is beyond end of object [20060707]

[   21.872000] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PSS] (Node df80dba8), AE_AML_PACKAGE_LIMIT

[   21.872000] ACPI Exception (acpi_processor-0235): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20060707]

[   21.872000] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (0FFFFFFFD) is beyond end of object [20060707]

[   21.872000] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PSS] (Node df80d9f0), AE_AML_PACKAGE_LIMIT

[   21.872000] ACPI Exception (acpi_processor-0235): AE_AML_PACKAGE_LIMIT, Evaluating _PSS [20060707]
```


I'm sort of new to Linux and would appreciate the help.

---

### Post by thomasaaron on 2007-05-08
Hi, logical_thought. Let's think about this logically :guitar:

1. If you unplug your A/C adaptor, does your battery icon show up in the upper left of your monitor?
If it does, right click the icon, choose 'preferences', choose the 'general' tab, and select 'Always on'.  Now, watch the icon for a while and see if it is accurately tracking your power.

2. If there is no icon, right click on the upper bar, select 'Add to Panel', click on the 'Battery Charge Monitor' icon and configure it similarly to step #1. Then watch it.

3. If none of this works, what programs did you install before you noticed the problem? Let me know, and I'll tell you if they have any bearing on this issue. (But they probably do not). But if they did, you could uninstall them and run your System 76 driver to restore your system to default settings.

4. Suspend can be problematic with the Gazelle Value. But any thing it breaks (that is, if it broke your battery monitoring), I would think could be fixed by rebooting. Does it work after rebooting?

Best,
Tom

---

### Post by logical_thought on 2007-05-08
I tried the first two options before I posted.

And you were right about the reboot .... I rebooted twice and it still would not read, but after the third try it was reading again. I&#8217;m not certain why a third reboot worked, unless letting it sit for an hour or two helped. :)

---

