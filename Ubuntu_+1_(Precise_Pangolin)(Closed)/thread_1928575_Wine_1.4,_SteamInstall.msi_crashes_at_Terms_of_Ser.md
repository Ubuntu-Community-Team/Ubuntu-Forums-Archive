---
title: "Wine 1.4, SteamInstall.msi crashes at Terms of Service (terminal output posted)"
date: 2012-02-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Notselfcreated on 2012-02-20
```

jeff@ubuntu:~/Downloads$ winetricks steam
Executing w_do_call steam
Executing load_steam
Executing mkdir -p /home/jeff/.cache/winetricks/steam
Executing wine msiexec /i SteamInstall.msi
[COLOR="Red"]Wine cannot find the ncurses library (libncurses.so.5).
fixme:storage:create_storagefile Storage share mode not implemented.
wine: Unhandled page fault on write access to 0x000000b4 at address 0x7bc450e6 (thread 0046), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc47aac[/COLOR]
------------------------------------------------------
Note: command 'wine msiexec /i SteamInstall.msi' returned status 5.  Aborting.
------------------------------------------------------

```

Reinstalling libncurses5 doesn't change the behavior at all.

So whatcha think?

---

### Post by dino99 on 2012-02-20
watch winehq steam database

---

