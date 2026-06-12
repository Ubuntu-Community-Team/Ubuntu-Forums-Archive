---
title: "squirrelmail - empty 'From:' field in some messages"
date: 2016-02-12
forum: Server Platforms
---

### Post by marchello_lippi2 on 2016-02-12
Hi all,


Some of messages in my inbox are displayed with empty 'From:' field.


I tried to compare those messages with empty 'From:' field with normal
messages.


Normally, "From:" field in header has "Some name" <user@host>, but this
'Some name' is absent and "From:" is only <user@host>


How do I display <user@host> instead of empty 'From:' field?


Sorry if this was discussed already before, I tried to google it, but
found nothing.

I already posted this question in main squirrelmail mailing list, but it is seems to be silent. 

version: 
SquirrelMail 1.4.23 [SVN]
Apache/2.4.7
Ubuntu 14.04.3 LTS


Thanks ahead.

---

### Post by howefield on 2016-02-12
Thread moved to the "*Server Platforms*" forum.

---

### Post by marchello_lippi2 on 2016-02-12
Looked at [https://sourceforge.net/p/squirrelmail/bugs/2806/](https://sourceforge.net/p/squirrelmail/bugs/2806/) according to suggestion at main squirrelmail mailing list. 
Found patch [COLOR=#000000]quoted_printable_fix-1.4.x-version_3.diff
[/COLOR]Looking for the way to apply it (did not do it before).

---

