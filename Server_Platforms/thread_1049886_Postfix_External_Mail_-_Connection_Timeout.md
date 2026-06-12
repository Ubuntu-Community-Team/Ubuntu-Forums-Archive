---
title: "Postfix: External Mail - Connection Timeout"
date: 2009-01-25
forum: Server Platforms
---

### Post by qoar on 2009-01-25
Hello,

For the past three days I have been trying to allow my ubuntu server (ubuntu desktop but using server functions of apache, postfix, etc) to send email to external websites.

I AM able to: send/receive mail locally, receive mail from external websites
I AM NOT able to: send mail to external websites
My ISP does NOT block port 25
I do NOT have a firewall installed
I HAVE tried other alternatives also
I AM using a router, but the ports are accessible

When I do the telnet function (in the terminal) to another mail server, I am not getting a response...


The error logs are as follows:

931FB414161      750 Sun Jan 25 00:58:16  [email]www-data@mail.[mydomain].com[/email]
    (connect to g.mx.mail.yahoo.com[209.191.118.103]:25: Connection timed out)
                                         [to email address]@yahoo.com

Please, please help. I have not been able to find any solutions that work on these forums, google, or even on ubuntu's website.

Thank you very much!!

---

### Post by HermanAB on 2009-01-25
Check your DNS using 'dig'.  To successfully send mail, you MUST have an A, PTR and MX record.

Cheers,

Herman

---

### Post by qoar on 2009-01-25
I have ensured that my DNS has all the required records and it does.

But I still can not send emails...

Thanks!

---

### Post by HermanAB on 2009-01-25
You can send mail locally, so Postfix works.  If you cannot telnet to port 25 of another mail server (eg mine would be "telnet mail.aeronetworks.ca 25"), then your ISP is dropping the packets on the floor.

If the ISP is dropping the packets, but you can access the ISP mail server (telnet mail.yourisp.net 25), then define the ISP mail server as a Smart Host and relay outgoing mail through that.

Cheers,

Herman

---

