---
title: "FP10 + FFADO aren't working"
date: 2008-07-06
forum: Ubuntu Studio
---

### Post by wurdien on 2008-07-06
Hi,

I bought FP10 some time ago. I didn't get it working with freebob (crashed after few seconds/minutes), so I tried ffado.

Sometimes this works very well. However, sometimes I am not able to get any sound out. I can see all inputs and outputs, gscanbus detects which device is plugged and I can even get audio signal in and record it. But no audio out. Hardware monitoring always works well.

The state of that thing (can I get audio out or not) can change when starting jack, but never while jack is running. Also, it seems that there is no such problem with alsa and PCI-soundcard.

---

### Post by Stochastic on 2008-07-07
FFADO is still in beta and doesn't officially support presonus products, my firepod is working great with FFADObeta6, but I was also lucky with freebob supporting my card with only minor issues.

I'd suggest filing a bug report on launchpad, or the ffado developers mailing list.  You'll probably get some more enlightening advice there.

---

### Post by wurdien on 2008-07-07
Is your audio interface firepod or fp10? I think there's some difference in their firmwares. I don't know if the new firmware could cause there problems.

When trying to use freebob, it just stops after few seconds with errors "zombified - calling shutdown handler" or something similar.

---

