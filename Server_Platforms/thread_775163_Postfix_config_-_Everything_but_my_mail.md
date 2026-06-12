---
title: "Postfix config - Everything but my mail"
date: 2008-04-29
forum: Server Platforms
---

### Post by rendon on 2008-04-29
Hey there,

I'm wondering if anyone can help me solve this issue, I'm no newbie to linux, however a complete newbie to STMP and IMAP.  I got my IMAP up and running with dovecot, everything seems to be working fine, and Postfix is even receiving and send mails regularly...HOWEVER:

I can receive everything BESIDES the mail I expect to be receiving!

I'm receive tons of spam, and I can send mails fine, but I don't know what settings I have to config to get the actual mail for the user of my server.

my main.cf looks like this:

```

myhostname = domain.com
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
myorigin = domain.com
mydestination = localhost, www.domain.com, domain.com, localhost.domain.com, localhost.www.domain.com
relayhost =
mynetworks = 127.0.0.0/8
inet_interfaces = all
mail_spool_directory = /var/mail
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_alias_maps = hash:/etc/postfix/virtual
local_recipient_maps =

```

you can see I even allowed local_recipient_maps to allow everything, but I'm still only getting mail to users who don't exist, I know why of course, it's because I set the virtual alias table like this:

```

username@domain.com username
@domain.com username


```

so you can see I'm receiving the wildcard emails under my usernames mailbox.  But I'm still not recieving the username's ordinary emails!!!

I seem to have success when I send emails to:

[email]username@**www**.domain.com[/email]

but not to:

[email]username@domain.com[/email]

my aliases table looks like this:

```

# Added by installer for initial user
root:   username
username: username
amavis: root
clamav: root


```


anyone know what I'm doing wrong?

---

### Post by rendon on 2008-04-29
by the way, I should mention that when I try to send the mails from  gmail to [email]user@domain.com[/email] I get something like this:

```

This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

    user@domain.com

Technical details of permanent failure:
PERM_FAILURE: Gmail tried to deliver your message, but it was rejected by the recipient domain. The error that the other server returned was: 550 550-5.1.1 This Gmail user does not exist. Please try double-checking
550-5.1.1 the recipient's email address for typos or unnecessary spaces.
550-5.1.1 Learn more at
550 5.1.1 http://mail.google.com/support/bin/answer.py?answer=6596 i34si2529347wxd.15. We recommend contacting the other email provider for further information about the cause of this error. Thanks for your continued support. (state 14)

```

which obviously points to a recipient problem... but...?

again, I was successful with [email]user@www.domain.com[/email] ... so I was wondering if it's possible that settings need to be changed in apache or something to allow just domain.com

of course, I already have **ServerAlias = domain.com** configed and working fine...

---

