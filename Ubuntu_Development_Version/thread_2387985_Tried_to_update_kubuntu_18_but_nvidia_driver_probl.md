---
title: "Tried to update kubuntu 18 but nvidia driver problems"
date: 2018-03-26
forum: Ubuntu Development Version
---

### Post by jorritTyb on 2018-03-26
Hi, I just tried to update my system. There were 900 packages to be updated so I started this. After that evertyhing seemed ok but then I restarted my system and I can no longer select the recommended nvidia driver (390). It always switches back to the XOrg default.

The update manager crashes when I try it now. I then switched to commandline and try to purge and reinstall the nvidia driver but this gives me errors like this:

```

dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'

```

sudo apt --fix-broken install gives same error

What can I do to restore the nvidia driver? Thanks

---

### Post by SeijiSensei on 2018-03-27
I'm waiting until the release date.

---

### Post by cariboo on 2018-03-27
Duplicate thread. Closed.

---

