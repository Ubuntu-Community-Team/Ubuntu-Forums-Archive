---
title: "Hardy ltsp/x11vnc with LDM_DIRECTX=True help needed!"
date: 2008-06-07
forum: Server Platforms
---

### Post by geograf on 2008-06-07
Because no one has found my postig at [http://ubuntuforums.org/showthread.php?p=4971244#post4971244](http://ubuntuforums.org/showthread.php?p=4971244#post4971244), I  post it here again:

LTSP/x11vnc -Problem:

The procedure described in [https://wiki.edubuntu.org/InstallX11VncOnLtspClients](https://wiki.edubuntu.org/InstallX11VncOnLtspClients)
works also in Hardy!

BUT: When set LDM_DIRECTX=True in lts.conf, x11vnc doesnt work anymore!

Witch options for x11vnc are neccessary in this case?

---

### Post by krunge on 2008-06-09
> **geograf said:**
> Because no one has found my postig at [http://ubuntuforums.org/showthread.php?p=4971244#post4971244](http://ubuntuforums.org/showthread.php?p=4971244#post4971244), I  post it here again:

LTSP/x11vnc -Problem:

The procedure described in [https://wiki.edubuntu.org/InstallX11VncOnLtspClients](https://wiki.edubuntu.org/InstallX11VncOnLtspClients)
works also in Hardy!

BUT: When set LDM_DIRECTX=True in lts.conf, x11vnc doesnt work anymore!


My guess is somehow LDM_DIRECTX=True changes the environment variable $DISPLAY (x11vnc -display option) and/or the environment variable $XAUTHORITY (x11vnc -auth option) in ways that it stops working. Maybe the script that starts x11vnc needs to be informed of the changes needed for these environment variables.

---

