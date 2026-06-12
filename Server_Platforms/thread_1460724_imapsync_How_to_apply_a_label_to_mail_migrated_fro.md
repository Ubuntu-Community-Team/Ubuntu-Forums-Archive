---
title: "imapsync: How to apply a label to mail migrated from imap-server(A) to gmail(B)?"
date: 2010-04-23
forum: Server Platforms
---

### Post by JJRabbit on 2010-04-23
I would like to be able to read e-mail from imap-server(A) in gmail(B). In order to achieve this I use this command:

> sudo imapsync --host1 imap.server-A.com --port1 993 --ssl1 --user1 <my_username> --passfile1 /etc/secret1 --authmech1 LOGIN --host2 imap.gmail.com --port2 993 --ssl2 --user2 <my_username> --passfile2 /etc/secret2 --authmech2 LOGIN --delete --expunge1

The problem is that all mail now goes directly to inbox, while I want all mail from imap-server(A) to be accessable under the label 'Server-A'. Does anyone know how to apply a label to these e-mails automatically?

---

