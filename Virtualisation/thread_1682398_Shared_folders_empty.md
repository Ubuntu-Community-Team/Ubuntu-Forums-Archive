---
title: "Shared folders empty"
date: 2011-02-05
forum: Virtualisation
---

### Post by jcoles on 2011-02-05
I configured two Shared Folders: 
/home/jcoles/Downloads shared as Downloads
/home/jcoles/Music shared as Music
Both are set to auto-mount.
Both host and guest are Linux. 

In the Guest, /media contains sf_Downloads, but it is empty.
There is no sf_Music folder.

What could I have done wrong?

---

### Post by jcoles on 2011-02-09
Even mounting manually is a complete fail!

mount -t vboxsf Music /home/jcoles/hostMusic
/sbin/mount.vboxsf: mounting failed with the error: No such device

Which item doesn't exist? vboxsf I would guess. But Guest Additions installed without error. Twice.

Perhaps I just have a bum VM. Typing in a guest terminal is quite laggy.

---

