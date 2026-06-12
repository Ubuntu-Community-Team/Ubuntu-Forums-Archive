---
title: "Incorrect information in file:"
date: 2008-02-17
forum: Server Platforms
---

### Post by trymbill on 2008-02-17
Hi guys!

I was just moving to a virtual server from my original Ubuntu 7.10 server so right now I'm using Ubuntu 6.06 on a Virtual Server 2005 from MS on Windows 2003 server.

I got everything working ... well almost! :)  I've moved my SQL dir from my old server to my new one and it looks to be O.K. but when I try to view tables that are using the InnoDB engine I get this error:

"Incorrect information in file: './leifur/events.frm'"

All my MyISAM tables are doing just great, but it seems as though my InnoDB tables are "damaged" or something.  I've tried running "REPAIR TABLE events" but that just gives me the same error.

Does any one here know what the problem could be? :- /

---

### Post by faulkes on 2008-02-17
> **trymbill said:**
> Hi guys!

I was just moving to a virtual server from my original Ubuntu 7.10 server so right now I'm using Ubuntu 6.06 on a Virtual Server 2005 from MS on Windows 2003 server.

I got everything working ... well almost! :)  I've moved my SQL dir from my old server to my new one and it looks to be O.K. but when I try to view tables that are using the InnoDB engine I get this error:

"Incorrect information in file: './leifur/events.frm'"

All my MyISAM tables are doing just great, but it seems as though my InnoDB tables are "damaged" or something.  I've tried running "REPAIR TABLE events" but that just gives me the same error.

Does any one here know what the problem could be? :- /

Which version of mysql was the data created in and which version of mysql are you now using?

The issue may be that the data formats are not consistent if the version differences are large.

I believe mysql.org keeps a chart of when and where data is not migratable.

Your best option, would be to perform a mysqldump of the original database (data and schema) and then import that into the new mysql instance.

See the mysqldump manpage for further information on doing so.

Faulkes

---

### Post by trymbill on 2008-02-17
Yeah, I thought about just exporting and then importing.  I'll probably end with that :)

---

