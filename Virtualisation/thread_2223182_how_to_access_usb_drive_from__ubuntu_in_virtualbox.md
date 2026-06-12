---
title: "how to access usb drive from  ubuntu in virtualbox?"
date: 2014-05-09
forum: Virtualisation
---

### Post by tony44 on 2014-05-09
[COLOR=#333333][FONT=Lucida Grande]USB device 'LaCie LaCie iamaKey ' with UUID {b4ad974d-64a2-4218-ae7f-9498cb6f7cad} is busy with a previous request. Please try again later.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Result Code: E_INVALIDARG (0x80070057)[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Component: HostUSBDevice[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Interface: IHostUSBDevice {173b4b44-d268-4334-a00d-b6521c9a740a}[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Callee: IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}

What's the problem here? is it because the virtualbox itself?
I've done many suggestions posted on the web but no success so far.
Any success story?

thanks[/FONT][/COLOR]

---

### Post by kc1di on 2014-05-09
is this on a ubuntu host machine or windows machine?

if ubuntu is the host them in a terminal and add your usr to virtualbox  like this : ```
sudo adduser yourusername vboxusers
```

---

### Post by TheFu on 2014-05-10
USB devices can only be controlled by 1 OS at a time. If the hostOS has already accessed the device, then a clientOS cannot.  Have the hostOS "eject"/umount the USB drive first.

---

