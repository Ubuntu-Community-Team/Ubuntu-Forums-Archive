---
title: "Click a non mounted partition on dock causes system hang"
date: 2023-03-31
forum: Ubuntu Development Version
---

### Post by corradoventu on 2023-03-31
I have 3 drives with different partitions all ext4, Ubuntu desktop is configured to show unmounted volumes.
If I click on a partition listed in the dock nothing happens, if i double-click the system hangs, only mouse arrow moves.
The .crash file seems point to gnome-shell.
This may be an old problem, usually my Ubuntu desktop is configured to NO show unmounted volumes.
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/2013469](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/2013469)

---

### Post by TheFu on 2023-03-31
Oops. I didn't notice this was for the Dev pre-release testing.  Sorry.

Original post follows:

You can kill the offending process by either switching to a different TTY or ssh'ing into the system from a different machine. Your choice.

I've had a similar issue with storage that isn't ready and I'm not using a GUI to access it, just from a normal shell.  I end up killing the terminal window, which kills all child processes.  I use **xkill** to do this, but if your entire GUI is locked up, which I've never seen related to this issue, since I don't use any DE, changing to a different tty and killing the offending process is probably the easiest.  Then switch back to the GUI tty (is that still F7 or F1?).

---

