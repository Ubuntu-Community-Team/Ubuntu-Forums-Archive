---
title: "Optiarc DVD detection problem"
date: 2008-11-07
forum: System76 Support
---

### Post by perez2000 on 2008-11-07
During boot up of a Bonobo Professional the laptop will hang for 30 seconds and error out trying to initialize the DVD drive. I see strange "qc timeout" and "revalidation failed" messages.

uname -a: Linux ubuntu 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux

Portion of dmesg after power on:

```

[  107.467434] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  107.483306] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, SX01, max UDMA/100, ATAPI AN
[  107.484749] usb 2-2: new low speed USB device using uhci_hcd and address 3
[  107.542536] usb 2-2: configuration #1 chosen from 1 choice
[  107.783188] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  107.957476] usb 3-1: configuration #1 chosen from 1 choice
[  137.469106] ata2.00: qc timeout (cmd 0xa1)
[  137.469170] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  137.469232] ata2.00: revalidation failed (errno=-5)
[  137.469297] ata2: failed to recover some devices, retrying in 5 secs
[  137.575689] ata2: port is slow to respond, please be patient (Status 0x80)
[  137.627178] ata2: COMRESET failed (errno=-16)
[  137.633209] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  137.663998] ata2.00: configured for UDMA/100
[  137.664063] ata2: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
[  137.664126] ata2: irq_stat 0x40000008

```

There are 2 workarounds for this problem but I don't want to use either:

1) Disable AHCI in the BIOS and select IDE instead for the SATA drive setup. This can be done by selecting "Other OS" rather than "Vista".

2) Ctrl-Alt-Del after it gets stuck. On reboot (not power off) the DVD is detected. It is like there a race condition that is fixed when rebooted. After reinstalling ubuntu to setup LUKS, this is the workaround I have been using to get the passphrase prompt to appear.

Correct dmesg after ctrl-alt-del:

```

[   34.005787] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   34.009139] usb 1-1: configuration #1 chosen from 1 choice
[   34.033653] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, SX01, max UDMA/100, ATAPI AN
[   34.036584] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   34.051202] ata2.00: configured for UDMA/100

```

Suggestions on a fix?

---

### Post by Guille Damke on 2008-11-08
I don't have a solution, but a problem.

Since I have had troubles with my sound (this is not a complain against my Pangolin Performance panp4n, I did something wrong for sure), I wanted to reinstall Ubuntu from scratch. After choosing reinstall, I got into a sort of shell, with a prompt like this "(initramfs)", and I get these errors:

(initramfs) ata2.00: failed to IDENTIFY (I/O error, err)mask=0x4
 ata2.00: COMRESET failed (errno=-5)
 ata2.00: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
 ata2.00 irq_stat 0x40000008
(initramfs)

I think it is a problem related to yours.
Does anyone has tried to reinstall Ubunut 8.04? 

Guille.

---

### Post by thomasaaron on 2008-11-10
perez2000, those are the only workarounds we've found thus far.

Guille, go into your BIOS and disable AHCI. Also, you may need to install 8.04 using "Safe Graphics" mode. This is available via pressing F4 in the live CD menu.

---

### Post by perez2000 on 2008-11-12
I was looking for a kernel boot option or BIOS setting (other than disable AHCI).

If AHCI is disabled, are there any ramifications such as degraded SATA performance or loss of functionality?

---

### Post by thomasaaron on 2008-11-13
I'm not entirely sure. But definitely not that I notice. I'll ask R&D about it. I'll ask them about a boot option too, but I'd be slightly surprised if one exists.

---

