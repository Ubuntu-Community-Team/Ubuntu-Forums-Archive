---
title: "upgrade to 14.04.1 breaks Dovecot"
date: 2014-09-29
forum: Server Platforms
---

### Post by pdcooper on 2014-09-29
I've upgraded and I cant connect to my localhost mail. Its delivered with exim to ~/Maildir  but TB IMAP  fails to login 

$ doveconf -n
# 2.2.9: /etc/dovecot/dovecot.conf
# OS: Linux 3.2.0-57-generic i686 Ubuntu 14.04.1 LTS 
auth_mechanisms = plain login
mail_location = maildir:~/Maildir: :INBOX=~/Maildir/.INBOX
namespace inbox {
  inbox = yes
  location = 
  mailbox Drafts {
    special_use = \Drafts
  }
  mailbox Junk {
    special_use = \Junk
  }
  mailbox Sent {
    special_use = \Sent
  }
  mailbox "Sent Messages" {
    special_use = \Sent
  }
  mailbox Trash {
    special_use = \Trash
  }
  prefix = 
}
passdb {
  driver = pam
}
protocols = " imap pop3"
ssl_cert = </etc/dovecot/dovecot.pem
ssl_key = </etc/dovecot/private/dovecot.pem
userdb {
  driver = passwd
}

$ telnet localhost 143
Trying ::1...
Connected to localhost.localdomain.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN AUTH=LOGIN] Dovecot (Ubuntu) ready.
a login "xxxx" "xxxx" 
* BYE Internal error occurred. Refer to server log for more information.
Connection closed by foreign host

$ tail -n 2 /var/log/mail.err
Sep 29 21:17:43 M266 dovecot: imap(jonny): Error: user jonny: Initialization failed: Namespace '': Unknown setting:  
Sep 29 21:17:43 M266 dovecot: imap(jonny): Error: Invalid user settings. Refer to server log for more information.
mars@twelve-M266:~/Maildir/new$ 
and the Maildir folder 
r$ ls ~/Maildir/
cur            dovecot.index.cache  dovecot-keywords     dovecot-uidlist      dovecot-uidvalidity.536bec74  new            tmp
dovecot.index  dovecot.index.log    dovecot.mailbox.log  dovecot-uidvalidity  maildirsize                   subscriptions


Google hasnt really helped me 
and mail is arriving in ~/Maildir/new


thanks  for any pointers

---

### Post by JKyleOKC on 2014-09-29
I'm having a rather similar problem; see my posts at [http://ubuntuforums.org/showthread.php?t=2246048](http://ubuntuforums.org/showthread.php?t=2246048) for details and some log file excerpts. However I'm not using imap, just pop3. Perhaps between us we can figure it out -- or find someone who can offer some leads to a fix!

---

### Post by CharlesA on 2014-09-29
What do your other config files look like? The last time I used dovecot.conf was in dovecot 1.x.

As far as namespaces go, see here:
[http://wiki2.dovecot.org/Namespaces](http://wiki2.dovecot.org/Namespaces)

---

