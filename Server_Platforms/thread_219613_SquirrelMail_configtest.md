---
title: "SquirrelMail configtest"
date: 2006-07-20
forum: Server Platforms
---

### Post by matko on 2006-07-20
hello.

i configured mail. and SquirrelMail configtest says it cant connect to mysql.
i am sure i created table, users.

here is what it says.
```
SquirrelMail version:	1.4.4
Config file version:	1.4.0
Config file last modified:	20 July 2006 14:31:43
Checking PHP configuration...
    PHP version 4.4.0-3ubuntu2 OK.
    PHP extensions OK.
Checking paths...
    Data dir OK.
    Attachment dir OK.
    Plugins are not enabled in config.
    Themes OK.
    Default language OK.
    Base URL detected as: http://****/mail/src
Checking outgoing mail service...
    SMTP server OK (220 **** ESMTP Postfix (Ubuntu))
Checking IMAP service....
    IMAP server ready (* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION] Courier-IMAP ready. Copyright 1998-2004 Double Precision, Inc. See COPYING for distribution information.)
    Capabilities: * CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION
Checking internationalization (i18n) settings...
     gettext - Gettext functions are available. You must have appropriate system locales compiled.
     mbstring - Mbstring functions are available.
     recode - Recode functions are unavailable.
     iconv - Iconv functions are available.
     timezone - Webmail users can change their time zone settings.
Checking database functions...
     PHP Pear DB support is present.
    mysql database support present.

    ERROR: Database error: connect failed in preferences DSN.
```

here is also my configuretion of database

```
SquirrelMail Configuration : Read: config.php (1.4.0)
---------------------------------------------------------
Database
1.  DSN for Address Book   : mysql://root:******@127.0.0.1/maildb
2.  Table for Address Book : address

3.  DSN for Preferences    : mysql://root:******@127.0.0.1/maildb
4.  Table for Preferences  : userprefs
5.  Field for username     : user
6.  Field for prefs key    : prefkey
7.  Field for prefs value  : prefval

8.  DSN for Global Address Book            :
9.  Table for Global Address Book          : global_abook
10. Allow writing into Global Address Book : false
11. Allow listing of Global Address Book   : false

```

where can be problem.  chceck my configuretion pklease.

thank you all

---

