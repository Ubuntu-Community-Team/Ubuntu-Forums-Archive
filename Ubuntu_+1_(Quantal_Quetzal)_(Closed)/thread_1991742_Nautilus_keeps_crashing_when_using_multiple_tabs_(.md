---
title: "Nautilus keeps crashing when using multiple tabs (64-bit)"
date: 2012-05-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by OGpmpdog on 2012-05-30
Hi all, I hope all is well...UDS-Q was amazing, I was overwhelmed by passionate developers sharing their Ubuntu knowledge.

Using GUI, Nautilus keeps crashing whenever I use multiple tabs to view files in different locations...my updates are current, and this crash keeps happening.

I've been using Gnome 3, so I dont know if this bug recurs in Unity or Classic.

Using Desktop w/ Sandy Bridge CPU and Nvidia 8400GS Card...

I want to learn as much as I can this cycle:lolflag:...is there a log I can view to see what made Nautilus unhappy?

Thanks...it's breakage time...

---

### Post by jerrylamos on 2012-05-31
Nautilus keeps crashing when using multiple tabs (32-bit).  On a tower, a notebook, and this netbook.

Just updated 31 May and nautilus still crashes.  Launchpad closed my bug #1006651 because it wasn't entered to their satisfaction.  That doesn't fix the bug.

Jerry

---

### Post by mc4man on 2012-05-31
It's possible you're seeing this current bug or a variation of
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1002506](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1002506)

When it happens ck. in bottom of  ~/.xsession-errors, you may see something like this or similar
ERROR:nautilus-places-sidebar.c:1885:open_selected_bookmark: assertion failed: (sidebar->go_to_after_mount_slot == NULL)

---

### Post by jerrylamos on 2012-05-31
There are a ton of errors in .xsession-erros.  One is:

ERROR:nautilus-places-sidebar.c:1885:open_selected_bookmark: assertion failed: (sidebar->go_to_after_mount_slot == NULL)

Nothing today in /var/crash.

I'm getting muliple tab error on tower, netbook, and notebook.  I haven't found a way to get ubuntu-bug to successfully issue a launchpad bug.  Example ubuntu-bug /var/crash/whichever crash never successfully starts launchpad.  Yes I do chmod 666 on the crash report.  

Let me try again specifying xorg.  Entered bug #1007001.

Jerry

---

### Post by mc4man on 2012-05-31
> **jerrylamos said:**
> There are a ton of errors in .xsession-erros.  One is:

ERROR:nautilus-places-sidebar.c:1885:open_selected_bookmark: assertion failed: (sidebar->go_to_after_mount_slot == NULL)
  Entered bug #1007001.

Jerry

Well good luck with that - 
The nautilus bug I linked above, which has been easily confirmed by other users based on description has now, like your previous, been marked invalid & requested that a new be filed using apport or ubuntu-bug > the /var/crash/,crash

What they (Seb) don't seem to get is that is currently impossible, no matter how you do it all /var/crash/whatever.crash go somewhere or nowhere but won't open a LP report
Atm it's just a bit of waste of time, if they're going to some db , well great, not doing the reporter any good

Maybe they're going/adding to here except this doesn't have dev related, only releases
[https://errors.ubuntu.com/](https://errors.ubuntu.com/)

---

