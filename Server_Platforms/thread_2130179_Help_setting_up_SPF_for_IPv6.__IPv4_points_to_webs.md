---
title: "Help setting up SPF for IPv6.  IPv4 points to website, IPv6 points to home comp"
date: 2013-03-28
forum: Server Platforms
---

### Post by MechaMechanism on 2013-03-28
SOLVED

Using EXIM4 MTA and I have a web site at an IPv4 address at a hosting company that graciously donated for free and I have an IPv6 AAAA record pointing to my home computer.  I have SPF working for IPv4 but when I setup my SPF for IPv6 it don't work.  Gmail keeps saying softfail.  I have 2 domains, the IPv4 domain at universal-mechanism.org (@ 64.251.17.25) and the IPv6 domain at universal-mechanism.org (separate computer @ 2001:470:1f04:1a82::2).  I should note that EXIM4 is configured with the setting of Internet site and it works great.  This only has to do with getting SPF working with the IPv6 address.  Google needs to pass both the IPv4 address and the IPv6 address even though they point to separate servers.  I have included a screenshot of my DNS settings.

A
@ 64.251.17.25

CNAME
www @

MX
@ MX 10 homier.dyndns.org
@ MX 0 mxin.mxes.net

SPF
@ v=spf1 include:customer-spf.mxes.net ~all
@ v=spf1 mx mx:homier.dyndns.org include:homier.dyndns.org ~all

AAAA
@ 2001:470:1f04:1a82::2

---

### Post by sanderj on 2013-03-28
I don't know about SPF, but is your mail setup good?

1) universal-mechanism.org has no MX records pointing to your IPv6 address.
2) when I manually set up a SMTP session over IPv6, your system (thus?) refuses the mail.


```
sander@toverdoos:~$ mailsend -v  -smtp 2001:470:1f04:1a82::2 -from [email]testermaster@gmail.com[/email] -to [email]blablabla@universal-mechanism.org[/email] -sub testing
Connecting to 2001:470:1f04:1a82::2:25
libmsock: using getaddrinfo
 AF_INET6
 IPv6 address: 2001:470:1f04:1a82::2
 EINPROGRESS=115,EWOULDBLOCK=11
 connect(): socket=3,rc=-1, errno=115
 Try socket 3
[S] 220 saturn.hyperion.local ESMTP Exim 4.76 Thu, 28 Mar 2013 15:20:31 -0600
[C] EHLO localhost
[S] 250-saturn.hyperion.local Hello localhost [2001:blabla:eef:8637:e45b]
[S] 250-SIZE 52428800
[S] 250-PIPELINING
[S] 250-STARTTLS
[S] 250 HELP
[C] MAIL FROM: <testermaster@gmail.com>
[S] 250 OK
[C] RCPT TO: <blablabla@universal-mechanism.org>
[S] 550 relay not permitted
Error: RCPT TO: <blablabla@universal-mechanism.org> failed '550:relay not permitted'

[S] 250 Reset OK
Could not send mail
sander@toverdoos:~$
```


EDIT:

homier.dyndns.org. neither accepts mail for ...@universal-mechanism.org. Not good, I would say
HTH

---

