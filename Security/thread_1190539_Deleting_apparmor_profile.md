---
title: "Deleting apparmor profile"
date: 2009-06-18
forum: Security
---

### Post by Barriehie on 2009-06-18
I was editing a profile and now i've got usr.bin.opera~ in my /etc/apparmor.d/ directory.  I tried deleting it but it's still being skipped and still there!  Aside from disabling profiles how can you actually delete / remove them from the apparmor application???

Many thanks,
Barrie

---

### Post by rookcifer on 2009-06-18
> **Barriehie said:**
> I was editing a profile and now i've got usr.bin.opera~ in my /etc/apparmor.d/ directory.  I tried deleting it but it's still being skipped and still there!  Aside from disabling profiles how can you actually delete / remove them from the apparmor application???

Many thanks,
Barrie

The "~" indicates the file is a backup.  You just delete it like any other file.

```
cd /etc/apparmor.d

sudo rm usr.bin.opera~
```

Restart AppArmor when done.

---

### Post by Barriehie on 2009-06-18
Thank you rookcifer!  I'm pretty sure I tried that but it appears to have worked this time.

Barrie

---

### Post by samiux on 2009-06-18
> **Barriehie said:**
> I was editing a profile and now i've got usr.bin.opera~ in my /etc/apparmor.d/ directory.  I tried deleting it but it's still being skipped and still there!  Aside from disabling profiles how can you actually delete / remove them from the apparmor application???

Many thanks,
Barrie


Try to disable the profile before deleting it.

[https://help.ubuntu.com/community/AppArmor]("https://help.ubuntu.com/community/AppArmor")

---

