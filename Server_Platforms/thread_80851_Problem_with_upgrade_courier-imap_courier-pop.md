---
title: "Problem with upgrade courier-imap courier-pop"
date: 2005-10-23
forum: Server Platforms
---

### Post by ivomans on 2005-10-23
During apt-get upgrade the upgrade of courier-imap and courier-pop packages gets stuck on an error:
```
unable to create `./usr/share/courier/webadmin/admin-45pop3.html': Permission denied
``` I tried [FONT=Courier New]sudo rm /usr/share/courier/webadmin/admin-45pop3.html[/FONT] but this also results in a Permission denied.

I tried to see if this file is opened by some process with [FONT=Courier New]sudo fuser[/FONT], but this doesn't report an open file.

The file permissions: [FONT=Courier New]-rw-r--r-- root root
[FONT=Verdana]
What else could block this file?

Ivo.

[/FONT][/FONT]

---

