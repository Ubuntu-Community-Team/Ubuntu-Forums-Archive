---
title: "? ubuntu automysqlbackup bug ?"
date: 2013-12-02
forum: Server Platforms
---

### Post by pdcooper on 2013-12-02
previously i've used automysqlbackup from sourceforge, but on my new server have installed the ubuntu package. 
the script looks for  /etc/default/automysqlbackup   which lets you set the db username and password. 
But the /etc/default/automysqlbackup  file  gets a database list,  trying to use the  /etc/mysql/debian.cnf   file for credentials ,even if the username and pw have been redefined a few lines higher in the script.
 the problem is this line 
DBNAMES=`mysql --defaults-file=/etc/mysql/debian.cnf --execute="SHOW DATABASES" | awk '{print $1}' | grep -v ^Database$ | grep -v ^mysql$ | tr \\\r\\\n ,\ `

it needs to use $USERNAME and $PASSWORD , but i dont know how to do that in bash without gettign quotes and backticks and the rest all muddled

---

### Post by pdcooper on 2013-12-02
got it  - it needs to be replaced with this 
DBNAMES=`mysql -u $USERNAME -p$PASSWORD --execute="SHOW DATABASES" | awk '{print $1}' | grep -v ^Database$ | grep -v ^mysql$ | tr \\\r\\\n ,\ `
echo $DBNAMES

---

