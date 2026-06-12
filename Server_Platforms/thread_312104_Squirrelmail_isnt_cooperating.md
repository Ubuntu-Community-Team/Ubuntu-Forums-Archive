---
title: "Squirrelmail isnt cooperating"
date: 2006-12-03
forum: Server Platforms
---

### Post by scrupul0us on 2006-12-03
First some info:

-Running fresh install of 6.10 edgy
-Followed the guide for "The perfect setup" on howtoforge
-Installed squirrelmail (apt-get install squirrelmail)

This is what the config file says:
```

SquirrelMail configtest

  This script will try to check some aspects of your SquirrelMail configuration and point you to errors whereever it can find them. You need to go run conf.pl in the config/ directory first before you run this script.
   SquirrelMail version:1.4.8 Config file version:1.4.0 Config file last modified:01 December 2006 23:52:48  
  Checking PHP configuration...
    PHP version 5.1.6 OK.
    PHP extensions OK.
Checking paths...
    Data dir OK.
    Attachment dir OK.
    Plugins OK.
    Themes OK.
    Default language OK.
    Base URL detected as: http://xxx.xxx.xxx.xxx/mail/src (location base autodetected)
Checking outgoing mail service....
    SMTP server OK (220 xxx.xxx.com ESMTP Sendmail 8.13.8/8.13.8/Debian-2; Sat, 2 Dec 2006 00:25:11 -0500; (No UCE/UBE) logging access from: localhost.localdomain(OK)-localhost.localdomain [127.0.0.1])
Checking IMAP service....
    IMAP server ready (* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION] Courier-IMAP ready. Copyright 1998-2005 Double Precision, Inc. See COPYING for distribution information.)
    Capabilities: * CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION 
Checking internationalization (i18n) settings...
     gettext - Gettext functions are available. You must have appropriate system locales compiled.
     mbstring - Mbstring functions are available.
     recode - Recode functions are unavailable.
     iconv - Iconv functions are available.
     timezone - Webmail users can change their time zone settings.
Checking database functions...
    not using database functionality.
   Congratulations, your SquirrelMail setup looks fine to me!

```

and when i tried to login via the web it said:
"ERROR: Connection dropped by IMAP server."

any idea?

---

### Post by scrupul0us on 2006-12-04
cmon, someone MUST have squirrelmail installed on edgy that can shed some light or tell me how they installed it or setup courier

im gettin desperate here people ;)

---

