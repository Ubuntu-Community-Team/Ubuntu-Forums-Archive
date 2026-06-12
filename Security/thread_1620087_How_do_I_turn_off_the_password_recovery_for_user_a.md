---
title: "How do I turn off the password recovery for user account."
date: 2010-11-12
forum: Security
---

### Post by MechaMechanism on 2010-11-12
I remember my password very well and have no need of the password recovery.  Everywhere I look it's how to recover and I don't want that.  The kind where you boot into root recovery console to change the password.

---

### Post by CharlesA on 2010-11-12
Recovery mode is there for more then just resetting yer password.

If you remove it, you remove an important diagnostic tool.

---

### Post by MechaMechanism on 2010-11-12
> **CharlesA said:**
> Recovery mode is there for more then just resetting yer password.

If you remove it, you remove an important diagnostic tool.
I just want to remove the password recovery part.  I still want the recovery console in general for non password stuff.  I don't want some one to change my password on me.

---

### Post by cariboo on 2010-11-12
There really is no password recovery part, you can try removing passwd, but I don't know what affect it will have on your installation. 

I really wouldn't advise you try it, unless you try it in a vm, to see what affect it has on the rest of the system.

The one thing to keep in mind, is that if someone has physical access to your system, and they know what they are doing, they can pretty well do anything they want.

**Warning**: [COLOR="Red"]r**emoving passwd could make your system unusable**.[/COLOR]

---

### Post by MechaMechanism on 2010-11-12
Thanks for the replies.  I'll just encrypt the home directory.

---

