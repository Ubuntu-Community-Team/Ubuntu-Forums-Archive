---
title: "Postfix sends, but won't receive"
date: 2007-11-06
forum: Server Platforms
---

### Post by ktindle on 2007-11-06
I have a fresh Gutsy install with an odd problem- the plain Jane install of Postfix will send mail, but is not looking up the recipient address.

main.cf:

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

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=no
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = aatf.gws.uky.edu
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = aatf.gws.uky.edu, localhost.gws.uky.edu, localhost
relayhost = [mg3.uky.edu] 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
---
mail.log says:

Recipient address rejected: User unknown in local recipient table

I have populated /etc/aliases, and have tried setting up a custom transport map.  /etc/passwd and /etc/aliases is being ignored.  I have restarted the postfix service and used the newalises command.  All mail to this machine dies because there are no valid recipients on this machine as far as Postfix is concerned.

---

### Post by MJN on 2007-11-06
Post your /etc/aliases file - does it have the appropriate mapping?
 
Do you logs say anything when you restart Postfix? Config errors are usually only noted in the logs (and not the screen).
 
Mathew

---

### Post by HermanAB on 2007-11-06
You modified the wrong file.  User names are looked up in another file - can't remember what though.  So go back to the postfix web site and read a bit.

Cheers,

H.

---

### Post by ktindle on 2007-11-06
I found this page:

[http://www.postfix.org/LOCAL_RECIPIENT_README.html](http://www.postfix.org/LOCAL_RECIPIENT_README.html)

However, adding

local_recipient_maps =

to /etc/postfix/main.cf does not stop mail from being rejected with code 550.  Now, mail.log does not say anything, except showing a clean restart of the postfix daemon and confirming that it is using main.cf

Can (must) the virtual transport be used, instead of the default local transport?  Is postfix chrooted?  Is this so hard to do because you aren't supposed to receive mail in Ubuntu before acquiring guru status?

---

### Post by MJN on 2007-11-06
/etc/aliases (via the alias_maps directive) is the correct file to use - it is referred to for any mail destined for local users (as defined by the mydestination, and some other, directives).

However, I notice you have not changed the local_recipient_maps directive. The default is to check the validity of local users and it's not clear from your post whether the destination addresses are indeed local users with accounts. Try setting this to blank (i.e. local_recipient_maps = ) to turn off local user checking and restarting. If your Postfix is chrooted then it won't be able to access the passwd file (but we're jumping ahead of ourselves here).

Mathew

---

### Post by MJN on 2007-11-06
Our responses overlapped there.

Post your /etc/aliases file and mail.log when an incoming message arrives.

Mathew

---

### Post by ktindle on 2007-11-06
Here is the /etc/aliases:

# Added by installer for initial user
root:	<a valid local user name edited for security>

mailman:		"|/var/lib/mailman/mail/mailman post mailman"
mailman-admin:		"|/var/lib/mailman/mail/mailman admin mailman"
mailman-bounces:	"|/var/lib/mailman/mail/mailman bounces mailman"
mailman-confirm:	"|/var/lib/mailman/mail/mailman confirm mailman"
mailman-join:		"|/var/lib/mailman/mail/mailman join mailman"
mailman-leave:		"|/var/lib/mailman/mail/mailman leave mailman"
mailman-owner:		"|/var/lib/mailman/mail/mailman owner mailman"
mailman-request:	"|/var/lib/mailman/mail/mailman request mailman"
mailman-subscribe:	"|/var/lib/mailman/mail/mailman subscribe mailman"
mailman-unsubscribe:	"|/var/lib/mailman/mail/mailman unsubscribe mailman"

concours:		"|/var/lib/mailman/mail/mailman post concours"
concours-admin:		"|/var/lib/mailman/mail/mailman admin concours"
concours-bounces:	"|/var/lib/mailman/mail/mailman bounces concours"
concours-confirm:	"|/var/lib/mailman/mail/mailman confirm concours"
concours-join:		"|/var/lib/mailman/mail/mailman join concours"
concours-leave:		"|/var/lib/mailman/mail/mailman leave concours"
concours-owner:		"|/var/lib/mailman/mail/mailman owner concours"
concours-request:	"|/var/lib/mailman/mail/mailman request concours"
concours-subscribe:	"|/var/lib/mailman/mail/mailman subscribe concours"
concours-unsubscribe:	"|/var/lib/mailman/mail/mailman unsubscribe concours"

When a message comes in, for a valid local Unix user OR an alias defined in /etc/aliases, the mail.log does not react- at all.

The point of my previous post- local_recipient_maps IS set to a null value in main.cf.  I had log entries "User unknown in local recipient table" before running 'sudo newaliases', but now there are no entries in the log except for clean re-starting of the Postfix daemon, and nothing else.

I have tried setting up a custom transport using the postfix-to-mailman.py script, but the lack of user look-up happens before there is any thought of mail delivery.

All mail, to any local user or alias, is returned to sender with SMTP code 550, status 5.1.1.  Hard solid bounce.

---

### Post by MJN on 2007-11-06
You're using a format I'm not familiar with.

Try a simple:

someuser: localuseraccount

e.g. sales: mark

Does that work? Does mail to 'root' work? That is, does the <valid local user> get the mail? If so, then the alias database is working.

If you are specifically talking about mailman integration then I'd say that's where your problem lies (and I'm curious as to why you didn't mentioned mailman in your original post!)

Post your full mail.log - I'm curious as to what you mean by 'mail.log does not react at all'. Does it not even show a connection? You might wish to add a **-v** flag to the smptd command at the end of the smpt line in /etc/postfix/master.cf.

Mathew

---

### Post by ktindle on 2007-11-06
The simple

someuser: localuseraccount

does NOT work.

Mailman is irrelevant.  The SMTP code 550 can only come from an angry MTA, Mailman is glue code mostly written in Python, it doesn't get involved with the dirty details of SMTP.  Not relevant, hence not mentioned.

There are no entries in mail.log as messages come in, which is what I mean by no reaction.

---

### Post by MJN on 2007-11-06
Is your machine connected to the Internet? Is aatf.gws.uky.edu your machine? Is 128.163.114.12 your current IP? What's an example of an e-mail address you're testing? (PM me if you don't want to post it)

I propose to connect from here and see what happens. Something is not adding up here... It's sounding like the machine you're configuring is not the machine you're observing as a client! How are you testing? Local/remote mail client? Manual telnet?

If there are no entries in mail.log coinciding with when you are supposedly connecting then you are not connecting to that machine. Simple as that. 

Mathew

---

### Post by MJN on 2007-11-07
Thanks for the confirmations (via PM).
 
I can connect to aatf.gws.uky.edu and mail was accepted:
 
-----
**telnet aatf.gws.uky.edu 25**
Trying 128.163.114.12...
Connected to aatf.gws.uky.edu.
Escape character is '^]'.
220 aatf.gws.uky.edu ESMTP Postfix (Ubuntu)
**ehlo mail.newtonnet.co.uk**
250-aatf.gws.uky.edu
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
**mail from: ****nosuchuser@newtonnet.co.uk**
250 2.1.0 Ok
**rcpt to: [email]1stsuggesteduser@****aatf.gws.uky.edu[/email]**
250 2.1.5 Ok
**data**
354 End data with <CR><LF>.<CR><LF>
**This is a test.**
**.**
250 2.0.0 Ok: queued as 9D0CC33C182
**mail from: ****nosuchuser@newtonnet.co.uk**
250 2.1.0 Ok
**rcpt to: [email]2ndsuggesteduser@****aatf.gws.uky.edu[/email]**
250 2.1.5 Ok
**data**
354 End data with <CR><LF>.<CR><LF>
**This is another test.**
**.**
250 2.0.0 Ok: queued as 9FE8133C182
**quit**
221 2.0.0 Bye
Connection closed by foreign host.
-----
 
If none of that appeared in your mail.log then as I said you're configuring the wrong machine!
 
I note you don't have any MX records for aatf.gws.uky.edu - howcome? It shouldn't matter given the A record fallback but it's a curious arrangement to have in place.
 
Mathew

---

### Post by dothebart on 2007-11-07
why don't you use citadels dict-tcp implementation? details can be found here:
[http://www.citadel.org/doku.php/faq:installation:configuring_postfix_to_validate_email_addresses_against_a_citadel_server](http://www.citadel.org/doku.php/faq:installation:configuring_postfix_to_validate_email_addresses_against_a_citadel_server)

---

### Post by ktindle on 2007-11-07
OK, I have your test messages here in good shape.

The solution-

At first, I failed to run 'newaliases' after altering /etc/aliases.  I had thought rebooting the machine (for other reasons) would accomplish the same thing- nope.  You have to run 'newaliases'.  Period.

I was sending remote test mail through a mail server that is set to never relay anything in its home domain of uky.edu-  It will bounce with a 550 code instead.  This mail server is relatively new, and these security settings are also new, and caught me flatfooted.  The reason for no log activity- no connection attempt was ever made.

Before, I had sent test mail from a server outside uky.edu to check for this, but that was when I had not yet run 'newaliases', so the (correct) "User not in local recipient table" was recorded in the mail log.  After running 'newaliases' to build a fresh /etc/aliases.db, it works a treat.  I have the vanilla config back too, no special tricks needed.

Thanks, MJN, for working with me to resolve this.  It seems Postfix DOES work in Gutsy, after all!  :-)

---

### Post by ktindle on 2007-11-07
Oh, the reason for the funky DNS is: gws.uky.edu is a subdomain of funky machines, so they get a funky DNS config.  So they tell me.

---

### Post by MJN on 2007-11-07
What a relief... I'm so glad you're sorted. Really - that was starting to become rather surreal...

Cheers,

Mathew

---

