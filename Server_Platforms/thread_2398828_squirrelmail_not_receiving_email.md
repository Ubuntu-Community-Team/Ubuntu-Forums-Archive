---
title: "squirrelmail not receiving email"
date: 2018-08-17
forum: Server Platforms
---

### Post by abdrakhman on 2018-08-17
I have this kind of issue.
Here is my dovecot configuration
```

mail_location = mbox:~/mail:INBOX=/var/mail/%u
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
ssl = no
userdb {
  driver = passwd
}



```

Here is my postfix configuration file.

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


# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = ip-172-31-44-78.us-west-2.compute.internal
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, ktlwik.ga, mail.ktlwik.ga, localhost
relayhost = 
mynetworks = 0.0.0.0/0
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maidir/



```

But I found out suspicious  thing in log
```

Aug 17 20:39:25 ip-172-31-44-78 postfix/smtpd[22845]: connect from mail-ua1-f46.google.com[209.85.222.46]
Aug 17 20:39:25 ip-172-31-44-78 postfix/smtpd[22845]: E72863F7F7: client=mail-ua1-f46.google.com[209.85.222.46]
Aug 17 20:39:26 ip-172-31-44-78 postfix/cleanup[22849]: E72863F7F7: message-id=<CA+CYVA0Rtr6xNuk3kMy1VwZXK35s7aHjpikmPYkpQ6AgE-=fuw@mail.gmail.com>
Aug 17 20:39:26 ip-172-31-44-78 postfix/qmgr[22689]: E72863F7F7: from=<ismail.abdrakhman@gmail.com>, size=2665, nrcpt=1 (queue active)
Aug 17 20:39:26 ip-172-31-44-78 postfix/local[22850]: E72863F7F7: to=<abdrakhman@ktlwik.ga>, relay=local, delay=0.21, delays=0.2/0/0/0, dsn=2.0.0, status=sent (delivered to maildir)
Aug 17 20:39:26 ip-172-31-44-78 postfix/qmgr[22689]: E72863F7F7: removed
Aug 17 20:39:26 ip-172-31-44-78 postfix/smtpd[22845]: disconnect from mail-ua1-f46.google.com[209.85.222.46] ehlo=2 starttls=1 mail=1 rcpt=1 data=1 quit=1 commands=7



``` 
After I can't figure out what to do

---

### Post by darkod on 2018-08-18
What is the problem exactly? That log example at first glance looks standard when message is received. It says delivered to maildir and then removed (from queue). That message should be received correctly.
About squirrelmail, thats webmail program and has nothing to do with receiving as far as I know.
The problem is receiving or accessing by webmail? Can you see the messages by imap or pop3?

---

### Post by abdrakhman on 2018-08-18
What data you need to observe problem?

---

### Post by SeijiSensei on 2018-08-18
Mail services are divided between Mail Transport Agents like Postfix and sendmail, and Mail Delivery Agents which route the mail after it arrives.  You need both for a Squirrelmail setup.  The standard MDA these days is dovecot, available from the repositories, and the standard mailbox protocol is IMAP.  After it has been installed, you can run the configuration Perl script (config.pl as I recall) to point to the IMAP server address.

---

### Post by abdrakhman on 2018-08-18
Where is config.pl?

---

### Post by abdrakhman on 2018-08-18
And how to check is  IMAP And MTA working?

---

### Post by darkod on 2018-08-18
Try to connect with any email client to a mailbox on that server and check if the email messages sent to it are there. That's the first thing you need to do to verify mails are received. How do you know they are not otherwise?

---

### Post by abdrakhman on 2018-08-18
Also google gave me this
```

[TABLE="class: m_-1748165719020875843email-wrapper"]
[TR]
[TD="align: left"][FONT=monospace]DNS Error: 7549989 DNS type 'mx' lookup of [ktlwik.ga]("http://ktlwik.ga/") responded with code NOERROR 7549989 DNS type 'aaaa' lookup of [mail.ktlwik.ga]("http://mail.ktlwik.ga/"). responded with code NXDOMAIN 7549989 DNS type 'a' lookup of [mail.ktlwik.ga]("http://mail.ktlwik.ga/"). responded with code NXDOMAIN[/FONT][/TD]
[/TR]
[/TABLE]


```

---

### Post by darkod on 2018-08-18
Well, if that's your domain it seems like you have a MX record pointing to mail.ktlwik.ga but there is no A record for mail.ktlwik.ga. You need to create that A record too which will point to the mail server public IP.

Here are the dig results:
```
darko@nuc6:~$ dig mx ktlwik.ga

; <<>> DiG 9.10.3-P4-Ubuntu <<>> mx ktlwik.ga
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38004
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 5

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;ktlwik.ga.   IN	MX

;; ANSWER SECTION:
ktlwik.ga.  14440	IN	MX	10 mail.ktlwik.ga.

;; AUTHORITY SECTION:
ktlwik.ga.  300	IN	NS	ns04.freenom.com.
ktlwik.ga.  300	IN	NS	ns01.freenom.com.
ktlwik.ga.  300	IN	NS	ns02.freenom.com.
ktlwik.ga.  300	IN	NS	ns03.freenom.com.

;; ADDITIONAL SECTION:
ns01.freenom.com.	2548	IN	A	54.77.56.63
ns02.freenom.com.	2548	IN	A	54.171.233.154
ns03.freenom.com.	2548	IN	A	104.155.27.112
ns04.freenom.com.	2548	IN	A	104.155.29.241

;; Query time: 226 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Sat Aug 18 23:16:44 CEST 2018
;; MSG SIZE  rcvd: 210

darko@nuc6:~$ dig mail.ktlwik.ga

; <<>> DiG 9.10.3-P4-Ubuntu <<>> mail.ktlwik.ga
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 3827
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;mail.ktlwik.ga.   IN	A

;; AUTHORITY SECTION:
ktlwik.ga.  300	IN	SOA	ns01.freenom.com. soa.freenom.com. 1534538640 10800 3600 604800 3600

;; Query time: 146 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Sat Aug 18 23:17:14 CEST 2018
;; MSG SIZE  rcvd: 99
```

---

### Post by abdrakhman on 2018-08-19
Am I did correctly, I have added A record.

---

### Post by abdrakhman on 2018-08-19
[HR][/HR]Also I want to ask how INBOX folder looks like.
This is folders of one user.
```


drwxrwxrwt 3 abdrakhman abdrakhman 4096 Aug 19 15:07 ./
drwxr-xr-x 4 abdrakhman abdrakhman 4096 Aug 19 15:04 ../
drwx------ 9 abdrakhman abdrakhman 4096 Aug 17 20:37 .imap/
-rw------- 1 abdrakhman abdrakhman   54 Aug 17 20:33 .subscriptions
-rw------- 1 abdrakhman abdrakhman    0 Aug 17 20:19 Drafts
-rw------- 1 abdrakhman abdrakhman    0 Aug 17 20:33 INBOX.Drafts
-rw------- 1 abdrakhman abdrakhman 1463 Aug 19 15:07 INBOX.Sent
-rw------- 1 abdrakhman abdrakhman    0 Aug 17 20:33 INBOX.Trash
-rw------- 1 abdrakhman abdrakhman    0 Aug 17 20:19 Sent
-rw------- 1 abdrakhman abdrakhman    0 Aug 17 20:19 Trash

```

---

### Post by darkod on 2018-08-19
I would say the folder structure is secondary. It is what it is for a Maildir setup.

Do emails arrive correctly now? That's the important part, not the folder structure on the email server. That part is transparent to the users anyway.

---

### Post by abdrakhman on 2018-08-19
How can I check it?

---

### Post by SeijiSensei on 2018-08-20
First, if you have this in dovecot.conf

```
mail_location = mbox:~/mail:INBOX=/var/mail/%u
```

you're using mbox format, not Maildir.  Each user's inbox is stored in /var/mail/username.  Their folders are stored in /home/username/mail/.  In mbox format, each folder is a single file with an empty line delimiting the messages.

One very useful tool for diagnosing mail is the command-line email client called alpine (formerly pine).  It can connect to the mail folders using IMAP or directly through the directory structure if you're running it on the server.

The file tree you listed above with names like INBOX.Trash was generated by Squirrelmail, so it apparently knows where the mail is stored.

Sorry, it's not config.pl, but conf.pl.  It is in the config directory of SquirrelMail.  You have read the SM documentation, right? In particular 
look at [http://squirrelmail.org/docs/admin/admin-5.html](http://squirrelmail.org/docs/admin/admin-5.html).

---

### Post by abdrakhman on 2018-08-21
I think I figured out i don't have empty inbox in SQMail. The main question "Do mail folders must be equal on dovecot and postfix"

---

### Post by abdrakhman on 2018-08-21
I checked for receiving and sending. They work correctly. I figured out everything except one. How Squirrelmail takes email?

---

