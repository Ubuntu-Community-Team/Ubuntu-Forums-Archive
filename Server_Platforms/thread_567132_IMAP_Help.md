---
title: "IMAP Help"
date: 2007-10-04
forum: Server Platforms
---

### Post by DavidRussellCA on 2007-10-04
I've got everything working with my IMAP server except for incoming mails.  They're being received by the server and showing up in /var/mail/username as "New Mail!" but they aren't showing up in my inbox.  When set up through Thunderbird/Mail.app - all the folders appear, including sent (which contains emals sent from the account which do work), trash, etc.  Just the inbox doesn't seem to be synchronizing even though the emails are being recieved by the server.

Permissions on the Maildir match those given in the tutorials in community help.

Any ideas?

---

### Post by MJN on 2007-10-04
What mail and IMAP server are you using?
 
It sounds like a simple case of your client (due either to its, or the IMAP server's, settings) looking in the wrong place (home directory) for your Inbox given your mail server is dumping mail in /var/mail/username.
 
You need to either change where your mail server is dumping mail, or tell your IMAP server where that place (Inbox) is.
 
Where are your folders stored?
 
Mathew

---

### Post by DavidRussellCA on 2007-10-04
I followed the tutorials here:

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

I'm using Courier IMAP / Postfix.  I set up the directories as described in the Courier tutorial on that page.  If I create a new folder in the Maildir, it shows up in SquirrelMail / Mail.app (OS X).  It's in the home directory ~/Maildir.  (Where the username of the home directory matches that of /var/mail/username) I can't see any settings on how to set up Courier to dump the mail there.  If I use Squirrel Mail to send out mail it sends fine (to Gmail, for instance) and appears in the sent folder in all programs.  I'm stumped :(

thanks for the response :)

---

### Post by MJN on 2007-10-04
Try **home_mailbox = Maildir/** in /etc/postfix/main.cf then this will make Postfix dump incoming mail there.

Mathew

---

### Post by DavidRussellCA on 2007-10-04
Gave that a shot and reloaded/restarted postfix without any luck.   Any other ideas?

---

### Post by MJN on 2007-10-04
If you post your Postfix config we can take a look.

Mathew

---

### Post by DavidRussellCA on 2007-10-04
Here it is:

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.eng.server.ca
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.server.ca, mail.Eng.server.CA, localhost.Eng.server.CA, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
relay_domains = mail.eng.server.ca
transport_maps = hash:/etc/postfix/transport
mailman_destination_recipient_limit = 1
content_filter=smtp-amavis:[127.0.0.1]:10024
home_mailbox = Maildir/

Could one of the problems be to do with the alias?  mail.server.ca is a alias of mail.eng.server.ca (simplified :p).  Mail sent to [email]account@mail.server.ca[/email] goes through and shows up in /var/mail/account, but not in IMAP.  Mail sent to [email]account@mail.eng.server.ca[/email] gets rejected saying "user does not exist".

---

### Post by MJN on 2007-10-04
Ah okay, as you're using procmail for final delivery remove the home_mailbox directive we've just added and change the mailbox_command to:

```
mailbox_command = procmail -a "$EXTENSION" DEFAULT=$HOME/Maildir/ MAILDIR=$HOME/Maildir
```

Mathew

---

### Post by DavidRussellCA on 2007-10-04
You are my hero!  It works!!

Thank you so much for your help :D

---

### Post by MJN on 2007-10-04
No problem - a pleasure to help.

(we've all been there at some stage, and there's nothing worse than hitting a brick wall with seemingly no way through!)

Mathew

---

### Post by DavidRussellCA on 2007-10-04
Forgot to ask - how did you know how to do that?  I'm curious to how you knew that would fix it or was it just from experience?

Also, do you know of any easy way to set up an address to redirect somewhere with my setup?  [email]username@mail.server.ca[/email] -> [email]someone@gmail.com[/email]?

Cheers!

---

### Post by DavidRussellCA on 2007-10-04
Also - this seems to have overridden the transport settings I had which had mailman working properly.  Mail is getting lost it seems going to my mailman list - as it's not getting rejected, but not going through anywhere.

---

### Post by MJN on 2007-10-04
Just experience and, most importantly, keeping notes of things I've done/changed/found etc as I was always solving problems and then bumping into them again at a later date only to have to reinvent the wheel and re-solve them having forgotten how to do things! Also, commenting config files when you add/change something really helps too!

There are many ways to forward mail, one of the simplest being to edit the /etc/aliases file. There will probably already be an entry in it defining who gets root's mail and will take the form **<local user>: <address>**.  If you add the line **<username>: [EMAIL="someone@gmail.com"]someone@gmail.com[/EMAIL]**, save it and run **sudo newaliases**, then reload Postfix.

I'm not sure about your mailman issue as I'm not familiar with it. Does your /var/log/mail.log give any clues?

Mathew

---

