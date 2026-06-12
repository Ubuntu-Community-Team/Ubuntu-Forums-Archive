---
title: "Postfix won't receive external email"
date: 2008-06-27
forum: Server Platforms
---

### Post by fred!head on 2008-06-27
Hi,

Running Hardy Heron, Postfix, Dovecot, have SMTP AUTH working so that I can send email from my Outlook to the mail server and then out to email addressess not on the mail server. I also can on the mail server, using Virtualmin and the Postfix module, send email from one domain to another. Same with telnet from my computer.

What I can't get working is email sent to a domain on my server. Postfix won't accept any email yet does not appear to have any failure notices in the log files.

Here's postconf -n output:

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
mail_spool_directory = /home/mail
mailbox_command = procmail -a $EXTENSION
mailbox_size_limit = 0
mydestination = www.redwrangler.com, localhost.redwrangler.com,localhost
myorigin = /etc/mailname
recipient_delimiter = +
relayhost =
smtp_sasl_security_options = noanonymous
smtp_tls_note_starttls_offer = yes
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,rejec      t_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = private/auth-client
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 4
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
virtual_alias_maps = hash:/etc/postfix/virtual

```


Here's the master.cf file, if that's useful:

```

10025      inet  n       -       -       -       -       smtpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
	-o smtp_fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

```


In the mail.err file I get these errors:

```
Jun 27 04:55:35 www postfix/smtpd[26701]: fatal: no debugger_command variable set up
Jun 27 04:56:35 www postfix/qmgr[26794]: fatal: no debugger_command variable set up

```


And in the syslog file I get this:

```
Jun 27 04:57:37 www postfix/master[26791]: warning: process /usr/lib/postfix/qmgr pid 26799 exit status 1
Jun 27 04:57:37 www postfix/master[26791]: warning: /usr/lib/postfix/qmgr: bad command startup -- throttling

```


As noted, I can relay email fine from my Outlook through this mail server to email addresses not located on my mail server. However, when people hit reply and send email back to a domain on my mail server, the mail server does not collect the email and does not appear to throw of any explicit bounce messages in any log files or to the person who sent me email.

Also I'm a newbie but I'm willing to dig in and learn.

Thanks for any help!

---

### Post by MJN on 2008-06-28
Something doesn't quite add up. You're using Postfix yet the mail server listed as responsible for redwrangler.com is using Exim:

```
$ host redwrangler.com
redwrangler.com has address 74.50.20.27
redwrangler.com mail is handled by 0 redwrangler.com.

$ telnet redwrangler.com 25
Trying 74.50.20.27...
Connected to redwrangler.com.
Escape character is '^]'.
220-camilla.lunarservers.com ESMTP Exim 4.69 #1 Sat, 28 Jun 2008 02:20:31 -0700
220-We do not authorize the use of this system to transport unsolicited,
220 and/or bulk e-mail.
quit
221 camilla.lunarservers.com closing connection
Connection closed by foreign host.

```You need to fix your DNS to point to you as mail isn't reaching your machine, hence the lack of logs.

(I would also explicitly list redwrangler.com as a domain in your mydestination directive)

Mathew

---

### Post by fred!head on 2008-06-28
Sorry to not have explained that detail. I'm in the process of moving servers. I got the Postfix/Dovecot server working fine this Monday "as is" with the DNS for that particular domain pointing to one server while I set up the new server. The new server has/had a DNS record and a virtual host set up through Virtualmin for that particular domain on the new server. The mail server worked just fine in that environment for two days until something changed on the server. I can't figure out what changed on the server and, as I said, the only negative impact is that suddenly I'm unable to get mail to the virtual host domains setup in Virtualmin.

If you want to telnet, try mail.redhorsecommunications.com with the custom port number.

I also added redwrangler.com to the mydestination directive. In looking through the Postfix SMTP AUTH documentation, I also set the smtpd_sasl_local_domain = $myhostname. It had been blank before.

Finally, there is another oddity, perhaps related perhaps not because I did not do this test after the Postfix/Dovecot server was working fine early this week. When I telnet and relay email I get a 554 message, I believe, that says I can't relay through a telnet session. So one question I have is how to test if SMTP AUTH is working: any ideas how to confirm that is not somehow the problem preventing mail from being collected by the server? I assume SMTP AUTH works because I can relay email through Outlook to the mail server and out again using some sort of password.

Thanks again for any assistance!

---

### Post by MJN on 2008-06-28
You've completely lost me.

Give me an e-mail address that's not receiving mail and we'll take it from there.

A test as per your instruction appears to work fine:

```
$ telnet mail.redhorsecommunications.com 10025
Trying 75.127.97.70...
Connected to mail.redhorsecommunications.com.
Escape character is '^]'.
220 www.redwrangler.com ESMTP Postfix (Ubuntu)
ehlo mail.newtonnet.co.uk
250-www.redwrangler.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: mailme-1@newtonnet.co.uk
250 2.1.0 Ok
rcpt to: postmaster@redwrangler.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
Test
.
250 2.0.0 Ok: queued as BE5FBA11B
quit
221 2.0.0 Bye
Connection closed by foreign host.
```Mathew

---

### Post by fred!head on 2008-06-28
Try sending to [email]tim@redhorsecommunications.com[/email], thanks!

---

### Post by MJN on 2008-06-28
Again, no problem:

```
$ telnet mail.redhorsecommunications.com 10025
Trying 75.127.97.70...
Connected to mail.redhorsecommunications.com.
Escape character is '^]'.
220 www.redwrangler.com ESMTP Postfix (Ubuntu)
ehlo mail.newtonnet.co.uk
250-www.redwrangler.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: mailme-1@newtonnet.co.uk
250 2.1.0 Ok
rcpt to: tim@redhorsecommunications.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
Test
.
250 2.0.0 Ok: queued as 4B630A11B
quit
221 2.0.0 Bye
Connection closed by foreign host.
```Mathew

---

### Post by fred!head on 2008-06-28
Exactly: when you connect to the mail server and send email to a local domain configured for that mail server it works fine. If you go to GMail and email to the same address, however, your email will not be accepted by the mail server. Your email will bounce. That is the problem I need to solve.

---

### Post by MJN on 2008-06-29
[duplicate post deleted]

---

### Post by MJN on 2008-06-29
I'm confused as to what setup you've got here.

Your instance of Postfix running on port 10025 works fine, but no MTA is going to connect to it - they will all connect to the process running on port 25 which is not configured correctly.

Given you do not have a port 25 instance listed in master.cf it's not clear what you've done and why.

If the port 10025 instance is a result of testing, you are restarting Postfix each time to ensure all configuration is reloaded?

Explain what the port 10025 instance is for, and the lack of a transport on port 25 then we can take it from there.

Mathew

---

### Post by fred!head on 2008-06-29
Matthew, you win the prize! Unfortunately there's no cash or travel attached to the prize... 8-)

As you note, the problem was that I left off the first smtp line in the master.cf file:

```

smtp      inet  n       -       -       -       -       smtpd

```

I had left off port 25 thinking I did not need it because my internet service provider, and a few others in the US, routinely block access to this port. When I put this line back in to the master.cf file, Postfix was/is able to receive email to all the virtual domains I set up with Virtualmin.

So thank you for pointing this out!

---

### Post by MJN on 2008-06-29
Oh... some prize...

Oh well, it's working so that'll do I guess!

Mathew

---

