---
title: "Set hardware clock to local time at shutdown?"
date: 2016-04-10
forum: Ubuntu Development Version
---

### Post by sgage on 2016-04-10
It seems as though the default behavior in Ubuntu has changed with Xenial back to saving the system clock to the hardware clock as UTC at shutdown. This obviously causes problems when dual-booting with Windows 7, which expects the hwclock to be local time. Surely there is a way to get Ubuntu to save the time as local, as of old. The gambit of putting UTC=no in /etc/defaults/rcS no longer has any effect. 

I have searched and searched, but can not find any recent info on this. Does anyone here know the secret?

TIA...

---

### Post by sgage on 2016-04-10
This seems to do it:

```
sudo hwclock --systohc --localtime
```

I thought I had tried it earlier, and found it not to persist across boots, but it seems that it does.

---

### Post by VMC on 2016-04-10
> **sgage said:**
> This seems to do it:

```
sudo hwclock --systohc --localtime
```

I thought I had tried it earlier, and found it not to persist across boots, but it seems that it does.

That has the same effect as ```
timedatectl set-local-rtc 0
```

If you issue ```
timedatectl
```, you'll see it 'complains' about daylight time settings.

---

