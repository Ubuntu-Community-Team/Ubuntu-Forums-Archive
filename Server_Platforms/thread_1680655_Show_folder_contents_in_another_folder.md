---
title: "Show folder contents in another folder"
date: 2011-02-02
forum: Server Platforms
---

### Post by mrfarrell on 2011-02-02
can i use one samba share with a folder showing the contents of another directory.
shortcuts don't work on non ubuntu systems and it won't resolve links to files no on the share

---

### Post by AlecJ on 2011-02-02
In Windows you have to Map the share to a drive.
F: and so on, then you can shortcut to a folder.

---

### Post by mrfarrell on 2011-02-03
i should have said i meant a shortcut in the share to a directory, also on the server, that is not shared. Does that help?

---

### Post by AlecJ on 2011-02-03
> **mrfarrell said:**
> i should have said i meant a shortcut in the share to a directory, also on the server, that is not shared. Does that help?

Not much.

if you share for example on PC 1
/media/Music

you will see on the network PC 1\Music

Oh I see you want to put a shortcut in the Music folder to elsewhere on PC1?

If the folder you want to shortcut too is also shared, it should work, but not if it's not shared.

---

### Post by dtfinch on 2011-02-03
Samba by default will disable symbolic links to files/folders outside of a share as a security precaution.

[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WIDELINKS](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#WIDELINKS)

If you enable wide links (allowing symlinks to outside the share), disable unix extensions (because otherwise it disables wide links), and restart samba, you should be able to have it follow symlinks. There's also a follow symlinks option but it's enabled by default.

---

### Post by mrfarrell on 2011-02-03
Thank you!
thats a perfect solution!

---

