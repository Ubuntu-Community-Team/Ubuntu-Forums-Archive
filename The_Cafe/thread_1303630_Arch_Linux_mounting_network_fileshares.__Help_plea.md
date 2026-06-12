---
title: "Arch Linux mounting network fileshares.  Help please."
date: 2009-10-28
forum: The Cafe
---

### Post by Crunchy the Headcrab on 2009-10-28
Hey guys.  I'm trying out Arch Linux again.  I've got it almost to the point where I want it with one exception.  I keep having a slow boot up whenever I'm not connected to my network because it gets to the process of mounting network file shares and fails (slowly).  I don't know why it is trying to mount network drives anyway.  I never asked it to do that and I don't WANT it to.  Help please.

---

### Post by Icehuck on 2009-10-28
> **Crunchy the Headcrab said:**
> Hey guys.  I'm trying out Arch Linux again.  I've got it almost to the point where I want it with one exception.  I keep having a slow boot up whenever I'm not connected to my network because it gets to the process of mounting network file shares and fails (slowly).  I don't know why it is trying to mount network drives anyway.  I never asked it to do that and I don't WANT it to.  Help please.

You can edit /etc/rc.conf and go down to daemons and put a ! in front of rpcbind portmap and nfs-common(nfs-lock). So they would look like !rpcbind !portmap and !nfs-common. Though if you are going to use Arch, read the wiki. Just about everything is in the Wiki.

---

### Post by Tibuda on 2009-10-28
No idea, as I don't use Arch, but have you looked at your fstab (if there's such file in arch)?

I think you would get better support at [http://bbs.archlinux.org/](http://bbs.archlinux.org/)

EDIT: or what Icehuck said

---

### Post by Crunchy the Headcrab on 2009-10-28
Edit: ah, it was there.  netfs has now become !netfs (thanks)

---

