---
title: "MySQL 4, remote connection, error 2013"
date: 2005-11-18
forum: Server Platforms
---

### Post by heisters on 2005-11-18
Hi all. I'm setting up a simple MySQL DB, but running into strange, and probably stupid (on my part) problems. I've got MySQL running, I can login on localhost la-de-da. I went into /etc/mysql/my.cnf and added a bind-address to the host's IP address, but when I try to login form a remote workstation I get

```

$ mysql -u website -h host -p
Enter password: 
ERROR 2013 (HY000): Lost connection to MySQL server during query

```

WTF? Am I missing some simple configuration flag? netstat makes it look dandy:

```

tcp        0      0 host.domain:mysql *:*                     LISTEN     2574/mysqld

```

Any suggestions would be greatly appreciated. This is on Breezy.

---

### Post by mgor on 2005-11-18
do your user have rights to connect from anywhere else then localhost?
type this in mysql as root,
```
use mysql;
select Host, User from user;
```

if it says 'localhost' for your user, then that's where the problem lies.

if you want your user to be able to connect from any host, run something like
```
grant select,insert,update,delete on database.* to <user>@'%';
```

you could change % to a hostname if you want to limit the access.

---

### Post by heisters on 2005-11-18
Hm, I don't think that's it. My user table has this:
```

+-----------+------------------+
| Host      | User             |
+-----------+------------------+
| %         | website          |

```
Which, I would think would allow the user 'website' to connect from any host. Which is what I've been trying.

Thanks for the suggestion.

---

### Post by heisters on 2005-11-21
any other ideas, anyone?

---

### Post by heisters on 2005-11-21
Solved. Added

```

mysqld:all

```

to /etc/hosts.allow The clue was that mysql wasn't logging any errors or warnings, even with elevated logging, so the connection must have been denied before it ever got to mysqld. Still, the client's error message could be a good deal clearer.

---

