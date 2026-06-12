---
title: "Forwardings"
date: 2007-02-02
forum: Server Platforms
---

### Post by Tspiritstorm on 2007-02-02
I am trying to get forwardings to work and it is the last thing I need to do in order to start performance testing. Anyone have any ideas why it might not be working?

Here is my config:

mysql-forwards.cf

user = xxx
password = xxx
dbname = xxx
table = forwardings
select_field = destination
where_field = source
hosts = 127.0.0.1

mysql - forwards -table

CREATE TABLE forwardings (
source varchar(80) NOT NULL,
destination TEXT NOT NULL,
PRIMARY KEY (source) )
TYPE=MyISAM;

mysql logs

070202 12:55:38     996 Connect     mail@localhost on maildb
                    996 Query       SELECT 'virtual' FROM domains WHERE domain=' fromdomain.com'
                    996 Query       SELECT 'virtual' FROM domains WHERE domain='mydomain.com'
                    997 Connect     mail@localhost on maildb
                    997 Query       SELECT destination FROM forwardings WHERE source='postmaster@mydomain.com'
                    996 Query       SELECT 'virtual' FROM domains WHERE domain=' mydomain.com'
                    998 Connect     mail@localhost on maildb
                    998 Query       SELECT CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/') FROM users WHERE email=' [email]postmaster@mydomain.com[/email]'
                    998 Query       SELECT CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/') FROM users WHERE email='@ mydomain.com'
                    999 Connect     mail@localhost on maildb
                    999 Query       SELECT destination FROM forwardings WHERE source='mkeck@fromdomain.com'
                   1000 Connect     mail@localhost on maildb
                   1000 Query       SELECT email FROM users WHERE email='mkeck@fromdomain.com'
                    999 Query       SELECT destination FROM forwardings WHERE source='mkeck'
                   1000 Query       SELECT email FROM users WHERE email='mkeck'
                    999 Query       SELECT destination FROM forwardings WHERE source='@ fromdomain.com'
                   1000 Query       SELECT email FROM users WHERE email='@fromdomain.com'
                    996 Query       SELECT 'virtual' FROM domains WHERE domain=' fromdomain.com'

----

ON top of qhich when I run a query based off the results I see.. I find the correct info. It is like it sees it in the query but ignores it and moves on or doesn't know how to handle. 

Someone please help as I have been stuck on this for 3 days!

---

