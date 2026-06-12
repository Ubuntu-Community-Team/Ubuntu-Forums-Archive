---
title: "Automount on Ubuntu Server (Hardy / 8.10)"
date: 2008-12-28
forum: Server Platforms
---

### Post by flamacue on 2008-12-28
I would like for my Ubuntu Server machine to automount USB drives, eSATA drives, and CD/DVD-ROMs, like ubuntu-desktop does.

I can understand why this isn't the default behavior (if indeed it isn't), but I would think it ought to be an option, and an easy thing to enable.  However, I haven't found anything that works.

I'm running Hardy (8.10) Server on AMD64.  I do have webmin installed, but there is no GUI (i.e. no X, no ubuntu-desktop, etc.).

Thanks in advance for any help.

---

### Post by Drezard on 2008-12-28
Theres no real magical way of doing it sorry.

The only way really is through the mount command. The only complex solution (as sys admins like to do) is to write a perl or bash script that checks for new devices and automounts them, but otherwise im not sure there is a package (google it) for this.

Daniel

---

