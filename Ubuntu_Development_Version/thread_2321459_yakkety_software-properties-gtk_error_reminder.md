---
title: "yakkety software-properties-gtk error reminder"
date: 2016-04-22
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-04-22
After you have converted to yakkety you will get software-properties-gtk error.

Here is the fix:  [https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

---

### Post by dino99 on 2016-04-22
??????????????????
BaseURI: cdrom:\[Ubuntu.*15.
MatchURI: cdrom:\[Ubuntu.*15.10

---

### Post by ventrical on 2016-04-22
> **dino99 said:**
> ??????????????????
BaseURI: cdrom:\[Ubuntu.*15.
MatchURI: cdrom:\[Ubuntu.*15.10

I just converted the naming convention in that file.  Cariboo is the maintainer. Should they be 16.04?

actually after looking at other Ubuntu.info files that segement is not there but I am not going to edit it. I'll leave message for Cariboo

Regards.

---

### Post by cariboo on 2016-04-22
I haven't finished updating the wiki yet, I actually removed that section from my working copy, as we didn't have that problem during the Xenial cycle.

---

