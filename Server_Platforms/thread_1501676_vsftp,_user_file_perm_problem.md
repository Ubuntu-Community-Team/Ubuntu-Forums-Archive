---
title: "vsftp, user file perm problem"
date: 2010-06-04
forum: Server Platforms
---

### Post by Mainer82 on 2010-06-04
I installed and configured vsftp and have a local user created that can FTP into the server from another computer on the network, however whenever they upload a file/folder the file permission is not set right, I have to manually set it to 755 each time something is created.

I am using Ubuntu 9.10 Server

What am I doing wrong?

---

### Post by pricetech on 2010-06-04
There's a setting for that in the configuration file.  I don't remember what the default is, but it's well worth checking.

---

### Post by Bachstelze on 2010-06-04
> **pricetech said:**
> There's a setting for that in the configuration file.  I don't remember what the default is, but it's well worth checking.

[font=monospace]local_umask[/font]. It should be set to [font=monospace]022[/font] to have files chmodded 755 (it is 077 by default, so files are chmodded 700).

---

