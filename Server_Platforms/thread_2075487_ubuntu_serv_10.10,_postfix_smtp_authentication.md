---
title: "ubuntu serv 10.10, postfix smtp authentication"
date: 2012-10-23
forum: Server Platforms
---

### Post by cyclobs on 2012-10-23
hey guys,

so been pulling my hair out for the last 2 days on trying to get my email server running with virtual users / domains coming out of an mysql server. One last hurdle i need to get over is SMTP fails to authenticate my users correctly and because of this they can't send out email. All other aspects are working fine (sending via non authed smtp, receiving, logging into virtual email and getting e-mails)

now i've been using this tutorial to help me out: [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts)

after doing some packet sniffing and debugging i think the problem is when postfix tries to auth my account it's sending this query to mysql

```

SELECT password FROM users WHERE email = 'cyclobs'

```

which will return null because my accounts consist of [email]username@domain.com[/email] since mysql returns null postfix can't auth the user. Now i've tested this theory with 2 different e-mail clients as well as directly connecting to smtp via telnet my self all of which produce the same result.

what the query should be reading is this:

```

SELECT password FROM users WHERE email = 'cyclobs@domain.com'

```

and in the smtp config the query is set up as follows:

```

select `password` from `users` where `email` = '%u@%r'

```

is there a config setting i'm missing somewhere that's causing postfix to drop the domain? i'm lost on what i can do from here.

Running postfix with courier and sasl.

any help appreciated, thanks guys

---

### Post by clonedone on 2012-10-24
We just use %s:

```

root@mail:/etc/postfix# grep SELECT *
mysql_relay_domains_maps.cf:query = SELECT domain FROM domain WHERE domain='%s' and backupmx = '1'
mysql_virtual_alias_maps.cf:query = SELECT goto FROM alias WHERE address='%s' AND active = 1
mysql_virtual_domains_maps.cf:query = SELECT domain FROM domain WHERE domain='%s'
mysql_virtual_domains_maps.cf:#query = SELECT domain FROM domain WHERE domain='%s' and backupmx = '0' and active = '1'
mysql_virtual_mailbox_limit_maps.cf:query = SELECT quota FROM mailbox WHERE username='%s'
mysql_virtual_mailbox_maps.cf:query = SELECT maildir FROM mailbox WHERE username='%s' AND active = 1

```Don't have SELECT `password` in any of my configs mate. Not sure if that helps, its not actually ubuntu 10.10 on that box.

---

### Post by cyclobs on 2012-10-24
ah yes they are different config files which all appear to be working fine. The one i'm looking at atm is /etc/postfix/sasl/smtp.conf

smtp:
```

pwcheck_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: sql
sql_engine: mysql
sql_hostnames: <secrete>
sql_user: <secrete>
sql_passwd: <secrete>
sql_database: <secrete>
sql_select: select `password` from `users` where `email` = '%u@%r'

```

Those other queries are very similar to mine but i'm pretty sure they don't have anything to to with smtp authenticating

---

### Post by clonedone on 2012-10-25
Found this: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

Which lists almost exactly what you have

```
In /etc/postfix/sasl/smtpd.conf 
pwcheck_method: auxprop 
auxprop_plugin: sql 
mech_list: plain login cram-md5 digest-md5 
sql_engine: mysql 
sql_hostnames: 127.0.0.1 
sql_user: postfix 
sql_passwd: yourpassword 
sql_database: postfix 
sql_select: select password from mailbox where username='%u@%r' and active = 1
```

---

### Post by cyclobs on 2012-10-25
> **clonedone said:**
> Found this: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

Which lists almost exactly what you have

```
In /etc/postfix/sasl/smtpd.conf 
**pwcheck_method: auxprop **
auxprop_plugin: sql 
mech_list: plain login cram-md5 digest-md5 
sql_engine: mysql 
sql_hostnames: 127.0.0.1 
sql_user: postfix 
sql_passwd: yourpassword 
sql_database: postfix 
sql_select: select password from mailbox where username='%u@%r' and active = 1
```

Using this (as bolded above) brings back the domain in my queries but then I don't think postfix is being able to use sasl to match the passwords with.

i dunno i give up on it :mad:

---

