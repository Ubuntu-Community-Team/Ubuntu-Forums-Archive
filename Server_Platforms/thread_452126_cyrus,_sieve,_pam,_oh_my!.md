---
title: "cyrus, sieve, pam, oh my!"
date: 2007-05-23
forum: Server Platforms
---

### Post by zenkick on 2007-05-23
I've used this tutorial on Ubuntu a few times:

[http://openmailadmin.ossdl.de/wiki/howto/Postfix-SASL-Cyrus-MySQL-Amavis-Postgrey-SpamAssassin-ClamAV-Squirrelmail-Mailman-Mailgraph-OMA](http://openmailadmin.ossdl.de/wiki/howto/Postfix-SASL-Cyrus-MySQL-Amavis-Postgrey-SpamAssassin-ClamAV-Squirrelmail-Mailman-Mailgraph-OMA)

However, this is the first time that I'm attempting to use sieve to manage filters.

My authentication is fine via imtest, and I'm able to manage email via IMAP, send with postfix, authentication works with everything (except sieve) without an issue:

# imtest -u cyrus -a cyrus localhost
S: * OK zane Cyrus IMAP4 v2.2.13-Debian-2.2.13-10ubuntu2 server ready
C: C01 CAPABILITY
S: * CAPABILITY IMAP4 IMAP4rev1 ACL QUOTA LITERAL+ MAILBOX-REFERRALS NAMESPACE UIDPLUS ID NO_ATOMIC_RENAME UNSELECT CHILDREN MULTIAPPEND BINARY SORT THREAD=ORDEREDSUBJECT THREAD=REFERENCES ANNOTATEMORE IDLE STARTTLS
S: C01 OK Completed
Please enter your password: 
C: L01 LOGIN cyrus {9}
S: + go ahead
C: <omitted>
S: L01 OK User logged in
Authenticated.
Security strength factor: 0
[/INDENT]

My /etc/pam.d/sieve is a symlink to /etc/pam.d/imap, so it should be using the same auth:

# ls -l sieve imap 
-rw------- 1 root root 768 2007-05-21 17:06 imap
lrwxrwxrwx 1 root root   4 2007-05-23 00:24 sieve -> imap

I can reach timsieved locally:
# telnet localhost 2000
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
"IMPLEMENTATION" "Cyrus timsieved v2.2.13-Debian-2.2.13-10ubuntu2"
"SIEVE" "fileinto reject envelope vacation imapflags notify subaddress relational comparator-i;ascii-numeric regex"
"STARTTLS"
OK

But, sieveshell and sivtest do not work as expected:

# sivtest -u cyrus -a cyrus localhost
root@zane:/etc/pam.d# sivtest -u cyrus -a cyrus localhost
S: "IMPLEMENTATION" "Cyrus timsieved v2.2.13-Debian-2.2.13-10ubuntu2"
S: "SIEVE" "fileinto reject envelope vacation imapflags notify subaddress relational comparator-i;ascii-numeric regex"
S: "STARTTLS"
S: OK
Authentication failed. generic failure
Security strength factor: 0
C: LOGOUT
OK "Logout Complete"
Connection closed.

# sieveshell -u cyrus -a cyrus localhost
connecting to localhost
unable to connect to server at /usr/bin/sieveshell line 179.
Anyone have any ideas? I'm at my wits-end.

-dave

---

