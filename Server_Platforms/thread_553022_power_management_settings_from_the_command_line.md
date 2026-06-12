---
title: "power management settings from the command line"
date: 2007-09-17
forum: Server Platforms
---

### Post by Micha401 on 2007-09-17
Hi,
I'm using 6.06 sever without desktop. Is there a possibility to set power saving settings via the command line? My server should never go to any sleep state.
Thanks,

---

### Post by bentheo on 2007-10-06
I'm setting up a server install, and I was wondering this same question. Is there a way to configure power with just command line access?

---

### Post by netlogic on 2007-10-06
I'm a pretty sure there is an easier and more elegant way, but I just did it from the grub. i put acpi=off and removed apmd.

---

