---
title: "Struggling with mail server for 8 hours!"
date: 2022-02-22
forum: Server Platforms
---

### Post by sebawri on 2022-02-22
(First, I'm not sure where to put this thread, so I thought General Help was right.)

Hi all, I'm going nuts here. I can't get my mail server to send emails to any email address that isn't within my VPS account. For example, I can send an email from [email]admin@domain1.com[/email] to [email]admin@domain2.com[/email]. They're both sitting in my Vultr account, but they're on different servers.

So I have two servers: domain1.com and domain2.com.

Domain1.com can send and receive emails without any issues.
Domain2.com can send emails to anyone at domain1.com and domain2.com, but it can't send email to an outside service like gmail or yandex.

I've spent the last eight hours trying everything under the sun to get it to work. Including deploying and setting up a new VPS instance. Working from scratch, and I still can't get it to work. I'm pretty dizzy now after trying absolutely everything.

I'm running openlitespeed server and cyberpanel. Everything works fine, except the mail server. If I ssh in and execute mail [email]email@domain.com[/email], type a subject, type some text, and hit control-D, it sends the email to anyone and works perfectly.

But I can't for the life of me get an application working. For example, neither Thunderbird nor Evolution are able to send an email normally.

I would really appreciate any help. I'm not even sure what information to provide. Like I said, 8 hours and my eyes are starting to bleed...

Thanks for your help.
Sebastian

---

### Post by sebawri on 2022-02-22
Edit: I know that port 25 is working on the server because telnet portquiz.net 25 [FONT=monospace][COLOR=#000000]successfully connects. I also keep getting self-signed certificate errors when I check the mail servers certificate, yet I've issued and reissued them like 5 times in Cyberpanel and on the CLI using certbot --standalone.[/COLOR][/FONT]

---

### Post by slickymaster on 2022-02-22
*Thread moved to **Server Platforms**.*

---

### Post by sebawri on 2022-02-22
Okay. Thanks for moving (and not deleting) my thread...

---

### Post by SeijiSensei on 2022-02-22
> I'm running openlitespeed server and cyberpanel. 

Some of us might be able to help if you were running the standard suite of email software that comes with Ubuntu like postfix+dovecot and maybe procmail for local delivery. I, for one, have no idea what either of those applications you mention are.

---

### Post by sebawri on 2022-02-22
Okay. openlitespeed is a server. Kind of apache2 and nginx. Cyberpanel is a webmin user interface for configuring a website/domain. Like a reseller panel because you have configure many virtualhosts through it. This problem is happening on a public facing VPS, and I am using postfix and dovecot. (I'm also not too experienced with mailservers.)

I'm running Ubuntu 20.04.

I have an update:

---

### Post by sebawri on 2022-02-22
**Update: **Things just got weirder. I'm not exactly sure what I did, but it's working 50% better now. :o So, the email from domain1.com can send and receive internationally. It's perfect. 

Now for the development. [EMAIL="admin@domain2.com"]admin@domain2.com[/EMAIL] has passed. It can send and receive internationally. However, and this is the stumper, [EMAIL="info@domain2.com"]info@domain2.com[/EMAIL] cannot send emails out side of domain2.com... :-|:-|:-|

---

### Post by SeijiSensei on 2022-02-22
Well, let's start with the contents of /var/log/mail.log if you have one.  Open a terminal in one window and run "tail -f /var/log/mail.log". Then try to send an email and see what happens.

---

### Post by TheFu on 2022-02-22
Are DNS records all setup?  MX, TXT for SFP? Are they all propagated world-wide?
I refuse email from any domain that doesn't pass a reverse DNS lookup.

SMTP is for sending email and server-to-server transfers.
IMAP/POP is for reading email using thick clients.

I see lots of descriptions above, but no config files and other "FACTS" - for every statement made, please post the text config that proves that statement.  Usually, by doing that, you'll see the issue yourself.  Make a checklist for both systems. What is different?

---

