---
title: "backup questions..."
date: 2007-01-11
forum: Server Platforms
---

### Post by tocleora on 2007-01-11
I want to use one server to backup .sql and web page files from other servers on my network.  All the servers are Linux.  Is there a good gui to do this?  And do I have to use samba to map those drives or ssh to each server or ftp or what's the best way to get the files from each server?  Thanks in advance.

---

### Post by LotsOfPhil on 2007-01-11
Do you only want to do this a few times? I do something similar and just wrote a script and then used cron. 

#!/bin/bash
/usr/bin/mysqldump --all-databases -u root --password=yourPW > ~/all_DB.sql
tar cjf /all_DB.tar.bz2 /all_DB.sql
mv /all_DB.tar.bz2 /storage
rm /all_DB.sql

You could put this on your server with the .sql and web stuff. Then just make the cron job "ssh server /run/the/script"

---

### Post by tocleora on 2007-01-11
That looks like that's for the same server, this server will be dedicated to backing up so it will need to get the files from a different server.  so somehow through either samba or ftp or ssh I need to move the files from one server to the other.  Am I misunderstanding what you're saying?

---

### Post by LotsOfPhil on 2007-01-11
How about:

#!/bin/bash
/usr/bin/mysqldump --all-databases -u root --password=yourPW > ~/all_DB.sql
tar cjf /all_DB.tar.bz2 /all_DB.sql
scp /all_DB.tar.bz2 othercomputer:/where/it/should/go
rm /all_DB.sql all_DB.tar.bz2

If you put that script on the remote computer and execute it via "ssh remotecomputer:/run/the/script" it will work.

---

