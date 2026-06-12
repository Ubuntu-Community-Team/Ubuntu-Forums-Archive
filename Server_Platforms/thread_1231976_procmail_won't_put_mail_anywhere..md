---
title: "procmail won't put mail anywhere."
date: 2009-08-05
forum: Server Platforms
---

### Post by artheus on 2009-08-05
Hey!

I've got a problem now.. My procmail won't put my incoming mail in my "~/Maildir/" So my dovecot can read it.. *(please notice that I'm using maildir not mbox)*


Here's my postfix main.cf

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

myhostname = theidan.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = hurricane, localhost.localdomain, localhost, theidan.com
relayhost = smtprelay1.telia.com
mynetworks = 192.168.1.0/24 198.0.0.0/24 127.0.0.0/24 127.0.1.0/24
#mailbox_command = procmail -a "$EXTENSION"
mailbox_command = procmail
mailbox_size_limit = 40960000 recipient_delimiter = + inet_interfaces = all
#virtual_mailbox_domains = /usr/local/postfix/etc/virtual_domains
myorigin = /etc/mailname
inet_protocols = ipv4
```

And here's my /etc/procmailrc

```

DROPPRIVS=YES
ORGMAIL=${HOME}/Maildir/
DEFAULT=${ORGMAIL}

```

In Dovecot I'm using these setup for the mailbox

```

mail_location = maildir:~/Maildir

namespace private {
   separator = .
   prefix = INBOX.
   #location =
   inbox = yes
   #hidden = yes
   #list = yes
   # subscriptions = yes
}


```

Hope someone can help me!


Cheers,
Artheus

---

### Post by artheus on 2009-08-05
In my /var/log/mail.err I got this output

```

Aug  5 11:38:56 hurricane postfix/local[22047]: fatal: bad numerical configuration: mailbox_size_limit = 40960000 recipient_delimiter = + inet_interfaces = all
Aug  5 11:39:02 hurricane dovecot: IMAP(hurricane): FETCH for mailbox INBOX UID 1 failed to read message input: Is a directory

```

So I fixed the postfix problem... **But what on earth is the problem with dovecot!?**

What happens right now is that there is no messages in the INBOX but still it says that it is "Receiving 1 of 2 message headers" and no messages turn up.. And there is no messages in the "~/Maildir/new" folder either.. Cause the procmail will never put the messages in there!

Help! :S

---

### Post by ryanckoch on 2011-04-09
I realize this an old thread, but did you ever find a solution? I have run across the exact same issue.

Any help is greatly appreciated.
Thanks in advance!

---

### Post by SeijiSensei on 2011-04-09
> **ryanckoch said:**
> I realize this an old thread, but did you ever find a solution? I have run across the exact same issue.

Any help is greatly appreciated.
Thanks in advance!

If you're using procmail, add these lines to the top of $HOME/.procmailrc:

```

VERBOSE=yes
LOGFILE=$HOME/procmaillog

```

so you can see what procmail is doing with the mail.  Do you also have an /etc/procmailrc?  If so, you might want to add logging to that as well.

---

