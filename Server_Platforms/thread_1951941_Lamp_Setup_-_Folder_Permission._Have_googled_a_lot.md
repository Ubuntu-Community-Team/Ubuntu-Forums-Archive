---
title: "Lamp Setup - Folder Permission. Have googled a lot, but still dont get it."
date: 2012-04-03
forum: Server Platforms
---

### Post by bizge on 2012-04-03
HI,

I am configuring a dedicated LAMP server provided by our Hosting Company. Managed to get vsftpd to upload files to var/www where the website will sit. I have chmod 777 the var/www folder but after I copy files I still need to chmod again otherwise PHP gives me a blank page.

Can you please help?

Thanks

---

### Post by nsnidanko on 2012-04-03
Do not chmod files to 777! Bad idea. Instead try to change owner and group. Apache2 runs as a www-data user and group (by default). 

So just do the following:

chown -R wwww-data /var/www
chgrp -R www-data /var/www

You upload files as a different user thus you get blank pages, apache2 doesn't have permissions on these files.

---

### Post by bizge on 2012-04-03
HI nsnidanko, 

thanks for your advice. I did as you have advised than gave a new passw to www-data and used that for ftp-upload. it seems to work now well. Just one more questions. Do I need to specifiy my domain that will be here or the zone file A record pointing to my IP will do the job? So its gets automatically loaded from /var/www doesnt it?

Thanks :)

---

