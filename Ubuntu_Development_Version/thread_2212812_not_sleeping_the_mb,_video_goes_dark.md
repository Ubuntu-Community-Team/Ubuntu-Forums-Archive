---
title: "not sleeping the mb, video goes dark"
date: 2014-03-23
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-23
sudo pm-suspend does not let it sleep nor does the menu clicking.

So where is the log?

---

### Post by sdowney717 on 2014-03-23
in sys log notice what it does

```
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.469956] PM:** Entering standby sleep**
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.469983] Suspending console(s) (use no_console_suspend to debug)
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.470390] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.476671] sd 0:0:0:0: [sda] Stopping disk
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.496260] parport_pc 00:0e: disabled
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.496409] serial 00:0d: disabled
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.496457] i8042 kbd 00:0b: System wakeup enabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.496609] serial 00:05: disabled
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.728130] PM: suspend of devices complete after 257.858 msecs
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.728426] PM: late suspend of devices complete after 0.293 msecs
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.728568] pcieport 0000:00:1c.1: System wakeup enabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.744154] ehci-pci 0000:00:1d.7: System wakeup enabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.760071] uhci_hcd 0000:00:1d.3: System wakeup enabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.760107] uhci_hcd 0000:00:1d.2: System wakeup enabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.760141] uhci_hcd 0000:00:1d.1: System wakeup enabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.760176] uhci_hcd 0000:00:1d.0: System wakeup enabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.760277] PM: noirq suspend of devices complete after 31.849 msecs
[COLOR="#B22222"][COLOR="#FF0000"]Mar 23 09:17:14 boat-MS-7529 kernel: [   76.760628] ACPI: Preparing to enter system sleep state S1
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.760849] PM: Saving platform NVS memory[/COLOR][/COLOR]
[B]Mar 23 09:17:14 boat-MS-7529 kernel: [   76.761144] Disabling non-boot CPUs ...
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.762473] kvm: disabling virtualization on CPU1
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.864070] smpboot: CPU 1 is now offline
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.868057] PM: Restoring platform NVS memory
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.868057] Force enabled HPET at resume
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.868057] Enabling non-boot CPUs ...
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.868057] x86: Booting SMP configuration:
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.868057] smpboot: Booting Node 0 Processor 1 APIC 0x1
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.868057] kvm: enabling virtualization on CPU1
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.877873] CPU1 is up[/B]
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.879626] ACPI: Waking up from system sleep state S1
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.892178] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.892214] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.892251] uhci_hcd 0000:00:1d.2: System wakeup disabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.892283] uhci_hcd 0000:00:1d.3: System wakeup disabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.908059] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.956246] PM: noirq resume of devices complete after 76.353 msecs
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.956380] PM: early resume of devices complete after 0.105 msecs
Mar 23 09:17:14 boat-MS-7529 kernel: [   76.956506] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
```

---

### Post by sdowney717 on 2014-03-23
dmesg sleep log entry, notice that cpu gpoes offline, then restoring platform NVS memory.
So what is it doing?

```
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.016620] ACPI: Preparing to enter system sleep state S1
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.016840] PM: Saving platform NVS memory
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.017180] Disabling non-boot CPUs ...
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.018426] kvm: disabling virtualization on CPU1
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.120040] smpboot: CPU 1 is now offline


Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.124018] PM: Restoring platform NVS memory
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.124018] Force enabled HPET at resume
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.124018] Enabling non-boot CPUs ...
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.124018] x86: Booting SMP configuration:
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.124018] smpboot: Booting Node 0 Processor 1 APIC 0x1
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.124018] kvm: enabling virtualization on CPU1
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.133842] CPU1 is up
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.135610] ACPI: Waking up from system sleep state S1
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.148175] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.148211] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.148249] uhci_hcd 0000:00:1d.2: System wakeup disabled by ACPI
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.148280] uhci_hcd 0000:00:1d.3: System wakeup disabled by ACPI
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.164051] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.212231] PM: noirq resume of devices complete after 76.361 msecs
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.212364] PM: early resume of devices complete after 0.103 msecs
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.212476] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.212556] usb usb2: root hub lost power or was reset
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.212596] usb usb3: root hub lost power or was reset
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.212634] usb usb4: root hub lost power or was reset
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.212673] usb usb5: root hub lost power or was reset
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.212730] radeon 0000:01:00.0: ffff8800368fbc00 unpin not necessary
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.254487] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.255705] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.255709] radeon 0000:01:00.0: WB enabled
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.255712] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000010000000 and cpu addr 0xffff8800b9024000
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.255731] [drm] radeon: ring at 0x0000000010001000
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.255759] [drm] ring test succeeded in 8 usecs
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.255773] [drm] ib test succeeded in 0 usecs
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.316050] pciehp 0000:00:1c.1:pcie04: Device 0000:03:00.0 already exists at 0000:03:00, cannot hot-add
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.316053] pciehp 0000:00:1c.1:pcie04: Cannot add device at 0000:03:00
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.316859] serial 00:05: activated
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.316909] i8042 kbd 00:0b: System wakeup disabled by ACPI
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.317633] serial 00:0d: activated
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.318457] parport_pc 00:0e: activated
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.318528] pcieport 0000:00:1c.1: System wakeup disabled by ACPI
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.329545] r8169 0000:03:00.0 eth0: link down
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.376293] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.376295] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.387009] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.387011] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.412894] ata1.00: configured for UDMA/100
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.412938] sd 0:0:0:0: [sda] Starting disk
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4733.692074] usb 2-1: reset low-speed USB device number 2 using uhci_hcd
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4735.377388] r8169 0000:03:00.0 eth0: link up
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4739.972537] PM: resume of devices complete after 6760.170 msecs
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4739.972838] PM: Finishing wakeup.
Mar 23 10:35:35 boat-MS-7529 NetworkManager[749]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Mar 23 10:35:35 boat-MS-7529 NetworkManager[749]: <info> (eth0): carrier now ON (device state 100)
Mar 23 10:35:35 boat-MS-7529 kernel: [ 4739.972840] Restarting tasks ... done.
Mar 23 10:35:35 boat-MS-7529 anacron[6008]: Anacron 2.3 started on 2014-03-23
Mar 23 10:35:35 boat-MS-7529 anacron[6008]: Normal exit (0 jobs run)
Mar 23 10:35:36 boat-MS-7529 anacron[6057]: Anacron 2.3 started on 2014-03-23
Mar 23 10:35:36 boat-MS-7529 anacron[6057]: Normal exit (0 jobs run)
Mar 23 10:36:07 boat-MS-7529 dbus[630]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Mar 23 10:36:07 boat-MS-7529 dbus[630]: [system] Successfully activated service 'org.freedesktop.hostname1'
```

---

### Post by kurt18947 on 2014-03-23
I suspect it depends on the machine but I did a BIOS reset on a desktop machine.  The default suspend mode was S1 during which the power LED flashed and the Power Supply fan operated.  Changing the suspend mode from S1 to S3 restored the 'quiet dark machine' suspend operation I expected.  "sudo pm-suspend" works on my 14.04 install.

---

### Post by sdowney717 on 2014-03-23
That fixed it, my setting was s1.:P
set to s3 and wake by keboard and it is working.

---

