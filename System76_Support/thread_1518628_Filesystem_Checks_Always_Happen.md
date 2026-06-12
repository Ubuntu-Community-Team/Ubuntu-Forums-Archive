---
title: "Filesystem Checks Always Happen"
date: 2010-06-26
forum: System76 Support
---

### Post by pnjabi on 2010-06-26
Hello - Everytime I start my system the filesystem checks happen. They go all the way to 100 before the system boots. Sometimes I hit ESC, but don't know if there is any problem with the filesystem.

Any ideas why this is happening? Thank You.

System Config:
Meerkat Nettop
Ubuntu 9.10

---

### Post by MorphWVUtuba on 2010-06-27
Dunno if it could be the same cause, but my old 800MHz server on my desk does this because the CMOS battery is dead.

---

### Post by riseringseeker on 2010-06-27
> **pnjabi said:**
> Hello - Everytime I start my system the filesystem checks happen. They go all the way to 100 before the system boots. Sometimes I hit ESC, but don't know if there is any problem with the filesystem.

Any ideas why this is happening? Thank You.

System Config:
Meerkat Nettop
Ubuntu 9.10

You might try running this:

```
sudo tune2fs -c XX /dev/sda1
```

Where XX = the number of times between file checks, and /dev/ points to the proper drive(s).  

See man tune2fs for more info.

---

### Post by pnjabi on 2010-06-28
I also posted another problem where my computer is not shutting down. I have to hold the power button for 10 seconds for it to shutdown. Can these two issues be related? Is the filesystem bad?

---

### Post by isantop on 2010-06-28
I believe it is checking the filesystem each boot because it thinks it was not unmounted correctly. If we fix that problem, I suspect that the others will also disappear.

---

