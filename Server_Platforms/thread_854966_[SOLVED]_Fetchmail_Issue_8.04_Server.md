---
title: "[SOLVED] Fetchmail Issue 8.04 Server"
date: 2008-07-10
forum: Server Platforms
---

### Post by sil3nt on 2008-07-10
Hi Guys,
        This may be a no brainer, I have fetchmail its connecting to my externally hosted mail server and pulling down my email, it gets to reading the first message and fails?

Here is the error output :

```
fetchmail: POP3> LIST 1
fetchmail: POP3< +OK 1 2641
fetchmail: POP3> RETR 1
fetchmail: POP3< +OK 2641 octets follow.
reading message user@example.com@example.com:1 of 965 (2641 octets)
Trying to connect to 127.0.0.1/25...connection failed.
fetchmail: connection to localhost:smtp [127.0.0.1/25] failed: Connection refused.
fetchmail: SMTP connect to localhost failed
fetchmail: POP3> QUIT
fetchmail: POP3< I can't hear you=20
fetchmail: SMTP transaction error while fetching from user@example.com@mail.example.com and delivering to SMTP host localhost
fetchmail: 6.3.8 querying mail.example.com (protocol POP3) at Thu 10 Jul 2008 12:49:21 WST: poll completed
fetchmail: Query status=10 (SMTP)
fetchmail: normal termination, status 10
```

It's mentioning SMTP, but I have no idea why it referencing SMTP for incoming mail? or is this a SMTP issue on the remote server?

Any help would be appreciated

---

### Post by sil3nt on 2008-07-14
Fixed it myself, I didn't realize you needed the mail server installed on my end to dump the mail.

Installed Postfix using the Internet and Smart host option, works just fine now ;)

---

### Post by Iain71 on 2008-09-02
I am having the same problem so please could you possibly explain how you solved it in more detail.  I was thinking of using Dovecot on my server but if you have a solution that works it would be a great help.  Thanks.  Iain

---

