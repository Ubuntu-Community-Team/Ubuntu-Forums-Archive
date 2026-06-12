---
title: "Extending vdi allocated storage space"
date: 2010-06-28
forum: Virtualisation
---

### Post by ppepperr on 2010-06-28
I am trying to clone my Vista vdi to another larger vdi using VBoxManage but keep getting the following message:

[FONT=Courier New]sudo VBoxManage clonevdi HardDisks/vista.vdi HardDisks/VistaHD2.vdi
Sun VirtualBox Command Line Management Interface Version 3.1.8
(C) 2005-2010 Sun Microsystems, Inc.
All rights reserved.

ERROR: Could not find file for the medium '/home/phillip/.VirtualBox/HardDisks/vista.vdi' (VERR_FILE_NOT_FOUND)
Details: code VBOX_E_FILE_ERROR (0x80bb0004), component Medium, interface IMedium, callee nsISupports
Context: "OpenHardDisk(Bstr(szFilenameAbs), AccessMode_ReadWrite, false, Bstr(""), false, Bstr(""), srcDisk.asOutParam())" at line 628 of file VBoxManageDisk.cpp[/FONT]

Using ls -lt shows that both vdi exist. Could somebody point me in the right direction or tell me another way to extend my Vista vdi. 

I've got so used to using Linux that I forgot how much space a windows install takes.

Thanks for any help.

Found another post referring to CloneVDI which run successfully using CrossOver. Thanks to Don Milne.

---

