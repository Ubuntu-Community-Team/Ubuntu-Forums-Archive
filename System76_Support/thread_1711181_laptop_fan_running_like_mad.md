---
title: "laptop fan running like mad"
date: 2011-03-20
forum: System76 Support
---

### Post by dstrozzi on 2011-03-20
Hi,

I have a Pengolin Penguin laptop from System76 (panp7).  I re-formatted the system partition, and installed Ubuntu 10.10 from scratch yesterday.  I applied all updates.  The fan runs quit a lot, at what sounds like full throttle, pretty much continuously.  System Monitor says there's very little cpu load.  I went to the bios setup menu on booting, and found no ACPI/APM/power mgmt settings.

Does anyone know how to fix this?

Thanks,
Dave

---

### Post by isantop on 2011-03-21
Hi Dave.

You might want to make sure the ATI proprietary Drivers are installed. If they are, then you probably have a dust bunny in your heat sink.

---

### Post by Flyers2391 on 2011-03-21
> **dstrozzi said:**
> Hi,

I have a Pengolin Penguin laptop from System76 (panp7).  I re-formatted the system partition, and installed Ubuntu 10.10 from scratch yesterday.  I applied all updates.  The fan runs quit a lot, at what sounds like full throttle, pretty much continuously.  System Monitor says there's very little cpu load.  I went to the bios setup menu on booting, and found no ACPI/APM/power mgmt settings.

Does anyone know how to fix this?

Thanks,
Dave

After you re-installed ubuntu, did you also install the System76 driver?  The latest driver is [http://planet76.com/repositories/system76-driver-2.6.1.deb](http://planet76.com/repositories/system76-driver-2.6.1.deb) from [http://planet76.com/repositories/](http://planet76.com/repositories/)

---

### Post by dstrozzi on 2011-03-22
Hi isantop,

I did not have the ATI driver activated.  That solves the problem!  You are a prince among men!

---

