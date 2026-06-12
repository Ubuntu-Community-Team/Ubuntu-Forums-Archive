---
title: "postfix - virtual_alias_maps problem"
date: 2006-03-10
forum: Server Platforms
---

### Post by nullEX on 2006-03-10
We have installed a mail server in an Ubuntu 5.10 (Breezy Badger). We use Postfix + MySQL + SASL2 + Courier + Amavis + Spamassassim + ClamAV. The system is based on VIRTUAL domains and users that we store in a MySQL database.

The server with users and domains, works perfectly. It can be sent and received emails between virtual existing users without problems. But we wish implement a fine improvement, groups and redirections. The groups are an email addresses that have not mailbox. It's an alias from one mail address to a list of directions that we store in the database; and the redirections are some alias from one mail address that redirects to one existing mailboxes.

The file "/etc/postfix/main.cf" contains these lines to be able to realize the needed operations:

```

Virtual_alias_domains =
Virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_domain s.cf
Virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_email2 email.cf mysql:/etc/postfix/mysql-virtual_forwar dings.cf mysql:/etc/postfix/mysql-virtual_groups .cf
Virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailbo xes.cf
Virtual_mailbox_base =/home/vmail
Virtual_uid_maps = static:5000
Virtual_gid_maps = static:5000
#relocated_maps = mysql:/etc/postfix/mysql-virtual_reloca ted.cf

```

The files mysql-virtual_xxxxxxxx.cf contains truth conection information to the database and the sentence that must be executed.

Well, this setup in a Debian Sarge works perfectly; groups, users and forwards; but Ubuntu's Postfix package is like if the existence of the users only was using "virtual_alias_maps" for validations:

Imagine that we have: 'user1@example.com' and 'user2@example.com'; an alias that redirects 'user11@example.com' to 'user1@example.com'. And at last the group: 'todos@example.com' that redirects to 'user1@example.com' and 'user2@example.com':

**Users:**
  email			|	      password
------------------------------------
[email]user1@example.com[/email] |	xxxxxx
[email]user2@example.com[/email] |	xxxxxx

**Fws:**
 source			|	      destination
------------------------------------
[email]user11@example.com[/email] |	[email]user1@example.com[/email]

**groups_users:**
 gmail			|	      umail
------------------------------------
[email]todos@example.com[/email] |	[email]user1@example.com[/email]
[email]todos@example.com[/email] |	[email]user2@example.com[/email]

If we send an email to 'user1@example.com' or 'user2@example.com', everything works perfectly, but for example, sendding an email to 'user11@example.com' it validates that the user exists and  confirms SMTP request. But at time of sending it, server doesn't verify that it's an alias and tries to look for its mailbox, that doesn't exist. We've checked this mistake by making a bit hard SQL sentence for looking for the users mailbox, doing that looks also for an user alias.



And finally we come to the mistake that we cannot correct: When we send from 'user1@example.com' to 'todos@example.com'. The address is good and leaves you to finish the SMTP request, but when one prepares to send the mail instead of interpreting with alias that has to redirect to a series of address, looks its maildir, which does not exist...

The mysql-virtual_mailboxes.cf file:

```

user = mysql_user_reader
password = xxxxxxxxxxx
dbname = dbmail
query = SELECT distinct CONCAT(SUBSTRING_INDEX(u.email,'@',-1),'/', SUBSTRING_INDEX(u.email,'@',1),'/') FROM users u, forwardings f WHERE u.email='%s' OR (u.email = f.destination AND f.source = '%s')
hosts = localhost

```

Also we've tried to compile an old postfix version but we'd problems with ubuntu mysql libraries; but in spite of compile, the postfix-mysql package doesn't works. So we keep using ubuntus precompiled package...

The mail.log:

```

Sea 9 11:37:39 server-mail postfix/smtpd [11836]: D924C48519: client=cliente.midominio.com [192.168.123.98, sasl_method=LOGIN, sasl_username=user1@example.com
Sea 9 11:37:39 server-mail postfix/cleanup [11848]: D924C48519: message - go =
Sea 9 11:37:39 server-mail postfix/qmgr [11829]: D924C48519: from =, size=2011, nrcpt=1 (queue it(he,she) activates)
Sea 9 11:37:40 server-mail postfix/smtpd [11853]: connect from localhost.localdomain [127.0.0.1]
Sea 9 11:37:40 server-mail postfix/smtpd [11853]: 0A9BD4851A: client=localhost.localdomain [127.0.0.1]
Sea 9 11:37:40 server-mail postfix/cleanup [11848]: 0A9BD4851A: message - go =
Sea 9 11:37:40 server-mail postfix/qmgr [11829]: 0A9BD4851A: from =, size=2478, nrcpt=1 (queue it(he,she) activates)
Sea 9 11:37:40 server-mail postfix/smtpd [11853]: disconnect from localhost.localdomain [127.0.0.1]
Sea 9 11:37:40 server-mail amavis [7009]: (07009-07) Passed, - >, Message - Go:, Hits:-
Sea 9 11:37:40 server-mail postfix/lmtp [11849]: D924C48519: to =, relay=127.0.0.1 [127.0.0.1, delay=1, status=sent (250 2.6.0 Ok, id=07009-07, from MTA: 250 Ok: queued seize 0A9BD4851A)
Sea 9 11:37:40 server-mail postfix/qmgr [11829]: D924C48519: remove
Sea 9 11:37:40 server-mail postfix/virtual [11857]: 0A9BD4851A: to =, relay=virtual, delay=0, status=bounced (unknown user: "todos@example.com")
Sea 9 11:37:40 server-mail postfix/cleanup [11848]: 1BBCB4851B: message - go =

```

And that MySQL.log:

```

060309 11:37:39 194 Connect mail_reader@localhost on dbmail
194 Quit
195 Connect mail_reader@localhost on dbmail
195 Quit
196 Connect mail_reader@localhost on dbmail
196 Query BEGIN
196 Query select password from users where email ='user1@example.com '
196 Query select password from users where email ='user1@example.com '
196 Query COMMIT
196 Quit
197 Connect mail_reader@localhost on dbmail
197 Quit
198 Connect mail_reader@localhost on dbmail
198 Query 'virtual' SELECT FROM domains WHERE domain ='example.com '
198 Query 'virtual' SELECT FROM domains WHERE domain ='example.com '
199 Connect mail_reader@localhost on dbmail
199 Query SELECT email FROM users WHERE email ='todos@example.com '
200 Connect mail_reader@localhost on dbmail
200 Query SELECT destination FROM forwardings WHERE source ='todos@example.com '
201 Connect mail_reader@localhost on dbmail
201 Query SELECT umail FROM groups_users WHERE gmail ='todos@example.com '
060309 11:37:40 198 Query 'virtual' SELECT FROM domains WHERE domain ='example.com '
198 Query 'virtual' SELECT FROM domains WHERE domain ='example.com '
202 Connect mail_reader@localhost on dbmail
202 Query SELECT email FROM users WHERE email ='todos@example.com '
203 Connect mail_reader@localhost on dbmail
203 Query SELECT destination FROM forwardings WHERE source ='todos@example.com '
204 Connect mail_reader@localhost on dbmail
204 Query SELECT umail FROM groups_users WHERE gmail ='todos@example.com '
198 Query 'virtual' SELECT FROM domains WHERE domain ='example.com '
205 Connect mail_reader@localhost on dbmail
205 Query SELECT distinct CONCAT (SUBSTRING_INDEX (u.email, '',-1), '/', SUBSTRING_INDEX (u.email, '', 1), '/') FROM users or, forwardings f WHERE u.email ='todos@example.com ' OR (u.email = f.destination AND f.source = ' todos@example.com ')
205 Query SELECT distinct CONCAT (SUBSTRING_INDEX (u.email, '',-1), '/', SUBSTRING_INDEX (u.email, '', 1), '/') FROM users or, forwardings f WHERE u.email = ' example.com ' OR (u.email = f.destination AND f.source = '@example.com')
206 Connect mail_reader@localhost on dbmail
206 Query SELECT email FROM users WHERE email ='user1@example.com '
198 Query 'virtual' SELECT FROM domains WHERE domain ='example.com '
205 Query SELECT distinct CONCAT (SUBSTRING_INDEX (u.email, '',-1), '/', SUBSTRING_INDEX (u.email, '', 1), '/') FROM users or, forwardings f WHERE u.email ='user1@example.com ' OR (u.email = f.destination AND f.source = ' user1@example.com ')

```

We do not know why this version of the Postfix only uses virtual aliases for the authoritation of a mail address, but not for its transport. It's possible that a new field exists for this work, but after 5 days exploring Internet, reading tutorials, documents, manuals and other things; we can't realize this.

If someone can help us or knows what is happend...

Thank you very much in advance.

PS: Sorry for my horrible English.

---

