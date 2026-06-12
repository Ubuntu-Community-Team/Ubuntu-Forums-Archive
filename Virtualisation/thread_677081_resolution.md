---
title: "resolution"
date: 2008-01-24
forum: Virtualisation
---

### Post by SyCo123 on 2008-01-24
I'm using Ubuntu 7.10 inside virtualbox on Vi$ta (at work)
The monitor is LCD 1280X1024 but I'd like to set it at 1024X768. currently stuck at 800X600 and I can't change the resolution to 1024x768.  I've tried with system>pref>scren res and I just get a messed up screen of lines. With system>admin>screen and graphics I've tried generic>LCD 1024X768, generic>LCD 1280X1024 and even  generic>monitor 1280X1024, all resulting on Test in a black and white small checkered screen with the keep configuration dialog window clearly viewable. As I cant see anything other than the dialog, I'm not keen to press OK although the dialog is displaying OK.

Am I good to go or should I expect to see the desktop on the test?

Also for extra info the boot screen look like it is at 1024x768.

---

### Post by bernied on 2008-01-24
Have you run the virtualbox additions. There is an .iso image that comes with the install, which you specify as a cd drive in the virtual machine.

I haven't run linux inside windows, only the other way round. I like to keep microsoft imprisoned and linux free - haha.

---

### Post by SyCo123 on 2008-01-24
That's how I do it at home, but at work I have no say. :(

I had already installed the guest additions CD and the mouse isn't captured by the VM.

---

### Post by SyCo123 on 2008-01-28
THe issue was actually quite simple to fix.

I edited /etc/X11/xorg.cof and change the 800x600 to 1024X768 restarted x and it was all good!.

---

