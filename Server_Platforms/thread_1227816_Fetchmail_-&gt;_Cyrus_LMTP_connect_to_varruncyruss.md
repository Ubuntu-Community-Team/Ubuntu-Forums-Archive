---
title: "Fetchmail -&gt; Cyrus:: LMTP connect to /var/run/cyrus/socket/lmtp failed"
date: 2009-07-31
forum: Server Platforms
---

### Post by lightnb on 2009-07-31
I'm pulling my hair out trying to get fetchmail to put my mail messages into Cyrus.

When fetchmail runs, the log shows:

```
Jul 31 05:08:35 IMAP fetchmail[2042]: Server CommonName mismatch: localhost != mail.mydomain.com 
Jul 31 05:08:35 IMAP fetchmail[2042]: Server certificate verification error: self signed certificate 
Jul 31 05:08:35 IMAP fetchmail[2042]: Invalid command. 
Jul 31 05:08:36 IMAP fetchmail[2042]: LMTP connect to /var/run/cyrus/socket/lmtp failed 
Jul 31 05:08:36 IMAP fetchmail[2042]: SMTP transaction error while fetching from user@mydomain.com@mail.mydomain.com and delivering to SMTP host /var/run/cyrus/socket/lmtp 

```

I have a feeling that the "LMTP connect to failed" message is the problem, but it doesn't elaborate on why the connection failed.

.fetchmailrc:
```
set syslog;
set daemon 90;

poll "mail.mydomain.com"
with protocol pop3
user "user@mydomain.com" there with password "123456" is "user" here
smtphost "/var/run/cyrus/socket/lmtp"

```

How can I figure out what's going wrong?

---

### Post by lightnb on 2009-08-01
No one knows how to get messages into Cyrus?

---

