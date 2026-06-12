---
title: "Ubuntu 14.04 Boot - Display/Keyboard Issue"
date: 2014-05-09
forum: Server Platforms
---

### Post by jasonvp on 2014-05-09
Hey folks -

I'd opened a thread about the console locking up during 14.04 Server's boot, thinking it had something to do with plymouth.  I've since closed that thread because it has nothing to do with plymouth (that I can tell).  The basic issue seems to be: if there's an active display and keyboard attached to the server, everything works fine.  If the display is off or unattached, or the keyboard isn't attached, then the boot process never completes on the console.  And by that I mean: it gets as far as enabling the swap space, and then it basically freezes.  The server finishes booting, but the console (tty1) is forever locked up.

I have 2 Ubuntu 14.04 servers sitting next to one another with a KVM device connected to both.  If I boot one of the servers with the KVM device set to display the other server's console, the first server's console locks up during boot.  If I switch back to it with the KVM device, it never recovers.  The first server's console is forever locked up even though it finished the boot process.

I'm not exactly sure what's going on here, but I suspect it has something to do with trying to initialize specific display drivers in the kernel.  That needs to stop in server land.  It's a SERVER, not a workstation.  Stop initializing nVidia, ATI/AMD, or Intel display drivers specifically.  Stop trying to switch over to a graphical or semi-graphical console.  It's.  A.  Server!  The console should be boring 80x24 vt100-style text and nothing more than that.

In /etc/default/grub, I uncommented the line:

```
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console
```

That doesn't appear to make any difference at all.

Any other suggestions?

---

