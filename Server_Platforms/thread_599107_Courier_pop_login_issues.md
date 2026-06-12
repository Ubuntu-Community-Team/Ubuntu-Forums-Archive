---
title: "Courier pop login issues"
date: 2007-11-01
forum: Server Platforms
---

### Post by buddajah on 2007-11-01
i cannot login to courier pop via client or telnet. can someone help me out. maybe i missed something ? or more likely messed the config up somehow. any help or advice would be helpful. 

here are the logs - 

**_mail.err:_**

Oct 31 18:30:44 pill courierpop3login: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Oct 31 18:31:16 pill courierpop3login: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Oct 31 19:03:59 pill courierpop3login: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Oct 31 19:09:42 pill courierpop3login: LOGIN FAILED, ip=[::ffff:127.0.0.1]

**_mail.info:_**

Oct 31 18:30:44 pill courierpop3login: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Oct 31 18:31:16 pill courierpop3login: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Oct 31 19:03:14 pill authdaemond.mysql: restarting authdaemond children
Oct 31 19:03:14 pill authdaemond.mysql: modules="authmysql", daemons=5
Oct 31 19:03:15 pill authdaemond.mysql: modules="authmysql", daemons=5
Oct 31 19:03:59 pill courierpop3login: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Oct 31 19:09:00 pill authdaemond.mysql: restarting authdaemond children
Oct 31 19:09:00 pill authdaemond.mysql: modules="authmysql", daemons=5
Oct 31 19:09:01 pill authdaemond.mysql: modules="authmysql", daemons=5
Oct 31 19:09:42 pill courierpop3login: LOGIN FAILED, ip=[::ffff:127.0.0.1]


text of courier config files - 

**_authmodulelist_**

authdaemon

**_authdaemonrc_**

##VERSION: $Id: authdaemonrc.in,v 1.8 2001/10/07 02:16:22 mrsam Exp $

authmodulelist="authmysql"
authmodulelistorig="authcustom authcram authuserdb authldap authpgsql authmysql authpam"
daemons=5
version=""
authdaemonvar=/var/run/courier/authdaemon

**_authmysqlrc_**

MYSQL_SERVER 127.0.0.1
MYSQL_USERNAME user
MYSQL_PASSWORD pass
MYSQL_SOCKET /var/run/mysqld/mysqld.sock
#Use MYSQL_SOCKET instead of MYSQL_PORT.
#If you can't do that, use MYSQL_PORT
#If your socket path is in a different location, please modify it.
MYSQL_PORT 0
MYSQL_DATABASE database
MYSQL_USER_TABLE accounts
MYSQL_CRYPT_PWFIELD cypher
MYSQL_CLEAR_PWFIELD text
MYSQL_UID_FIELD uid
MYSQL_GID_FIELD gid
MYSQL_LOGIN_FIELD addy
MYSQL_HOME_FIELD home
MYSQL_NAME_FIELD name
MYSQL_MAILDIR_FIELD concat (home, '/', maildir)
MYSQL_QUOTA_FIELD quota
MYSQL_AUXOPTIONS_FIELD
CONCAT("disableimap=",disableimap,",disablepop3=",disablepop3,",disablewebmail=",disablewebmail,",sharedgroup=",sharedgroup)
MYSQL_WHERE_CLAUSE access='y'

**_pop3d_**

PIDFILE=/var/run/courier/pop3d.pid
MAXDAEMONS=40
MAXPERIP=4
AUTHMODULES="authdaemon"
AUTHMODULES_ORIG="authdaemon"
DEBUG_LOGIN=0
POP3AUTH="LOGIN PLAIN,CRAM-MD5 CRAM-SHA"
POP3AUTH_ORIG="LOGIN CRAM-MD5 CRAM-SHA1"
POP3AUTH_TLS="LOGIN PLAIN"
POP3AUTH_TLS_ORIG="LOGIN PLAIN"
PORT=110
ADDRESS=0
TCPDOPTS="-nodnslookup -noidentlookup"

IMAP_CAPABILITY="IMAP4rev1 UIDPLUS CHILDREN NAMESPACE
THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA
AUTH=CRAM-MD5 AUTH=CRAM-SHA1 IDLE"

POP3DSTART=YES
MAILDIRPATH=Maildir


Please let me know if there is anything else you need and i can post it here. thank you

---

### Post by buddajah on 2007-11-01
ok, no fish so far. well i changed the log level to 7 for courier and here are the relative log entries i hope this helps some one help me. thanks:

**_mail.log_**

Nov  1 15:29:46 pill courierpop3login: Connection, ip=[::ffff:192.168.1.29]
Nov  1 15:29:46 pill courierpop3login: LOGIN: DEBUG: ip=[::ffff:192.168.1.29], command=USER
Nov  1 15:29:46 pill courierpop3login: LOGIN: DEBUG: ip=[::ffff:192.168.1.29], command=PASS
Nov  1 15:29:46 pill courierpop3login: LOGIN: DEBUG: ip=[::ffff:192.168.1.29], username=user@fubar.com
Nov  1 15:29:46 pill courierpop3login: authdaemon: starting client module
Nov  1 15:29:46 pill courierpop3login: authdaemon: TEMPFAIL - no more modules will be tried
Nov  1 15:29:51 pill courierpop3login: LOGIN FAILED, ip=[::ffff:192.168.1.29]

---

### Post by buddajah on 2007-11-01
is it possible that ubuntu does not compile courier-authlib with mysql support?

 and if so how would i do that using dpkg with out breaking anything ?

---

### Post by buddajah on 2007-11-01
here is a list of installed packages :

 aptitude installed packages

i   courier-authdaemon                                                    - Courier Mail Server - Authentication daemon
i   courier-authmysql                                                     - Courier Mail Server - MySQL authentication
i   courier-base                                                          - Courier Mail Server - Base system
i   courier-doc                                                           - Courier Mail Server - Additional documentation
i   courier-imap                                                          - Courier Mail Server - IMAP server
i   courier-imap-ssl                                                      - Courier Mail Server - IMAP over SSL
i   courier-maildrop                                                      - Courier Mail Server - Mail delivery agent
i   courier-pop                                                           - Courier Mail Server - POP3 server
i   courier-ssl                                                           - Courier Mail Server - SSL/TLS Support
i   courier-webadmin                                                      - Courier Mail Server - Web-based administration frontend

aptitude avialable for install packages :

p   courier-authpostgresql                                                - Courier Mail Server - PostgreSQL Authentication
p   courier-faxmail                                                       - Courier Mail Server - Faxmail gateway
p   courier-filter-perl                                                   - purely Perl-based mail filter framework for the Courier MTA
p   courier-ldap                                                          - Courier Mail Server - LDAP support
p   courier-mlm                                                           - Courier Mail Server - Mailing list manager
p   courier-mta                                                           - Courier Mail Server - ESMTP daemon
p   courier-mta-ssl                                                       - Courier Mail Server - ESMTP over SSL
p   courier-pcp                                                           - Courier Mail Server - PCP server
p   courier-pop-ssl                                                       - Courier Mail Server - POP3 over SSL
p   couriergraph                                                          - Mail statistics RRDtool frontend for Courier-{POP,IMAP}
p   cyrus2courier  

did i forget to install anything that was needed ?

---

### Post by buddajah on 2007-11-02
i fixed the issue. turned on logging fo mysql and courier. the logs indicated issues with the authmysqlrc file. i commented out the crypt line and fixed the syntax error with the concat statment. the authentication issues is now resolved.

---

