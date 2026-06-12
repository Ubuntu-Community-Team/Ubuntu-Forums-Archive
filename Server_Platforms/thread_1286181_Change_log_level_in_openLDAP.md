---
title: "Change log level in openLDAP"
date: 2009-10-08
forum: Server Platforms
---

### Post by matthewboh on 2009-10-08
I need to change the log level in openLDAP and I'm having problems finding out how.

I'm not using slapd.conf, but using the newer special DIT cn=config but everywhere I look, it only talks about slapd.conf

I know I want to change the log level to stats.  How would I do that?

Thanks

---

### Post by MidSpeck on 2009-11-02
Hi matthewboh,

I'm curious if you ever figured out how to change the log level of openldap with the new cn=config configuration files.  I am looking for the same information.

Willie

UPDATE:
From what I've found, use a program to edit your LDAP directory.  Bind as: cn=admin,cn=config with your administrative password.  In cn=config, there is an attribute (olcLogLevel) that can be set to "stats".
If you've locked yourself out somehow, I suppose you could edit /etc/ldap/slapd.d/cn=config.ldif manually and then restart slapd.  From what I've read, the beauty of using LDAP itself to modify it is that the changes are automatically applied without having to restart.  See [http://www.zytrax.com/books/ldap/ch6/slapd-config.html](http://www.zytrax.com/books/ldap/ch6/slapd-config.html)

---

### Post by jk7 on 2011-12-05
Hi,
you can change log level in cn=config.ldif file. Setup olcLogLevel directive to one of:

[COLOR=Red]Level[/COLOR] [COLOR=SeaGreen]Keyword[/COLOR][COLOR=SandyBrown] Description[/COLOR]
-1 any enable all debugging
0 no debugging
1 (0x1 trace) trace function callss
2 (0x2 packets) debug packet handling
4 (0x4 args) heavy trace debugging
8 (0x8 conns) connection management
16 (0x10 BER) print out packets sent and received
32 (0x20 filter) search filter processing
64 (0x40 config) configuration processing
128 (0x80 ACL) access control list processing
256 (0x100 stats) stats log connections/operations/results
512 (0x200 stats2) stats log entries sent
1024 (0x400 shell) print communication with shell backends
2048 (0x800 parse) print entry parsing debugging
16384 (0x4000 sync) syncrepl consumer processing
32768 (0x8000 none) only messages that get logged whatever log level is set


E.g.
olcLogLevel: trace

---

