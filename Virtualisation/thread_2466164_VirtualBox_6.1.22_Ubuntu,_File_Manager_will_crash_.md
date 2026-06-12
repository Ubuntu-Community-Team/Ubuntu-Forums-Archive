---
title: "VirtualBox 6.1.22_Ubuntu, File Manager will crash VM when X the File Manager"
date: 2021-08-21
forum: Virtualisation
---

### Post by amccombs on 2021-08-21
on Ubuntu 20.04 host, VirtualBox 6.1.22_Ubuntu r144080

virtualbox-6.1_6.1.26-145957~Ubuntu~eoan_amd64.deb,  Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack (newer  extension pack breaks USB 2+), virtualbox-guest-additions-iso  (6.1.22-1~ubuntu1.20.04.1)

1. Boot a VM, I am using Windows 10.
2. on VirtualBox menu, select Machine > File Manager
3. close the File Manager by clicking the X button on the top right of the File Manager

actual results:
VM crashes

expected results:
File Manager to close

note:
clicking the Close button works as expected

attached:
VirtualBox log file

---

### Post by monkeybrain20122 on 2021-08-21
> **amccombs said:**
> on Ubuntu 20.04 host, VirtualBox 6.1.22_Ubuntu r144080

virtualbox-6.1_6.1.26-145957~Ubuntu~eoan_amd64.deb,  Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack (newer  extension pack breaks USB 2+), virtualbox-guest-additions-iso  (6.1.22-1~ubuntu1.20.04.1)




Your guest Addition's version has to match VB's.

---

### Post by amccombs on 2021-08-21
I did sudo apt install -y -f  virtualbox-guest-additions-iso, and apt found virtualbox-guest-additions-iso  (6.1.22-1~ubuntu1.20.04.1)

When vbox-extpack match, then VM will not even boot. 
With Oracle_VM_VirtualBox_Extension_Pack-6.1.26.vbox-extpack 

When I have USB 1.1 enabled:
OS will boot but VirtualBox will not mount USB:
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
ConsoleWrap
Interface: 
IConsole {872da645-4a9b-1727-bee2-5585105b9eed}


When I have USB 2.0 enabled:
Failed to open a session for the virtual machine Windows_10_TurboTax.
The VM session was aborted.
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: SessionMachine
Interface: ISession {c0447716-ff5a-4795-b57a-ecd5fffa18a4}

When I have USB 3.0 enabled:
Failed to open a session for the virtual machine Windows7_1.
Failed to construct device 'usb-xhci' instance #0 (VERR_PDM_DEVHLP_VERSION_MISMATCH).
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}

---

### Post by monkeybrain20122 on 2021-08-21
> **amccombs said:**
> I did sudo apt install -y -f  virtualbox-guest-additions-iso, and apt found virtualbox-guest-additions-iso  (6.1.22-1~ubuntu1.20.04.1)

When vbox-extpack match, then VM will not even boot. 
With Oracle_VM_VirtualBox_Extension_Pack-6.1.26.vbox-extpack 

When I have USB 1.1 enabled:
OS will boot but VirtualBox will not mount USB:
Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
ConsoleWrap
Interface: 
IConsole {872da645-4a9b-1727-bee2-5585105b9eed}


When I have USB 2.0 enabled:
Failed to open a session for the virtual machine Windows_10_TurboTax.
The VM session was aborted.
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: SessionMachine
Interface: ISession {c0447716-ff5a-4795-b57a-ecd5fffa18a4}

When I have USB 3.0 enabled:
Failed to open a session for the virtual machine Windows7_1.
Failed to construct device 'usb-xhci' instance #0 (VERR_PDM_DEVHLP_VERSION_MISMATCH).
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}


Uninstall your VB and download VB and the matching guest additions from [Oracle]("https://www.virtualbox.org/wiki/Downloads").

---

### Post by amccombs on 2021-08-21
oh, ok, Thank you.

---

