---
title: "vbox help"
date: 2008-11-14
forum: Virtualisation
---

### Post by benjaminjames on 2008-11-14
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}


Hi all i am trying to set up a vista vbox but i get this message does anyone know how to fix it????/ also is virtualbox compatible with 64bit os's
thanks all any help will be greatly appreciated

---

### Post by benjaminjames on 2008-11-14
well i got it set up and im not to worried about usb at the mo the most important thing is that i can access the internet ive tried a few walk throughsbut i cannot understand them im a prety newbish level user any one no of any gui tools for doin this or really well explained walk through?

---

### Post by jsully1 on 2008-11-18
Do:
sudo gedit /etc/fstab

add this line to the botton:

none /proc/bus/usb usbfs devgid=20,devmode=666 0 0

Save and reboot, then when you start a virtual machine you should be able to select the USB device from the Devices pulldown.

---

