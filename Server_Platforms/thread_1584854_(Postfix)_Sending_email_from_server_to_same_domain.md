---
title: "(Postfix) Sending email from server to same domain doesn't work"
date: 2010-09-29
forum: Server Platforms
---

### Post by Total Legend on 2010-09-29
As the title says: Sending email from server to same domain doesn't work.

I'll explain some more.

Say I have an Ubuntu Server (10.4). On it I am hosting a web site. The domain for that website is, for example: [http://sz.com](http://sz.com)

I have installed LAMP and PostFix on the server, configured it as such to allow PHP Forms to send out emails. This works great.

While the emails going out works fine, it ONLY works if the domain of the email is not the same as the domain the web server is using. 

I can send an email to: [email]anyone@anydomain.com[/email], but I cannot send an email to: [email]anyone@sz.com[/email].

My assumption is that Postfix is intercepting emails going out that match what the server is using, thinking it's the actual mail server for incoming mails. I use an external service for email with my domain name, but I also need my server to be able to send emails to the same domain name.

It's confusing me and I haven't been able to find a solution through my hours of searching. Anyone have any tips?

Thanks!

---

