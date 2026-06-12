---
title: "Samba permissions vs. Linux Permissions"
date: 2021-07-21
forum: Security
---

### Post by bdbell73 on 2021-07-21
Hello, everyone!  I have a question for some of the experts here...

Would you agree or disagree:  I have found that it's easier to just set  up wide open permissions in Samba, then control access using Linux user  permissions instead.  This plan seems to work for me, and I've tested  it, but I figured I'd put it here and consider everyone else's comments.   Perhaps some of you will spot a downside that I just don't see.

On the surface, my theory DOES work.  I create a share, give it 777 and  allow read/write/etc to all users, then I set the user permissions in  the Linux file system, and it seems to work very well.

Is this safe? Am I missing something?  Does anyone else do this?

Thank you in advance!

---

### Post by CharlesA on 2021-07-21
Yes, it will work that way. file-level permissions will override shared level permissions.

However, you should still assign share level permissions for the rare event the file level permissions are changed either by mistake or intentionally.

Security is about layers.

---

### Post by bdbell73 on 2021-07-21
> **CharlesA said:**
> Yes, it will work that way. file-level permissions will override shared level permissions.

However, you should still assign share level permissions for the rare event the file level permissions are changed either by mistake or intentionally.

Security is about layers.

Agreed! Thank you

---

