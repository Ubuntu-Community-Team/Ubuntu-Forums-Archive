---
title: "Non-graphical FTP client"
date: 2009-08-20
forum: Server Platforms
---

### Post by Kenzo on 2009-08-20
I'd like to hear from anyone using a non-graphical FTP client/user to send files to a Proftpd server - Jaunty 9.04 or other version.
Thanks

---

### Post by Bachstelze on 2009-08-20
```
man ftp
```

---

### Post by chalex on 2009-08-20
the session would go something like this
ftp
open server.name.fqdn
(enter username and password)
bin
put filename.avi
bye

---

### Post by grantemsley on 2009-08-20
My favorite is gftp.

---

### Post by scorp123 on 2009-08-20
> **Kenzo said:**
> I'd like to hear from anyone using a non-graphical FTP client/user to send files to a Proftpd server You could give **mc** a try, looks and feels like good ol' Norton Commander. And it can handle remote connections too, e.g. FTP. I personally use **ncftp** and **yafc**. The latter can also handle SSH/SFTP connections.

---

### Post by nix4me on 2009-08-20
lftp is my favorite.

---

### Post by Kenzo on 2009-08-21
Thanks to all for the suggestions.  Have you struck any problems with PAM  -  unable to determine displaydevice at login?

---

