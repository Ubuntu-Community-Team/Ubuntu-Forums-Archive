---
title: "Random Reboots on 8.04 Hardy"
date: 2008-12-13
forum: Server Platforms
---

### Post by Jack Collins on 2008-12-13
HP DL380 G5 with 8.04 Hardy is reboots/crashes several times a week, sometimes more than once per day. I can't seem to find any reason for this to be happening.

I noticed this one series of entry from dmesg on boot: 

   80.954670] ACPI: SSDT CFE5F800, 00D8 (r1 HP      CPU0CST        1 INTL 20061109)
[   80.954790] ACPI Error (psargs-0355): [CS03] Namespace lookup failure, AE_NOT_FOUND
[   80.954795] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0._CST] (Node f7f690f0), AE_NOT_FOUND
[   80.954998] ACPI: SSDT CFE5F900, 00D8 (r1 HP      CPU1CST        1 INTL 20061109)
[   80.955111] ACPI Error (psargs-0355): [CS03] Namespace lookup failure, AE_NOT_FOUND
[   80.955115] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._CST] (Node f7f690d8), AE_NOT_FOUND
[   80.955313] ACPI: SSDT CFE5FA00, 00D8 (r1 HP      CPU2CST        1 INTL 20061109)
[   80.955422] ACPI Error (psargs-0355): [CS03] Namespace lookup failure, AE_NOT_FOUND
[   80.955426] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._CST] (Node f7f69060), AE_NOT_FOUND
[   80.955623] ACPI: SSDT CFE5FB00, 00D8 (r1 HP      CPU3CST        1 INTL 20061109)
[   80.955732] ACPI Error (psargs-0355): [CS03] Namespace lookup failure, AE_NOT_FOUND
[   80.955735] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU3._CST] (Node f7f69108), AE_NOT_FOUND
[   80.955934] ACPI: SSDT CFE5FC00, 00D8 (r1 HP      CPU4CST        1 INTL 20061109)
[   80.956043] ACPI Error (psargs-0355): [CS03] Namespace lookup failure, AE_NOT_FOUND
[   80.956046] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU4._CST] (Node f7f690c0), AE_NOT_FOUND
[   80.956245] ACPI: SSDT CFE5FD00, 00D8 (r1 HP      CPU5CST        1 INTL 20061109)
[   80.956354] ACPI Error (psargs-0355): [CS03] Namespace lookup failure, AE_NOT_FOUND
[   80.956357] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU5._CST] (Node f7f69078), AE_NOT_FOUND
[   80.956558] ACPI: SSDT CFE5FE00, 00D8 (r1 HP      CPU6CST        1 INTL 20061109)
[   80.956666] ACPI Error (psargs-0355): [CS03] Namespace lookup failure, AE_NOT_FOUND
[   80.956670] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU6._CST] (Node f7f69120), AE_NOT_FOUND
[   80.956870] ACPI: SSDT CFE5FF00, 00D8 (r1 HP      CPU7CST        1 INTL 20061109)
[   80.956978] ACPI Error (psargs-0355): [CS03] Namespace lookup failure, AE_NOT_FOUND
[   80.956982] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU7._CST] (Node f7f690a8), AE_NOT_FOUND
[   80.958005] ACPI: Thermal Zone [THM0] (8 C)
[   81.180045] USB Universal Host Controller Interface driver v3.0
[   81.330147] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   81.768597] eth0: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem f8000000, IRQ 16, node addr 00:1e:0b:ca:ee:a4
[   82.806281] ACPI: PCI Interrupt 0000:01:04.4[B] -> GSI 22 (level, low) -> IRQ 20
[   82.806289] uhci_hcd 0000:01:04.4: UHCI Host Controller
[   82.806305] uhci_hcd 0000:01:04.4: new USB bus registered, assigned bus number 6
[   82.806316] uhci_hcd 0000:01:04.4: port count misdetected? forcing to 2 ports
[   82.807255] uhci_hcd 0000:01:04.4: irq 20, io base 0x00003800
[   82.807557] usb usb6: configuration #1 chosen from 1 choice

---

### Post by ajgreeny on 2008-12-13
I can't help with your error messages, but the random reboots you speak of can be caused by overheating.  Investigate this and you may be able to get past the problem.

---

### Post by Jack Collins on 2008-12-13
Thanks Greeny, 

That was a thought I had too. This is a rack mount server and it does seem a bit hot at some times. Does anybody have any experience or suggestions for detecting thermal issues on an HP DL380 G5 or similar server?

---

