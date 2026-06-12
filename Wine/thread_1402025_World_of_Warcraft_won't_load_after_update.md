---
title: "World of Warcraft won't load after update"
date: 2010-02-08
forum: Wine
---

### Post by xnerdx on 2010-02-08
Hey everyone, I just used update manager to update my ubuntu 9.04 system (Seems that it was upgrading to the latest linux kernel images) and now wine will no longer load world of warcraft. The following is the output when I attempt to run wow.exe from terminal (It ran perfectly fine before I reset my system after the update):
```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  227
  Current serial number in output stream:  227

```

I assume I'm going to have to change my settings to load from the previous kernel images but I don't recall how that is done, any help would be greatly appreciated. Thank you :)

---

### Post by asdfoo on 2010-03-12
> **xnerdx said:**
> Hey everyone, I just used update manager to update my ubuntu 9.04 system (Seems that it was upgrading to the latest linux kernel images) and now wine will no longer load world of warcraft. The following is the output when I attempt to run wow.exe from terminal (It ran perfectly fine before I reset my system after the update):
```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  227
  Current serial number in output stream:  227

```

I assume I'm going to have to change my settings to load from the previous kernel images but I don't recall how that is done, any help would be greatly appreciated. Thank you :)


what's the output of glxinfo?

Maybe your video drivers have changed or need updating?

---

### Post by xnerdx on 2010-03-16
I'm sorry, I just modified the GRUB menu file so that it opens the correct kernel.

---

