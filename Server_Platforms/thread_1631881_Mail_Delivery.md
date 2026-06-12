---
title: "Mail Delivery"
date: 2010-11-27
forum: Server Platforms
---

### Post by wasanzy on 2010-11-27
Hi,

I have in my /home/vpopmail/domains/domain/.qmai-default

| preline procmail -m -p -t /etc/procmailrc
| /home/vpopmail/bin/vdelivermail '' bounce-no-mailbox


Which the first line is passing the mails to procmail and the second is delivering the mails directly to the recipients.

Now my problem is, I want procmail to takecare of the delivery. But when I remove the second line, and put this in procmail:
DEFAULT= | /home/vpopmail/bin/vdelivermail '' bounce-no-mailbox

The mails are not being deliver any more, and I don't kow where they been kept. 

For example, if I have a rule in procmail like this:
:0H
* ^To.*postmaster@dot.com.gh
/dev/null

which said to delete any message to [email]postmaster@dot.com.gh[/email], I can see the mails are still being delivered.

How can I achive my goal please any one to help?

Regards

Emmanuel

---

### Post by SeijiSensei on 2010-11-27
Individual users' procmail rules usually live in $HOME/.procmailrc.  Try putting it in there.

If you want to create a global rule, create a file /etc/procmailrc (note no initial dot) and put the rule there.

---

