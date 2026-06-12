---
title: "Outlook and Ubuntu Webmail"
date: 2012-03-25
forum: Server Platforms
---

### Post by bosco555 on 2012-03-25
Hi All,

newbie here as far as Ubuntu goes.  I am in the process of migrating from another flavour of Linux to Ubuntu server.  I had read some place that with Ubuntu, users could have outlook and Webmail in sync.

In other words, whenever a user sends an email in outlook, the same email would show in the Webmail sent items folder and vice-versa.  Could someone please direct me on the right path on how to achieve this?

Thank you all in advance and best regards

bosco

---

### Post by jonobr on 2012-03-26
Hello


I may not be the right person to answer this, and am open to correction,  however, if you are using outlook client and a webmail client, synchronization is performed using Imap which synchronizes folders between the server and the client,
So, If i delete something in one folder or get a message on one interface, it will be replicated on the other,
POP on the other hand, will get the message from the server and its default action would be to delete the message on the server.

This would mean that I could have one message on my client in outlook and another in the webmail interface.

I could choose to leave them on the server and not delete, but I guess you loose the cross platform synching.

---

### Post by Habitual on 2012-03-26
+1
imap.

---

### Post by bosco555 on 2012-03-27
Hi all and thank you for the replies...will go with imap then, no worries.  I had trouble with imap and outlook in the past where outlook didn't show all the folders though..hopefully this has been resolved.

I was reading about evolution and it would be great if users could get used to the idea of using a web interface for their email..

thank you again and best to all

bosco

---

### Post by SeijiSensei on 2012-03-27
IMAP uses the concept of "subscribing" to folders.  If Outlook didn't see some of a user's folders, you need to check which folders are subscribed to and add the missing ones.  Since I don't use Outlook, I can't tell you where that option might be, though.  Sorry!

Squirrelmail is an excellent webmail client; it's in the repositories.

---

