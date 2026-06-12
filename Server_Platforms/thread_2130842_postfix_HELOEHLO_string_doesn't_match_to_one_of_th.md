---
title: "postfix HELO/EHLO string doesn't match to one of the names in the rDNS"
date: 2013-03-30
forum: Server Platforms
---

### Post by pythonimus on 2013-03-30
Hello,

my postfix mail server got listed by v4bl.org.
So I used their tool to show whats wrong in my configuration.
Everything is just fine except:

[TABLE]
[TR]
[TH="colspan: 3, align: left"]FCrDNS Test[/TH]
[/TR]
[TR="class: clrTestOk"]
[TD]rDNS for IP x.x.x.x[/TD]
[TD]
[LIST]
[*]dom.tld 
[/LIST]
[/TD]
[TD]OK[/TD]
[/TR]
[TR="class: clrTestOk"]
[TD]IP Addresses for dom.tld[/TD]
[TD]
[LIST]
[*]x.x.x.x 
[/LIST]
[/TD]
[TD]OK[/TD]
[/TR]
[TR="class: clrTestOk"]
[TD="colspan: 2"]At least one IP address of the DNS lookup for dom.tld matches the original IP[/TD]
[TD]OK[/TD]
[/TR]
[/TABLE]
    [TABLE]
[TR]
[TH="colspan: 3, align: left"]HELO/EHLO Tests[/TH]
[/TR]
[TR="class: clrTestOk"]
[TD="colspan: 2"]The HELO/EHLO string "mail.dom.tld" is a valid host- or domainname[/TD]
[TD]OK[/TD]
[/TR]
[TR="class: clrTestOk"]
[TD]IP Addresses for "mail.dom.tld"[/TD]
[TD]
[LIST]
[*]x.x.x.x 
[/LIST]
[/TD]
[TD]OK[/TD]
[/TR]
[TR="class: clrTestOk"]
[TD="colspan: 2"]At least one IP address of the DNS lookup for "mail.dom.tld" matches to the connecting IP x.x.x.x[/TD]
[TD]OK[/TD]
[/TR]
[TR="class: clrTestFailed"]
[TD="colspan: 2"]The HELO/EHLO string "mail.dom.tld" doesn't match to one of the names in the rDNS from connecting IP[/TD]
[TD]Failed[/TD]
[/TR]
[/TABLE]

I dont know what to do here...
My rDNS is mail.dom.tld
MX is mail.dom.tld.
Config for postfix is smtpd_banner = $myhostname ESMTP $mail_name
$myhostname = mail.dom.tld
FQDN is mail.dom.tld too.

Connecting with Telnet:
220 mail.dom.tld ESMTP Postfix
EHLO mail.dom.tld
250-mail.dom.tld
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

Does anyone know what to do?

Tnak you!

---

### Post by pythonimus on 2013-04-01
Here the correct configuration for postfix:
myhostname = mail.xyz.ab (MX)
mydomain = xyz.ab
myorigin = $mydomain

---

