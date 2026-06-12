---
title: "Virtualbox vmmouse.sys and vmxnet.sys missing"
date: 2009-03-05
forum: Virtualisation
---

### Post by Jennifer82 on 2009-03-05
[COLOR="Purple"]
Hi everyone,

Everytime I load up the guest system (XP 32 bit) I am prompted twice for:
> The file 'vmmouse.sys' on VMware Pointing Device Disk is needed.
The file 'vmxnet.sys' on VMware Pointing Device Disk is needed.

The result is that the Ethernet Controller is not properly installed (and no internet access) on the guest OS.

The guest additions is already mapped to the D: and I can go in to the guest OS and run the installation file *VBOXWindowsAdditions-x86.exe* successfully, but after the reboot of the guest os the ethernet still doesn't work.

Peeking into the \32Bit folder I noticed a readme:
[I]Sun xVM VirtualBox Guest Additions
Where have the Windows drivers gone?
- The Windows Guest Additions drivers were removed from this directory to save space on your hard drive. To get the files you have to extract them from the Windows Guest Additions installers:

To extract the 32-bit drivers to "C:\Drivers", do the following:
  VBoxWindowsAdditions-x86 /extract /D=C:\Drivers[/I]

If I run:
> sudo sh VBoxWindowsAdditions-x86 /extract /D=C:\Drivers

I get the message > Detected unsupported amd64 environment. and nothing is extracted in the /32Bit directory.

Can anyone help shed some insight into what I'm doing wrong?

Thanks a ton in advance :)

Other information:
VirtualBox version: virtualbox-21_2.1.4-42893_Ubuntu_intrepid_amd64.deb
Host system: Ubuntu 8.10 64 bit (intel processessor)
Guest system: XP sp2 32 bit

[/COLOR]

---

### Post by Jennifer82 on 2009-03-06
Resolved my own issue by going into the settings for the XP virtual machine and changing adapter type to Intel Pro/1000 MT Desktop in the Network section.

---

