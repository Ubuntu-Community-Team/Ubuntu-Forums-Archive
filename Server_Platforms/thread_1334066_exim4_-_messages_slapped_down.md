---
title: "exim4 - messages slapped down"
date: 2009-11-22
forum: Server Platforms
---

### Post by flimflamflizm on 2009-11-22
Greeting chaps and chapettes. I am the typical linux noob although I've been using ubuntu at home for about a year now.

I've recently set up a server box at home behind my ADSL router running ubuntu server to host a website for my sister's business. Have successfully set up the site using drupal, apache2, ftp server, ssh and firewall, which I am quite proud of.

Problem is, I've been racking my brains for **literally** 2 days solid trying to get a mail server up and running, and I'm at my wit's end.

I first tried postfix and made little progress, it seemed to acknowledge the fact that I was trying to send mail, and that other emails were trying to get through, but did this "relay access denied" nonsense that I just couldn't solve. At this point I am trying out exim4 with a similar level of success. I suspect these issues I've been having may be related and nothing to do with the actual MTA configuration but rather with my DNS settings, external network, domain name host etc, but I'm not familiar enough with domain name hosting and MX records and all that jibba jabba I've been hearing so much about to figure out what's going on :(

Looking at my exim mainlog excerpt here I bet some boffin can get me on the right track. Any help is greatly appreciated!

Emails altered to protect the innocent:

```

2009-11-22 18:59:08 [5938] H=(mail-vw0-f181.google.com) [209.85.212.181]:49683 I=[10.1.1.4]:25 incomplete transaction (QUIT) from <my.gmail.address@gmail.com$
2009-11-22 18:59:08 [5938] SMTP connection from (mail-vw0-f181.google.com) [209.85.212.181]:49683 I=[10.1.1.4]:25 closed by QUIT
2009-11-22 19:00:25 [4623] SMTP connection from [209.85.212.183]:50454 I=[10.1.1.4]:25 (TCP/IP connection count = 1)
2009-11-22 19:00:26 [4623] SMTP connection from [209.85.212.181]:57680 I=[10.1.1.4]:25 (TCP/IP connection count = 2)
2009-11-22 19:00:46 [6057] H=mail-vw0-f183.google.com [209.85.212.183]:50454 I=[10.1.1.4]:25 F=<my.gmail.address@gmail.com> temporarily rejected RCPT <f$
2009-11-22 19:00:46 [6057] H=mail-vw0-f183.google.com [209.85.212.183]:50454 I=[10.1.1.4]:25 incomplete transaction (QUIT) from <my.gmail.address@gmail.com$
2009-11-22 19:00:46 [6057] SMTP connection from mail-vw0-f183.google.com [209.85.212.183]:50454 I=[10.1.1.4]:25 closed by QUIT
2009-11-22 19:00:47 [6058] H=mail-vw0-f181.google.com [209.85.212.181]:57680 I=[10.1.1.4]:25 F=<my.gmail.address@gmail.com> temporarily rejected RCPT <f$
2009-11-22 19:00:47 [6058] H=mail-vw0-f181.google.com [209.85.212.181]:57680 I=[10.1.1.4]:25 incomplete transaction (QUIT) from <my.gmail.address@gmail.com$
2009-11-22 19:00:47 [6058] SMTP connection from mail-vw0-f181.google.com [209.85.212.181]:57680 I=[10.1.1.4]:25 closed by QUIT
2009-11-22 19:00:49 [4623] SMTP connection from [209.85.212.181]:44470 I=[10.1.1.4]:25 (TCP/IP connection count = 1)
2009-11-22 19:00:49 [6059] no IP address found for host mail (during SMTP connection from [209.85.212.181]:44470 I=[10.1.1.4]:25)
2009-11-22 19:01:10 [6059] H=(mail-vw0-f181.google.com) [209.85.212.181]:44470 I=[10.1.1.4]:25 F=<my.gmail.address@gmail.com> temporarily rejected RCPT $
2009-11-22 19:01:10 [6059] H=(mail-vw0-f181.google.com) [209.85.212.181]:44470 I=[10.1.1.4]:25 incomplete transaction (QUIT) from <my.gmail.address@gmail.com$
2009-11-22 19:01:10 [6059] SMTP connection from (mail-vw0-f181.google.com) [209.85.212.181]:44470 I=[10.1.1.4]:25 closed by QUIT
2009-11-22 19:01:23 [4623] SMTP connection from [65.54.190.157]:46101 I=[10.1.1.4]:25 (TCP/IP connection count = 1)
2009-11-22 19:01:43 [6061] H=mc4-f21.bay6.hotmail.com (bay0-omc3-s19.bay0.hotmail.com) [65.54.190.157]:46101 I=[10.1.1.4]:25 F=<myhotmailaddress@hotmail.com> tempor$
2009-11-22 19:01:44 [6061] H=mc4-f21.bay6.hotmail.com (bay0-omc3-s19.bay0.hotmail.com) [65.54.190.157]:46101 I=[10.1.1.4]:25 incomplete transaction (RSET) f$
2009-11-22 19:01:44 [6061] SMTP connection from mc4-f21.bay6.hotmail.com (bay0-omc3-s19.bay0.hotmail.com) [65.54.190.157]:46101 I=[10.1.1.4]:25 closed by QU$
2009-11-22 19:01:53 [4623] SMTP connection from [209.85.212.181]:50279 I=[10.1.1.4]:25 (TCP/IP connection count = 1)
2009-11-22 19:01:53 [6063] no IP address found for host mail (during SMTP connection from [209.85.212.181]:50279 I=[10.1.1.4]:25)
2009-11-22 19:01:57 [6062] Start queue run: pid=6062
2009-11-22 19:01:57 [6064] 1NC5En-0001om-Bh Message is frozen
2009-11-22 19:01:57 [6065] 1NC6Kv-0001MM-De Message is frozen
2009-11-22 19:01:57 [6066] 1NC63Z-0001Ii-Si Message is frozen
2009-11-22 19:01:57 [6067] 1NC5ee-00021i-GF Message is frozen
2009-11-22 19:01:57 [6068] 1NC5wy-0001Lf-IC Message is frozen
2009-11-22 19:01:57 [6069] 1NC5aM-0001wq-22 Message is frozen
2009-11-22 19:01:57 [6070] 1NC5zn-0001GF-S1 Message is frozen
2009-11-22 19:01:57 [6071] 1NC5Sw-0001so-1j Message is frozen
2009-11-22 19:01:57 [6072] 1NC5Ks-0001qj-JS Message is frozen
2009-11-22 19:01:57 [6073] 1NC5ih-0001D7-H8 Message is frozen
2009-11-22 19:01:57 [6074] 1NC62O-0001IU-Kx Message is frozen
2009-11-22 19:01:57 [6075] 1NC5Jt-0001p8-BO Message is frozen
2009-11-22 19:01:57 [6062] End queue run: pid=6062
2009-11-22 19:02:14 [6063] H=(mail-vw0-f181.google.com) [209.85.212.181]:50279 I=[10.1.1.4]:25 F=<my.gmail.address@gmail.com> temporarily rejected RCPT $
2009-11-22 19:02:14 [6063] H=(mail-vw0-f181.google.com) [209.85.212.181]:50279 I=[10.1.1.4]:25 incomplete transaction (QUIT) from <my.gmail.address@gmail.com
2009-11-22 19:02:14 [6063] SMTP connection from (mail-vw0-f181.google.com) [209.85.212.181]:50279 I=[10.1.1.4]:25 closed by QUIT
2009-11-22 19:02:28 [4623] SMTP connection from [209.85.212.181]:38156 I=[10.1.1.4]:25 (TCP/IP connection count = 1)
2009-11-22 19:02:28 [6076] no IP address found for host mail (during SMTP connection from [209.85.212.181]:38156 I=[10.1.1.4]:25)
2009-11-22 19:02:49 [6076] H=(mail-vw0-f181.google.com) [209.85.212.181]:38156 I=[10.1.1.4]:25 F=<my.gmail.address@gmail.com> temporarily rejected RCPT $
2009-11-22 19:02:49 [6076] H=(mail-vw0-f181.google.com) [209.85.212.181]:38156 I=[10.1.1.4]:25 incomplete transaction (QUIT) from <my.gmail.address@gmail.com
2009-11-22 19:02:49 [6076] SMTP connection from (mail-vw0-f181.google.com) [209.85.212.181]:38156 I=[10.1.1.4]:25 closed by QUIT
2009-11-22 19:04:01 [6079] 1NC7QP-0001a3-62 <= flimflam@mail.mydomainname.com.au U=flimflam P=local S=566 from <flimflam@mail.mydomainname.com.au>$

```

---

### Post by kkady32 on 2009-11-22
im not expert in this but maybe problem is the port settings
because for example i use thunderbird for gmail(IMAP) and the default port for me is not 25 is 587 (whenn i use SSL/TSL for smtp) and for incomming mail is 993

---

### Post by flimflamflizm on 2009-11-22
Thanks kady but I'm using gmail's webmail.
Although interestingly enough, here's the nmap of my internal network, pointing at the server:

```

PORT    STATE  SERVICE
21/tcp  open   ftp
22/tcp  open   ssh
**25/tcp  open   smtp**
80/tcp  open   http
113/tcp closed auth
143/tcp closed imap
443/tcp closed https
465/tcp closed smtps
587/tcp closed submission
993/tcp closed imaps

```

and here's the nmap pointing at my .com address:

```

PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
23/tcp    open  telnet
80/tcp    open  http
52869/tcp open  unknown

```

Note the conspicuously absent port 25! I doubt this is normal..

However, despite this, even if I send mail internally I get the same errors. :(

---

### Post by kkady32 on 2009-11-22
u must setup exim to connect to gmail server and they use a specific ports for POP3 or IMAP
exim is an MTA(message transfer agent) and this work with an MUA (mail user agent) like thunderbird or mutt or another mail client
like most client programs, an MUA is only active when a user runs it. messages arrive on the Mail Transfer Agent (MTA) server. unless the MUA has access to the server's disk, messages are stored on a remote server and the MUA has to request them on behalf of the user.
when u use webmail then u not need email client(that work under browser)

what u see here with nmap is the open port from u server and u must undestand the mail concepts( u must connect to gmail servers not to u servers for internet mails)

---

