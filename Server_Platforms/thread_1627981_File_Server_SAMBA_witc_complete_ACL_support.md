---
title: "File Server SAMBA witc complete ACL support"
date: 2010-11-22
forum: Server Platforms
---

### Post by pinguino99 on 2010-11-22
Hi all,

Actually we have a win2003 file server in a windows active directory, with more domain in trust.

I'd like to replace this file server with a samba file server.

With samba, Is it possible to specify permission only of the samba shares? If a directory is not shared,
can i specify its permission anyway? (in windows file server i can specify permission even of a single file).

Samba permission can be set only with setacl command or also using a windows gui, in the same way i do in win 2003 ?

Samba allow to specify every single permission? (read/write/change/delete etc) like in win 2003 "right click/properties/permissions" ?

Samba manages the locks of the files?? Example: if i am working on file xyz.doc, and my colleague try to access to the same file,
how samba acts??

I tried openfiler and freenas, but i don't have complete ACL support.
Also ASMDM (i am not sure if it's the right name) but no way.

Any suggestions?

Thanks anyway and regards
I.P.

---

