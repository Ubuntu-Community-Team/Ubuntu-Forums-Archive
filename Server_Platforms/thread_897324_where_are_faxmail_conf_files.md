---
title: "where are faxmail conf files?"
date: 2008-08-22
forum: Server Platforms
---

### Post by ahmedbadak on 2008-08-22
Hi
I use Ubuntu 8.04 LTS and hylafax 4.4.4, faxmail use this files;
-------------------------------------------------------------
~/.hylarc                          per-user configuration file
/usr/local/lib/fax/pagesizes       page size database
/usr/local/lib/fax/faxmail.ps      POSTSCRIPT prologue
/usr/local/lib/fax/hyla.conf       system-wide configuration file
/usr/local/lib/fax/faxmail.conf    system-wide configuration file
/usr/local/lib/fax/sendfax.conf    system-wide configuration file for direct delivery
/usr/local/lib/fax/faxmail         hierarchy for external MIME converters
%rom%lib/:/usr/local/share/ghostscript/8.57/lib:/usr/local/share/ghostscript/8.57/Resource:/usr/local/share/ghostscript/fontsfor font metrics
/var/spool/hylafax/tmp/faxmailXXXXXXtemporary files
------------------------------------------------------------
But where are they in ubuntu? I searched this files and i don't find.
(I need to "faxmail.conf" and "sendfax.conf")
Thanks.

---

### Post by windependence on 2008-08-22
/etc/hylafax/faxmail.conf 

/etc/hylafax/sendfax.conf 

-OR-

/var/lib/fax/sendfax.conf

-Tim

---

