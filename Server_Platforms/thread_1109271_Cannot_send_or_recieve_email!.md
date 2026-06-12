---
title: "Cannot send or recieve email!"
date: 2009-03-28
forum: Server Platforms
---

### Post by linuxisevolution on 2009-03-28
I am trying to setup squirrelmail with courier-imap. I have setup squirrelmail correctly(finally) , but for some reason courier-imap does not receive or send any of my mail! I have everything setup correctly at the dns level(freedns.afraid.org). 

What exactly do I have to do to make courier except and send email outside of my network?

I will post my config files if necessary. 

Thanks!

---

### Post by Bachstelze on 2009-03-28
courier-imap does not send or recieve mail. That's not its job. It's the job of the MTA (Sendmail, Postfix, Exim...).

I suggest you do a bit of research before you try to set up a mail server. It is *not* a trivial task.

Also moved to Server Platforms.

---

### Post by linuxisevolution on 2009-03-28
> **HymnToLife said:**
> courier-imap does not send or recieve mail. That's not its job. It's the job of the MTA (Sendmail, Postfix, Exim...).

I suggest you do a bit of research before you try to set up a mail server. It is *not* a trivial task.

Also moved to Server Platforms.


Well sorry for not *knowing* that...
I was simply following instructions that I found, so blame them, not me.

Anyway... The logs:
```

Mar 27 15:07:15 debian imapd: LOGIN, user=winrid, ip=[::ffff:127.0.0.1], protocol=IMAP
Mar 27 15:08:02 debian imapd: LOGOUT, user=winrid, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=38, sent=387, time=47
Mar 27 15:19:41 debian postfix/smtpd[23236]: warning: cannot get private key from file /etc/ssl/private/smtpd.key
Mar 27 15:19:41 debian postfix/smtpd[23236]: warning: TLS library problem: 23236:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('/etc/ssl/private/smtpd.key','r'):
Mar 27 15:19:41 debian postfix/smtpd[23236]: warning: TLS library problem: 23236:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
Mar 27 15:19:41 debian postfix/smtpd[23236]: warning: TLS library problem: 23236:error:140B0002:SSL routines:SSL_CTX_use_PrivateKey_file:system lib:ssl_rsa.c:648:
Mar 27 15:19:41 debian postfix/smtpd[23236]: cannot load RSA certificate and key data
Mar 27 15:19:41 debian postfix/smtpd[23236]: connect from mail-gx0-f176.google.com[209.85.217.176]
Mar 27 15:19:41 debian postfix/smtpd[23236]: warning: unknown smtpd restriction: "."
Mar 27 15:19:41 debian postfix/smtpd[23236]: NOQUEUE: reject: RCPT from mail-gx0-f176.google.com[209.85.217.176]: 451 4.3.5 Server configuration error; from=<winrid@gmail.com> to=<winrid@directoryadmin.info> proto=ESMTP helo=<mail-gx0-f176.google.com>
Mar 27 15:19:41 debian postfix/cleanup[23240]: E06DF244D1: message-id=<20090327191941.E06DF244D1@hsd1.pa.comcast.net>
Mar 27 15:19:42 debian postfix/smtpd[23236]: disconnect from mail-gx0-f176.google.com[209.85.217.176]
Mar 27 15:19:42 debian postfix/qmgr[2662]: E06DF244D1: from=<double-bounce@hsd1.pa.comcast.net>, size=930, nrcpt=1 (queue active)
Mar 27 15:19:42 debian postfix/qmgr[2662]: E06DF244D1: to=<postmaster@72.206.223.52>, orig_to=<postmaster>, relay=none, delay=0.3, delays=0.23/0.07/0/0, dsn=5.1.3, status=bounced (bad address syntax)
Mar 27 15:19:42 debian postfix/bounce[23242]: warning: E06DF244D1: undeliverable postmaster notification discarded


```

Look interesting? I cannot figure this out..

What is easiest to configure? sendmail, postfix, or exim?

---

### Post by hyper_ch on 2009-03-28
IMHO postfix :)

---

### Post by Dr Small on 2009-03-28
> **hyper_ch said:**
> IMHO postfix :)
I second that.

---

### Post by linuxisevolution on 2009-03-29
Ok, postfix then :)

Is there a decent but simple howto for postfix,courier,and squirrelmail?

I think I have courier and squirrelmail setup correctly...

---

### Post by Dr Small on 2009-03-29
> **linuxisevolution said:**
> Ok, postfix then :)

Is there a decent but simple howto for postfix,courier,and squirrelmail?

I think I have courier and squirrelmail setup correctly...
I always follow this guide:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by linuxisevolution on 2009-03-29
> **Dr Small said:**
> I always follow this guide:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Thanks! I'm not running Ubuntu but it should work anyway. :P

---

### Post by hyper_ch on 2009-03-29
I usually follow falko's perfect howtos over at [http://www.howtoforge.com](http://www.howtoforge.com)

---

### Post by Dr Small on 2009-03-29
> **linuxisevolution said:**
> Thanks! I'm not running Ubuntu but it should work anyway. :P
It generally applies to most Debian based distros, although sometimes they package things differently and you have to solve a few problems that don't follow the guide exactly ;)

---

### Post by linuxisevolution on 2009-03-29
> **Dr Small said:**
> It generally applies to most Debian based distros, although sometimes they package things differently and you have to solve a few problems that don't follow the guide exactly ;)
I am running Debian:P

But I've ran into a snag with that howto.

> To configure the mailbox format for Maildir: 
sudo postconf -e 'home_mailbox = Maildir/'
You may need to issue this as well: 
sudo postconf -e 'mailbox_command ='
Note: This will place new mail in /home/username/Maildir so you will need to configure your Mail Delivery Agent to use the same path.

How do I set courier to use that same directory for the mail?

---

### Post by linuxisevolution on 2009-03-29
I have one trivial question:
I have the domain directoryadmin.info for my website. I then have mail.directoryadmin.info directed to the squirrelmail page with apache.

So what would my email be?

[email]username@directoryadmin.info[/email]

or

[email]username@mail.directoryadmin.info[/email]
:confused:

---

### Post by hyper_ch on 2009-03-29
depending on how you set it up you can use either one.

---

### Post by linuxisevolution on 2009-03-29
> **hyper_ch said:**
> depending on how you set it up you can use either one.

So if I set it up with directoryadmin.info then it will be [email]username@directoryadmin.info[/email] ?

---

### Post by hyper_ch on 2009-03-29
you setup a virtual table where you say what email address is routed to what system user account for example.

---

### Post by linuxisevolution on 2009-03-29
> **hyper_ch said:**
> you setup a virtual table where you say what email address is routed to what system user account for example.

By virtual table to you mean <virtualhost *> in apache?

I just added this to my apache config, is this correct?

```

<VirtualHost *>
 ServerName mail.directoryadmin.info 
 ServerAlias mail.*
 ServerAdmin  <snip>@directoryadmin.info ##I don't think this line that important...
 DocumentRoot  /usr/share/squirrelmail  ##do you mean this line?
 </VirtualHost>

```

---

### Post by linuxisevolution on 2009-03-29
IT WORKS!!!!

Thanks for all your help guys, I feel smart. w00t!

I'm gonna go rub it in yahoo's face now. :KS

---

### Post by hyper_ch on 2009-03-29
no, in postfix:

e.g. in main cf
```

virtual_maps = hash:/etc/postfix/virtual

```

and then in virtual
```

user1@domain.com       sysuser1
user2@domain.com       sysuser2
...

```

and postmap the virtual file then

---

