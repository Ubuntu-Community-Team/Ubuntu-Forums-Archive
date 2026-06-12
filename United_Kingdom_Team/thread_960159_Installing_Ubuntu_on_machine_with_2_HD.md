---
title: "Installing Ubuntu on machine with 2 HD"
date: 2008-10-27
forum: United Kingdom Team
---

### Post by Mark224 on 2008-10-27
Hi,

I have installed Ubuntu 8.04 on a machine with 2 x 80GB hard disks.  I accepted all the default options and it has formatted and installed Ubuntu on one disk and left the other disk completely alone.  I would like to use the second hard disk but I am not sure how to do this.  Can anyone advise which tools are used for this?

Also what would be a good layout?  Should I move the swap and/or home directories onto the other disk?  If so, how?

TIA, M.

---

### Post by freesitebuilder on 2008-10-29
I use Gparted (Gnome partition editor) [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) to partition my disks and move the partitions when I need. Make sure you backup important data first though!

I've got two drives - I have root and /home on one, /swap and backup on the other.

I have Gparted on a liveCD - I boot from gparted Cd when I want to move partitions, so my system isn't running when I do it. The tutorials on the gparted documentation page are good.

---

### Post by Mark224 on 2008-10-30
Thanks. I have done this.  However it mounts it in a hidden directory under my home directory.  How can I get it to mount somewhere else so it is accessible to all users?

Thanks.

---

