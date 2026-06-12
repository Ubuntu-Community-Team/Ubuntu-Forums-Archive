---
title: "Virtualbox 5.1.12r112440, Windows 7 x64, Apple USB support problem"
date: 2017-01-04
forum: Virtualisation
---

### Post by Roy_Bettle on 2017-01-04
Failed to open a session for the virtual machine **Win7x64**.
Implementation of the USB 3.0 controller not found!
Because the USB 3.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the **'Oracle VM VirtualBox Extension Pack'** or disable USB 3.0 support in the VM settings (VERR_NOT_FOUND).
[TABLE="width: 100%"]
[TR]
[TD]Result Code:[/TD]
[TD]NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component:[/TD]
[TD]ConsoleWrap[/TD]
[/TR]
[TR]
[TD]Interface:[/TD]
[TD]IConsole {872da645-4a9b-1727-bee2-5585105b9eed}[/TD]
[/TR]
[/TABLE]

Linux kernel 4.4.0-57
Distribution Xubuntu 16.04.1 LTS

Actual "lsb" output:

```
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

```
I was trouble-shooting a problem whereby my iPod 5th generation is not being seen by the Windows 7 x64 guest.  At the time, my VirtualBox Extensions Pack was 5.0.24 and version 5.1.12-112440 was available.  So I downloaded the updated extensions pack and installed it.  Now the Windows 7 x64 guest won't start with the "Implementation of the USB 3.0 controller not found!" error message at the top.  I'm about to move USB support for the guest back to USB 2/EHCI and see if it will boot.

However, I'm thinking that I haven't solved for the iPod issue.  Anyone else dealing with this PITA?  Thanks!

---

### Post by Roy_Bettle on 2017-01-04
Yeah, so, rolling back USB support to 2.0/EHCI didn't help:

Failed to open a session for the virtual machine **Win7x64**.
Implementation of the USB 2.0 controller not found!
Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the **'Oracle VM VirtualBox Extension Pack'** or disable USB 2.0 support in the VM settings.
Note! This error could also mean that an incompatible version of the **'Oracle VM VirtualBox Extension Pack'** is installed (VERR_NOT_FOUND).
[TABLE="width: 100%"]
[TR]
[TD]Result Code: [/TD]
[TD]NS_ERROR_FAILURE (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component: [/TD]
[TD]ConsoleWrap[/TD]
[/TR]
[TR]
[TD]Interface: [/TD]
[TD]IConsole {872da645-4a9b-1727-bee2-5585105b9eed}[/TD]
[/TR]
[/TABLE]

Now to uninstall the updated Extension pack ... just as soon as Google shows me how ... =)

---

### Post by Roy_Bettle on 2017-01-04
Basically, I believe that VirtualBoxis probably not very good at managing itself.  I followed these directions - [http://zqscm.qiniucdn.com/data/20130322230608/index.html](http://zqscm.qiniucdn.com/data/20130322230608/index.html) - for uninstalling the existing Extension Pack, to include running the "cleanup" option at the end, reinstalled 5.1.12 and now the guest runs fine with USB 2.0 and 3.0.

Still no luck with the iPod however.  [sigh]

---

