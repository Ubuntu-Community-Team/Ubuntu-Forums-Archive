---
title: "Specific block devices with user level r/w?"
date: 2012-11-13
forum: Security
---

### Post by Pro_D on 2012-11-13
Not really sure how to ask since I seem to be having a hard time framing the question for a Google search.  Here is an example.

System has 3 physical devices, sda, sdb, sdc (and related numbers for partitions, ie sda1).  These are root/disk permission and this is good.

I plug in 2 more disk drives (esata hot swap) and these devices show up as sdd and sde, also with root/disk permission.  This is not so good.

What I would love to have happen is for those additional devices to show up user/disk (or something like that).  This way I can use tools like dd on them at the user level, no sudo, no adding the user to disk group.

This would allow me to keep from damaging sda-sdc with a typo (I haven't yet but it's bound to happen eventually).  Also this would ease my mind some if I wasn't the one typing the commands.

Ideally the partitions would also be user level (so sdd1 and sde1 if they each had one partition).

If it helps/matters the systems in question are an ubuntu server (12.04), though another system is ubuntu desktop (10.04, for now).

hrm, finally got a hit on udev, need to do some reading...

[edit]
Wow, that ended up easier than I expected... I figured I would be reading and whatnot for a while.  Still not the best solution but what I have is:

create a new file /etc/udev/rules.d/disk-permissions.rules
Add in one line each for each device like so:
KERNEL=="<blockdev>*", OWNER="<user>"
where <blockdev> is something like sdd and <user> is the account to own the object.
for example
KERNEL=="sdd*", OWNER="user"
This will cause the device that ends up in sdd and all partitions (the asterisk) to have ownership of user instead of root. :)

Now the hard part, leaving sda-sdc as root/disk while having all after have user/disk permission, preferably without tons of lines.  I will need a separate machine (vm) to see if I can figure this bit out.
[/edit]

---

