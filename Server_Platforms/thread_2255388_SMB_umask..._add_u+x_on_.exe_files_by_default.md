---
title: "SMB umask... add u+x on .exe files by default?"
date: 2014-12-04
forum: Server Platforms
---

### Post by talz13 on 2014-12-04
I use a LAN share on my ubuntu server as my Downloads folder on my win7 desktop.  Lately I've noticed that I cannot run programs from my downloads folder over the LAN, and tracked it down to the permissions that are being applied on the server on file creation (600).

Is there a simple way to automatically apply a 700 permission set to specific file extensions on creation?  I really don't want to make EVERYTHING executable if I can help it, just looking to save myself from having to manually add X permission all the time.

---

### Post by nerdtron on 2014-12-04
Hmmm... just passing by and haven't analyzed thoroughly but maybe this link can help [http://askubuntu.com/questions/210808/set-umask-set-permissions-and-set-acl-but-samba-isnt-using-those](http://askubuntu.com/questions/210808/set-umask-set-permissions-and-set-acl-but-samba-isnt-using-those)

---

