---
title: "Email Forwarding"
date: 2014-03-19
forum: Server Platforms
---

### Post by wolfgentleman on 2014-03-19
I have searched to no avail. I cannot seem to figure out how to add a forward to my current setup. I used [this]("https://library.linode.com/email/postfix/postfix2.9.6-dovecot2.0.19-mysql") to get it up and running, and a combo of posts to add SpamAssasin+Procmail. I have 2 domains for email, one that is actually hosted on my server and the other which is supposed to be a catch-all-and-forward.
Here is my configs:
**POSTFIX**
[TABLE]
[TR]
[TD]**main.cf**[/TD]
[/TR]
[TR]
[TD]```

## MISCsmtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
recipient_delimiter = +
mailbox_size_limit = 0


## AUTH & SECURITY
smtpd_tls_cert_file=/etc/ssl/certs/dovecot.pem
smtpd_tls_key_file=/etc/ssl/private/dovecot.pem
smtpd_use_tls=yes
smtpd_tls_auth_only = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions =
   permit_sasl_authenticated,
   permit_mynetworks,
   reject_unauth_destination


## IP ADDRESSES & DOMAIN NAMES
myhostname = mail.twprogrammers.com
myorigin = /etc/mailname
mydestination = localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
inet_interfaces = all


## VIRTUAL USERS, MAILBOXES, ALIASES, ECT.


alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_transport = procmail
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf

```[/TD]
[/TR]
[TR]
[TD]**master.cf**[/TD]
[/TR]
[TR]
[TD]```

smtp  inet  n   -   -   -   -   smtpdpickupfifo  n   -   -   60  1   pickup
cleanup   unix  n   -   -   -   0   cleanup
qmgr  fifo  n   -   n   300 1   qmgr
tlsmgrunix  -   -   -   1000?   1   tlsmgr
rewrite   unix  -   -   -   -   -   trivial-rewrite
bounceunix  -   -   -   -   0   bounce
defer unix  -   -   -   -   0   bounce
trace unix  -   -   -   -   0   bounce
verifyunix  -   -   -   -   1   verify
flush unix  n   -   -   1000?   0   flush
proxymap  unix  -   -   n   -   -   proxymap
proxywrite unix -   -   n   -   1   proxymap
smtp  unix  -   -   -   -   -   smtp
relay unix  -   -   -   -   -   smtp
showq unix  n   -   -   -   -   showq
error unix  -   -   -   -   -   error
retry unix  -   -   -   -   -   error
discard   unix  -   -   -   -   -   discard
local unix  -   n   n   -   -   local
virtual   unix  -   n   n   -   -   virtual
lmtp  unix  -   -   -   -   -   lmtp
anvil unix  -   -   -   -   1   anvil
scacheunix  -   -   -   -   1   scache
procmail  unix  -   n   n   -   -   pipe
  flags=RO user=vmail argv=/usr/bin/procmail -t -m USER=${user}
  EXTENSION=${extension} RECIPIENT=${recipient} /etc/procmail/main.rc
uucp  unix  -   n   n   -   -   pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmailunix  -   n   n   -   -   pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp unix  -   n   n   -   -   pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix-nn-2pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -   n   n   -   -   pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

```[/TD]
[/TR]
[TR]
[TD]**mysql-virtual-alias-maps.cf**[/TD]
[/TR]
[TR]
[TD]```

user = mailuser
password = REMOVED
hosts = 127.0.0.1
dbname = mailserver
query = SELECT IFNULL(a.destination,u.email) AS destination FROM virtual_aliases a INNER JOIN virtual_users u ON a.destination=u.email WHERE a.source='%s' OR u.email='%s'

```[/TD]
[/TR]
[TR]
[TD]**mysql-virtual-mailbox-maps.cf**[/TD]
[/TR]
[TR]
[TD]```

user = mailuser
password = REMOVED
hosts = 127.0.0.1
dbname = mailserver
query = SELECT 1 FROM virtual_users WHERE email='%s'

```[/TD]
[/TR]
[TR]
[TD]**mysql-virtual-mailbox-domains.cf**[/TD]
[/TR]
[TR]
[TD]```

user = mailuser
password = REMOVED
hosts = 127.0.0.1
dbname = mailserver
query = SELECT 1 FROM virtual_domains WHERE name='%s'

```[/TD]
[/TR]
[/TABLE]
**MYSQL**
[TABLE]
[TR]
[TD="align: center"]**virtual_aliases**[/TD]
[/TR]
[TR]
[TD][TABLE="class: grid, align: center"]
[TR]
[TD="align: center"]**id**[/TD]
[TD="align: center"]**domain_id**[/TD]
[TD="align: center"]**source**[/TD]
[TD="align: center"]**destination**[/TD]
[/TR]
[TR]
[TD="align: center"]1[/TD]
[TD="align: center"]1[/TD]
[TD="align: center"]REMOVED@twprogrammers.com[/TD]
[TD="align: center"]REMOVED@twprogrammers.com[/TD]
[/TR]
[TR]
[TD="align: center"]2[/TD]
[TD="align: center"]1[/TD]
[TD="align: center"]REMOVED@twprogrammers.com[/TD]
[TD="align: center"]REMOVED@twprogrammers.com[/TD]
[/TR]
[TR]
[TD="align: center"]3[/TD]
[TD="align: center"]1[/TD]
[TD="align: center"]REMOVED@twprogrammers.com[/TD]
[TD="align: center"]REMOVED@twprogrammers.com[/TD]
[/TR]
[TR]
[TD="align: center"]100[/TD]
[TD="align: center"]1[/TD]
[TD="align: center"]@twprogrammers.com[/TD]
[TD="align: center"]REMOVED@twprogrammers.com[/TD]
[/TR]
[TR]
[TD="align: center"]101[/TD]
[TD="align: center"]3[/TD]
[TD="align: center"]@hawkladybeadery.com[/TD]
[TD="align: center"]REMOVED@satx.rr.com[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD="align: center"]**virtual_domains**[/TD]
[/TR]
[TR]
[TD][TABLE="class: grid, align: center"]
[TR]
[TD="align: center"]**id**[/TD]
[TD="align: center"]**name**[/TD]
[/TR]
[TR]
[TD="align: center"]1[/TD]
[TD="align: center"]twprogrammers.com[/TD]
[/TR]
[TR]
[TD="align: center"]2[/TD]
[TD="align: center"]mail.twprogrammers.com[/TD]
[/TR]
[TR]
[TD="align: center"]3[/TD]
[TD="align: center"]hawkladybeadery.com[/TD]
[/TR]
[TR]
[TD="align: center"]4[/TD]
[TD="align: center"]mail.hawkladybeadery.com[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD="align: center"]**virtual_users**[/TD]
[/TR]
[TR]
[TD][TABLE="class: grid, align: center"]
[TR]
[TD="align: center"]**id**[/TD]
[TD="align: center"]**domain_id**[/TD]
[TD="align: center"]**password**[/TD]
[TD="align: center"]**email**[/TD]
[/TR]
[TR]
[TD="align: center"]1[/TD]
[TD="align: center"]1[/TD]
[TD="align: center"]HASHEDPASS[/TD]
[TD="align: center"]REMOVED@twprogrammers.com[/TD]
[/TR]
[TR]
[TD="align: center"]2[/TD]
[TD="align: center"]1[/TD]
[TD="align: center"]HASHEDPASS[/TD]
[TD="align: center"]REMOVED@twprogrammers.com[/TD]
[/TR]
[TR]
[TD="align: center"]3[/TD]
[TD="align: center"]1[/TD]
[TD="align: center"]HASHEDPASS[/TD]
[TD="align: center"]REMOVED@twprogrammers.com[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
What am I doing wrong? How can I fix it so that all mail to hawkladybeadry.com is forwarded to the satx.rr.com address?


EDIT:
When I send a message to say -- [email]test@hawkladybeadery.com[/email] it bounces back with this:
> 
This Message was undeliverable due to the following reason: 
 
Each of the following recipients was rejected by a remote mail server. 
The reasons given by the server are included to help you determine why 
each recipient was rejected. 
 
    Recipient: <[test@hawkladybeadery.com]("http://webmail.satx.rr.com/do/mail/message/mailto?to=test%40hawkladybeadery.com")> 
    Reason:    5.1.1 <[test@hawkladybeadery.com]("http://webmail.satx.rr.com/do/mail/message/mailto?to=test%40hawkladybeadery.com")>: Recipient address rejected: 
User unknown in virtual mailbox table 
 
 
Please reply to <[Postmaster@email.rr.com]("http://webmail.satx.rr.com/do/mail/message/mailto?to=Postmaster%40email.rr.com")> 
if you feel this message to be in error. 
[COLOR=#000000][FONT=arial]Open Attachment: [[]    ]("http://webmail.satx.rr.com/do/mail/message/download?msgId=INBOXDELIM11548&part=2&l=en-US&v=twc_theme")[/FONT][/COLOR]
[TABLE]
[TR]
[TD="class: mainPanelReadTxt_12"]--- Forwarded Message ---[/TD]
[/TR]
[TR]
[TD="class: mainPanelReadTxt_12"]Date:[/TD]
[TD="class: mainPanelReadTxt_12"][LEFT][{DATE}][/LEFT]
[/TD]
[/TR]
[TR]
[TD="class: mainPanelReadTxt_12"]From:[/TD]
[TD="class: mainPanelReadTxt_12"]{FROM}[/TD]
[/TR]
[TR]
[TD="class: mainPanelReadTxt_12"]To:[/TD]
[TD="class: mainPanelReadTxt_12"]test@hawkladybeadery.com [/TD]
[/TR]
[TR]
[/TR]
[TR]
[TD="class: mainPanelReadTxt_12"]Subject:[/TD]
[TD="class: mainPanelReadTxt_12"]{SUBJECT}[/TD]
[/TR]
[/TABLE]
[COLOR=#000000][FONT=arial]{MESSAGE}[/FONT][/COLOR]


---

### Post by CharlesA on 2014-03-19
Are you sure your server is allowed to send mail to that satx.rr.com address? I have mine set up to forward mail from one of my domains to another domain but that domain is on the same mail server..

Everything looks right to me, though.

---

### Post by wolfgentleman on 2014-03-19
> **CharlesA said:**
> Are you sure your server is allowed to send mail to that satx.rr.com address?
Oh, I am sorry I forgot to add the bounce message! Adding it now.

---

### Post by CharlesA on 2014-03-19
Try changing the alias to send it to an address on the same server and see if you get the same error back.

I'm guessing the catchall isn't working properly.

---

### Post by wolfgentleman on 2014-03-23
> **CharlesA said:**
> Try changing the alias to send it to an address on the same server and see if you get the same error back.

I'm guessing the catchall isn't working properly.

Ok, I just did and it went through... So... do I need to add the email to virtual_users and satx.rr.com to virtual_domains? Will try that and report tomorrow.

---

### Post by CharlesA on 2014-03-23
The only issue I see with doing that is the mail server could accept mail for satx.rr.com, whether that is a real issue or not, I do not know.

---

### Post by wolfgentleman on 2014-03-24
> **CharlesA said:**
> The only issue I see with doing that is the mail server could accept mail for satx.rr.com, whether that is a real issue or not, I do not know.

Well... it delivered to the void... Tried poking around in /var/mail/vhosts to see if procmail delivered it like that, but no go. Also looked @ mail logs in /var/log and it shows no sign of it being received.

---

### Post by wolfgentleman on 2014-05-10
bump

---

### Post by SeijiSensei on 2014-05-13
Where are the procmailrc files in this setup?  With virtual users, what's the equivalent of $HOME/.procmailrc?

The reason I ask is that you can do forwardings there as well.  One solution to your problem might be to create a recipe in the system-wide /etc/procmailrc like this:
```

:0
* ^TO.*hawkladybeardery
! removed@satx.rr.com

```

---

### Post by wolfgentleman on 2014-05-14
> **SeijiSensei said:**
> Where are the procmailrc files in this setup?  With virtual users, what's the equivalent of $HOME/.procmailrc?
I have a folder structure in /etc/procmail/ that looks like this:
/etc/procmail/main.rc
/etc/procmail/spam.rc
/etc/procmail/filters/$USER/pre.rc
/etc/procmail/filters/$USER/post.rc

In main.rc it makes the declarations of $USERNAME and $DELIVER then INCLUDERC=/etc/procmail/filters/$USER/pre.rc then INCLUDERC=/etc/procmail/spam.rc then INCLUDERC=/etc/procmail/filters/$USER/post.rc then delivers everything else to the inbox with $DELIVER -u $USERNAME
Some of the above may be inaccurate as I am not looking at the rc file at this very moment, however I think I got it.

> **SeijiSensei said:**
> 
The reason I ask is that you can do forwardings there as well.  One solution to your problem might be to create a recipe in the system-wide /etc/procmailrc like this:
```

:0
* ^TO.*hawkladybeardery
! removed@satx.rr.com

```

I will try this in a few minutes and update my post.

Update:
Using the above it delivered it to the 'void'. Not sure what is going on there... nothing shows in the logs, not even postfix's. The MX records seem to be in proper order. I guess now I just wait for it to cough up at me with a post master error. :-/

---

### Post by SeijiSensei on 2014-05-15
You need to see whether you can actually deliver to that address:
```

$ host -t mx satx.rr.com
satx.rr.com mail is handled by 10 cdptpa-pub-iedge-vip.email.rr.com.
$ telnet cdptpa-pub-iedge-vip.email.rr.com 25
Trying 107.14.166.70...

```
It times out from here.  How about from your server?

---

### Post by wolfgentleman on 2014-05-15
> **SeijiSensei said:**
> You need to see whether you can actually deliver to that address
Well, whether it means anything or not, I can send messages from my mail server to an satx.rr.com address.
> **SeijiSensei said:**
> 
```

$ host -t mx satx.rr.com
satx.rr.com mail is handled by 10 cdptpa-pub-iedge-vip.email.rr.com.
$ telnet cdptpa-pub-iedge-vip.email.rr.com 25
Trying 107.14.166.70...

```
It times out from here.  How about from your server?
Hmm... It doesn't timeout, it gives this:
```
$ host -t mx satx.rr.com
satx.rr.com mail is handled by 10 cdptpa-pub-iedge-vip.email.rr.com.
$ telnet cdptpa-pub-iedge-vip.email.rr.com
Trying 107.14.166.70...
telnet: Unable to connect to remote host: No route to host
```

Let me try forwarding it to a different host, like GMail.

Update:
I tried GMail and got this:
```
$host -t mx gmail.comgmail.com mail is handled by 30 alt3.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 40 alt4.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 5 gmail-smtp-in.l.google.com.
gmail.com mail is handled by 20 alt2.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 10 alt1.gmail-smtp-in.l.google.com.
$ telnet gmail-smtp-in.l.google.com
Trying 2607:f8b0:4003:c02::1b...
Trying 173.194.64.26...
telnet: Unable to connect to remote host: Connection timed out
```

However, this is irrelevant as it seems that the problem was not in procmail's recipe or the satx.rr.com mail server, but a problem of postfix's SQL table. When I tested the recipe last night nothing happened. However when I went to send a new test message from the same email as last time I noticed 2 automated messages from the postmaster. When I sent the test message this time it went through! Granted it took half an hour, but at least it is running now. Either way it's working now. Thank you!

---

