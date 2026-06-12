---
title: "Mail and Web Server"
date: 2009-01-11
forum: Server Platforms
---

### Post by Tom_T on 2009-01-11
Currently I run a Windows 2003 server that manages the following:

1. Email (3 domains) Mercury32 with POP3, SMTP and IMAP, Anti Virus (ClamAV), AntiSpam (SpamHalter), content and transaction filtering.

2. Web Server. IIS, PHP, ASP (not to bothered about this) and MySQL.

3. DHCP Server

4. Proxy Server with whitelists, time and content control.


Now I'm looking to move to Ubuntu and try to configure the above using Linux apps.

I would like to use Ubuntu with a GUI desktop to make it easier to manage.

Has anyone got any suggestions, advice or links to good How To's ??

Or suggestions for complete apps that are partly preconfigured and easy to manage( A quick search found ebox, any comments or advice on this ? )

Many Thanks:)

---

### Post by ezacon on 2009-01-11
for the mail part, take a look to Zimbra.
[www.zimbra.com](www.zimbra.com)

---

### Post by Tom_T on 2009-01-11
Thanks for the reply.

But is this a true mail server or does it talk to a mail server ??

---

### Post by spiderbatdad on 2009-01-11
I used this guide: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
It takes a bit of work and debugging, but I think it will get you 95% of the way.

---

### Post by HighCommander540 on 2009-01-11
If you are looking for a GUI. You are going to need a really good system for the server, because the whole point of the Ubuntu server is to have the greatest preformance you can. Which meas no GUI.

You can install a GUI after you configure your server, but Ubuntu server doesn't come with it pre-installed.

---

### Post by HermanAB on 2009-01-12
Zimbra and Citadel are complete mail systems.  Qmail, Postfix, Sendmail and the like are Lego blocks which must be combined with a zoo of other little Lego blocks to make a mail system, which can be very interesting and can keep you out of trouble for several weeks.

Citadel is the easiest to set up - takes about 20 minutes - and well, it 'Just Works':
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

Cheers,

Herman

---

### Post by Tom_T on 2009-01-12
> **spiderbatdad said:**
> I used this guide: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
It takes a bit of work and debugging, but I think it will get you 95% of the way.

I'm going to take a look at this and Apache.

If I'm using the server edition and then adding a GUI.. is it easier to with 8.10 desktop or would that cause issues ??

Thanks

---

### Post by spiderbatdad on 2009-01-12
> **Tom_T said:**
> I'm going to take a look at this and Apache.

If I'm using the server edition and then adding a GUI.. is it easier to with 8.10 desktop or would that cause issues ??

Thanks
Personally...I installed 8.04 LTS Xubuntu for the lightweight desktop manager and windowing system, for the rare occasion when I want to turn the monitor on...or forward X through a tunnel to a remote machine. I then added the server applications I wanted...like openssh-server, apache, etc...So I guess if the primary use for the machine is server, but you want a desktop or window manager occasionally, I would recommend xfce4.

---

