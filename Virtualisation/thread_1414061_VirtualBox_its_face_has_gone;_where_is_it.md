---
title: "VirtualBox: its face has gone; where is it?"
date: 2010-02-23
forum: Virtualisation
---

### Post by greenshirt11 on 2010-02-23
virtualbox-3.1.4 (from [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/))
kubuntu-9.10
kernel 2.6.31-19-generic

About a month ago everything worked ok with virtualbox-3.1.2. 
Now for some reason the GUI of VirtualBox does not show up anymore.
The icon shows up on the panel for a while and then disappears.

No error messages from kernel logs or otherwise as i can see.
Following is running afterwards:

```
ps ax | grep Box
12097 ?        Sl     0:00 /usr/lib/virtualbox/VirtualBox
12111 ?        S      0:00 /usr/lib/virtualbox/VBoxXPCOMIPCD
12120 ?        Sl     0:00 /usr/lib/virtualbox/VBoxSVC --pipe 8 --auto-shutdown

```

I completely uninstalled virtualbox and reinstalled again without change.
Has anybody got an idea what is going on or how to approach this?
Should i reinstall 3.1.2?

thanks

---

### Post by greenshirt11 on 2010-02-26
From what i have now it seems to me a Kubuntu problem:
- removed virtualbox completely
- created a separate user account for system administration (install packs, user admin)
- installed virtualbox again from that account
- created a new user account; only member of vboxusers, no other groups
- reboot
- login on new user account; run VirtualBox

This works for now. There are some things happening that seem strange nonetheless.

---

