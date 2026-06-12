---
title: "Samba file sharing service"
date: 2012-05-30
forum: Server Platforms
---

### Post by mosaic2s on 2012-05-30
Using samba for sharing folders over network. Have changed the permissions of folders by using

> chmod ugo+rwx . -R


When someone creates a new folder within the shared folder, the new folder shows a lock sign. Can this be avoided?

---

### Post by lykwydchykyn on 2012-05-30
Yes.  your share definitions can make use of directives like "create mode", "directory mode", "force user", or "force group" to set the ownership & permissions of created files & folders automatically.

For usage information see this:

[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

---

### Post by mosaic2s on 2012-05-31
Changed file and directories permissions to 0777 from 0700 in smb.conf.
It is working okay now.

---

