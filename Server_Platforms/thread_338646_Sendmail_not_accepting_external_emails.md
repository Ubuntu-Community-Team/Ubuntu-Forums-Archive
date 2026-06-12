---
title: "Sendmail not accepting external emails"
date: 2007-01-14
forum: Server Platforms
---

### Post by Permafrost91 on 2007-01-14
I followed the [this]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html") tutorial on the Ubuntu Documentation Wiki to install an email server on Dapper. This is an old P3 machine that sits behind a Netgear router which, in turn, is hooked to a cable modem (not a fancy setup, but it suits my needs).

At any rate, the server hosts a website and I can send emails to the server using this website's contact page (which utilizes PHP's mail() function) and I can access those emails via my POP server.

However, emails send to users on my domain from outside our home-network don't seem to reach me. I don't have enough mail server experience to start tracking down whether these emails actually get to me or not or what the actual problems is so any help figuring out this problem would be appreciated. GMail bounces emails send to my domain back to me saying "TEMP_FAILURE: Could not initiate SMTP conversation with any hosts". The webserver can be accessed from the outside.

Thanks!

---

### Post by Jerry Wright on 2008-05-11
By default Sendmail only allows local delivery.  You need to edit the sendmail.mc file to make it work.

Open /etc/mail/sendmail.mc

Scroll down to DAEMON_OPTIONS(`Port=smtp,Addr=127.0.0.1, Name=MTA')dnl

It needs to read DAEMON_OPTIONS(`Port=smtp,Name=MTA')dnl

That 127.0.0.1 locks it into Local Only.

After that you need to run the following command:

make -C /etc/mail

Then restart Sendmail with

service sendmail restart

Hope this helps you and others...

--Jerry

---

