---
title: "Postfix won't accept my mail anymore"
date: 2010-07-01
forum: Server Platforms
---

### Post by tacom6 on 2010-07-01
Hey guys,

I set up my Postfix/Dovecot Sasl implementation according to the Server Docs. Now it worked both for SSL POP3 and sending via SSL SMTP. But recently it simply stopped accepting my mail, I can't send out.

Any help would be appreciated as I am annoyed that even though I had this working before it suddenly stopped working.

Cheers,
Nile

---

### Post by sh1ny on 2010-07-02
Try sending an email and then post the ouput of :

> tail -f /var/log/mail.log -n 200

( Use something like pastebin for that, don't paste it here ).

---

### Post by tacom6 on 2010-07-02
> **sh1ny said:**
> Try sending an email and then post the ouput of :

( Use something like pastebin for that, don't paste it here ).

Since I only got 2 lines, and later the 3rd.

Jul  2 12:22:07 integrecomm dovecot: pop3-login: Login: user=<nilator>, method=PLAIN, rip=76.224.209.52, lip=63.247.203.170, TLS
Jul  2 12:22:07 integrecomm dovecot: POP3(nilator): Disconnected: Logged out top=0/0, retr=0/0, del=0/50, size=1955224
Jul  2 12:25:03 integrecomm postfix/tlsmgr[9529]: tlsmgr_cache_run_event: start TLS smtpd session cache cleanup

Both of those are for POP3, when I try to send to SMTP 25 via a mail client, it times out and nothing is written to the log... ???? Weird or what ??

When I send from gmail to my domain.. here is what i get:

Jul  2 12:27:01 integrecomm postfix/smtpd[10431]: initializing the server-side TLS engine
Jul  2 12:27:01 integrecomm postfix/smtpd[10431]: connect from mail-ew0-f54.google.com[209.85.215.54]
Jul  2 12:27:01 integrecomm postfix/smtpd[10431]: 7B3BB520D15: client=mail-ew0-f54.google.com[209.85.215.54]
Jul  2 12:27:01 integrecomm postfix/cleanup[10436]: 7B3BB520D15: message-id=<AANLkTilM9uEx5ueLIuC3hR3KxlNymvAMOqj-xRBqDLEN@mail.gmail.com>
Jul  2 12:27:01 integrecomm postfix/qmgr[7910]: 7B3BB520D15: from=<tacom67@gmail.com>, size=1840, nrcpt=1 (queue active)
Jul  2 12:27:01 integrecomm postfix/local[10437]: 7B3BB520D15: to=<nilator@integrecomm.com>, relay=local, delay=0.54, delays=0.47/0/0/0.07, dsn=2.0.0, status=sent (delivered to maildir)
Jul  2 12:27:01 integrecomm postfix/qmgr[7910]: 7B3BB520D15: removed

Something is wrong with SASL??? please help.

Thanks,
Nile

---

### Post by tacom6 on 2010-07-02
> **tacom6 said:**
> Since I only got 2 lines, and later the 3rd.

please help.

Thanks,
Nile

K, I enable verbose ssl, I get the following now when I try to send to port 587 (smtp).

Jul  2 20:53:56 integrecomm postfix/smtpd[10814]: initializing the server-side TLS engine
Jul  2 20:53:56 integrecomm postfix/smtpd[10814]: connect from 76-224-209-52.lightspeed.iplsin.sbcglobal.net[76.224.209.52]
Jul  2 20:54:27 integrecomm postfix/smtpd[10814]: lost connection after UNKNOWN from 76-224-209-52.lightspeed.iplsin.sbcglobal.net[76.224.209.52]
Jul  2 20:54:27 integrecomm postfix/smtpd[10814]: disconnect from 76-224-209-52.lightspeed.iplsin.sbcglobal.net[76.224.209.52]

TLS engine starts, but then nothing happens.

---

### Post by tacom6 on 2010-07-04
Well... nevermind guys I switched to an easier to manage mail server as this is ridiculously complicated for a beginner like me.

---

### Post by Vegan on 2010-07-04
what are you using now?

---

### Post by tacom6 on 2010-07-04
> **Vegan said:**
> what are you using now?

I switched to Firstclass 10 server core and Internet Services. They have a fully functional demo with a license for 5 users. I plan to buy more licenses as customers join my server. Although it is a lot more than just a SMTP server. Check out at [http://www.firstclass.com/](http://www.firstclass.com/)

Cheers,
Nile

---

### Post by tacom6 on 2010-07-04
> **tacom6 said:**
> They have a fully functional demo with a license for 5 users.

Here is the introductory version: [http://www.firstclass.com/Divisions/FAV13-0024FC95/?OpenItemURL=S047C50E5](http://www.firstclass.com/Divisions/FAV13-0024FC95/?OpenItemURL=S047C50E5)

:)

---

### Post by Vegan on 2010-07-04
Nothing for Linux, oh well back to the corporate favorite, Postfix is sponsored by IBM

---

### Post by tacom6 on 2010-07-04
> **Vegan said:**
> Nothing for Linux, oh well back to the corporate favorite, Postfix is sponsored by IBM

Gosh there is a Linux package, they are cross-platform. That is what I am running on Ubuntu 10.04 64bit. Do you want me to give you a direct link from my server?

---

### Post by robowen on 2010-07-05
hi there, I just had a riveting (!) few weeks working with dovecot & postfix so if you still have any interest in trying to crack it I may be able to help

the o'reilly postfix definitive guide is pretty thorough and easy to follow if you can spare a few days time for reading it.

cheers
rob

---

