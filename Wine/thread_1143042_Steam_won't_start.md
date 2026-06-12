---
title: "Steam won't start"
date: 2009-04-29
forum: Wine
---

### Post by Questioneer on 2009-04-29
Hello-
I'm trying to run Steam in ubuntu 9.04 with wine-1.0.1. However, when loading steam, the program hangs(never loads) and I get:

```
err:ntdll:RtlpWaitForCriticalSection section 0xafe2bc "?" wait timed out in thread 001e, blocked by 001f, retrying (60 sec)
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
user@user-desktop:~/.wine/drive_c/Program Files/Steam$ Deleting active MRSW lock (0x111db4), expect failure

```

Does anyone know what might be wrong? I can't find a reference to such an error anywhere else.

Thanks.

---

### Post by Bios Element on 2009-04-29
Well I don't know about the error but your WINE Version is way outta date. You need to update it to 1.1.20. I'd also recommend re-installing Steam.

---

### Post by u235sentinel on 2009-04-30
> **Bios Element said:**
> Well I don't know about the error but your WINE Version is way outta date. You need to update it to 1.1.20. I'd also recommend re-installing Steam.

I agree.  I've had issues with 1.0.1 and while it usually worked for me, I had many issues with latency.  Since upgrading to 1.1.20 it seems to be working far better and now I've gone from 30-50 fps to over 200 regularly!

---

