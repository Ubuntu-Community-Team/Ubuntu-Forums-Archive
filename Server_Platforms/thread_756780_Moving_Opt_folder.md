---
title: "Moving /Opt folder"
date: 2008-04-16
forum: Server Platforms
---

### Post by Emj on 2008-04-16
Are there are things I should look out for before moving the /Opt folder?

I have a 7.10 server with two fixed disk arrays (with /root, /home, etc mounted on one and /var mounted on another). I want to add a third disk array and move /opt to that new one. /Opt is currently empty and will have Lotus Domino installed (which is why I need the extra space).

Is it just a matter of deleting the current /Opt folder and mounting the new drive as /Opt?

Many thanks.

---

### Post by kidders on 2008-04-17
Hi there & welcome,

The short answer is yes, really. Some pointers ...

[LIST]
[*]Normally, you would first do something like **lsof | grep /opt**, just to be sure nothing you are about to move/delete is in use by anything that might get upset. Your /opt is empty though, so you can ignore that step.
[*]There is no reason to delete & recreate /opt. You *do* want to do something like **ls -ld /opt** though, so you can note the directory's ownership & permissions. If mounting your new /opt filesystem causes them to change, you'll need to correct that.
[*]Running **mount /dev/whatever /opt** as root is basically it. Afterwards, you should check the mount point's permissions & update your /etc/fstab, so /opt will be mounted automatically in future.
[*]Unlike /boot or /, there are not normally any restrictions on your choice of filesystem type/configuration, so you can use whatever would make Domino happiest. Where applicable (eg for Ext3), you might want to set the reserved disk space percentage to zero.
[/LIST]

I hope that helps.

---

