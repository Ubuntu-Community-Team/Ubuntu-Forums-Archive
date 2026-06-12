---
title: "ACPI errors in dmesg"
date: 2013-04-28
forum: System76 Support
---

### Post by elboulangero on 2013-04-28
Hi,

I'm the happy owner of a gazelle profesionnal (gazp7).

The laptop works great, but I have some problems with a USB soundcard. By trying to understand what's wrong with it, I had to look closely to the boot logs from the kernel, just to see if anything is working properly. And I stumbled on this numerous ACPI errors.
So, this thread is not about the USB soundcard, but about the ACPI errors I discovered in the kernel logs.

I don't use Ubuntu usually, but I tried to boot an Ubuntu 13.04 image, just to compare the logs. It happens that I see the same errors with Ubuntu so I think it's relevant to post in this forum.

The logs I'm talking about are the following ones:
```

ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

```

Does anybody know what it really means ? Anything serious behind this ?

Do you think that upgrading the BIOS could change anything ? Do you know where I can find the latest BIOS for this laptop ? And how I'm supposed to upgrade it ?

Thanks a lot for your replies

---

### Post by isantop on 2013-04-29
Unless you're seeing problems or the messages are filling half of the log, I wouldn't worry about them.

We typically don't issue BIOS updates. They aren't necessary with Ubuntu.

---

### Post by Toz on 2013-04-29
[This]("https://bugzilla.kernel.org/show_bug.cgi?id=48811") might be of interest.

> Agreed, these log messages can be bothersome, and given the number of complains
we already received about them, we certainly should do something to improve the
wording, but this is a general issue with ACPI resource conflict reporting, not
specific to gpio-ich.

---

### Post by bonzini on 2013-04-30
For what it's worth, I get this same message on my gazelle and on my daughters' Dell Inspiron 14z laptops.  I guess it's a pretty generic message.  Still it would be nice to fix the problem (if possible).

---

