---
title: "Are Kernel Power Saving Tweaks still needed?"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by donniezazen on 2012-04-06
Hello,

Power management has drastically improved in recent kernel/Ubuntu development. I was wondering if these suggested kernel power saving tweaks are still needed.

GRUB Kernel Line
```
i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 drm.vblankoffdelay=1
```

ALPM
```
echo SATA_ALPM_ENABLE=true | sudo tee /etc/pm/config.d/sata_alpm
```

Reduce Wakeup Events
```
gconftool-2 --type string --set /apps/gnome-terminal/profiles/Default/cursor_blink_mode off
```

[Source]("https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks")

Thanks.

---

### Post by MacUntu on 2012-04-06
> **donniezazen said:**
> ALPM
```
echo SATA_ALPM_ENABLE=true | sudo tee /etc/pm/config.d/sata_alpm
```

Seems to default to false according to /usr/lib/pm-utils/power.d/sata_alpm.

> **donniezazen said:**
> Reduce Wakeup Events
```
gconftool-2 --type string --set /apps/gnome-terminal/profiles/Default/cursor_blink_mode off
```

Still blinking (and I'll keep it that way).

---

