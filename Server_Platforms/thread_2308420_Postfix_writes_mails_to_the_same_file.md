---
title: "Postfix writes mails to the same file"
date: 2016-01-02
forum: Server Platforms
---

### Post by Adrian_Veliz on 2016-01-02
I've set up postfix and can both send and receive mails from and to the outside, however all mails received are put into a file in /var/mail/username rather than a folder in the virtual folder, and every new email is just appended to the end of the existing text.

virtual_mailbox_base is set to /var/spool/mail/virtual
virtual_mailbox_maps is set to  mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
and /etc/postfix/mysql-virtual-mailbox-maps.cf looks like this:

```

user = mail
password = password (there for testing purposes)
hosts = 127.0.0.1
dbname = maildb
query = SELECT maildir FROM users WHERE id="%s"


```

---

