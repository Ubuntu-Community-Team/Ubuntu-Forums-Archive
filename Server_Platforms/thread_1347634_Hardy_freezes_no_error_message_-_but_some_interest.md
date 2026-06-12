---
title: "Hardy freezes no error message - but some interesting things in dmesg"
date: 2009-12-06
forum: Server Platforms
---

### Post by tinodj on 2009-12-06
My server freezes randomly. Every 2-3 days. Just freezes, no error message, nothing. I found some interesting details in dmesg:

```


[   74.483125] ACPI: Core revision 20070126
[   74.483181] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   75.153909] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  98, should be 8D [20070126]

[   76.204015] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   76.204018] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   76.204305] Freeing unused kernel memory: 328k freed
[   76.204906] Write protecting the kernel read-only data: 1044k
[   76.368726] fuse init (API version 7.9)
[   76.384961] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
[   76.384974] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
[   76.384986] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
[   76.384996] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]

[  111.213722] i2c-adapter i2c-1: lm85: Detected SMSC chip
[  111.213775] i2c-adapter i2c-1: lm85: Unrecognized version/stepping 0x68 Defaulting to Generic LM85.
[  111.355321] i2c-adapter i2c-1: lm85: Detected SMSC chip
[  111.355385] i2c-adapter i2c-1: lm85: Unrecognized version/stepping 0x68 Defaulting to Generic LM85.


```

I can also provide whole dmesg, or any information needed. I have upgraded bios 6months ago, and I have 2.6.24-24-server kernel. 

Please help me to resolve this problem. It is around for a year :( 

Please suggest anything?! Should I try acpi=off noapic ? Will all of the processors work when using noapic?

Any suggestion is very very very welcomed.

---

