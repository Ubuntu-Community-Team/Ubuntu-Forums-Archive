---
title: "postfix flexible aliases"
date: 2007-10-25
forum: Server Platforms
---

### Post by Darling on 2007-10-25
After spending hours to get my mail system running ok (thanks flurdy ;-) I'm starting to get an idea of how postfix (and the other services and programs) work . I even managed to get DSpam running.

But I also found a trick to create very flexible aliases.
* I'm storing my users and aliases in a Mysql DB
* It would be great if I could use wildcards in the aliases.
* regexp is even greater (geekier).
* In GMail the dots aren't relevant in the alias. so geert.vandamme@... is the same as geertvandamme@... or geert.van.d.a.m.m.e@ ....

Since Postfix 2.2 the parameters you specified in the mysql_alias.cf file are changed. The old params still work, but you can also specify 'query' 
[http://www.postfix.org/mysql_table.5.html](http://www.postfix.org/mysql_table.5.html)

That gives us much more flexibility in specifying the query.

My alias table is 
```
CREATE TABLE  `maildb`.`alias` (
  `id` int(11) NOT NULL auto_increment,
  `mail` varchar(120) NOT NULL default '',
  `destination` text NOT NULL,
  `enabled` tinyint(1) NOT NULL default '1',
  `priority` int(11) NOT NULL default '100',
  PRIMARY KEY  (`id`),
  UNIQUE KEY `mail` (`mail`)
) 

```
If you use something like 
```
query=SELECT destination FROM alias WHERE '%s' LIKE mail and enabled = 1 order by priority limit 1
```

that allows you to use the normal 'SQL LIKE' wildcards '?' and  '%' in the 'mail' field.
If you prefer regular expressions you can specify 
```
query=SELECT destination FROM alias WHERE '%s' LIKE mail and enabled = 1 order by priority limit 1
```

Also the gmail dot trick is easily implemented now:
```
query=SELECT destination FROM alias WHERE replace('%s',".","") LIKE mail and enabled = 1 order by priority  limit 1
```

But in that case, you should remove all the dots in the mail column as well. 
I guess these tricks might give performance problems on a 1000's aliases list, but for smaller setups, it's great.

---

