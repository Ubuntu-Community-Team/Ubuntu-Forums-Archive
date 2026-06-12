---
title: "Pangolin internal keyboard cannot be used to wake from suspend"
date: 2022-01-08
forum: System76 Support
---

### Post by &amp;KyT$0P# on 2022-01-08
System76 Pangolin (pang11) running Xubuntu 21.10.  When it's suspended, there are only two ways I can wake it up:

1) Opening the lid.

2) "Medium-pressing" the power button - not short pressing, not long-pressing like to force-poweroff, but something in between.

I would like to also be able to wake it with the internal keyboard.

I know this type of issue is usually solved using [FONT=Courier New]acpitool[/FONT], but in this case I can't figure out which listing is the internal keyboard, or if it's even listed at all? -
```
$ acpitool -w
   Device       S-state   Status   Sysfs node
  ---------------------------------------
  1. GPP0         S4    *disabled
  2. GPP1         S4    *disabled
  3. GPP2         S4    *enabled   pci:0000:00:01.3
  4. WWAN         S3    *disabled  pci:0000:01:00.0
  5.            *disabled  platform:rtsx_pci_sdmmc.0
  6. O2CR         S3    *disabled
  7. GPP3         S4    *enabled   pci:0000:00:02.1
  8. RTL8         S4    *disabled  pci:0000:02:00.0
  9. GPP4         S4    *enabled   pci:0000:00:02.2
  10. GPP5        S4    *disabled
  11. GP17        S4    *enabled   pci:0000:00:08.1
  12. XHC0        S4    *enabled   pci:0000:05:00.3
  13. XHC1        S4    *enabled   pci:0000:05:00.4
  14. GP19        S4    *disabled
  15. SLPB        S3    *enabled   platform:PNP0C0E:00
  16. LID0        S3    *enabled   platform:PNP0C0D:00

```

Same behavior occurs in a live USB of Pop!_OS 21.10, so this isn't caused by something I've done to the OS.  I did not see any EFI settings related to this, nor did I change any EFI settings on this machine.

External keyboard can wake it from suspend.  But that is not physically portable enough to be a viable workaround.

How to enable using the internal keyboard to wake this computer from suspend?  Or has it been intentionally disabled by System76 because there are issues with that?

---

### Post by &amp;KyT$0P# on 2022-01-10
How safe is it to trial-and-error enable all the disabled wakeup devices (except possibly that weird blank #5) to confirm for sure whether any of those are the keyboard?

---

### Post by &amp;KyT$0P# on 2022-01-11
> **halogen2 said:**
> How safe is it to trial-and-error enable all the disabled wakeup devices (except possibly that weird blank #5) to confirm for sure whether any of those are the keyboard?

Ok, tried to enable all disabled wakeup devices in a live USB environment and found two things:

1) Not all the disabled wakeup devices can be enabled - some of them continue to show as disabled regardless of toggling with acpitool.

2) None of the wakeup devices that can be enabled at the OS level are the keyboard.

Now I'm thinking this looks deeper than OS level issue, in which case I should contact System76 rather than ask here.  Sorry if this took anyone's time here.

---

### Post by &amp;KyT$0P# on 2022-01-14
> **halogen2 said:**
> should contact System76

Done and solved.  The internal keyboard DOES wake the machine from suspend, this just requires specifically pressing Fn+F12 (the crescent moon logo key).  Thanks to System76 for the solution! :KS

---

