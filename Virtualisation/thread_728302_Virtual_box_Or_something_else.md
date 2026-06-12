---
title: "Virtual box? Or something else?"
date: 2008-03-18
forum: Virtualisation
---

### Post by MSdefecter on 2008-03-18
Hi
I am fairly new to Ubuntu and Linux in general for that matter and except for a few minor annoyances I am liking my new platform. I would like to be able to install windows and other distributions of linux via a virtual server and have been looking at the virtual box software. Although I have used this before and found it fairly simple to use I do not think that you can get full screen on it. I don't know if this was just me or if it is designed like that. Does anyone know if you can run it in a full window and if not any other VM ware that will?

---

### Post by scragar on 2008-03-18
VirtualyBox will run in full screen, there is an option for it(not sure where), to prevent it from distorting your graphic's though you may need to make it use the same resolution as your desktop.

---

### Post by sosipator on 2008-03-18
You can try vmware server or workstation, here some howto.


[http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by dmitriyp13 on 2008-03-18
VirtualBox has a full screen mode.  To access it, go to the 'Machine' menu or use the shortcut HostKey + F (the host key is the right 'Ctrl' key by default).

---

### Post by itsbradman on 2008-03-18
It also has a seamless mode, once you enable the add ons, which is quite nice!

---

### Post by Hero of Time on 2008-03-18
Though seamless is only available for Windows Guests.

---

### Post by dark_harmonics on 2008-03-20
I really like virtual box. I highly recommend it. The only improvement I would ask for, is better support for USB devices (i think it points to the wrong place to look for them).

---

### Post by rpainter on 2008-03-20
While I am also new to Linux, I can recommend VirtualBox also. I have WinXP installed in it, and full screen mode works fine.

---

### Post by Tomatz on 2008-03-20
Vbox is good.

Vmware workstation is better :)

---

### Post by davekenny on 2008-03-20
does virtual box support usb 2.0 assuming I can get it to work?
what about parallel ports?
what about using an existing winxp boot drive? I think I've posts on the this but has some done it?
I have linux and winxp in a dual boot on one physical drive. I sure would like to get rid of the dual boot and just use linux. but some programs don't under linux and/or don't exist in the linux world

thanks

davekenny

---

### Post by valke on 2008-03-20
@MSdefecter...yeah, vbox is pretty sweet. nothing like a dual boot, but it does fullscreen and auto-fixes the resolution. 

@davekenny...i recently installed vbox and arsgeek has a nice little writeup on how to enable usb. 

here's the writeup, and there is a link to the arsgeek article in there too. plenty off screenshots as well! [http://suprablog.com/index.php/2008/03/20/review-virtualbox/](http://suprablog.com/index.php/2008/03/20/review-virtualbox/)

---

### Post by davekenny on 2008-03-20
enabling usb..is this 1.0 or 2.0
I found the vmare doesn't enable the same level as the hardware? does virtual box?

davekenny

---

### Post by valke on 2008-03-24
2.0. i honestly don't know if 1.0 would work or not.

---

### Post by Hero of Time on 2008-03-24
I doubt if usb 1.0 still exists. It's all 1.1 or 2.0. If you forget to enable the EHCI controller, you have the slow usb, else you have usb 2.0.

---

