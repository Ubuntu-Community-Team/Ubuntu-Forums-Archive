---
title: "Squirrelmail shows an empty inbox? (Postfix, Courier)"
date: 2006-01-19
forum: Server Platforms
---

### Post by jimwillsher on 2006-01-19
Help! I've wasted 12 hours so far, and I'm sure it'll be simple! I'm obviosuly missing a vital bit!

Here's my entire main.cf:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = arachnid.jimwillsher.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname

mydestination = arachnid.jimwillsher.co.uk, localhost.jimwillsher.co.uk, localhost
virtual_alias_domains = jimwillsher.co.uk, broadband4blackford.co.uk, chriswillsher.co.uk, andiwillsher.co.uk, bulkrenameutility.co.uk, phpfreenews.co.uk
virtual_alias_maps = hash:/etc/postfix/virtual

relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 102400000
recipient_delimiter = +
inet_interfaces = all

# mailbox_command =
# mailbox_command = /usr/bin/procmail -f- -a "$USER"
mailbox_command = /usr/bin/procmail -a "$EXTENSION"
# mailbox_command = /usr/bin/procmail

smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/

```

and here's my /etc/procmailrc

```

VERBOSE=yes

# Now run as the recipient user
# DROPPRIVS=yes

MAILDIR=$HOME/Maildir

# Use a seperate directory to store reciepes and logs
PMDIR=$HOME

# Tell procmail where to put the log file
LOGFILE=$PMDIR/procmail.log

```

Now, in my main.cf, if I remove the line

```

mailbox_command = /usr/bin/procmail -a "$EXTENSION"

```

and replace it with

```

mailbox_command = 

```

new emails show up correctly in squirrelmail's inbox. But of course, I'm not able to filter my mail based upon the headers (I'm using clamav and spamassassin via amavisd-new). Hence why I want to use procmail recipes.

But with the

```

mailbox_command = /usr/bin/procmail -a "$EXTENSION"

```

code, the spamassassin mailboxes remain empty - EVEN THOUGH the mail is still delivered to /var/mail/username

As you can see frm main.cf I've also tried a variant of the procmail call but with the same results.

I'm currently using dovecot (dovecot-pop3d, dovecot-imap), but I spent most of yesterday trying with courier and had the same.

What am I missing? Is it squirrelmail that's misconfigured? Or is it procmail? Or imap? In all cases squirrelmail successfully logs onto the imap mailboxes, but they are always empty. I'm guessing it relates partial to the "Maildir" entry in main.cf, or to the mailbox format.

Please can somebody put me out of my misery :( 

Many thanks,



Jim

---

### Post by jimwillsher on 2006-01-19
In the cold light of day, setting this:

```
default_mail_env = mbox:~/Maildir/:INBOX=/var/mail/%u
```

in /etc/dovecot/dovecot.conf appears to now be working. I guess there was a similar setting in courier - I'll try that today and report back!


Jim

---

### Post by MJN on 2006-01-19
You appear to be mixing mbox and maildir formats, with the inevitable odd side effects that this will cause!

'Traditional' UNIX mailboxes uses the mbox format, and thus mail is usually delivered to /var/spool/mail/<user>. Any IMAP implementation would then go on to store folders and stored messages in the users' home directory e.g. $home/Mail. Of course, all these locations are configurable but this is the common default.

The maildir format, on the other hand, usually stores all mail (i.e. the inbox and every other folder) within the user's directory, by convention the default is $home/Maildir.

Incidentally, I used to use the mbox format (on RedHat with Postfix and UW-IMAP) but now that I've moved to Kubuntu (with Postfix and Dovecot) I've also switched to maildir format. The performance increase has been amazing but, unfortunately, I've changed too many variables to be able to quantify the mbox-maildir variation however I can definitely say I sit more comfortable with having all my messages stored in a standard format - not to mention being able to have mail folders contain messages **and** other folders!

Back to the issue in hand, are you all up-and-running again now?

Mathew

** EDIT: Bu66er it... re-reading your config you appear not to be mixing up mbox with maildir, indeed it seems you're using mbox throughout. Apologies... I'll leave my post if only to avoide wasting the effort of me typing it out in the first place! You never know, it might help someone searching the archives and a similar, but different, problem...** ;)

---

### Post by jimwillsher on 2006-01-20
Hey hey, don;t worry :-)

I thought I'd try Courier as I was following a howto at [http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10) - but I soon gave up and went for dovecot, which I was more familiar with. And it works a treat! All mail is delivered to /var/spool/mail etc, but SquirrelMai correctly reads this and allows me to move messages to folders in /home/user/mail - which is exactly what I was after.

But many thanks for the explanation, I now know how the Maildir etc stuff works....

Cheers,


Jim

---

