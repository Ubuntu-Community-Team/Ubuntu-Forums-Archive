---
title: "mysql and dotProject backup (ubuntu 7.04)"
date: 2007-09-20
forum: Server Platforms
---

### Post by artfutura on 2007-09-20
I´ve written the following script to take a full offline backup of dotproject and all mysql databases

Perhaps somebody will find it helpful

I suggest running it at 4am with cron as root

```
#!/bin/sh
# This script has been tested with ubuntu server 7.04 use it with caution elsewhere verifying paths are correct
#next line stops mysql so we can do a flat backup
sudo /etc/init.d/mysql stop
tar cvpfz /root/mysqlbackup.tar.gz /var/lib/mysql /etc/mysql /var/www/dotproject
# next line generates timestamp : YYYYMMDD-mmss
timestamp=$(date +"%Y%m%d-%M%S")
# next line renames backup file to a unique name by appending a timestamp to its name
mv /root/mysqlbackup.tar.gz /root/mysqlbackup.tar.gz.$timestamp
#next line start mysql 
sudo /etc/init.d/mysql start

```

---

