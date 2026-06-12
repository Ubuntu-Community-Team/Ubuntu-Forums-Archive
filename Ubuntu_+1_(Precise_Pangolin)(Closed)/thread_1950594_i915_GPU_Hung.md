---
title: "i915 GPU Hung"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lucazade on 2012-04-01
When using some java applications, like Oracle SQL developer, I get a GPU hang.. for some seconds the screen becomes black and unresponsive then it comes back to life.

This issue was not present in Oneiric so it seems a regression.

The laptop is a Dell L702X with an integrated Intel GPU..
this is the lcpci:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
 Subsystem: Dell Device 0571
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
 Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0
 Interrupt: pin A routed to IRQ 52
 Region 0: Memory at f2400000 (64-bit, non-prefetchable) [size=4M]
 Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
 Region 4: I/O ports at 5000 [size=64]
 Expansion ROM at <unassigned> [disabled]
 Capabilities: <access denied>
 Kernel driver in use: i915
 Kernel modules: i915

and this is the error found in dmesg after the hangup:

[ 4889.687609] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
[ 4889.687669] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
[ 4889.699461] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 332264 at 332261, next 332265)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/970596](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/970596)

---

### Post by dino99 on 2012-04-01
> **lucazade said:**
>  [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
[ 4889.687669] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
[ 4889.699461] [drm:i915_wait_request] *ERROR* i915_wait_request returns -11 (awaiting 332264 at 332261, next 332265)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/970596](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/970596)

here i see two things:
- drm
- look for more information in /debug/dri/0/i915_error_state

so the system wait for the drm event, explaining the little freeze : is that a path issue, or a setting to tweak ?
maybe the java log have some info too.

---

### Post by lucazade on 2012-04-01
> **dino99 said:**
> here i see two things:
- drm
- look for more information in /debug/dri/0/i915_error_state

so the system wait for the drm event, explaining the little freeze : is that a path issue, or a setting to tweak ?
maybe the java log have some info too.

there is no /debug/.. directory so I don't know where to look for it :)

tried also to reset settings for the java app and to upgrade jre from 6 to 7 but w/o luck.
starting the app from terminal also doesn't show any error or warning.. mmh :/

---

