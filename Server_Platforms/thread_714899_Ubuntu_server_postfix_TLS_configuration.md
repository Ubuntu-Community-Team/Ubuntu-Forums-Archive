---
title: "Ubuntu server postfix TLS configuration"
date: 2008-03-04
forum: Server Platforms
---

### Post by dqsis on 2008-03-04
Dear Ubuntu users, 

Recently I installed an Ubuntu7.04 server (with Apache, MySQL, php).
The last days I am trying to install a **mail server** in order to use the php mail() function and to create email accounts [email]user@server.myserver.com[/email]. 

I followed (almost blindly) the manual given here:
[http://howtoforge.com/perfect_setup_ubuntu704](http://howtoforge.com/perfect_setup_ubuntu704)
installing postfix, bind9, TLS and so on...

At the end, this is how my postfix/main.cf file looks like:
```

myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no

myhostname = server.myserver.com
mydestination = server.myserver.com, localhost.localdomain, localhost
mynetworks = 127.0.0.0/8

relayhost =

#mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all

home_mailbox = Maildir/

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

```

Next I tried:
```

sudo telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 server.myserver.com ESMTP Postfix (Ubuntu)
ehlo localhost
250-server.myserver.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

mail from: user@server.myserver.com
250 2.1.0 Ok
rcpt to: user@server.myserver.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
Test
.
250 2.0.0 Ok: queued as 23FE08685FC
quit
221 2.0.0 Bye

```
and everything works fine! I can read the email at my ~/Maildir and I can download it using Evolution mail. 

[COLOR="Red"]HOWEVER,[/COLOR] when I try (with telnet) to send an email to a **non-local account** (user@gmail.com) I get [COLOR="Red"]NO[/COLOR] warnings but the mail [COLOR="Red"]NEVER[/COLOR] arrives. 
When I try to do the same with Evince, I get:
*Please enter the SMTP password for user on host [NUMERIC IP]*
and when I give the user's password, the warning comes:
[COLOR="Red"]Unable to authenticate to SMTP server.
Bad authentication response from server.[/COLOR]

Additionally, when I try to send an email from gmail to myserver, nothing arrives. 

Any help please? :(

---

### Post by zazuge on 2008-03-04
I think your problem is  a little complicated.
honestly I think you should try more easy smtp servers like smtp.mail.yahoo.fr
because smtp.gmail.com require STARTTLS
but if youa re stuborn then take a look at this one :
[http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html](http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html)

hope you can solve your problem fater than I did.

---

### Post by bmathis on 2008-03-04
If all you need to do is setup a simple mail server, then howtoforge is way to much. try using this tutorial which will get you up and going in less than an hour.

[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")

---

### Post by dqsis on 2008-03-05
Hello there, 

I ALSO tried the manual under 'Ubuntu Community Documentation' that you mentioned. 
I still can't get it to work though. 

Any more suggestions? Can something be wrong with my postfix configuration files?

Isn't the SMTP password the for user the smtpd pass phrase?

Thanks :(

---

### Post by dqsis on 2008-03-05
Some extra information:

Hello there, 

I opened the /var/log/mail.log file and this is what I get (last lines) when I try to send an email to the address dk [AT] dqdev [DOT] net:
```

Mar  5 12:16:41 server postfix/smtp[8443]: connect to mail.dqdev.net[69.72.212.86]: No route to host (port 25)
Mar  5 12:16:41 server postfix/smtp[8443]: 674268685FC: to=<dk [AT] dqdev [DOT] net>, relay=none, delay=20, delays=17/0.01/3/0, dsn=4.4.1, status=deferred (connect to mail.dqdev.net[69.72.212.86]: No route to host)

```

What can the warning [COLOR="Red"]No route to host[/COLOR] mean?

Additionally, when I check the file mail.warn I get:
```

Mar  5 12:16:07 server postfix/smtpd[8438]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled

```

Any ideas?  :confused:
Thanks

---

### Post by zazuge on 2008-03-06
I don't know what you are trying to do
but the log messages are clear the first error is that postfix can't find the domain that the mail is intended for .
if the main.conf you posted is all the text is , then you need
if you have a DNS and perhaps a MX record then you need a
relay_domains = somedistantdomains
if you don't have a domain name then you need
relay_host = somedistanthost
so that if postfix don't know whow to deliver to it relay it instead

for the second message it seem that postfix try to find user account in a directory service (NIS in this case) thought I didn't see it in your main.conf ,could be it you didn't show it completly?

---

### Post by dqsis on 2008-03-07
> I don't know what you are trying to do
I have a domain name and a server. 
On this server I host a company's website.
PHP, MySQL, Apache all work fine. 
Now what I would like to do, it to install a **mail server** (I am not sure about the terminology) so that I can have [email]user@company.com[/email] accounts that can **send and receive emails** to and from everywhere. 
This is why I installed postfix.

> If the main.conf you posted is all the text there is
Yes, that's all of it! 

> if you have a DNS and perhaps a MX record
I am pretty sure I have DNS but I do **not** think I have an MX record. Could you tell me what to do to find if I really have the above and how to get an MX record?

> relay_domains = somedistantdomains
What exactly goes for 'somedistantdomains'? Can you give an example? Should I manually give all the distant domains where I want to send emails to?

> postfix try to find user account in a directory service (NIS in this case)
It seems that this is not what I want. I don't want to send emails to user accounts locally, but f.e. to [email]someone@gmail.com[/email]

Any more ideas zazuge or anyone?
Thanks for the help so far...

---

