---
title: "Need help postfix mailserver attacked hard"
date: 2011-08-02
forum: Security
---

### Post by wsonar on 2011-08-02
How can I prevent this?

Jul 25 09:25:10 namedited pop3d: Connection, ip=[::ffff:66.240.182.167]
Jul 25 09:25:10 namedited authdaemond: received auth request, service=pop3, authtype=login
Jul 25 09:25:10 namedited authdaemond: authmysql: trying this module
Jul 25 09:25:10 namedited authdaemond: SQL query: SELECT username, password, "", '5000', '5000', '/home/vmail', maildir, concat(quota,'S'), name, "" FROM mailbox WHERE username = 'market'
Jul 25 09:25:10 namedited authdaemond: zero rows returned
Jul 25 09:25:10 namedited authdaemond: no password available to compare
Jul 25 09:25:10 namedited authdaemond: authmysql: REJECT - try next module

---

### Post by wsonar on 2011-08-02
edited

---

