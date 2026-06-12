---
title: "Fix for Brother Scanner problem"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kurt18947 on 2012-02-18
I don't consider this a bug because I found the fix in launchpad but thought I'd post this for Brother MFD users.  There is already additional work required in 11.10, copying some files from /user/lib64  to /user/lib as documented here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

This is required (so far) in 12.04 as well.  Copying the files didn't make my scanner work in Precise however, except for running the scanner software with elevated privileges.  The fix was to add each user wishing to use the scanner to 'lp' group.

```
sudo adduser <user_name> lp
```This is in addition to the editing documented here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

Now desktop users can print and scan normally.  It certainly seems that Brother could stand to work on their scanner install scripts and make users' lives simpler.  On the other hand, Linux support *does* exist which is more than can be said for some other manufacturers.

---

### Post by ajgreeny on 2012-02-18
One other thing I needed in Lucid 10.04 was to install libsane-extras, then

    1. Open "/lib/udev/rules.d/40-libsane.rules" file.

    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

```
    3. Restart the OS. 

Without that the scanner was just a glass plate.  This may not be needed any more, but I offer the info just in case it still is.

---

### Post by kurt18947 on 2012-02-18
> **ajgreeny said:**
> One other thing I needed in Lucid 10.04 was to install libsane-extras, then

    1. Open "/lib/udev/rules.d/40-libsane.rules" file.

    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

```    3. Restart the OS. 

Without that the scanner was just a glass plate.  This may not be needed any more, but I offer the info just in case it still is.

That is indeed still needed.  The scanner will work only with elevated privileges which is not recommended, adding that line makes the scanner available to 'normal' users. What wasn't clear was having to add users to the lp group which was not easy to find.  I let Brother know about this fix though they don't publicly offer support until the O.S. is released.

---

