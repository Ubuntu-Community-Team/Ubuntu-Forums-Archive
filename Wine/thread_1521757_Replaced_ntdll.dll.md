---
title: "Replaced ntdll.dll"
date: 2010-07-01
forum: Wine
---

### Post by sarthorks on 2010-07-01
How do i find out if i have the wrong ntdll.dll in my system32 folder? I think i may have replaced the original one with some-other downloaded from the net.
I'm on Ubuntu 10.04 using wine-1.2-rc4.

---

### Post by asdfoo on 2010-07-02
> **sarthorks said:**
> How do i find out if i have the wrong ntdll.dll in my system32 folder? I think i may have replaced the original one with some-other downloaded from the net.
I'm on Ubuntu 10.04 using wine-1.2-rc4.

you can delete it, things should still work, the file is normally just a place holder.

If you want, you can create a new prefix and then copy the fake dll from there to your existing one.

---

### Post by hikaricore on 2010-07-02
There was a thread about this exact topic the other day.
You really don't want to replace that particular dll file, infact if i recall WINE will not let you.

---

