---
title: "Libvte3 (0.34.5-1ubuntu1) is broken"
date: 2013-05-24
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-05-24
Upgrading libvte3 (to 0.34.5-1ubuntu1) you get a broken installation, which is stuck to tty1 without a desktop.
You may or may not get X if you login and command "startx".
The workaround is to downgrade libvte3 (packages libvte-2.90-9 and libvte-2.90-common) to the previous version 0.34.2-0ubuntu2.

Here:
[https://launchpad.net/ubuntu/+source/vte3/1:0.34.2-0ubuntu2](https://launchpad.net/ubuntu/+source/vte3/1:0.34.2-0ubuntu2)

---

### Post by dino99 on 2013-05-25
I does not get trouble here on i386 with libvte-2.90-9 0.34.5 (libvte9 is also installed)

---

### Post by Harry33 on 2013-05-25
> **dino99 said:**
> I does not get trouble here on i386 with libvte-2.90-9 0.34.5 (libvte9 is also installed)

Do you use lightdm or gdm?
I use gdm which does not seem to work with the new libvte9.

---

### Post by dino99 on 2013-05-25
> **Harry33 said:**
> Do you use lightdm or gdm?
I use gdm which does not seem to work with the new libvte9.

i'm using lightdm + lightdm-gtk-greeter since a while.

---

### Post by tista on 2013-05-26
Hi Harry33,

Today I could confirm this issue, too...
And thanks for your workarounds. ;)

Best Regards,
Tista

---

### Post by Harry33 on 2013-05-27
There is a new libvte3 version (0.34.5-1ubuntu2) in Saucy-proposed now.
Here:
[https://launchpad.net/ubuntu/saucy/+source/vte3/1:0.34.5-1ubuntu2](https://launchpad.net/ubuntu/saucy/+source/vte3/1:0.34.5-1ubuntu2)

That one should fix the gdm breaking issue.

This is the bug (1184132) report:
[https://bugs.launchpad.net/ubuntu/+source/vte3/+bug/1184132](https://bugs.launchpad.net/ubuntu/+source/vte3/+bug/1184132)

---

### Post by VinDSL on 2013-05-27
> **Harry33 said:**
> There is a new libvte3 version (0.34.5-1ubuntu2) in **[COLOR="#FF0000"]Saucy-proposed[/COLOR]** now.[...]
Must remember this, the next time someone badmouths "Proposed".  :)

Thanks, Harry!

---

### Post by Harry33 on 2013-05-28
This issue has been solved with the latest update to vte3 (0.34.5-1ubuntu2) and new pango (1.32.5-5).

---

