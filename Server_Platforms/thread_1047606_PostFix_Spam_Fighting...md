---
title: "PostFix Spam Fighting.."
date: 2009-01-22
forum: Server Platforms
---

### Post by Tom_T on 2009-01-22
Hi

I've just installed postfix etc following this HowTo:
[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.10](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.10)

Just wondering what the best way to fight spam is.

On my current Win server I use the following to help fight spam and was hoping some one could tell me how to do this with Postfix !!

SMTP Server
1. Do not permit SMTP relaying of non local mail
2. Use Strict Relaying
3. Authenticated User SMTP Connections may relay mail ( I specify these)
4. Blacklist look ups.
5. Compliance: Check originator against kill file, Refuse messages that have no subject field.
6. Refuse any EHLO/HELO that aren't fully qualified domains. (WITH Certain exceptions)

Can anyone help me get the above on Postfix ??

Many Thanks :)

---

### Post by Tom_T on 2009-01-30
I've managed to find some advice with blocking malformed EHLO/HELO entries.
So I can block any domain that doesn't have a '.' in it, BUT can I add a white/exception list to this ??
Thanks

---

