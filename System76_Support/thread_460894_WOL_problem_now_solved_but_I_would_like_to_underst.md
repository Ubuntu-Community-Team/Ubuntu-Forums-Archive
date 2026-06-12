---
title: "WOL problem now solved but I would like to understand it"
date: 2007-06-01
forum: System76 Support
---

### Post by blackhole54 on 2007-06-01
I am running a Ratel headless, **ssh**ing in from another computer.  I had configured the BIOS for Wake-On-LAN.   And using **ether-wake** from another computer, the Ratel turned on as expected ... the first time.  Then WOL refused to work again until after I had unplugged the computer, allowing *plenty* of time for things to discharge, and then plugged it back in again. And again, it would work  *once*.

*ethtool* revealed that WOL was disabled.  Adding the line

```

ethtool -s eth0 wol g

```

in */etc/rc.local* seems to have taken care of the problem.

My question is why this is even necessary when the BIOS is set to enable WOL.  Is there something in the boot sequence that is disabling this?

---

### Post by flamacue on 2007-06-06
(FYI, esp. for other readers:  more detailed HOWTO here: [http://ubuntuforums.org/showthread.php?t=360901]("http://ubuntuforums.org/showthread.php?t=360901").)

To answer your question regarding why this is necessary...  As I understand it, enabling WOL in the BIOS is a prerequesite (obviously), but doesn't do the whole job, as the NIC driver can control the state in which the NIC shuts down, i.e. WOL can be disabled in software--which is the default in Ubuntu (or perhaps the driver itself?).  The solution you found uses ethtool to change that software setting from the default (disabled) to enabled every time the system starts up.

Make sense?

---

### Post by blackhole54 on 2007-06-08
Thanks for the reply and the link.   I noticed that the how-to used the same solution in */etc/rc.local* that I had come up with.  It just seems strange that something in the boot sequence (perhaps the initial loading of the driver?) alters the state the BIOS originally put it in.  After all, the BIOS does put it into an enabled state when the board is first powered up (computer is plugged in).  Maybe sometime when I feel like hooking a montitor up to it (so I can change BIOS settings) I will see if the BIOS setting is even required at all.

---

### Post by blackhole54 on 2007-06-16
I finally got around to running some tests.

First, to get anything to happen with WOL, it *does* have to be enabled in the BIOS as *flamacue* predicted.  Second, *flamacue*'s post (thanks) jarred my brain  into realizing I could test whether or not it is the driver itself that is causing the change of state.  As it turns out, simply loading the driver causes WOL to get disabled:

```

root@ratel:~# ethtool eth0 | grep Wake
        Supports Wake-on: pumbg
        Wake-on: g
root@ratel:~# modprobe -r via_rhine; modprobe via_rhine
root@ratel:~# ethtool eth0 | grep Wake
        Supports Wake-on: pumbg
        Wake-on: d

```

(I suppose it could be *unloading* the driver that resets things, but there is no way to test the state with the driver unloaded.)  It still seems strange to me the driver wouldn't just leave the setting alone.  I can find no config file that might dictate this behavior.

---

### Post by flamacue on 2007-08-17
> **blackhole54 said:**
> (I suppose it could be *unloading* the driver that resets things, but there is no way to test the state with the driver unloaded.)
I doubt it.  Doesn't the driver get unloaded when the computer shuts down?  If so, and if the unloading were disabling WOL, then you'd be disabling it on shutdown...
> It still seems strange to me the driver wouldn't just leave the setting alone.  I can find no config file that might dictate this behavior.
I'd imagine it's just a matter of starting up (the driver, the interface, etc.) in a known state.

---

### Post by blackhole54 on 2007-08-19
> **flamacue said:**
> Doesn't the driver get unloaded when the computer shuts down?

I'd never really thought about it until now.  I don't remember ever seeing anything about it looking through the init scripts.  The interfaces get shut down, but unless doing that or unless the **shutdown** command itself unloads modules, I don't think modules do get unloaded.  But I agree that resetting WOL  is more likely to happen at load than unload.  I was just pointing out that my test didn't positively establish that.

Thanks for your posts.

---

