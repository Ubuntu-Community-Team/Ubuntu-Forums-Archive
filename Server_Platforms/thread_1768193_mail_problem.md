---
title: "mail problem"
date: 2011-05-26
forum: Server Platforms
---

### Post by tapi0n on 2011-05-26
I'm setting up a mail server with postfix and dovecot. But I can't seem to get any mail.

Now when running netcat I get this.

```
~# nc mx.sub.domain.tld 25
220 mx.sub.domain.tld ESMTP Postfix (Debian/GNU)
HELO test.sub.domain.tld
250 mx.sub.domain.tld
MAIL FROM:<user@othersub.domain.tld>
250 2.1.0 Ok
RCPT TO: <user1@sub.domain.tld>
250 2.1.5 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
From User <user@othersub.domain.tld>        
To: User One <user1@sub.domain.tld>
Subject: Test
Date: Thu, 26 Mar 2010 21:05:23 -0200
 
Dit is een test.

.   
250 2.0.0 Ok: queued as 5F3022B0C61C
QUIT
221 2.0.0 Bye

```So I'm assuming there's nothing wrong with my postfix configuration.

I'm using dovecot 2 as LMTP server. This is what is in */etc/dovecot/dovecot.conf *(only posting where I made changes).
```

# Protocols we want to be serving: imap imaps pop3 pop3s managesieve
# If you only want to use dovecot-auth, you can set this to "none".
protocols = imap imaps
...
mail_location = maildir:/var/vmail
...
auth default {
   ...
    passdb passwd-file {
    # File contains a list of usernames, one per line
    args = /etc/dovecot/passwddov
   }
   ...
passdb pam {
   ...
   # passwd-like file with specified location
   # </usr/share/doc/dovecot-common/wiki/AuthDatabase.PasswdFile.txt>
   userdb passwd-file {
   # [username_format=<format>] <Path for passwd-file>
   args = /etc/dovecot/passwddov
  }
   ...

}

```*ls -l /var/vmail *gives this.

```
drwxr-xr-x 2 root root 4096 May 26 22:10 user1

```So my permission is set correctly right?

But still I just don't receive emails.

This is what shows up in my mail.log:

```
postfix/virtual[1569]: warning: perhaps you need to create the maildirs in advance
May 26 22:15:36 gil postfix/virtual[1569]: AD48B2B0C624: to=<user1@sub.domain.tld>, relay=virtual, delay=0.01, delays=0.01/0/0/0, dsn=4.2.0, status=deferred (maildir delivery failed: create maildir file /var/vmail/user1/tmp/1306440936.P1569.gil: Permission denied)

```And this is what I get from dovecot.log:

```
2011-05-26 22:25:35 auth(default): Info: client in: AUTH    1    PLAIN    service=imap    secured    lip=xxx.xxx.xxx.xxx    rip=xxx.xxx.xxx.xxx    lport=993    rport=4996resp=AHVzZXIxQGdpbC52bGFuNzcuYmUAYWJlZWdpbGxucnN1dg==
2011-05-26 22:25:35 auth(default): Info: passwd-file(user1@sub.domain.tld,xxx.xxx.xxx.xxx): lookup: user=user1@sub.domain.tld file=/etc/dovecot/passwddov
2011-05-26 22:25:35 auth(default): Info: client out: OK    1    user=user1@sub.domain.tld
2011-05-26 22:25:35 auth(default): Info: master in: REQUEST    1    1651    1
2011-05-26 22:25:35 auth(default): Info: passwd(user1@sub.domain.tld,xxx.xxx.xxx.xxx): lookup
2011-05-26 22:25:35 auth(default): Info: passwd(user1@sub.domain.tld,xxx.xxx.xxx.xxx): unknown user
2011-05-26 22:25:35 auth(default): Info: passwd-file(user1@sub.domain.tld,xxx.xxx.xxx.xxx): lookup: user=user1@sub.domain.tld file=/etc/dovecot/passwddov
2011-05-26 22:25:35 auth(default): Info: master out: USER    1    user1@sub.domain.tld    uid=5000    gid=5000    home=/var/vmail/user1    mail=maildir:/var/vmail/user1
2011-05-26 22:25:35 imap-login: Info: Login: user=<user1@sub.domain.tld>, method=PLAIN, rip=xxx.xxx.xxx.xxx, lip=xxx.xxx.xxx.xxx, TLS
2011-05-26 22:25:35 IMAP(user1@sub.domain.tld): Error: mkdir(/var/vmail/user1/cur) failed: Permission denied (euid=5000(<unknown>) egid=5000(<unknown>) missing +w perm: /var/vmail/user1)
2011-05-26 22:25:35 IMAP(user1@sub.domain.tld): Info: Connection closed bytes=20/400

```I just keep going trough it and trough it. Checking the internet for possible solutions. Had a friend take a look at it. It's driving me crazy.

Anyone who's got an idea of what I'm doing wrong? 

Cheers

---

