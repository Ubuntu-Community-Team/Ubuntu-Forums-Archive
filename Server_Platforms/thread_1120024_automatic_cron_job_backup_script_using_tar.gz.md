---
title: "automatic cron job backup script using tar.gz"
date: 2009-04-08
forum: Server Platforms
---

### Post by plasmafusion on 2009-04-08
hello all
i'm looking to automate a back up of my webserver's directory stucture.
i've created a backup script like this...

> #!/bin/bash
tar czf /home/user/cloud/backup/web/web_backup_08_04_09.tar.gz /var/www/

and would like to stick it in cron.daily.
how could i change it so that the date is automatically adjusted to reflect the current date?
thanks in advance :)

---

### Post by unutbu on 2009-04-08
[PHP]#!/bin/bash
today=$(date '+%d_%m_%y')
tar czf /home/user/cloud/backup/web/web_backup_"$today".tar.gz /var/www/
[/PHP]

---

### Post by plasmafusion on 2009-04-08
crikey...that was quick!
thanks for getting back to me...i appreciate it. 
will give this a bash (pun intended) tomorrow.

EDIT :: UPDATE

that works a treat unutbu...cheers for your help.

---

