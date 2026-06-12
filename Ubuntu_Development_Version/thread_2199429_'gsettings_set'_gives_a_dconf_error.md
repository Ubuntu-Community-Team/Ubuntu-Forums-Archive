---
title: "'gsettings set' gives a dconf error"
date: 2014-01-13
forum: Ubuntu Development Version
---

### Post by rocky-oceans on 2014-01-13
gsettings set does not work for me, although gsettings get does:

```
$ gsettings set com.canonical.desktop.interface scrollbar-mode normal


(process:1978): dconf-WARNING **: failed to commit changes to dconf: Error spawning command line 'dbus-launch --autolaunch=bd07bc954bc88022a6a923fa52d13618 --binary-syntax --close-stderr': Child process exited with code 1

$ gsettings get com.canonical.desktop.interface scrollbar-mode
'overlay-auto'


```

I'm on Ubuntu 14.04 (installed the 11 Jan daily build and it is now updated to today). 64-bit.

---

### Post by rocky-oceans on 2014-01-14
This happens to me on 13.10 also. It happens when you do it through ssh. I thought the difference was 13.10 vs 14.04 but the difference was I was doing one through ssh and the other on the comp itself. Still puzzled why it happens but in any case it's not a 14.04 issue.

---

### Post by steeldriver on 2014-01-14
I think it happens because the DBUS_SESSION_BUS_ADDRESS is not available in an SSH session - I haven't tried 14.04 yet, but in previous releases it seems to be sufficient to set the DISPLAY variable to the appropriate value for your desktop session e.g.

```
**DISPLAY=:0** gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

You could explicitly set DBUS_SESSION_BUS_ADDRESS but it's harder to get ahold of

---

### Post by rocky-oceans on 2014-01-15
Thanks, steeldriver. That does indeed solve it! (it does work on 14.04). Now this thread really is "SOLVED" :)

Any idea how to always have DISPLAY set to :0 when I ssh anywhere?

---

