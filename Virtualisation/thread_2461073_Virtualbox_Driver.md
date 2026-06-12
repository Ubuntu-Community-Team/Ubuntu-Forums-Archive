---
title: "Virtualbox Driver"
date: 2021-04-23
forum: Virtualisation
---

### Post by dddman on 2021-04-23
Hello

I run win10 host and ubuntu 20.04 as guest.  I would think vbox proprietary drivers would give me better performance, however this screen seems to be locked and will not let me make any changes.

What's up with that?  Thanks

[ATTACH=CONFIG]288361[/ATTACH]

The "paperclip" option would not allow me to upload a png so I used ibb.

---

### Post by QIII on 2021-04-23
Different image file types have different maximum size limits.   Your original was over the limit for a .png.  I have re-scaled your image and added it using the attachment facility.

---

### Post by dddman on 2021-04-23
Thanks

---

### Post by QIII on 2021-04-23
Virtualbox supplies a hardware abstraction layer via its software.  There are no proprietary Linux drivers to be used.  With Virtualbox, your guest OS will only be "aware", to a certain extent, of what the actual CPU is.  The graphics adapter, etc, available is the software abstraction presented by the virtualization software.

Hence, no changes can be made.

---

### Post by dddman on 2021-04-24
That makes perfect sense, seeing that vbox driver offering threw me.  Would the same reasoning apply to the restricted-extras package?  Installing it would not have any effect in a virtual system.

And thanks again

---

### Post by QIII on 2021-04-24
The restricted-extras package really is not related to hardware directly.

Read the introduction [here]("https://help.ubuntu.com/community/RestrictedFormats") for details about what the package is for.

---

### Post by dddman on 2021-04-24
Excellent, that wraps this thread up.  Again thanks for clearing this up.

---

