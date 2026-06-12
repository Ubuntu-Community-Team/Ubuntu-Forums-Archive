---
title: "mysql - users"
date: 2009-06-17
forum: Server Platforms
---

### Post by Malg on 2009-06-17
Hi,

I am running ubuntu9 sever with mysql. I would like to check all mysql users and their privileges. Is there a simple way of doing so from the command line?

Thank you

---

### Post by Girya on 2009-06-17
> **Malg said:**
> Hi,

I am running ubuntu9 sever with mysql. I would like to check all mysql users and their privileges. Is there a simple way of doing so from the command line?

Thank you

login into mysql from the command line: 

> mysql -u "username" -p

you'll get a prompt like this: mysql>

type:

> use mysql;<enter>


type: 

> select user from user;<enter>

to exit the mysql prompt type \q;

the above will just give u your users

---

### Post by LepeKaname on 2009-06-17
Run this:

```
mysql -uroot -p mysql -e "SELECT user, host FROM user"
```

Its almost the same as Girya posted but only in one command. Also it displays the host which is very important.

Sometimes is good to show also passwords like:

```
"SELECT user, host, password FROM user"
```

to see if all of them has passwords and there is no "empty" password accounts.

To know if some user has access to some database you can execute for example:

```
SELECT u.user,u.host,d.db,d.select_priv,d.insert_priv FROM user u LEFT JOIN db d USING (user);
```

Which will show something like:
```

+------------------+-----------+----------------------------+-------------+-------------+
| root             | 127.0.0.1 | NULL                       | NULL        | NULL        | 
|                  | testhost  | test                       | Y           | Y           | 
|                  | testhost  | test\_%                    | Y           | Y           | 
| root             | testhost  | NULL                       | NULL        | NULL        | 
|                  | localhost | test                       | Y           | Y           | 
|                  | localhost | test\_%                    | Y           | Y           | 
| chenna1_admin    | localhost | blogs                      | Y           | Y           | 
| debian-sys-maint | localhost | NULL                       | NULL        | NULL        | 
| faquser          | localhost | faq                        | Y           | Y           | 
| mare_user        | localhost | bizmare                    | Y           | N           | 

```

Usually, Select_priv and (Insert_priv | Update_priv | Delete_priv) are the common ones, but you can select from:

Select_priv	
Insert_priv	
Update_priv	
Delete_priv	
Create_priv	
Drop_priv	
Grant_priv	
References_priv	
Index_priv	
Alter_priv	
Create_tmp_table_priv	
Lock_tables_priv	
Create_view_priv	
Show_view_priv	
Create_routine_priv	
Alter_routine_priv	
Execute_priv

I hope this helped.

---

