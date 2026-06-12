---
title: "Power settings to power down completely"
date: 2010-06-01
forum: Server Platforms
---

### Post by wesg on 2010-06-01
I want to get my server to work properly because of some upcoming upgrades, but whenever I issue the command ```
sudo shutdown -h now
``` the system halts, but the system is still powered up. 

I've posted here about this before, but what settings do I need to change either in Ubuntu or my BIOS to get this to happen? What does ACPI have to do with this sort of thing?

---

### Post by new_tolinux on 2010-06-01
According to the --help:
-h halt or power off after shutdown
-H halt after shutdown (implies -h)
-P power off after shutdown (implies -h)

According to that the command should be:
```
sudo shutdown -P now
```

---

### Post by disabledaccount on 2010-06-04
I suppose, that ACPI=force on the kernel line is what you need ;)
This is BIOS issue, not system...

---

### Post by Bachstelze on 2010-06-04
> **tomazzi said:**
> I suppose, that ACPI=force on the kernel line is what you need ;)
This is BIOS issue, not system...

You are wrong, new_tolinux gave the correct answer.

---

### Post by disabledaccount on 2010-06-04
> **Bachstelze said:**
> You are wrong, new_tolinux gave the correct answer.Well, you maybe right, but HALT should cause ACPI to power-off the system. Some BIOSes does not understand this, and you will get "system halted" message on the screeen. ACPI=force works well with GUI-shutdown and also with >sudo poweroff

---

### Post by Bachstelze on 2010-06-04
> **tomazzi said:**
> Well, you maybe right, but HALT should cause ACPI to power-off the system.

Yes, this is exactly why [font=monospace]shutdown[/font] normally doesn't power down the system (it just calls [font=monospace]halt[/font]), and you have to give it an additional argument if you want it to. :)

---

