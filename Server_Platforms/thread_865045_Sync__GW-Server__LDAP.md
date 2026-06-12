---
title: "Sync / GW-Server / LDAP"
date: 2008-07-20
forum: Server Platforms
---

### Post by mwerlberger on 2008-07-20
Hi,

I have some questions that are somehow related to each other. I have a Ubuntu Server that currently uses files to authenticate the users. Now the decision is to switch to LDAP and use some groupware stuff to offer the ability that the users can sync their contacts and calendars.

I have now setup the LDAP part and installed Open-XChange and got stuck when putting these two together. After installing ox i searched a little bit about syncing with different applications. Ok syncml and some other extensions are offered (the users use linux, windows and mac os and therefore i need a versatile solutiont...).

Now what can you suggest when it comes to a central authentication and a nice working groupware suite? LDAP would be used for web-access (for secured folders, webDAV, ...), SVN, shell logins, ....

Groupware should work with Outlook, Thunderbird, Evolution, Kontact and Apple Mail. And it would be great if there is a nice web interface for an overview of emails and tasks and such stuff...

Any suggestions what would be the best solution? I also had a look at zimbra... Maybe this is more a piece of cake than OX?

Thanks for any suggestions and comments.

Regards,
 Manuel

Ah yes: currently running for mail: postfix+dovecot+spamassasin but i would not mind to change the setup if the proposed needs can only be achieved with another combination....

---

