---
title: "Final Beta and Intel Haswell"
date: 2014-03-29
forum: Ubuntu Development Version
---

### Post by fjgaude on 2014-03-29
Well, well... can't install either Skype or Google Chrome in 14.04 latest update, with kernel 3.13.0-19.

Anyone else having this issue? 

Thanks!

###

Okay... updated to 3.13.0-20 and used dpkg -i to install instead of the Software Center and all went well, even with VirtualBox. Beta looking good!

---

### Post by QDR06VV9 on 2014-03-29
> **fjgaude said:**
> Well, well... can't install either Skype or Google Chrome in 14.04 latest update, with kernel 3.13.0-19.

Anyone else having this issue? 

Thanks!

###

Okay... updated to 3.13.0-20 and used dpkg -i to install instead of the Software Center and all went well, even with VirtualBox. Beta looking good!
I do not use ethier one but maybe this will [HELP]("http://askubuntu.com/questions/385705/skype-and-google-on-ubuntu-13-10")
Let us know.
Regards

---

### Post by gifford on 2014-03-29
The problem is with using the software center to install external deb files. This is a known and critical bug.
Your were correct in using the dpkg -i to install with. Until the bug is fixed this is the only way to install the external applications.

---

### Post by fjgaude on 2014-03-29
Thanks for the heads-up, Gifford!

---

