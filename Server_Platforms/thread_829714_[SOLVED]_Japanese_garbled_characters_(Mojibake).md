---
title: "[SOLVED] Japanese garbled characters (Mojibake)"
date: 2008-06-15
forum: Server Platforms
---

### Post by dash86no on 2008-06-15
Hi,

I have set up a postfix/dovecot/squirrelmail mail server on Ubuntu Hardy server.

Everything is working great, although Japanese characters are getting mangled on sent/received email from squirrel and on sent mail only when I send through my "User mail box" using webmin.

I installed Ubuntu server in English so I'm guessing the root of my problem is lack of Japanese language support. I went into /var/lib/locales/supported.d/locales and tried to add the lines:

ja-JP.UTF-8 UTF-8

but came up with the error message " cannot open locale definition file 'jp_JP" : No such file or directory

Can someone please advise me of how to get this fixed?

If more information is needed please let me know and I will post ASAP.

---

### Post by dash86no on 2008-06-17
Ok,

Have this fixed. I simply downloaded the packages:

squirrelmail-locales
squirrel-decode

then went into the "options" section in webmail and changed the display language to Japanese. 

Interestingly, the display remained in English (Which is fine for me but might not be great for a Japanese person). However, I can now send and receive email in Japanese. 

Actually after spending all this effort over the last couple of weeks getting my mail server up, i'm pretty disappointed now the thing is complete and i'm comparing it to Exchange 2007 OWA which we've just upgraded to at work! I know postfix/dovecot/squirrel must take up about 5% of the resources of exchange with higher reliability but squirrelmail's interface is really old fashioned and lame. 

I'll be giving Zimbra a whirl this weekend I think!

---

