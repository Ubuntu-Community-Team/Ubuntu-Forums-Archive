---
title: "AppArmor module fails to load at boot (kernel 2.6.31 with Ubuntu patch 11.36)"
date: 2009-09-28
forum: Security
---

### Post by mo0nykit on 2009-09-28
Hello!

I have succeeded in compiling, installing, and booting from a 2.6.31 kernel in Jaunty. But when I look at the startup screens, it says ```
loading AppArmor module... FAILED
```. When I finally get into the desktop, then into a terminal, I look up the **apparmor_status** and here's the output: ```
$apparmor_status
apparmor module is loaded.
apparmor filesystem is not mounted.
```Is this a conflicting report, considering that it FAILED at bootup? Is there something wrong?

Going back to the top of my source tree, I do a ```
make menuconfig
``` I go into **Ubuntu Supplied Third Party Drivers -->** and yes, AppArmor support is set as built-in. AppArmor boot parameter default value is 1, meaning, "start during boot up". Well I read an AppArmor bug report here [_apparmor fails to load at startup_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375422"). It refers to kernel 2.6.30. I don't know if it holds true for the patched 2.6.31 (Ubuntu patch 11.36)

---

### Post by ibuclaw on 2009-10-04
Hi mo0nykit,

Try downloading the Linux sources again, as it now appears to have been fixed in Ubuntu.
see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375422](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375422)

To download the 2.6.31 kernel, get it here: [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.31.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.31.orig.tar.gz)
And the ubuntu patches (that include apparmor) you can get here: [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.31-11.38.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux_2.6.31-11.38.diff.gz)

Regards
Iain

---

### Post by mo0nykit on 2009-10-05
Thank you very much :) I'll give it another try.

---

