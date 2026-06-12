---
title: "USB Dongles"
date: 2009-12-20
forum: Wine
---

### Post by -Ender on 2009-12-20
I've searched the forums and I didn't really find any solutions. I've found a couple of posts where the author stated that they found a solution but then didn't elaborate on what it was. 

Wine version: 1.1.35
Hardware issue: Sentinel SuperPro Dongle
Wine configuration: All defaults
Library overrides: none
Audio: OSS
Graphics: All defaults
Other wine applications: none

So then, here's my issue:
I'm running a piece of software that requires a Sentinel SuperPro dongle in order to function, but the software (Lightwave 9.6) reports that the device cannot be seen. Ubuntu sees the dongle (according to dmesg output), but the application within WINE cannot. I know that the application is functional since I can run it in demo mode, and it checks out on the WINE AppDB. However, on the AppDB, the tester posted that he simply installed the Sentinel drivers and it worked. I have tried that and Lightwave still cannot see the dongle. Any suggestions on what I should try (I'm a noob with WINE and pretty new to Linux in general)?

Another note that may be interesting: If I load Windows 7 in VirtualBox, it also cannot see the dongle.

---

### Post by -Ender on 2009-12-22
I'm trying to build Wine and add support for USB devices into it, but I'm not having much luck. I'm downloading the patches and am attempting to apply them, but the application fails with the following error:

```
git am *.txt
Applying: Add support of native Windows drivers for USB tokens.
error: patch failed: dlls/ntoskrnl.exe/ntoskrnl.exe.spec:551
error: dlls/ntoskrnl.exe/ntoskrnl.exe.spec: patch does not apply
error: patch failed: include/cfgmgr32.h:97
error: include/cfgmgr32.h: patch does not apply
error: patch failed: include/ddk/usb.h:82
error: include/ddk/usb.h: patch does not apply
error: patch failed: include/ddk/wdm.h:1041
error: include/ddk/wdm.h: patch does not apply
error: patch failed: server/protocol.def:3194
error: server/protocol.def: patch does not apply
error: patch failed: tools/wine.inf.in:2531
error: tools/wine.inf.in: patch does not apply
Patch failed at 0001 Add support of native Windows drivers for USB tokens.
When you have resolved this problem run "git am --resolved".
If you would prefer to skip this patch, instead run "git am --skip".
To restore the original branch and stop patching run "git am --abort".

```

Any advice?

---

### Post by hikaricore on 2009-12-23
I really don't think you're going to have much luck with this.
Have you checked the wine appdb for any possible workarounds for your software title?

Most likely you will need to dual boot to use Lightwave, I suggest trying an alternative such as Blender for your 3D work.

---

### Post by -Ender on 2009-12-23
There are rpms for the sentinel drivers, but apparently just running alien on them isn't enough to make them compatible with Ubuntu (though none of posts on the AppDB state that they needed them). I'm trying to work through pieces of it to see if I can manually make it work, but I'm not having a lot of luck.
On the Wine AppDB, there are two recent posts (one on Ubuntu 8.10, with Wine 1.1.19, the other on Mandriva 2009 with Wine 1.1.25) claiming that the Sentinel drivers installed and were functional. So apparently it CAN work, there's just some additional work needed for my particular install.

---

