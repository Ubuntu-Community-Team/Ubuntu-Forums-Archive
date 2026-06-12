---
title: "MariaDB - Export Users, Grants and Roles"
date: 2020-10-06
forum: Server Platforms
---

### Post by LHammonds on 2020-10-06
In the past, I've used the following command to export users and their privileges:

```
mysql --skip-column-names --no-auto-rehash --silent --execute="SELECT CONCAT('SHOW GRANTS FOR ''',user,'''@''',host,''';') FROM mysql.user WHERE user<>''" | mysql --skip-column-names --no-auto-rehash | sed 's/$/;/g' > /tmp/db-grants.sql
```

MariaDB [implemented roles]("https://mariadb.com/kb/en/roles/") in 2013 with version 10.  I have only just now started to utilize roles and found that it broke my backups.

That same command above will fail will it comes across a role name which is stored as a pseudo-user in the user table.  Example:

```
ERROR 1141 (42000) at line 4: There is no such grant defined for user 'r_myrole' on host '%'
```

To keep that syntax error from occurring, I modified the statement with a check for "is_role" as follows:

```
mysql --skip-column-names --no-auto-rehash --silent --execute="SELECT CONCAT('SHOW GRANTS FOR ''',user,'''@''',host,''';') FROM mysql.user WHERE user<>'' AND is_role='N'" | mysql --skip-column-names --no-auto-rehash | sed 's/$/;/g' > /tmp/db-grants.sql
```

Now the backup continues but the exported .sql file is worthless.  In the database design, all the grants were removed from the users and added to the roles which are not exported in that .sql file.  Even though the syntax is correct, the import will not work because it now looks like this:

```

GRANT `r_myrole` TO `u_myuser`@`localhost`;
GRANT USAGE ON *.* TO `u_myuser`@`localhost` IDENTIFIED BY PASSWORD 'mypassword';

```

#1 - The 1st command will not work when migrating to a new server because r_myrole does not exist AND the u_myuser does not yet exist.
#2 - The 2nd command will create the user but without any additional privileges (because the privileges are stored in the role).

So, to fix this, roles need to be exported 1st, then their associated grants, then the users and finally their granted role (with default setting)

I have yet to see where anyone on the Internet has addressed this since its inception 7 years ago.

I am thinking about writing a script that will create a usable .sql file  to import on a clean system but don't want to re-create the wheel if  not necessary.

Anyone know of a solution using the built-in features (preferred) or 3rd-party utility?

**EDIT #1:** Example of commands to create and assign a role:
```
CREATE ROLE r_db1;
GRANT SELECT,INSERT,UPDATE,DELETE ON db1.* TO r_db1;
CREATE USER 'u_db1'@'localhost' IDENTIFIED BY 'InsertPasswordHere';
GRANT r_db1 TO 'u_db1'@'localhost';
SET DEFAULT ROLE r_db1 FOR 'u_db1'@'localhost';

```

**EDIT #2:** The 1st roadblock is that this command does not exist:
```
SHOW CREATE ROLE r_dba1;
```
Which means I will have to export a list of roles and manually make each "create role" entry.

**EDIT #3:** I also asked this question at [MariaDB]("https://mariadb.com/kb/en/show-create-role/")

**EDIT #4:** Please up-vote these issues if you would like to see them resolved:

[MDEV-22311](https://jira.mariadb.org/browse/MDEV-22311) - implement SHOW CREATE ROLE
[MDEV-22313](https://jira.mariadb.org/browse/MDEV-22313) - SHOW GRANTS does not prints a user's default role

LHammonds

---

### Post by LHammonds on 2020-10-07
I will document the workaround for getting a good backup of users, grants and roles for the purpose of migrating a complete system from one server to another in this post.

The order these commands are executed are important so the creation of the commands will take account of this.  Role Creation -> Role Grants -> User Creation -> User Grants -> Role Defaults

[SIZE=5]Role Creation[/SIZE]

```
 mysql --skip-column-names --no-auto-rehash --silent --execute="SELECT User FROM mysql.user WHERE is_role = 'Y';" | sed 's/^/CREATE ROLE /;s/$/;/g;1s/^/## Create Roles ##\n/' > /tmp/role-create.sql
```

Example output:
```
## Create Roles ##
CREATE ROLE r_dba;
CREATE ROLE r_db1;
CREATE ROLE r_db2;
```

[SIZE=5]Role Grants[/SIZE]

```
mysql --skip-column-names --no-auto-rehash --silent --execute="SELECT CONCAT('SHOW GRANTS FOR ''',User,''';') FROM mysql.user WHERE is_role = 'Y'" | mysql --skip-column-names --no-auto-rehash | sed 's/$/;/g;1s/^/## Grants for Roles ##\n/' > /tmp/role-grants.sql
```

Example output:
```
## Grants for Roles ##
GRANT USAGE ON *.* TO `r_dba`;
GRANT ALL PRIVILEGES ON *.* TO `r_dba`;
GRANT USAGE ON *.* TO `r_db1`;
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE ON `db1`.* TO `r_db1`;
GRANT USAGE ON *.* TO `r_db2`;
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE ON `db2`.* TO `r_db2`;
```

[SIZE=5]User Creation[/SIZE]

```
mysql --skip-column-names --no-auto-rehash --silent --execute="SELECT User,Host,Password FROM mysql.user WHERE is_role = 'N' AND User NOT IN ('mariadb.sys','root','mysql');" | sed 's/\t/`@`/;s/\t/` IDENTIFIED BY `/;s/^/CREATE USER `/;s/$/`;/;1s/^/## Create Users ##\n/' > /tmp/user-create.sql
```

Example output:
```
## Create Users ##
CREATE USER `u_dba`@`localhost` IDENTIFIED BY `*0123456789012345678901234567891234567891`;
CREATE USER `u_db1`@`localhost` IDENTIFIED BY `*0123456789012345678901234567891234567891`;
CREATE USER `u_db2`@`localhost` IDENTIFIED BY `*0123456789012345678901234567891234567891`;
```

[SIZE=5]User Grants[/SIZE]

```
mysql --skip-column-names --no-auto-rehash --silent --execute="SELECT CONCAT('SHOW GRANTS FOR ''',User,'''@''',Host,''';') FROM mysql.user WHERE User <> '' AND is_role = 'N' AND user NOT IN ('mysql','mariadb.sys','root');" | mysql --skip-column-names --no-auto-rehash | sed 's/$/;/g;1s/^/## Grants for Users ##\n/' > /tmp/user-grants.sql
```

Example output:
```
## Grants for Users ##
GRANT `r_dba` TO `u_dba`@`localhost`;
GRANT USAGE ON *.* TO `u_dba`@`localhost` IDENTIFIED BY PASSWORD `*0123456789012345678901234567891234567891`;
GRANT `r_db1` TO `u_db1`@`localhost`;
GRANT USAGE ON *.* TO `u_db1`@`localhost` IDENTIFIED BY PASSWORD `*0123456789012345678901234567891234567891`;
GRANT `r_db2` TO `u_db2`@`localhost`;
GRANT USAGE ON *.* TO `u_db2`@`localhost` IDENTIFIED BY PASSWORD `*0123456789012345678901234567891234567891`;
```

[SIZE=5]Role Defaults[/SIZE]

```
mysql --skip-column-names --no-auto-rehash --silent --execute="SELECT default_role,User,Host FROM mysql.user WHERE is_role = 'N' AND User NOT IN ('mariadb.sys','root','mysql') AND default_role <> '';" | sed 's/\t/ FOR `/;s/\t/`@`/;s/^/SET DEFAULT ROLE /;1s/^/## Set Default Roles ##\n/;s/$/`;/' > /tmp/role-default.sql
```

Example output:
```
## Set Default Roles ##`;
SET DEFAULT ROLE r_dba FOR `u_dba`@`localhost`;
SET DEFAULT ROLE r_db1 FOR `u_db1`@`localhost`;
SET DEFAULT ROLE r_db2 FOR `u_db2`@`localhost`;
```

Thanks,
LHammonds

---

