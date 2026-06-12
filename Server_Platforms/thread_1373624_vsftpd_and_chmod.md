---
title: "vsftpd and chmod"
date: 2010-01-05
forum: Server Platforms
---

### Post by lafever on 2010-01-05
For some reason when I upload files using vsftpd they are default CHMOD to 700. I tried using this option in my vsftpd.conf

file_open_mode=0755 

to get them to default CHMOD at 755 but it's not working. Is this the right option to be using or is there another issue?

Thanks for the help.

---

