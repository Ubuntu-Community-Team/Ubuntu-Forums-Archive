---
title: "Problem updating python-gnome2-desktop"
date: 2007-07-08
forum: Repositories &amp; Backports
---

### Post by KYhillbilly2006 on 2007-07-08
I'm running Dapper Drake and would like to update my python-gnome2-desktop to the latest version.  When I try to apt-get this is what happens:

family@family-desktop:~$ apt-get install python-gnome2-desktop
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
family@family-desktop:~$ sudo apt-get install python-gnome2-desktop
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
family@family-desktop:~$ sudo apt-get python-gnome2-desktop
E: Invalid operation python-gnome2-desktop

What does all that mean?  I don't know what to do to fix it.  Help

---

### Post by dutch_gecko on 2007-07-11
The first error is since you aren't using root, which you do use in the second line. Here there's a conflict - do you already have some other program open and accessing the aptitude system? Make sure Synaptic, the Add/Remove programs dialogue and the update manager are all closed.

The last error is because you neglected to use "install" before giving the application name.

---

