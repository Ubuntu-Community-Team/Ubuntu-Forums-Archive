---
title: "Guest and 11.10 install"
date: 2012-01-18
forum: Virtualisation
---

### Post by jerrrys on 2012-01-18
Yesterday I did a fresh install of 11.10 with a 11.10 vBox and can't get it to work.  I have done this before and don't understand why Im getting so much grief now.

The vBox install starts out corrupted and in 20 minutes or so after install will become corrupted beyond use.  Things like keyboard slowing down; programs won't open; programs once open (after several tries) will show corruption on screen; etc.  For lack of a better way to put it; its like dbus is corrupted.  And all this without one error message.  

I have redone this install three times with same results in vBox.  And reinstalled the host once.

Build-essentials, dkms and all the right packages have been installed from the repositiories just like Ive done many times before.  Also PUEL installed (the right version).  Im running 4.1.2

The host basically is running lightdm, gnome-fallback, ubuntu-desktop (--no-recommends) and the guest will also run the same one day I hope.

any thoughts?

---

### Post by jerrrys on 2012-01-18
Update

Installed fluxbox and tried it.  First run; it worked out of the box for about 10 minutes before it too started to corrupt.  Tried to post from it, but ended up with system (guest) freeze before I could finish.

---

### Post by jerrrys on 2012-01-19
Well, it works today.  What I do to fix it?  Not sure; yesterday I screwed around with everything.  I am running the 3.*.0.9 kernel and afraid to change it.  Tis a mystery, but solved...

---

