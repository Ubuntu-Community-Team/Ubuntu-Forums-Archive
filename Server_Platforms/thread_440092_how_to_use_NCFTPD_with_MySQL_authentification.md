---
title: "how to use NCFTPD with MySQL authentification?"
date: 2007-05-11
forum: Server Platforms
---

### Post by prodsacnetworking on 2007-05-11
Hi,

I presently use ncftpd server but I to install it on a client's server and I'd like them to be able to add users easily.

So I want to create a DB they can modifi on a php page.

So anybody has a tutorial on how to use NCFTPD with MySQL authentification?

Thanks

---

### Post by judoka9999 on 2007-05-17
I'm unfamiliar w/ NCFTPD, but given its been 5 days and no one appears to have answered you I thought it may be worthwhile to point you to proftpd. On ubuntu or debian apt-get install proftpd and proftpd-mysql. Here is the link to the SQL module documentation on their website:

[http://www.proftpd.org/docs/directives/linked/config_ref_mod_sql.html](http://www.proftpd.org/docs/directives/linked/config_ref_mod_sql.html)

In addition, Here are snippets of one of my production configs which should help get you started.

--Judoka

#don't use ipv6 unless you actually have an ipv6 network
UseIPv6                         off

#tell it to use mysql, not postgres
SQLBackend                      mysql

#I use crypted password fields in my databases
SQLAuthTypes                    Crypt

#tell proftpd to authenticate users against the db
SQLAuthenticate                 users*

#The database connection info, obviously I changed them from production values
SQLConnectInfo                  user@server database password

#assume UID/GID if you aren't using system accounts and putting them in SQL
SQLDefaultGID                   33
SQLDefaultUID                   33

#set the min. UID/GID so they work for you
SQLMinUserGID                   33
SQLMinUserUID                   33

#the table name, followed by fields for username, password, and home dir
#if you store uid/gid and shell in the db then you can replace the NULL values
#as per documentation
SQLUserInfo                     users username crypt NULL NULL home NULL

#mainly useful for debugging, you can disable this after you get it working
SQLLogFile                      /var/log/proftpd/sql.log

#Since you aren't adding system users, they won't have valid shells
RequireValidShell               off

---

