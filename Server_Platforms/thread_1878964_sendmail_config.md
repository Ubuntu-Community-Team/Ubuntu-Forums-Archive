---
title: "sendmail config"
date: 2011-11-10
forum: Server Platforms
---

### Post by robbrandt on 2011-11-10
Using Ubuntu Linux 10.04.2

I have a server recently set up and it needs to be able to send out automatic notifications for various things.  I had no intention of installing a general purpose mail server such as postfix or exim on this server.  Most notifications will actually go out via smtp to another host (usually google apps for mail), but there are certain instances where a simple send from the server is most appropriate.

I have installed all the sendmail packages, and it *looks* like it's working, but no mail is received at the account (external to the server) where the mail is sent to.

My mail.log shows the following on recent attempts:

Nov 10 11:56:21 32262-1-742983 sendmail[22132]: pAAJuLuB022132: from=www-data, size=2506, class=0, nrcpts=0, msgid=<201111101956.pAAJuLuB022132@sub.domain.org>, relay=www-data@localhost

That was send was attempted via a simple mail() function in php.

Any suggestions?

---

### Post by SeijiSensei on 2011-11-10
Is that the only line in the logs for this message? Try running 
grep pAAJuLuB022132 /var/log/mail.log
to see all the entries.

Does your ISP block outbound port 25?

Do you have DNS correctly configured?

---

### Post by robbrandt on 2011-11-10
Yes, that is the only entry for pAAJuLuB022132.

I can telnet into port 25.

As far as I know, dns is configured correctly.  Any particular item?  The MX entry points elsewhere for sure.

---

