---
title: "Email Server"
date: 2009-03-23
forum: Server Platforms
---

### Post by rohitthakral on 2009-03-23
Hi Guys,

I have a number of domains with email hosted on Google Apps & websites hosted on my VPS servers. Google has limits on its email service.

Is it possible to use postfix as another outgoing email server for the marketing emails and the replies are monitored using Google?

Thanks for your help.
Rohit

---

### Post by BkkBonanza on 2009-03-23
Sure, why not. Just use a suitable reply-to address on the outgoing emails. Then replies will return back to the address you have served by google. Just don't be sending unsolicited spam. You don't want to get your ip banned/blacklisted and have difficulties rising from that.

---

### Post by rohitthakral on 2009-03-24
Thanks BkkBonaza.

Can Sendmail default configuration do it. As I just want to send emails? Is there an SMTP connector on Sendmail?

---

### Post by HermanAB on 2009-03-24
The absolutely easiest way to set up a mail server that can do everything (including mailing lists) is to install Citadel.  It only takes about 20 minutes to run the Easy Install script.  They also have a ready to run virtual machine available for download, for the super lazy.

[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

Cheers,

Herman

---

### Post by rohitthakral on 2009-03-24
Thanks Herman, But I am not looking for a full fledged Mail Server but a simple solution to send emails out without using the primary mail server (Google Apps). The receiving of emails can be taken care by the primary server.

---

### Post by Bachstelze on 2009-03-24
> **rohitthakral said:**
> Can Sendmail default configuration do it. As I just want to send emails? Is there an SMTP connector on Sendmail?

sendmail can't do that by default, but it's fairly easy to configure it to. However, you'll run into another problem: authentication. Surely you don't want to allow anyone to send mail to anyone using your server, so you must set up some kind of authentication. If all the machines you want to use your mail server on are on the same LAN, it's easy (just have your mail server check whether the IP address of the machine that wants to send mail belongs to the LAN). If you want to use it on machines all over the world, however, it will be a bit more tricky...

---

### Post by Dr Small on 2009-03-24
> **HymnToLife said:**
> sendmail can't do that by default, but it's fairly easy to configure it to. However, you'll run into another problem: authentication. Surely you don't want to allow anyone to send mail to anyone using your server, so you must set up some kind of authentication. If all the machines you want to use your mail server on are on the same LAN, it's easy (just have your mail server check whether the IP address of the machine that wants to send mail belongs to the LAN). If you want to use it on machines all over the world, however, it will be a bit more tricky...
It's not that much more tricky; Just setup authentication with SASL, for Postfix.

---

### Post by rohitthakral on 2009-03-24
Authentication is not a big problem as the application which is going to send the newsletter will most of the time be sitting on the same server or only one IP Address.

Just to make myself clear. The setup will only be used as a secondary outgoing email server as the primary server will be Google Apps. Not many users other than the eMarketing app will be using it to send outgoing emails.

---

