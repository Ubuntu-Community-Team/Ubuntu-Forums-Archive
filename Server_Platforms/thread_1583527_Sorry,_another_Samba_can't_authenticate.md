---
title: "Sorry, another Samba can't authenticate"
date: 2010-09-28
forum: Server Platforms
---

### Post by 1serveyou on 2010-09-28
I have samba allowing only known users, and on the ubuntu side, I have the folder permission 777. I have the same exact samba smb.conf file(locations of course matching new server), but I can't get it to authenticate with the new server(Old server is up and running too) and I'm lost. Any help would greatly be appreciated. I thought I had it figured out when I did my last server, but I seem to be missing something on this one.

---

### Post by HermanAB on 2010-09-28
Test it manually with 'smbclient'.  That will give you error messages that you can then Google for if they don't make sense immediately.

---

