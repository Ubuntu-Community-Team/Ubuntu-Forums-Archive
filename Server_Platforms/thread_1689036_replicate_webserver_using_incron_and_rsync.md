---
title: "replicate webserver using incron and rsync"
date: 2011-02-16
forum: Server Platforms
---

### Post by denzky on 2011-02-16
hi,
 
we have two web server and we want to replicate it when some changes are made to primary server. my idea are to use incron to monitor changes in directory and rsync to sync files when the directory are changes.
 
my problem are whenever incron call rsyc. it execute rsyc but rsync not do anthing. i did this setup from reading this [http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/](http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/)
 
here is my incrontab
/var/www/html/Sites/ IN_CREATE,IN_DELETE /usr/bin/rsync -a /var/www/html/Sites/ root@192.168.2.231:/var/www/html/Sites/
 
I did it also via script but the results are the same. here is my script
 
#!/bin/bash
 
#variable to modify
USER="root"
SRCDIR="/var/www/html/Sites/"
DSTDIR="/var/www/html/Sites/"
DSTIP="192.168.2.231"
OPTS=" --exclude '*.tmp' -a --delete"
 
#passwordless login
source $HOME/.keychain/$HOSTNAME-sh
 
rsync $OPTS $SRCDIR $USER@$DSTIP:$DSTDIR 
 
someone can help me to solve this problem. thank you

---

