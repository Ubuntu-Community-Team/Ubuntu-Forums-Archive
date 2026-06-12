---
title: "VM Crashing on start"
date: 2011-09-24
forum: Virtualisation
---

### Post by FLCL on 2011-09-24
When I attempt to launch my Windows XP VM it immediately crashes after initialization. By that I mean I see a black box pop up for a split second and then am presented with this error code:

```
Result Code:
NS_ERROR_CALL_FAILED (0x800706BE)
Component:
ProgressProxy
Interface:
IProgress {a163c98f-8635-4aa8-b770-a9941737f3ef}
``` 

I have tried uninstalling and reinstalling, disabling usb,audio. Running the latest version of virtualbox 4.1.2 and my other VM launches without issue. Can anybody help?

---

### Post by Dangertux on 2011-09-24
Sounds like possibly a corrupt snapshot, or possibly even a corrupt VM. 

You can try deleting your state file (from snapshots) , and reloading. Although if this isn't the issue can possibly permanently hose your VM.

---

### Post by FLCL on 2011-09-24
Well, it looks like I don't have any snapshot unfortunately..
I was looking through the log file and it looked like it was having a version mismatch on something but even when I downgraded to that version (4.0.10) Edit** there is no longer a mismatch but it still refuses to boot. It just immediately aborts and isn't giving me an error code anymore.

```
VirtualBox 4.1.2 r73507 linux.x86 (Aug 15 2011 13:23:47) release log
00:00:00.750 Log opened 2011-09-25T03:00:15.759259000Z
00:00:00.750 OS Product: Linux
00:00:00.750 OS Release: 2.6.35-30-generic-pae
00:00:00.750 OS Version: #56-Ubuntu SMP Mon Jul 11 21:51:12 UTC 2011
00:00:00.750 DMI Product Name: N61Jq
00:00:00.750 DMI Product Version: 1.0       
00:00:00.752 Host RAM: 3945MB RAM, available: 3566MB
00:00:00.752 Executable: /usr/lib/virtualbox/VirtualBox
00:00:00.752 Process ID: 15796
00:00:00.752 Package type: LINUX_32BITS_UBUNTU_10_10
00:00:00.921 Installed Extension Packs:
00:00:00.921   Oracle VM VirtualBox Extension Pack (Version: 4.0.10 r72436; VRDE Module: VBoxVRDP unusable because of 'VBoxExtPackRegister returned VERR_VERSION_MISMATCH, pReg=00000000 ErrInfo='VirtualBox version mismatch - expected 4.0 got 4.1'')
00:00:00.932 SUP: Loaded VMMR0.r0 (/usr/lib/virtualbox/VMMR0.r0) at 0xf9e20020 - ModuleInit at 00000000f9e36de0 and ModuleTerm at 00000000f9e36db0
00:00:00.932 SUP: VMMR0EntryEx located at 00000000f9e36c90, VMMR0EntryFast at 00000000f9e35b70 and VMMR0EntryInt at 00000000f9e35960
00:00:00.962 File system of '/home/mikado/.VirtualBox/Machines/Windows XP/Snapshots' (snapshots) is unknown
00:00:00.962 File system of '/home/mikado/.VirtualBox/HardDisks/Windows XP.vdi' is ext4
00:00:00.964 Using XKB for keycode to scan code conversion
00:00:00.968 File system of '/home/mikado/.VirtualBox/Machines/Windows XP/NewHardDisk1.vdi' is ext4
00:00:00.989 VBoxSharedClipboard mode: Bidirectional
```

---

