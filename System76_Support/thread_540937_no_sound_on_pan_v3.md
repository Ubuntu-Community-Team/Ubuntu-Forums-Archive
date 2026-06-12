---
title: "no sound on pan v3"
date: 2007-09-02
forum: System76 Support
---

### Post by kperkins on 2007-09-02
I have no sound since kernel update, and can't revert since the old kernel was removed automatically when upgraded. (That's really a no-no for linux) I'm assuming the kernel upgrade is the problem, since it was working before this.
My alsa mixer, and volume control are missing options they had before, also.
Help.
<edit>
Ok so I see that kernel 2.6.20-15 is still there, just taken out of menu.lst, so I can hand edit that, and boot into it to see if this is the cause, but really it's just a big pain. (I don't know if this is the system76 policy on this, or a new Ubuntu one, but in my opinion it's not a very good one)
<edit 2.0>
So never mind the previous edit--the upgrade takes out the initrd-img file for 2.16.20-15, so no luck with that route.  Not a good policy in my opinion.  
I'll wait for a fix.

---

### Post by rmaus on 2007-09-02
I have the same problem (no sound), with gazp2

---

### Post by kperkins on 2007-09-02
I reinstalled the system76 drivers, and sound works now.

---

### Post by rmaus on 2007-09-02
Thank you for that quick fix.

---

