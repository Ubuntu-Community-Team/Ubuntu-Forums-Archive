---
title: "Domain Name?"
date: 2009-02-06
forum: Server Platforms
---

### Post by ooobooontooo on 2009-02-06
Hi,

I wanted to install a SMTP server on my box and I was reading some guides, like [http://www.howtoforge.com/perfect-server-ubuntu-8.10]("http://www.howtoforge.com/perfect-server-ubuntu-8.10") and [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/"). I was wondering when they tell me to enter things like my domain name or server1.example.com I can just put in my hostname right? Or do I actually need to get my own domain name...like a commercial one? I mean my hostname is my local domain name right? Thanks in advance.

---

### Post by hyper_ch on 2009-02-06
do you just want to send email and where to?

---

### Post by ooobooontooo on 2009-02-06
Yeah. I just wanted to send email to myself. But I want it to be automated, so I was thinking of installing a SMTP server.

---

### Post by hyper_ch on 2009-02-06
if you followed the howtoforge setup then you have postfix setup... all you need to do there is setting up postfix so that it relays outgoing email through a real authenticated mail server (e.g. through your ISP)

and shall the server also be accessible from outside?

---

### Post by ooobooontooo on 2009-02-06
No it doesn't need to be accessible from the outside...but what do I put for the domain and server1.example.com?  My hostname?

---

### Post by hyper_ch on 2009-02-07
you can just put anything in there but I'd suggest you use a dynamic domain given by no-ip.com or dyndns.org

---

### Post by ooobooontooo on 2009-02-07
Yeah, but I didn't want to involve any third parties. Thanks. I'll just put anything I want for domain.

---

### Post by myvbiz on 2009-02-09
> **hyper_ch said:**
> you can just put anything in there but I'd suggest you use a dynamic domain given by no-ip.com or dyndns.org

Hi. I'm totally new here and have very limited experience. I have installed postfix and want to use my server to send mail only. I'm not sure what I must enter for the "System mail name" I have my own IP address for my server. When I enter my domain name, that is hosted by a third party, and check the /var/log/mail.log file it looks like the mail was sent without any errors but i'm not receiving the mail.

Please help?

---

