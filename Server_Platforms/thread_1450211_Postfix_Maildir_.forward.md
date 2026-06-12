---
title: "Postfix Maildir .forward"
date: 2010-04-08
forum: Server Platforms
---

### Post by CCG121 on 2010-04-08
I recently Re-did my Postfix configuration using 
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

The thing that that guide did not tell me was how to get email to forward to other accounts or if I can point multiple accounts to the same place like here:
[FONT=monospace]
[/FONT]/etc/postfix/vmaps:
(Change in bold)

[EMAIL="info@domain1.com"]info@domain1.com[/EMAIL]  domain1.com/info/
[EMAIL="sales@domain1.com"]sales@domain1.com[/EMAIL]  domain1.com/**info**/
[EMAIL="info@domain2.com"]info@domain2.com[/EMAIL]  domain2.com/info/
[EMAIL="sales@domain2.com"]sales@domain2.com[/EMAIL]  domain2.com/sales/

which I tried to do but didn't seem to work

I have also Tried:

/etc/postfix/vmaps:
(Change in bold)
 [EMAIL="info@domain1.com"]info@domain1.com[/EMAIL]  domain1.com/info/
[EMAIL="sales@domain1.com"]sales@domain1.com[/EMAIL] **info@domain1.com**
[EMAIL="info@domain2.com"]info@domain2.com[/EMAIL]  domain2.com/info/
[EMAIL="sales@domain2.com"]sales@domain2.com[/EMAIL]  domain2.com/sales/

finally I tried putting a .forward record in /home/vmail/domain.com/username directory which didn't work either.

---

### Post by CCG121 on 2010-04-09
A couple more things I have still been looking and want to share and/or ask

my /etc/postfix.main.cf file looks like:
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $myhostname
mynetworks = 127.0.0.0/8, 10.0.0.0/24
mailbox_size_limit = 0
home_mailbox = Maildir/
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
recipient_delimiter = +
inet_interfaces = all
```and can the /etc/aliases file be used 
because someone was saying that with actual unix users that it could
is there a way to make my virtual setup use it to forward.

---

