---
title: "virtualbox copy/paste"
date: 2010-05-18
forum: Virtualisation
---

### Post by gvr2600 on 2010-05-18
Hy guys

I am new to virtual box, and I was wondering if I can copy a text from my computer to the virtual box`s operating system.
I need to make some research  to a dns server and I am installing gentoo and there are a few lines to copy/paste.
Maybe there are some settings that I missed.


Thanks in advance,

---

### Post by TJRC on 2010-05-18
Warning, I have not tried the shared clipboard feature yet, but the documented process seems straightforward. I have installed the guest additions, and that looks like it's 90% of the process.

You'll first need to install the Guest Additions on your guest.  For example, I'm running VirtualBox on Windows Vista, and then running Ubuntu 10.04 in VirtualBox, so I installed the Linux guest additions into Ubuntu.  Basically, the guest additions let your Linux system know it's running in a virtual environment so it can cooperate with the host (including such things as sharing the clipboard with the host).

Instructions for installing the guest additions are at [http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)  I have done this, it really is straightforward, at least in my configuration (Windows hosting Ubuntu).

Once the guest additions are installed, the Shared Clipboard feature should be available.  To enable it, see the instructions at [http://www.virtualbox.org/manual/ch03.html#generalsettings](http://www.virtualbox.org/manual/ch03.html#generalsettings) for "Shared Clipboard":[INDENT]If the virtual machine has Guest Additions installed, you               can select here whether the clipboard of the guest  operating               system should be shared with that of your host. If you  select               "Bidirectional", then VirtualBox will always make sure  that both               clipboards contain the same data. If you select "Host to  guest"               or "Guest to host", then VirtualBox will only ever copy               clipboard data in one direction.[/INDENT]Good luck.

[Edit] Postscript: I just tried it, and it works as described.  To my surprise,               "Bidirectional" was already set.

---

