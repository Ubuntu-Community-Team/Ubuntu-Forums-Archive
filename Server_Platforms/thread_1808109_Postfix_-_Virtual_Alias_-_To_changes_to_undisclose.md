---
title: "Postfix - Virtual Alias - To: changes to undisclosed-recipients"
date: 2011-07-19
forum: Server Platforms
---

### Post by mribbons on 2011-07-19
Hi,
I have set up postfix with mysql and virtual domains as per [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

I'm using Ubuntu Server 10.04 with the latest updates.

All good so far, I can send and receive mail.

I want to forward all emails for some domains to a single mailbox for a group mail system, however I also want the mail delivered to the original recipient.

eg RCPT TO: <user@example.com>

would be delivered to [EMAIL="user@example.com"]user@example.com[/EMAIL] and [EMAIL="groupmail@example.com"]groupmail@example.com[/EMAIL]

I have inserted an alias record as follows:

mail: @example.com
destination: [EMAIL="groupmail@example.com"]groupmail@example.com[/EMAIL]

There are 2 problems:
1. The mail is only delivered to [EMAIL="groupmail@example.com"]groupmail@example.com[/EMAIL]
[EDIT:] If I create a new entry above as mail: [email]user@example.com[/email], [email]groupmail@example.com[/email] it nearly works - I get the original mail to [email]user@example.com[/email], but 2 copies of the email to [email]groupmail@example.com[/email]

2. The recipient appears as "To: undisclosed-recipients:;"
[EDIT:] This seems to happen for all emails, regardless of forwarding. I wonder if it's a proplem with my raw mail RCPT TO: command?
[EDIT:] This can be fixed by supplying a To: "person name" <user@example.com> line in the data section

Because it's a group mail system, we need to know who the mail was originally addressed to, so we need that To: to appear as it did in the original email.

Is virtual aliasing the right thing to use here?

If so how can I make it deliver to the original recipient, and include that address in the forwarded message?

---

### Post by mribbons on 2011-07-20
So my issue now is that the alias recipient receives 2 copies.

I found the recipient_bcc_maps option which does something similar to what I want, but postfix was still duplicating the copied mail.

This looks similar to my problem: [http://www.adras.com/recipient-bcc-maps-override.t6010-139.html](http://www.adras.com/recipient-bcc-maps-override.t6010-139.html)

So I disabled amavis in main.cf:
#content_filter = amavis:[127.0.0.1]:10024

And it now works as required, 1 message to original recipient, 1 to [email]groupmail@example.com[/email]

I would really like to use amavis - Is there a way to configure it so it doesn't filter both the original and the bcc?

---

### Post by mribbons on 2011-07-20
[http://tech.groups.yahoo.com/group/postfix-users/message/206048](http://tech.groups.yahoo.com/group/postfix-users/message/206048)

Use above + bcc_recipient_maps rather than a virtual alias.

---

