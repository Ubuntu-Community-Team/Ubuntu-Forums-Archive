---
title: "When to reboot after upgrade?"
date: 2008-11-11
forum: Server Platforms
---

### Post by jmirick on 2008-11-11
I apologize if this is a dimwit question that's answered elsewhere, but I can't find it.

After doing an upgrade, how do I know if the server needs to be rebooted?  If I see "linux-image" in the packages I assume I need to, but other than that, when?  The desktop systems tell me when to do it, but the server doesn't.  I'm never sure if I have to or not, and I don't want to reboot if I don't have to.

---

### Post by Coreigh on 2008-11-11
Is this a server with no GUI or a desktop? On the desktop when you use the update wizard it will tell you it needs a reboot.

As far as I know I have only seen my desktop ask for a reboot when the kernel was updated.

---

### Post by jmirick on 2008-11-11
Yeah, server with no GUI.  Apt-get upgrade just dumps you back at the command line and never says, "please reboot me" or something, yet it must know.

---

### Post by hictio on 2008-11-11
The things is that, usually, most of the time, there is no need to reboot Linux, unless you install a new kernel, and want to use it.
That's leaving aside hardware, of course you have to shutdown to add/ remove RAM :D

So, unless you are installing or upgrading a kernel, there should be no need to actually reboot the server.

Re-start the service that has been upgraded, if any, and check that everything is A Ok!

---

### Post by whitegourd on 2008-11-12
I have the exact same question ...

Hictio, thanks for linking from this thread ...
[http://ubuntuforums.org/showthread.php?t=979913](http://ubuntuforums.org/showthread.php?t=979913)

I'd hate to have to reboot the server even if it is a kernel upgrade.  Right now I'm just relying on the desktop reboot notification to remind me that I may need to reboot the server.

---

### Post by hictio on 2008-11-12
> **whitegourd said:**
> 
I'd hate to have to reboot the server even if it is a kernel upgrade.  Right now I'm just relying on the desktop reboot notification to remind me that I may need to reboot the server.

Me too! I usually, under normal circumstances try to avoid a reboot as much as the plague.
Specially if I don't have physical access to the server I have to reboot.
I don't breathe until I start getting ping replies, or even better, I'm logged in thru SSH again, to the given server.

Part of the game, I guess... "Deal with it. Rock 'n' Roll."

---

### Post by jpeddicord on 2008-11-12
I usually don't reboot unless there was a know kernel vulnerability, which hasn't really happened for a while now. Uptime of 120+ days so far. :D

---

