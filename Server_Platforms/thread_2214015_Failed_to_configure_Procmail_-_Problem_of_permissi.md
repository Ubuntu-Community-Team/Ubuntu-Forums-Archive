---
title: "Failed to configure Procmail - Problem of permissions?"
date: 2014-03-29
forum: Server Platforms
---

### Post by dudumomo on 2014-03-29
Hi everyone,

I've recently installed Postfix + Dovecot + SpamAssassin + Procmail, however I cannot make procmail work as expected. (If I don't use it, everything work well), but I wish to use it to move SPAM mails into a SPAM folder.
And it could come from a permissions issue...

Here is the procmail conf file I'm trying to use:
```
# file: /etc/procmailrc
# system-wide settings for procmail
# Use the following if you get "destination user parameter (-d user) not given":
DROPPRIVS="YES"
# fallback:
MAILDIR=$HOME/Maildir/
DEFAULT=$MAILDIR/

LOGFILE=/var/log/procmailrc.log
VERBOSE=yes
LOGABSTRACT=all

# Procmail rule to delete spam
:0:
* ^X-Spam-Status: Yes
.Junk E-mail
```

But in this case, I cannot see any mails in my Thunderbird client. However in /home/user/Maildir/new I can see I've received the mail....
And if I replace MAILDIR=$HOME/Maildir/ by MAILDIR=$HOME/somethingthatdoesn'texist, I can have access again to my mails with Thunderbird...(But SPAM are not filter)

Here is my postfix conf:
```
root@serverhome:/home/dudumomo# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
mailbox_command = /usr/bin/procmail -Y -a $DOMAIN
mailbox_size_limit = 0
mydestination = mail.freedif.org, freedif.org, localhost, localhost.localdomain
myhostname = mail.fredif.org
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/ssl/certs/freedif.pem
smtpd_tls_key_file = /etc/ssl/private/freedif.key
smtpd_tls_protocols = !SSLv2, !SSLv3
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
```

Any idea what could be the problem?

Oh and by the way, in /home/user, i've always 1 Maildir/ and 1 mail/
Is it normal?

Thanks for your help !

---

### Post by SeijiSensei on 2014-03-30
The file /etc/procmailrc is run with root permissions.  You probably don't need an /etc/procmailrc at all.  Instead, place your recipes in $HOME/.procmailrc, which is run with your own permissions during delivery.

From "[man procmail]("http://linux.die.net/man/1/procmail")":
> If no rcfiles and no -p have been specified on the command line, procmail will, prior to reading $HOME/.procmailrc, interpret commands from /etc/procmailrc (if present). Care must be taken when creating /etc/procmailrc, because, if circumstances permit, it will be executed with root privileges (contrary to the $HOME/.procmailrc file of course).

The only time you need an /etc/procmailrc is when you want to apply some recipes to all users' mail.  For instance, I once managed a server where we automatically routed likely spam messages to a folder in the user's directory.  In that case I placed the appropriate recipes in /etc/procmailrc and used the [LOGNAME]("http://linux.die.net/man/5/procmailrc") environment variable to direct the spammy messages to the appropriate user's folder.

---

### Post by dudumomo on 2014-03-31
Thanks SeijiSensei,

However, removing the /etc/procmailrc and adding a /home/myuser/.procmailrc didn't solve the issue.....
Any others idea?

Thank you!

---

### Post by SeijiSensei on 2014-03-31
The procmailrc you posted shows that you are logging its actions.  What do the logs show? Do you still have a permissions problem with a .procmailrc in your home directory.  Specifically which "issue" remained unsolved?

I would remove the MAILDIR and DEFAULT declarations and let procmail determine them.

I also don't know how procmail handles folder names with embedded spaces.  I avoid using embedded spaces in any file or folder name on Linux.  Anything being delivered to a folder called just "Junk?"

---

### Post by dudumomo on 2014-04-01
Okay I fixed the issue.

1) Align Dovecot and Postfix to use Maildir (I was using Maildir in Postix and Mbox in Dovecot), not sure if t has helped, but don't sounds consistent anyway
2) In Procmailrc, it needs to be in a folder not a file. Hence the .Junk, didn't work. But the .Junk/ worked.
3) And I needed to use directly the /home/myser/.procmailrc instead of /etc/procmailrc

Thank you Seiji for your hints !

---

### Post by SeijiSensei on 2014-04-01
Glad I could help!

---

