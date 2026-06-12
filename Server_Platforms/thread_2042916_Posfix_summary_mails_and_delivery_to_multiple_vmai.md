---
title: "Posfix summary mails and delivery to multiple vmailboxes"
date: 2012-08-15
forum: Server Platforms
---

### Post by peterpan007 on 2012-08-15
Hello all, so far I have managed to configure my postfix using maildirs and a
mapping in the file /etc/postfix/vmailbox.
I would like to add two more features, but can't find out where to start or what
they are called.

First feature is that I want a short summary of every mail arriving on the server
put in the mailbox of sum@domain. Summary means just the From, Subject and maybe
time or first 2-3 lines, not sure yet, so I don't need to login in all accounts to
check. I guess I need to call some other program to create these summary mails, just
how?

Second feature is only neccesarry if the first one doesn't work. If a mail arrives
for x1@domain, then i want a copy in x2@domain, both are at the moment configured in
vmailbox, but I guess I need to setup this somewhere else. Is it possible to deliver
to multiple maildirs somehow?

Working examples would be nice, but any hints are very welcome!

---

