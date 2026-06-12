---
title: "Bash Script not working"
date: 2011-12-03
forum: Server Platforms
---

### Post by DanHorniblow on 2011-12-03
Hi, I have got a little bash script for adding users to MySQL.

I want it to create a user and then grant all privileges on wildcard name (username\_%).

This is what I have now.

```
#!/bin/bash

EXPECTED_ARGS=2
E_BADARGS=65
MYSQL=`which mysql`


Q2="GRANT ALL ON '$1\_%' .* TO '$1'@'localhost' IDENTIFIED BY '$2';"
Q3="FLUSH PRIVILEGES;"
SQL="${Q2}${Q3}"

if [ $# -ne $EXPECTED_ARGS ]
then
  echo "Usage: $0 dbuser dbpass"
  exit $E_BADARGS
fi

$MYSQL -u root -p -e "$SQL"
```

When I run
```
./mysql.sh testusr testpass
```

I enter the MySQL root password, and then I get this error

```
ERROR 1064 (42000) at line 1: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''testusr\_%' .* TO 'testusr'@'localhost' IDENTIFIED BY 'testpass'' at line 1
```

Any ideas whats going wrong?

---

### Post by volkswagner on 2011-12-03
I would change:

```
'$1\_%' .*
```

to this:

```
'$1\_% .*'
```

I'm not sure if '\' is a valid character for a DB name.  If you are trying to have the DB nameing scheme = username, why not just do:

```
'$1.*'
```

or to keep the under score try:

```
'$1_.*'
```

I'm no script writer, but this type of interaction can help me and you!


OK, 

I ran through this.  You actually need to get rid of the single quotes all together as they are not needed when describing the database.

this seems to work:

```
#!/bin/bash

EXPECTED_ARGS=2
E_BADARGS=65
MYSQL=`which mysql`


Q2="GRANT ALL PRIVILEGES ON $1_.* TO '$1'@'localhost' IDENTIFIED BY '$2';"
Q3="FLUSH PRIVILEGES;"
SQL="${Q2}${Q3}"

if [ $# -ne $EXPECTED_ARGS ]
then
  echo "Usage: $0 dbuser dbpass"
  exit $E_BADARGS
fi

$MYSQL -u root -p -e "$SQL"

```

Again I'm not sure what you want the database name scheme to look like, so your setup will vary.

You will also need to create the database, as this does not create it for you.

---

### Post by DanHorniblow on 2011-12-03
Hi, thanks for your reply.

I am developing a hosting solution for the students at a College that I work at, I want a automated script that I can run, which will create a MySQL user and allow that user to create multiple databases named {username}_{databasename}.

With the script you posted, users can only create 1 database named "{username}?". Im very confused where the "?" is coming from?

Any sugestions

---

