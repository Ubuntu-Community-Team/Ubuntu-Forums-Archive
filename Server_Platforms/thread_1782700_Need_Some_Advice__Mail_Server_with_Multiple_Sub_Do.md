---
title: "Need Some Advice : Mail Server with Multiple Sub Domains"
date: 2011-06-14
forum: Server Platforms
---

### Post by pamuditha99 on 2011-06-14
Hi, 
[U][B]
I want to configure a single mail server to send and receive mail from multiple sub domains of my domain.[/B][/U]

I've already installed Postfix/Dovecot and it is perfectly working for mydomain.com. And also installed roundcube for Web Mail.

Can I further customize this setup to process mail to sub domains? ex- [EMAIL="someone@subdomain1.mydomain.com"]someone@subdomain1.mydomain.com[/EMAIL], [EMAIL="someone@subdomain2.mydomain.com"]someone@subdomain2.mydomain.com[/EMAIL], [EMAIL="someone2@subdomain1.mydomain.com"]someone2@subdomain1.mydomain.com[/EMAIL] (someone@subdomain1.mydomain.com and [EMAIL="someonet@subdomain2.mydomain.com"]someone@subdomain2.mydomain.com[/EMAIL] are 2 separate users. they should be able to log on to web interface separately)

Currently i use system account names as email user names. (ex - [EMAIL="systemusername@mydomain.com"]systemusername@mydomain.com[/EMAIL]). The only MX record in my domain DNS pointed to current server (mailhost.mydomain.com).

I read about postfix virtual domains. but couldnt figure out how to use it to achive my target.


Can you please give me some solution for this.

I do not need configuration details. Just explain me the way to do it. I can do the rest my self.

Thanks in advance.

---

### Post by pamuditha99 on 2011-06-14
sry. didnt mentioned my ubuntu version.

it's ubuntu server 10.40 LTS

---

