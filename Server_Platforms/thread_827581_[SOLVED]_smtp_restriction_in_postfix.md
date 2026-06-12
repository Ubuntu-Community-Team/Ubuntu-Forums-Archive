---
title: "[SOLVED] smtp restriction in postfix"
date: 2008-06-12
forum: Server Platforms
---

### Post by janskey on 2008-06-12
Hi All,

I need some advice on how I can restrict smtp(postfix). Here is the scenario:
- currently we have 9 servers + 1 smtp. all servers are inside the firewall.
1. prod1.test.com
2. prod2.test.com
....
....
....
6. prod6.test.com
7. nagios.test.com
8. jira.test.com
9. wiki.test.com
10. smtp.test.com

My problem is how can I restrict:
-&nbsp; if originator is prodx.test.ph uses smtp server, it can send to any recipient
-&nbsp; if non-prodx server, only @sistercompany.com recipient will be sent; ignore none @sistercompany.com

I tried looking on this solution
[http://www.postfix.org/RESTRICTION_CLASS_README.html](http://www.postfix.org/RESTRICTION_CLASS_README.html) , but don't know how to construct my class. I'm also confused on
smtpd_recipient_restrictions and smtpd_sender_restrictions. Which is best solution will do on this problem?

---

### Post by gtdaqua on 2008-06-13
> 
/opt/zimbra/postfix/conf/sales-senders
[email]user1@domain.com[/email]		OK
[email]user2@domain.com[/email]		OK

/opt/zimbra/postfix/conf/accounts-senders
[email]user3@domain.com[/email]		OK
[email]user4@domain.com[/email]		OK


/opt/zimbra/postfix/conf/protected_recipients
[email]accounts-dl@domain.com[/email]		accounts-senders-list
[email]sales-dl@bksec.com[/email]		sales-senders-list

/opt/zimbra/postfix/conf/update-sec-list
#!/bin/bash
echo "rebuild authorised sales-list senders..."
postmap /opt/zimbra/postfix/conf/sales-senders
echo "rebuild authorised accounts-list senders..."
postmap /opt/zimbra/postfix/conf/accounts-list-senders

echo "REBUILD protected_recipeints..."
postmap /opt/zimbra/postfix/conf/protected_recipients


/opt/zimbra/postfix/conf/main.cf
sales-senders-list = check_sender_access hash:/opt/zimbra/postfix/conf/sales-senders, reject
accounts-senders-list = check_sender_access hash:/opt/zimbra/postfix/conf/accounts-senders, reject

smtpd_restriction_classes = sales-senders-list, accounts-list

/opt/zimbra/conf/postfix_recipient_restrictions.cf
hash:/opt/zimbra/postfix/conf/protected_recipients


************ Auto CC of an account **************

to get it to work it did the following steps

In /opt/zimbra/postfix/conf create a file called "sender_bcc" and to it:
"employee@domain.com 	[email]monitor@domain.com[/email]"

In /opt/zimbra/postfix/conf/main.conf add
"sender_bcc_maps = hash:/opt/zimbra/postfix/conf/sender_bcc"

then run as zimbra user
"postmap /opt/zimbra/postfix/conf/sender_bcc"

restart postfix -
"postfix reload"


This is something I posted in Zimbra Forums long ago to have granular control over email accounts. You can configure granular level mail-relay access controls. For e.g. you can say only @abc.com can send to @xyz.com or even restrict certain accounts inside @abc.com to relay to @xyz.com. 

Quite confusing in the beginning, but you will get the hang of it.

Good luck ;)

---

