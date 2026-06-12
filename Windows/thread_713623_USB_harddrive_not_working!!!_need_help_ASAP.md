---
title: "USB harddrive not working!!! need help ASAP"
date: 2008-03-02
forum: Windows
---

### Post by M!K3_$ on 2008-03-02
ok i have had this USB external hard drive for about 4 months now, it has worked great, untill yesterday

i booted up XP and it wouldnt even let me get to the login unless the harddrive was turned off.
and if i tried to turn it on after i was logged in, explorer.exe would crash and my computer would freeze


i kno this isnt a hardware issue because it works in ubnutu, just not windows

help please
mike

---

### Post by amingv on 2008-03-02
Have you installed any program/hardware that may conflict with it?

If you need to get a file ASAP from it, try plugging it in failsafe mode. Also, try turning autostart off for that device.

---

### Post by M!K3_$ on 2008-03-02
nothing should conflict with it, it just randomly stoped working lastnight...

how do i turn off autostart for it?

maybe i should run a virus scan over it. can i run a virus scan that detects windows viruses from ubuntu?

---

### Post by amingv on 2008-03-02
If it mounts on failsafe, go to MyPC, right click on drive letter, properties, autostart (or autoplay, I don't remember quite clearly). If it's set to open up a certain program, change it to take no action. If it mounts on failsafe, you might also like to try to check the disk for errors:
Start>run>cmd.exe

```
chkdsk <drive_letter> /f
```

If you want to do a virus scan, you can use ClamAV on Ubuntu.

---

