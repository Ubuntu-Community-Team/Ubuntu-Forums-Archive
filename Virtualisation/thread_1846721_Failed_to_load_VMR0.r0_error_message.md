---
title: "Failed to load VMR0.r0 error message"
date: 2011-09-19
forum: Virtualisation
---

### Post by nbrebol on 2011-09-19
I was trying to load windows 8 dev in virtual box and i got it all set up correctly (i followed a how-to suggested by a person in another thread). When I started the virtual machine, I got an error message saying:

Failed to open a session for the virtual machine windows8dev.
Failed to load VMMR0.r0 (VERR_SUPLIB_OWNER_NOT_ROOT).
Unknown error creating VM (VERR_SUPLIB_OWNER_NOT_ROOT)

details:



Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {515e8e8d-f932-4d8e-9f32-79a52aead882}


Here is the log file:

00:00:01.745 VirtualBox 4.0.4_OSE r70112 linux.x86 (Jul 27 2011 16:29:17) release log
00:00:01.745 Log opened 2011-09-19T16:39:28.109834000Z
00:00:01.745 OS Product: Linux
00:00:01.745 OS Release: 2.6.38-11-generic
00:00:01.745 OS Version: #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011
00:00:01.745 DMI Product Name: IdeaPad Y560    
00:00:01.745 DMI Product Version: Rev 1.0                 
00:00:01.746 Host RAM: 2443MB RAM, available: 1577MB
00:00:01.746 Executable: /usr/lib/virtualbox/VirtualBox
00:00:01.746 Process ID: 23292
00:00:01.746 Package type: LINUX_32BITS_GENERIC (OSE)
00:00:01.854 pdmR3LoadR0U: pszName="VMMR0.r0" rc=VERR_SUPLIB_OWNER_NOT_ROOT szErr="The owner is not root: '/usr'"
00:00:01.854 VMSetError: /build/buildd/virtualbox-ose-4.0.4-dfsg/src/VBox/VMM/VMMR3/VM.cpp(573) int vmR3CreateU(UVM*, uint32_t, int (*)(VM*, void*), void*); rc=VERR_SUPLIB_OWNER_NOT_ROOT
00:00:01.854 VMSetError: Failed to load VMMR0.r0
00:00:01.854 VMSetError: /build/buildd/virtualbox-ose-4.0.4-dfsg/src/VBox/VMM/VMMR3/VM.cpp(348) int VMR3Create(uint32_t, const VMM2USERMETHODS*, void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**); rc=VERR_SUPLIB_OWNER_NOT_ROOT
00:00:01.854 VMSetError: Unknown error creating VM
00:00:01.854 ERROR [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={515e8e8d-f932-4d8e-9f32-79a52aead882} aComponent={Console} aText={Failed to load VMMR0.r0 (VERR_SUPLIB_OWNER_NOT_ROOT).
00:00:01.854 Unknown error creating VM (VERR_SUPLIB_OWNER_NOT_ROOT)}, preserve=false
00:00:01.953 Power up failed (vrc=VERR_SUPLIB_OWNER_NOT_ROOT, rc=NS_ERROR_FAILURE (0X80004005))



I then went back and re-did the whole thing exactly as the how-to did and got the same thing. I am not an expert at ubuntu, but i am guessing the error has something to do with permissions or where the files are located?


thank you in advance!

---

