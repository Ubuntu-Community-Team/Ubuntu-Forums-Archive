---
title: "Where is Maildir"
date: 2007-10-29
forum: Server Platforms
---

### Post by satimis on 2007-10-29
Hi folks,


Ubuntu 7.04 server amd64
Postfix 2.3.8


This is a newly built server.  I can't locate the Maildir after sending mail.


Steps performed as follows;

$ hostname```

ubuntu

```

$ hostname -f```

ubuntu.mydomain.com

```

$ cat /etc/postfix/main.cf | grep mailbox_command```

mailbox_command = 

```

$ cat /etc/postfix/main.cf | grep home_mailbox```

home_mailbox = Maildir/

```

$ cat /etc/postfix/main.cf | grep mydestination```

mydestination = ubuntu.mydomain.com, localhost.mydomain.com, localhost.localdomain, localhost

```

$ cat /etc/postfix/main.cf | grep inet_interfaces```

inet_interfaces = all

```

$ cat /etc/postfix/main.cf | grep inet_protocols```

inet_protocols = all

```

$ cat /etc/postfix/main.cf | grep mynetworks```

mynetworks = 127.0.0.0/8, 192.168.1.0/24"
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

```


ping both ubuntu.mydomain.com/mydomain.com works.

On browser type both ubuntu.mydomain.com/mydomain.com displaying Apache2 default page.


$ telnet mail.mydomain.com 25```

Trying 64.202.165.92...
telnet: Unable to connect to remote host: Connection timed out

```


$ telnet ubuntu.mydomain.com 25```

Trying 127.0.1.1...
Connected to ubuntu.mydomain.com.
Escape character is '^]'.
220 ubuntu.mydomain.com ESMTP Postfix (Ubuntu)
ehlo mydomain.com
250-ubuntu.mydomain.com
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
mail from: root@mydomain.com
250 2.1.0 Ok
rcpt to: fmaster@mydomain.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>

Subject: My first mail for my domain

Hi

Are you there?

Admin
.
250 2.0.0 Ok: queued as 85354DF0168
quit
221 2.0.0 Bye
Connection closed by foreign host.

```


$ su - fmaster
Password: 

fmaster@ubuntu:~$ ls -al```

total 24
drwxr-xr-x 2 fmaster fmaster 4096 2007-10-28 20:16 .
drwxr-xr-x 5 root    root    4096 2007-10-28 09:57 ..
-rw------- 1 fmaster fmaster  112 2007-10-29 01:40 .bash_history
-rw-r--r-- 1 fmaster fmaster  220 2007-10-28 09:57 .bash_logout

```
Where is the Maildir ???


Do I need changing hostname as "mydomain.com"?  If YES, please advice;

1) Apart from /etc/hosts and /etc/postifx/main.cf what other files I have to change as well ?

2) After changes made what command shall I run to activate the changes rather than rebooting the server ?


TIA


B.R.
satimis

---

### Post by MJN on 2007-10-29
The Maildir hierarchy/store is more the responsibility of your IMAP server - which one are you using?

You could kickstart it in the right direction by creating ~/Maildir/ and then it'll likely create the cur/new/tmp sub-directories for you.

Mathew

P.S. Don't post just snippets of config files as chances are we'll need the info you omitted. Besides which all that copy-and-pasting and code wrapping must take ages!

---

### Post by satimis on 2007-10-29
HI Mathew,


Thanks for your advice.

I'm now following;
PostfixBasicSetupHowto
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

to continue my test.


Previously I was following another document to build this Ubuntu 7.04 LAMP server amd64 as Host OS running on VMWare server.  

I'm a little bid confused on server name.  Which name will be more appropriate Ubuntu OR Mydomain?  I need to change it making it workable as there are other servers to be added later on this Virtual Machine.  I have only one domain.  Please shed me some light.

I'm running Fluxbox, a light-weight desktop manager, having not many items available on the desktop menu.


> **MJN said:**
> The Maildir hierarchy/store is more the responsibility of your IMAP server - which one are you using?

Sorry I don't follow please explain in more detail.  Thanks.


> 
You could kickstart it in the right direction by creating ~/Maildir/ and then it'll likely create the cur/new/tmp sub-directories for you.

Whether you meant, Login as fmaster and then run;

$ mkdir ~/Maildir

to create a temporary directory?

Would the mail be saved on this directory automatically?


> 
P.S. Don't post just snippets of config files as chances are we'll need the info you omitted. Besides which all that copy-and-pasting and code wrapping must take ages!
OK

$ cat /etc/postfix/main.cf```

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
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ubuntu.mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ubuntu.mydomain.com, localhost.mydomain.com, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8, 192.168.1.0/24"
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
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
home_mailbox = Maildir/

```

satimis

---

### Post by MJN on 2007-10-29
Your server name is fine (I am assuming you've used the domain 'mydomain.com' here purely to hide your real domain?)

For the Maildir side of things, it is merely a format for storing mail on a system. Your mail folders and messages obviously need to be stored somewhere an you've told Postfix that you'll be storing them in the users directory, within the 'Maildir' directory.

I don't use Courier however having had a quick glance at the guide you're following the configuration is a little thin on the ground hence I am assuming it works pretty much out of the box.

Courier, which you'll be using to actually access your mail once delivered/stored (using IMAP or POP) will looking inside ~/Maildir/ for your mail. It will create various files in there for its own use along with some directories (cur/new/tmp) to store current/new/temporary messages in.

What does your Postfix log say when you send it a mail?

Mathew

P.S. You also need to add 'mydomain.com' to your mydestination directive and remove the " from mynetworks.

---

### Post by satimis on 2007-10-30
Hi Mathew,


I found many doc on Internet and don't know which of them will the right one for me to follow;


What I need is to setup a virtual mail box with following function;

1) Create A/C for new users

2) Simultaneously corresponding Maildir for each user will be created automatically

3) Each Maildir has following subdirectories;
inbox
draft
sentbox
trash

4) User can move/delete/create/send mails

5) Create password for the users.  Password can be changed by users themselves later.
etc.


Would following doc be suitable for me to follow?
PostfixVirtualMailBoxClamSmtpHowto
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)


> 
What does your Postfix log say when you send it a mail?

$ tail /var/log/mail.log ```

Oct 29 18:25:33 ubuntu postfix/smtpd[5984]: disconnect from 59-112-86-131.dynamic.hinet.net[59.112
.86.131]
Oct 29 18:28:53 ubuntu postfix/anvil[5987]: statistics: max connection rate 1/60s for (smtp:59.112
.86.131) at Oct 29 18:25:32
Oct 29 18:28:53 ubuntu postfix/anvil[5987]: statistics: max connection count 1 for (smtp:59.112.86
.131) at Oct 29 18:25:32
Oct 29 18:28:53 ubuntu postfix/anvil[5987]: statistics: max cache size 1 at Oct 29 18:25:32
Oct 29 21:47:29 ubuntu authdaemond: stopping authdaemond children
Oct 29 21:47:29 ubuntu postfix/master[4893]: terminating on signal 15
Oct 29 23:16:57 ubuntu authdaemond: modules="authpam", daemons=5
Oct 29 23:16:57 ubuntu authdaemond: Installing libauthpam
Oct 29 23:16:57 ubuntu authdaemond: Installation complete: authpam
Oct 29 23:17:00 ubuntu postfix/master[4907]: daemon started -- version 2.3.8, configuration /etc/postfix

```


$ cat /var/log/mail.log  | grep err```

Oct 28 03:48:33 ubuntu postfix/smtpd[5406]: NOQUEUE: reject: RCPT from 59-112-84-6.dynamic.hinet.n
et[59.112.84.6]: 451 4.3.5 Server configuration error; from=<michael78694@MyMainServer.com> to=<ca
ndy59839@yahoo.com.tw> proto=SMTP helo=<www.MyMainServer.com>
Oct 28 09:17:57 ubuntu postfix/smtpd[5727]: NOQUEUE: reject: RCPT from localhost.localdomain[127.0
.0.1]: 451 4.3.5 Server configuration error; from=<root@localhost> to=<satimis@localhsot> proto=ES
MTP helo=<localhost>
Oct 28 09:21:07 ubuntu postfix/smtpd[5727]: NOQUEUE: reject: RCPT from localhost.localdomain[127.0
.0.1]: 451 4.3.5 Server configuration error; from=<root@localhost> to=<satimis@localhost> proto=ES
MTP helo=<localhost>
Oct 28 09:26:14 ubuntu postfix/smtpd[5743]: NOQUEUE: reject: RCPT from localhost.localdomain[127.0
.0.1]: 451 4.3.5 Server configuration error; from=<root@localhost> to=<fmaster@localhost> proto=ES
MTP helo=<localhost>
Oct 28 09:51:18 ubuntu postfix/smtpd[5793]: NOQUEUE: reject: RCPT from localhost.localdomain[127.0
.0.1]: 451 4.3.5 Server configuration error; from=<root@localhost> to=<fmaster@localhost> proto=ES
MTP helo=<localhost>
Oct 28 09:59:27 ubuntu postfix/smtpd[5839]: NOQUEUE: reject: RCPT from localhost.localdomain[127.0
.0.1]: 451 4.3.5 Server configuration error; from=<root@localhost> to=<fmaster@localhost> proto=ES
MTP helo=<localhost>
Oct 28 18:12:49 ubuntu postfix/smtpd[5396]: NOQUEUE: reject: RCPT from unknown[124.64.62.52]: 451 
4.3.5 Server configuration error; from=<d121726@nate.com> to=<rypxtnzjbvmo45@hanmail.net> proto=SM
TP helo=<7dwu84g9bj05gw3>

```

Firewall has problem on sending mail.  I have to stop it.


Others noted with thanks


B.R.
satimis

---

### Post by MJN on 2007-10-30
We need to see the log of when you send your server a message (using the manual method you used at the beginning of the thread).

Mathew

P.S. Stop grepping for things you think might be important - I know you mean well but it misses out what we need to see - copy-and-paste chunks verbatim as we need to see the context of what's happening! Presumably those log entries from the 28th are from before you fixed your restrictions directive?

---

