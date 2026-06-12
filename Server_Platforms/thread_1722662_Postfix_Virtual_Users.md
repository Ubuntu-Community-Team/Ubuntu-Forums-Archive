---
title: "Postfix Virtual Users"
date: 2011-04-06
forum: Server Platforms
---

### Post by Drezard on 2011-04-06
Basically, I want a "catch-all" user. (Not a domain catch-all, a user catch-all). 

So when mail is sent to user@* (as long as the * is a domain listed in vhosts) then the mail gets dropped in this users mailbox.

My configuration looks like the below...

The only problem is when I send emails here is the responses I'm getting:
```

Send an email to:
test@example1.com - example1.com/test/ - works perfectly :)
test@example2.com - example2.com/test/ - works perfectly :)
test01@example1.com - NDR - no user recognized - fails
test01@example2.com - NDR - no user recognized - fails

```

How I would like it to work:
```

Send an email to:
test@example1.com - example1.com/test/ 
test@example2.com - example2.com/test/ 
test01@example1.com - test/
test01@example2.com - test/

```

vmaps (It is being postmap'ed):
```

test01    test/
test@example1.com    example1.com/test/
test@example2.com    example2.com/test/

```

vhosts:
```

example1.com
example2.com

```

main.cf:
```

smtpd_banner = Mail Relay
biff = no

append_dot_mydomain = no

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mynetworks = 127.0.0.0/8
mailbox_command =
mailbox_size_limit = 0
home_mailbox = Maildir/
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /home/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:1000
virtual_gid_maps = static:1000
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
mydestination = $myhostname
relayhost =

```

mail.log:
```

Apr  6 10:28:15 mail-relay postfix/qmgr[6106]: D3FDC62B819F: from=<root@localhost>, size=354, nrcpt=1 (queue active)
Apr  6 10:28:15 mail-relay postfix/virtual[6117]: D3FDC62B819F: to=<test01@example1.com>, relay=virtual, delay=11, delays=11/0.02/0/0.02, dsn=5.1.1, status=bounced (unknown user: "test01@example1.com")

```

How do I go about setting this up?

Drez

---

### Post by venol on 2011-04-07
maybe use parameter "luser_relay"

---

### Post by usatonycuba on 2011-04-07
I always use mysql-base system for mail.. where is a easy way to conf... mysql-virtual_mailboxes.cf ...and using
 query = SELECT CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/') FROM users WHERE email='%s'

You always have to make sure that your domain NEED to be listed in vhosts.. in order to be recognize by your mysql-virtual_transports.cf

---

### Post by SeijiSensei on 2011-04-07
How will the sender be notified that an address does not exist?  NDN's are an important feature of the SMTP standard.

From [RFC 2821]("http://www.ietf.org/rfc/rfc2821.txt"):  
   If there is a delivery failure after acceptance of a message, the
   receiver-SMTP MUST formulate and mail a notification message.  This
   notification MUST be sent using a null ("<>") reverse path in the
   envelope.

When they say MUST, they mean MUST.

---

