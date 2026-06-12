---
title: "Can't mount USB-drive or any External Hard-drives"
date: 2009-01-01
forum: Virtualisation
---

### Post by Kdar on 2009-01-01
I have Windows XP installed in VirtualBox.
All other USB seem to working just fine now (mouse, keyboard.. etc).

But when I stick my USB-drive or turn on Hard-drve.. it give me this error message:


Not permitted to open the USB device, check usbfs options.

```
Failed to attach the USB device SanDisk U3 Cruzer Micro [0200] to the virtual machine XP.

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}
```

---

### Post by mikewhatever on 2009-01-01
Check out this guide.-> [http://ubuntuforums.org/showpost.php?p=6122145&postcount=4](http://ubuntuforums.org/showpost.php?p=6122145&postcount=4)

---

### Post by Kdar on 2009-01-01
When I do it.. Fixed that mouse errors.

But I still can't get my hard-drives to load. Whats wrong?

---

### Post by Kdar on 2009-01-01
Ok. I solved my problem.

[http://ubuntuforums.org/showthread.php?t=1015763](http://ubuntuforums.org/showthread.php?t=1015763)
I followed those instruction.

and also those:
[http://ubuntuforums.org/showthread.php?t=927491](http://ubuntuforums.org/showthread.php?t=927491)

> Hi, i finally managed to solve this problem in Ubuntu 8.10 Intrepid.
First i activated the usb support adding this line to /etc/fstab:

Code:

none /proc/bus/usb usbfs devgid=46,devmode=666 0 0

Warning: this works only in intrepid, activating the usb support in Hardy or previous requires a different procedure.

Than I started the virtual box and installed guest addition (without mouse support, you can reach the menu "Devices" by holding ctrl+home, then release and suddenly press d, from that menu you can install guest additions).

Than I turned off the VM.
**[COLOR="Red"]Now I enabled the USB support adding all the devices except the mouse![/COLOR]**
If I enabled the mouse, I had the described problem.
Without checking it, everything works fine!

So.. for some weird reason. I had to disable support for my mouse and it worked :D

---

### Post by HotShotDJ on 2009-01-02
> **Kdar said:**
> So.. for some weird reason. I had to disable support for my mouse and it worked :DAs counterintuitive as it may seem, this is exactly what is supposed to happen.  The keyboard and mouse (among other things) are virtualized -- that is, the guest OS does not directly access the hardware.  Remember, any time the guest OS gets direct access to hardware (such as an external drive or web cam) the host OS can not use that hardware until the guest releases it.  You can see that this could cause a problem if you gave the guest direct access to things like the keyboard, mouse, graphics card, etc.

When you enabled the USB mouse in your Virtual Machine, you set up a conflict -- essentially, the two OS's were fighting over the mouse, causing erratic and unexpected behavior.  Make sure that both the USB mouse and the USB keyboard are NOT enabled in your VirtualBox sessions.

Thank you for your PM, calling my attention to this and other threads where this was a problem.  I've edited my [HOWTO]("http://ubuntuforums.org/showthread.php?t=1015763") to include this issue.

---

### Post by Kdar on 2009-01-02
ah I see now. Thanks for explanation :).. I guess that why right-CTRL+L or F didn't work before too.

So.. are USB-drives are also vertualised? or if Linux have one mounted? Do I need to dis-mount and re-mount it in VirtualBox?

---

### Post by HotShotDJ on 2009-01-02
> **Kdar said:**
> So.. are USB-drives are also vertualised? or if Linux have one mounted? Do I need to dis-mount and re-mount it in VirtualBox?No.  USB drives require direct access.  But you do not need to unmount them in the host first, VirtualBox will take care of that for you. Just remember, the USB drive will not be accessible to the host until they have been unmounted from the guest.  The same is true of WebCam, local USB printers, scanners, cameras, etc.

---

