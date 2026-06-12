---
title: "Ubuntu 9.10 host has vmplayer/X problems"
date: 2009-11-30
forum: Virtualisation
---

### Post by Zetten on 2009-11-30
Hi,

I've posted this thread over at the [VMware forum]("http://communities.vmware.com/message/1427176#1427176"), but I figured it can't hurt to try here as well.

I'm running VMplayer 3.0.0 instances on an Ubuntu 9.10 host, with SLES9 and XP guests. XP runs fine, but I don't really tax it. I use SLES to run a few quite intensive applications, and this seems to be causing me problems.

Basically, VMplayer crashes and it seems to take X on the host (or parts of it) with it. The problem first manifested as a complete freeze - no display updates or keyboard or mouse action on the guest or the host. Had to do a hard reset to get back. I think the system itself was still running, as there's occasional HDD access, which is what made me think of a problem with X. This happened a few times, then seemed to move into the next phase of the error (not sure what triggered the change).

It also sometimes just crashed VMplayer itself, flashing up an error message about an unrecoverable error before killing itself completely. The host system was still usable after this sort of crash, but with keyboard problems as described below. This happened a few times as well.

After reinstalling VMplayer 3.0.0 the problems have persisted, but not in quite so severe a way. The error message now remains after the crash, so it looks like it's slightly more stable. However, keyboard input on the host is affected - modifier keys don't work, including Shift, Ctrl and Caps Lock - and the only way to recover is to restart X by logging out and in again. This is the only problem I'm having at the moment.

One result I found while googling suggested updating video drivers, so I've tried that with no effect. The problem also persists with vmplayer 2.5.3 (the log excerpt below is from 2.5.3, there's a sample 3.0.0 crash log on the VMware forum), so I've kept 3.0.0 installed for now.

As I say, it seems to be related to load on the guest machine - the harder I push it the more likely it crashes. Could it be a CPU error or something?

Note: this is a different log excerpt from that posted on the VMware forum. This particular crash was from vmplayer 2.5.3, and resulted in a complete dropout of vmplayer with no error message (or a briefly flashed error), resulting in wonky keyboard input on the host; i.e. the second type of error.

```
Nov 30 12:51:34.455: mks| Panic: dropping lock (was bug 49968)
Nov 30 12:51:34.455: mks| Unexpected signal: 6.
Nov 30 12:51:34.455: mks| Core dump limit is 0 KB.
Nov 30 12:51:34.459: mks| Child process 14186 failed to dump core (status 0x6).
Nov 30 12:51:34.459: mks| Backtrace:
Nov 30 12:51:34.459: mks| Backtrace[0] 0xb4305148 eip 0x80545a0
<snip>
Nov 30 12:51:34.459: mks| Backtrace[16] 00000000 eip 0x2f77ee
Nov 30 12:51:34.459: mks| SymBacktrace[0] 0xb4305148 eip 0x80545a0 in function (null) in object /usr/lib/vmware/bin/vmware-vmx loaded at 0x8048000
<snip>
Nov 30 12:51:34.460: mks| SymBacktrace[16] 00000000 eip 0x2f77ee in function clone in object /lib/tls/i686/cmov/libc.so.6 loaded at 0x22b000
Nov 30 12:51:34.466: mks| Msg_Post: Error
Nov 30 12:51:34.466: mks| [msg.log.error.unrecoverable] VMware Player unrecoverable error: (mks)
Nov 30 12:51:34.466: mks| Unexpected signal: 6.
Nov 30 12:51:34.466: mks| [msg.panic.haveLog] A log file is available in "/vmware/SLES9/vmware.log".  [msg.panic.requestSupport.withLog] Please request support and include the contents of the log file.  [msg.panic.requestSupport.vmSupport.windowsOrLinux.player]
Nov 30 12:51:34.466: mks| To collect data to submit to VMware support, run "vm-support".
Nov 30 12:51:34.466: mks| [msg.panic.response] We will respond on the basis of your support entitlement.
Nov 30 12:51:34.466: mks| ----------------------------------------
Nov 30 12:51:34.757: mks| XINFO IO fatal error. Exiting ...
Nov 30 12:51:34.757: mks| Detaching from window system.
Nov 30 12:51:34.838: mks| XINFO: Reserved fds 133 and 349 for X connection

```

I'm running out of ideas here, so any suggestions will be useful.

If you want a crash log from a 3.0.0 instance, I'm sure I'll have one soon :P

---

### Post by hinto on 2009-12-18
I don't have the answer, but I have the same problem.  Did you find an answer? -Hinto

---

### Post by Zetten on 2009-12-18
I'm afraid not. I was forced back to a native SLES9 machine because I just couldn't get any work done in the virtual installation.

I suspect, although it's really just a gut feeling with no proof, that the problem lies with the VMware 3.0.0 modules and their compatibility with the Ubuntu kernel. If that is the case, you just need to wait for VMware to release a new version of the player (or their kernel modules).

I'm pretty much stuck with my crappy SLES9 installation now, but if you get a chance you could try some other virtualisation software. Sun VirtualBox is supposed to be able to use/convert VMware machines, and is also free, so that would be my starting point. Let me know if vbox works any better, since I'd still like to get back to a more recent host OS.

---

### Post by hinto on 2009-12-18
I'm trying VirtualBox right now (VMWare are you listening?). The funny thing is that I haven't had any problems on an Intel core2 quad/XP64 or an AMD dual core Athlon/XP.  I'm having problems with the AMD Phenom X4/XP.  Could be cpu chip, could be nvidia... -H

---

### Post by fjgaude on 2009-12-18
These kinds of errors, crashes are tough to trace... likely could be a memory, RAM issue... bad RAM causes all kinds of errors like this.

How much RAM is allocated to the Player and each VM?

---

### Post by hinto on 2009-12-18
On the PC that crashes 1 or 2 gigs out of 6 will produce the crash. There have never been any crashes with VirtualBox.

---

### Post by fjgaude on 2009-12-18
Why then are you using VMware Player?

---

### Post by hinto on 2009-12-18
I originally had vmx/vmdks...  Also VMWare had better/easier bluetooth support _and_ Bridged Networking.  VirtualBox was a little behind the times.  -Hinto

---

