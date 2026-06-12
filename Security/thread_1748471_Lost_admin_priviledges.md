---
title: "Lost admin priviledges"
date: 2011-05-03
forum: Security
---

### Post by cwarner7_11 on 2011-05-03
I have encountered a new problem with administrative rights- essentially I have lost my sudo priviledges, and can't seem to get them back.  This appears to have occurred following a recent upgrade of Ubuntu 10.04.  It was working yesterday; today when I log on, I have no administrator privileges.  I have followed a number of differnet threads discussing this very same problem, and have tried the following:

1.  Boot into recovery mode.  Asks for a root password- my normal password does not work.  I have never to my knowledge activated the root account, and no root account shows up in "Users and Groups".

2.  Boot from live CD.  Mount the hard drive.  Edit the /media/[drive]/etc sodoers file.  Looks good, but add "[usrname]   ALL=(ALL)ALL" under the entry for "root" in the file.  Save it. chmod 0440 sudoers- not sure this was necessary, since the permissions looked OK anyway).

3.  My user is now included in "admin" group, but not in "sudo" group.  WHen I try to add the user in sudo group, I get this wiggly notice, something about needing authentication, that disappears too fast for me to read it.

This is a single-user installation.  Only one user, same user for 2 years, same password for two years, and suddenly I lose admin rights.  As I have said, I have followed a number of similar threads where the above actions were described, looked through the documentation, and find that I have hit a dead end.  Where do I go from here?

---

### Post by cwarner7_11 on 2011-05-07
OK, no replies or suggestions from anyone, so I had to solve this one myself.  Reinstalled Ubuntu 10.04 as dual boot, without erasing the faulty installation.  Everything works, and I still have access to my original installation...

---

### Post by aysiu on 2011-05-07
If you're asked for a password when you boot into recovery mode, then you set a root password at some point. If you've ever run the command ```
sudo passwd root
``` you've set a root password.

And this is precisely why many here discourage setting a root password. It makes recovery unnecessarily difficult.

In the future you can edit the /etc/group and /etc/sudoers files by booting up a Ubuntu live CD or USB and then mounting your drive and using ```
gksudo nautilus
``` to browse the mounted drive (otherwise you can't edit stuff). Or you could just not set a root password.

---

