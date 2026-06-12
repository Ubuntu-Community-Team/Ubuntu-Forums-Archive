---
title: "suspend problem with Unity/gnome-shell?"
date: 2012-09-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kurt18947 on 2012-09-15
I hesitate to report this as a bug if it's a known problem.  My 12.10 install using either Unity and gnome-shell does not want to suspend.  The menu item is there but when I click on it but the click has no apparent effect.  I have Xfce-desktop installed and suspend works properly there so I assume it's a gnome issue, not a linux issue.  I have an Nvidia GS8400 video card and current Nvidia drivers is use if that matters.    I can switch to an account with sudo privileges and "sudo bash pm-suspend" works properly.  New bug, known bug or I just don't know how to search properly? Thanks for any input.

The update on September 19 fixed the problem.  I also found that if I logged out then clicked 'suspend' it worked as expected.  I tried a new account thinking my 'normal user' account may have somehow become corrupted but nope, would not suspend using either Unity or Gnome shell.  I looked at different logs and couldn't see the problem.  All seems well now so I marked this "solved".

---

