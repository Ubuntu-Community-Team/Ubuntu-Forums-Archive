---
title: "EHLO gives different internal and external responses"
date: 2008-07-24
forum: Server Platforms
---

### Post by grandcross on 2008-07-24
I'm trying to debug settings that prevent me from authenticating externally. So I login to my server and do an EHLO from my localhost. This is what I get:

# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 ****************.com ESMTP Postfix
EHLO test.domain.com
250-****************.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH NTLM LOGIN PLAIN DIGEST-MD5 CRAM-MD5
250-AUTH=NTLM LOGIN PLAIN DIGEST-MD5 CRAM-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
quit
221 2.0.0 Bye
Connection closed by foreign host.

Now, when I connect from a remote host, I get:
telnet ottawa.entertain-me.com 25
Trying ...
Connected to ****************.com.
Escape character is '^]'.
220 ESMTP
EHLO test.domain.com
250 OK
quit
221 Bye
Connection closed by foreign host.

Why are they different? Obviously, this is preventing me from authenticating.

TIA,
Dave

---

### Post by MJN on 2008-07-24
Different machines? e.g. incorrect port forwarding on your router, or incorrect DNS configuration?
 
For what it's worth, I get the first dialogue (as thankfully you omitted the munging[1]) and so this suggests an internal issue. Try connecting via the server's IP address to rule out any problems with DNS resolution, cached results or local hosts file entries.
 
Mathew
 
[1] I do wonder why you munged the other names anyway - if you're vulnerable to attack it's just a matter of time until a random bot find you. Omitting/changing names just makes it more difficult to diagnose your problem.

---

### Post by grandcross on 2008-07-24
Yes, a bot can find me, but there's no reason to make it easy for the idiots out there :)

So, I've narrowed down what the problem is. In fact, the external conversation isn't with my mail server at all. I'm being intercepted along the line.

Now, I'm currently in a hotel, so I'm assuming this is just a means of reducing spam, but it's still very disturbing on a number of levels. I'd rather they block the port than intercept it.

*** Shudder ***

---

### Post by MJN on 2008-07-24
Just add another instance of Postfix listening on a different port and configure your client to use it. Indeed, the so-called submission port of 587 is ideal.

Add the following to /etc/postfix/master.cf

```
submission inet n       -       -       -       -       smtpd
```Mathew

---

