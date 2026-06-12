---
title: "Need help with postfix config."
date: 2008-06-30
forum: Server Platforms
---

### Post by lotsofish on 2008-06-30
I have a VPS server(SliceHost) running Hardy. At the office, I have a Windows 2003 server running an Exchange server for our mail. 

The exchange server is set up in the nameservers as mail.domain.com.
We host our website on the VPS as domain.com.

The problem I am having is I can't send emails from our VPS server to our email accounts for domain.com if I have the "mydomain" setting in main.cf set to domain.com. Postfix thinks that "user@domain.com" is local and tries to deliver it locally, instead of looking at the DNS records to send it to mail.domain.com.

If I change "mydomain" in main.cf to localhost, the main is delivered, but ends up in the spam bin.

I also tried sending the email to [email]user@mail.domain.com[/email] instead, but that didn't work either. I haven't tried adding a new email address called [email]user@mail.domain.com[/email] to users in Windows Server yet. It seems like that might work, but that doesn't seem like a great solution because I would have to add it to every user have in Exchange that would either receive mail from the website or forwarded through the VPS. I would rather use a different solution if I can.

Thanks for any ideas!

---

### Post by lotsofish on 2008-07-01
Bump?

---

### Post by windependence on 2008-07-02
mydomain should be set to domain.tld so there is someting else wrong here. Let me look at my setup and see how I have it working because all I do is use postfix for smtp and that is what you want to do as well.

-Tim

---

### Post by lotsofish on 2008-07-02
I agree, it should be domain.tld, but in my configuration it's not working. Mail is handled on a different server and this is set up with an MX record. However, if mydomain is changed to the domain.tld in the configuration, it thinks that the mail should be delivered locally and then of course it fails since the mail account is not set up locally.

SliceHost (the VPS) has their own DNS system that you can use in the manager, instead of installing a DNS server (like BIND) on your server. It's easier to use the manager to configure the DNS records, so that's what I did. I don't think this is the problem though. I think postfix is seeing that the mydomain is set to the same destination as the email address being delivered and it's trying to deliver it locally. If I 'dig' my domain, the MX record is listed correctly.

I don't have 'disable_dns_lookups = yes' specified in main.cf.

---

### Post by lotsofish on 2008-07-02
I found [this page]("http://www.nooblet.org/blog/2007/postfix-transport-maps-diverting-mail-traffic/") about setting up transport maps. I tried this and set it to:

domain.tld main.domain.tld:25

Still didn't work. Error log shows and error of "greeted me with my own hostname domain.tld"


Because of this message, I tried changing mydomain from domain.tld to [www.domain.tld](www.domain.tld) and this time I got the message, it didn't show up in the Junk folders like it had been doing with "localhost", so I think I figured it out. Probably not exactly perfect, but I think it will work.

:)

---

