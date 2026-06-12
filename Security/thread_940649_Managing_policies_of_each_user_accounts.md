---
title: "Managing policies of each user accounts?"
date: 2008-10-07
forum: Security
---

### Post by sh_son on 2008-10-07
Hi,

I just got to know to Linux been a while since my first install of Ubuntu but back to Macintosh for multimedia production.

I have a desktop at school in boarding house I'm thinking about to make that desktop as some kind of all-share computer, then creating accounts in groups (students, admin, viceadmin etc) with different policies applied such as can not open Terminal, No access to Filesystem folder, no external devices to be attached, limited broadband usage etc. 

In this way, they can not modify rights to themselves, playing around with system files; fully managed. Is this possible?

Thank you in advance.

---

### Post by cdenley on 2008-10-07
> **sh_son said:**
> Hi,

I just got to know to Linux been a while since my first install of Ubuntu but back to Macintosh for multimedia production.

I have a desktop at school in boarding house I'm thinking about to make that desktop as some kind of all-share computer, then creating accounts in groups (students, admin, viceadmin etc) with different policies applied such as can not open Terminal, No access to Filesystem folder, no external devices to be attached, limited broadband usage etc. 

In this way, they can not modify rights to themselves, playing around with system files; fully managed. Is this possible?

Thank you in advance.

Some of what you mentioned can be done through user properties.
System>Administration>Users and Groups
Users cannot modify any system files or user properties unless they are a member of the "admin" group.

I'm not sure what you meant by "No access to Filesystem folder". If you mean you want to prevent them from browsing outside their home directory, I'm not sure how that can be done besides making a chroot environment for each user.

You can change the permissions on gnome-terminal, but there will probably be another way for users to access a terminal (like ctrl+alt+f1).
```

sudo addgroup terminal
sudo adduser myuser terminal
sudo chgrp terminal /usr/bin/gnome-terminal /usr/bin/lxterm /usr/bin/uxterm /usr/bin/x-terminal-emulator /usr/bin/xterm
sudo chmod 750 /usr/bin/gnome-terminal /usr/bin/lxterm /usr/bin/uxterm /usr/bin/x-terminal-emulator /usr/bin/xterm

```

---

### Post by sh_son on 2008-10-07
Thanks for you reply,

Yes, I do not un-privileged users to access Filesystem so they can not force-modify or do something to the system. There seems not much policies I can give to each users. Maybe I should give more privileges.

Thanks btw;

---

### Post by cdenley on 2008-10-08
> **sh_son said:**
> Thanks for you reply,

Yes, I do not un-privileged users to access Filesystem so they can not force-modify or do something to the system. There seems not much policies I can give to each users. Maybe I should give more privileges.

Thanks btw;

Well, only users with root access can modify the system. Root is the owner, and the files are only writeable by root.
```

ls -L -h -l /usr/bin

```
You can't take away read permissions for the system, because the users actually need to use the system. There might be a way to disable the browsing through nautilus, but it's not like they will be able to change anything just because they can see it.

---

