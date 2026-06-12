---
title: "Dovecot won't recieve mail from external sources."
date: 2009-08-02
forum: Server Platforms
---

### Post by artheus on 2009-08-02
Hi!

I've got a problem with receiving mail to my mail at my own Ubuntu server using dovecot and postfix.

When I use the postfix smtp om my server and sending my mail to the address username@servername it works fine.. But when I send to the mail address [email]mail@mydomain.com[/email], which points to one of the users at my server, it won't work.

I've tried to set it up using some guides.. but no luck..

Here's the dovecot.conf

```

## Dovecot configuration file

protocols = imap imaps
log_timestamp = "%Y-%m-%d %H:%M:%S "
login_chroot = yes
login_user = dovecot
login_process_size = 256
login_greeting = Welcome to my IMAP server.
mail_location = mbox:~/mail:INBOX=/var/mail/%u
mail_privileged_group = mail

protocol imap {

}

protocol pop3 {

  pop3_uidl_format = %08Xu%08Xv

}

protocol managesieve {

  sieve=~/.dovecot.sieve

  sieve_storage=~/sieve
  
}

auth default {
  mechanisms = plain
  
  passdb pam {
  
  }

  userdb passwd {
  
  }
  
  user = root
  
}

dict {

}

plugin {

}


```

Well, I deleted all the commented areas.. And this is what is left..

Might be something missing.. or something is configured incorrectly?

I've opened all the required ports in the firewall, and on the router..

Cheers,
Artheus

---

### Post by fakrulalam on 2009-08-02
Hi,

It seems that your mail receiving problem is with SMTP service, not with Dovecot service. Dovecot only give the service of POP/IMAP. Please try to manually telnet to port 25 and try to send mail manually. Check what does the maillog says.

**Checking SMTP service manually**

telnet localhost 25
EHLO artheus
mail from:<username@localdomain.com>
rcpt to:<username@thedomain.com>
data
From:username@localdomain.com
To:username@thedomain.com
Subject: Test Mail

Test mail body.

.
quit

Now check the maillog. It will reflect if there is any thing wrong with SMTP configuration.

---

### Post by artheus on 2009-08-02
At first it told me to use "STARTTLS" before using the "mail from".. and when I do that It just closes the connection when I write "mail from: <mail@mydomain.com>"..

The port is 2525..

/Artheus

---

### Post by artheus on 2009-08-02
And one more thing.. It is possible to send mail to a eg. gmail account or hotmail account with the smtp server..
But is the smtp really the one who handles incoming mail too??

Cheers,
Artheus

---

### Post by fakrulalam on 2009-08-02
Hi,
It seems that you are having problem with your SMTP service. Do you configure postfix with STARTTLS? if you don't need TLS service, you can disable it from main.cf file & reload the postfix.

---

### Post by fakrulalam on 2009-08-02
"It is possible to send mail to a eg. gmail account or hotmail account with the smtp server"
--Yes definitely. If you have DNS entry configure correctly, you should be able to send are receive mail to any mail server.

"But is the smtp really the one who handles incoming mail too??"
--I am not clear about this thing. Could you please clarify it.

---

### Post by artheus on 2009-08-02
> "But is the smtp really the one who handles incoming mail too??"
--I am not clear about this thing. Could you please clarify it.
- Well I am asking if the SMTP server handles both incoming and outgoing mail?

Here's how I wrote the telnet thing :

```

220 hostname ESMTP Postfix (Ubuntu)
EHLO mail
250-hostname
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from:<a@b.com>
250 2.1.0 Ok
rcpt to:<mail@mydomain.com>
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
From:a@b.com
To:mail@mydomain.com
Subject: Test Mail

Test mail body

.
250 2.0.0 Ok: queued as 695B1120161

```

And this is the output in /var/log/mail.log

```

Aug  2 20:18:58 hostname postfix/smtpd[3439]: connect from localhost[127.0.0.1]
Aug  2 20:19:35 hostname postfix/smtpd[3439]: 695B1120161: client=localhost[127.0.0.1]
Aug  2 20:20:28 hostname postfix/cleanup[3442]: 695B1120161: message-id=<20090802181935.695B1120161@hostname>
Aug  2 20:20:28 hostname postfix/qmgr[3436]: 695B1120161: from=<a@b.com>, size=343, nrcpt=1 (queue active)
Aug  2 20:20:28 hostname postfix/smtp[3558]: 695B1120161: to=<mail@mydomain.com>, relay=smtprelay1.telia.com[81.228.9.101]:25, delay=73, delays=73/0/0.16$
Aug  2 20:20:28 hostname postfix/cleanup[3442]: 6305112016A: message-id=<20090802182028.6305112016A@hostname>
Aug  2 20:20:28 hostname postfix/bounce[3559]: 695B1120161: sender non-delivery notification: 6305112016A
Aug  2 20:20:28 hostname postfix/qmgr[3436]: 6305112016A: from=<>, size=2186, nrcpt=1 (queue active)
Aug  2 20:20:28 hostname postfix/qmgr[3436]: 695B1120161: removed
Aug  2 20:20:28 hostname postfix/smtp[3558]: 6305112016A: to=<a@b.com>, relay=smtprelay1.telia.com[81.228.9.101]:25, delay=0.21, delays=0.02/0/0.16/0.03, d$
Aug  2 20:20:28 hostname postfix/qmgr[3436]: 6305112016A: removed
Aug  2 20:20:33 hostname postfix/smtpd[3439]: disconnect from localhost[127.0.0.1]

```

---

### Post by artheus on 2009-08-02
And here's some output in the mail.info

```

Aug  2 20:18:33 hostname postfix/smtpd[3338]: connect from MyPC.local[198.0.0.89]
Aug  2 20:18:35 hostname postfix/smtpd[3338]: disconnect from MyPC.local[198.0.0.89]
Aug  2 20:18:39 hostname postfix/master[3332]: terminating on signal 15
Aug  2 20:18:39 hostname postfix/master[3434]: daemon started -- version 2.5.5, configuration /etc/postfix
Aug  2 20:18:41 hostname postfix/smtpd[3439]: connect from MyPC.local[198.0.0.89]
Aug  2 20:18:41 hostname postfix/smtpd[3439]: B192B120162: client=MyPC.local[198.0.0.89]
Aug  2 20:18:41 hostname postfix/cleanup[3442]: B192B120162: message-id=<4A75D872.10403@hotmail.com>
Aug  2 20:18:41 hostname postfix/smtpd[3439]: disconnect from MyPC.local[198.0.0.89]
Aug  2 20:18:41 hostname postfix/qmgr[3436]: B192B120162: from=<myusualmail@hotmail.com>, size=1068, nrcpt=1 (queue active)
Aug  2 20:18:42 hostname postfix/smtp[3443]: B192B120162: to=<myusualmail@hotmail.com>, relay=smtprelay1.telia.com[81.228.8.92]:25, delay=0.35, delays=0.04/0/0$
Aug  2 20:18:42 hostname postfix/qmgr[3436]: B192B120162: removed
Aug  2 20:18:58 hostname postfix/smtpd[3439]: connect from localhost[127.0.0.1]
Aug  2 20:19:35 hostname postfix/smtpd[3439]: 695B1120161: client=localhost[127.0.0.1]
Aug  2 20:20:28 hostname postfix/cleanup[3442]: 695B1120161: message-id=<20090802181935.695B1120161@hostname>
Aug  2 20:20:28 hostname postfix/qmgr[3436]: 695B1120161: from=<a@b.com>, size=343, nrcpt=1 (queue active)
Aug  2 20:20:28 hostname postfix/smtp[3558]: 695B1120161: to=<mail@mydomain.com>, relay=smtprelay1.telia.com[81.228.9.101]:25, delay=73, delays=73/0/0.16$
Aug  2 20:20:28 hostname postfix/cleanup[3442]: 6305112016A: message-id=<20090802182028.6305112016A@hostname>
Aug  2 20:20:28 hostname postfix/bounce[3559]: 695B1120161: sender non-delivery notification: 6305112016A
Aug  2 20:20:28 hostname postfix/qmgr[3436]: 6305112016A: from=<>, size=2186, nrcpt=1 (queue active)
Aug  2 20:20:28 hostname postfix/qmgr[3436]: 695B1120161: removed
Aug  2 20:20:28 hostname postfix/smtp[3558]: 6305112016A: to=<a@b.com>, relay=smtprelay1.telia.com[81.228.9.101]:25, delay=0.21, delays=0.02/0/0.16/0.03, d$
Aug  2 20:20:28 hostname postfix/qmgr[3436]: 6305112016A: removed
Aug  2 20:20:33 hostname postfix/smtpd[3439]: disconnect from localhost[127.0.0.1]
Aug  2 20:29:53 hostname postfix/smtpd[3606]: connect from Gilbert.local[198.0.0.89]
Aug  2 20:29:53 hostname postfix/smtpd[3606]: 81E5A120161: client=Gilbert.local[198.0.0.89]
Aug  2 20:29:53 hostname postfix/cleanup[3609]: 81E5A120161: message-id=<4A75DB11.3020900@mydomain.com>
Aug  2 20:29:53 hostname postfix/smtpd[3606]: disconnect from Gilbert.local[198.0.0.89]
Aug  2 20:29:53 hostname postfix/qmgr[3436]: 81E5A120161: from=<hostname@mydomain.com>, size=1076, nrcpt=1 (queue active)
Aug  2 20:29:53 hostname postfix/smtp[3610]: 81E5A120161: to=<hostname@mydomain.com>, relay=smtprelay1.telia.com[81.228.9.102]:25, delay=0.32, delays=0.03/$
Aug  2 20:29:53 hostname postfix/qmgr[3436]: 81E5A120161: removed

```

---

### Post by fakrulalam on 2009-08-02
Yes, SMTP handles both incoming & outgoing mail and deliver it to user inbox. POP/IMAP only fetch the mail from user inbox. Does mail is bouncing back to [email]a@b.com[/email]?

---

### Post by artheus on 2009-08-02
> Does mail is bouncing back to [email]a@b.com[/email]?

huh?

---

### Post by artheus on 2009-08-02
I think I understand now.. You ask if the mail I try to send, bounces back to the [email]a@b.com[/email]?

Well.. No it doesn't...

Cheers,
Artheus

---

### Post by artheus on 2009-08-02
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

myhostname = hostname
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = hostname, localhost.localdomain, localhost
relayhost = smtprelay.somedomain.com
mynetworks = 192.168.1.0/24 198.0.0.0/24 127.0.0.0/24 127.0.1.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 40960000
recipient_delimiter = +
inet_interfaces = all

myorigin = /etc/mailname
inet_protocols = ipv4

```

Here's the postfix main.cf.. Is there something here that should be configured?

---

### Post by artheus on 2009-08-02
Now I opened the port 25 in firewall, router and master.cf... It helped so much that I got a bounce on the mail I tried to send to my user at the server..

Here it is :

```

This is the Postfix program at host av7-1-sn3.vrr.skanova.net.

I'm sorry to have to inform you that the message returned
below could not be delivered to one or more destinations.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the message returned below.

			The Postfix program

<mail@mydomain.com>: host mydomain.com[81.233.202.3] said: 554 5.7.1
    <mail@mydomain.com>: Relay access denied (in reply to RCPT TO command)



Reporting-MTA: dns; av7-1-sn3.vrr.skanova.net
Arrival-Date: Sun,  2 Aug 2009 22:18:19 +0200 (CEST)

Final-Recipient: rfc822; mail@mydomain.com
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; host mydomain.com[81.233.202.3] said: 554 5.7.1
    <mail@mydomain.com>: Relay access denied (in reply to RCPT TO command)


```

I don't really understand what failed!?

/Artheus

---

### Post by artheus on 2009-08-02
fixed it all now.. By just changing the hostname to "mydomain.com" instead of hurricane.

Thanks for all the help I got on this!

Cheers,
Artheus

---

### Post by artheus on 2009-08-05
I knew it! The same day as I posted the first post here... I started getting spam to my mailaddress about Viagra and S**T... 
Hope someone else does not do that mistake!

---

