---
title: "squirrelmail error"
date: 2009-04-07
forum: Server Platforms
---

### Post by Ubunt2u on 2009-04-07
when trying to send mail through squirrelmail with attachment (4.45 MB) i get this error message: "ERROR:
Could not move/copy file. File not attached"

If i use thunderbird, it goes through perfectly.

This just started today.  Hasn't been an issue before.  I've made no changes to configuration to cause this.

Can anyone help?

ps, it seems to be related to file size.  when i send smaller files it works.  but like i said, i can send the big ones fine through thunderbird.

---

### Post by Ubunt2u on 2009-04-07
Fixed.

PHP must've been updated and reset to default values.  Changed the php.ini upload_max_filesize & post_max_size in /etc/php5apache2/php.ini and it works now.

---

