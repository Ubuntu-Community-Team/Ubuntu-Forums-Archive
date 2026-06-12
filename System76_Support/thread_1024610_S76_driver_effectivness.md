---
title: "S76 driver effectivness"
date: 2008-12-29
forum: System76 Support
---

### Post by val67 on 2008-12-29
Hi,

I guess this is directed to S76:

1. Why is that the S76 driver does not provide  a 100 % functional hardware (e.g. HDMI sound, suspend/resume - for some laptops, etc.)

2. Are the fixes from the driver submitted to Canonical, or would the fixes be removed by future updates coming from Ubuntu?

Thanks.
Val.

---

### Post by thomasaaron on 2008-12-29
Hi, Val67.

```
1. Why is that the S76 driver does not provide a 100 % functional hardware (e.g. HDMI sound, suspend/resume - for some laptops, etc.)
```

Most hardware is supported out of the box with Ubuntu. The System76 driver applies model-specific patches for the functionalities that we test for. 

If we find a fix, we will insert it into the driver. If we know a fix will be coming down the pike in a future update, we may or may not insert it into the driver. It really depends on a few things, such as: a) how long it will be until the fix comes down via automatic update, b) how adding project-specific fixes before they are officially integrated into Ubuntu will affect other functionality of the system(s). 

As for the HDMI-sound fix, we only recently learned of it, and R&D is aware of it. I'm not sure what they will decide, but there is testing still to be done with it.

```
2. Are the fixes from the driver submitted to Canonical, or would the fixes be removed by future updates coming from Ubuntu?
```

Yes. We feel it is always better to integrate the fixes into Ubuntu so that more systems are supported out of the box by Ubuntu. There are numerous fixes we have found that have been sent upstream to Canonical.

---

### Post by val67 on 2008-12-30
Thanks Thomas,

So the fact that after 7-8 months there is still no fix for the daru2 suspend problem, does that mean that the R&D team could not do a fix in this timeframe?

Would you mind sharing with the community how large the R&D team at S76 is?

Thanks.

val.

---

