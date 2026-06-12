---
title: "postfix + local + virtual domains"
date: 2006-10-13
forum: Server Platforms
---

### Post by mwerlberger on 2006-10-13
Hi!

I managed to configure postfix + dovecot the way that it works with virtual domains (with a mysql backend configuration) and a second time i can do it with local mail. But what i want is both. How can i tell postfix and dovecot that it should look for the user/passwords and maildirs either at the system and when it don't find any appropriate user look at the database for virtual systems. Is there a good howto to configure postfix+dovecot+mysql for virtual domains AND mail for "local users"?

My second question is how can i manage the aliases in a good way? Especially for the virtual domains. I have some users that wan't to have mailboxes for their domains. I want to give them virtual mailboxes. But i don't want to do all the administration like when the user want's to create an alias. (Scenario: the user [email]first@example.com[/email] wants a alias [email]second@example.com[/email] that is forwarded to [email]first@example.com[/email] of course and also wants the mail-addy [email]second@example.com[/email] available to send mail with (webmail and with smpt from his mail-client (e.g. thunderbird)).) How can i configure my setup so that the users can do such configuration themselfs and not give them too many rights.

Hope there are some good answers....

Regards,
 Manuel

---

