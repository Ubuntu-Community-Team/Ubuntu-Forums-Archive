---
title: "vitual mailbox base with mysql"
date: 2012-03-05
forum: Server Platforms
---

### Post by markp_2000 on 2012-03-05
I have a virtual mail server setup and working.  Howerver, I think I have the virtual_mailbox_base directive setup incorrectly.  Right now all virtual users get dumped into /var/mail/virtual and I would like the users to be segmented by domain.  For example /var/mail/virtual/domain1.com/mark and /var/mail/virtual/domain2.com/mark.

Right now I can't use the username mark for both domains.

```

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

```


Any idea?

---

### Post by markp_2000 on 2012-03-05
OK - I answered my own question.  When I define the folder in the mysql query I should specify the domain as well as the username.

Mark

---

