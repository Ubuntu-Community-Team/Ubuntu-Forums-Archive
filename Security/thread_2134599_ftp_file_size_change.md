---
title: "ftp file size change"
date: 2013-04-11
forum: Security
---

### Post by imagiz on 2013-04-11
.

---

### Post by conradin on 2013-04-11
This raises a bunch of questions, so ill start at the basics.
what are you downloading? Is this content from a personal FTP server or an ftp server from some company?
what client are you using to do the downloading? Filezilla, wget, terminal ftp?
can you provide a link for anyone else to try an replicate this?
are you sure you are using ftp? I mean, ftp is far more likely to drop packets than to add packets, and sometimes using a webbrowser can cause confusion about whether something is coming down via ftp or http, or some other protocol.
can you get a checksum of the materials you are downloading?
Finally, is this some sort of streaming media you are trying to download?

---

### Post by imagiz on 2013-04-12
.

---

### Post by azzamite on 2013-04-12
How about using rsync instead of ftp?

Here are some interesting options:
```
-c, --checksum              skip based on checksum, not mod-time & size
-b, --backup                make backups (see --suffix & --backup-dir)
```

I don't know if it can work over ftp though.

---

