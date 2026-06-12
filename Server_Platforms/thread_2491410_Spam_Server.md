---
title: "Spam Server"
date: 2023-10-07
forum: Server Platforms
---

### Post by tesla1886 on 2023-10-07
[COLOR=#050505][FONT=&quot][FONT=inherit]I am in need of a anti spam server. I have the server and even already have Ubuntu installed on it.[/FONT]
[/FONT][/COLOR]
[COLOR=#050505][FONT=&quot][FONT=inherit]Problem is that I already have a Microsoft Exchange server and every install / setup guide I found also included a mail server.[/FONT]
[/FONT][/COLOR]
[COLOR=#050505][FONT=&quot][FONT=inherit]I realize a spam server is essentially a mail server, but what I don't know is how to get legitimate mail from the spam server to the Exchange server.[/FONT]
[/FONT][/COLOR]
[COLOR=#050505][FONT=&quot][FONT=inherit]So [FONT=inherit][/FONT]what I am ask does anybody have a good guide to set up a anti spam server. From what I understand Spamassassin (but have also been told different) is one of the best if not the actual best, so I would prefer to use it.

Thank You[/FONT]
[/FONT][/COLOR]

---

### Post by TheFu on 2023-10-07
linuxbabe has guides.  Rather than "spam server", look for "email gateway" or "email proxy" as the keywords.
[https://www.linuxbabe.com/mail-server/mail-proxy-server](https://www.linuxbabe.com/mail-server/mail-proxy-server) is one. I didn't look too closely. My email gateway has lots of customization for the types of email I expect to get and blocks problem senders based on subnets and TLDs.  For example, .lat has been spamming a bunch the last 6 months, so I blocked all TLDs with \.lat$ matches.  Haven't seen any really spam the last 3 weeks since doing that.  

I've been blocking huge parts of the internet for years. No clients or friends would be emailing from those places.

I also monitor spammers daily.
```
$ egrep -ic reject /var/log/mail.log
9555
```

Lots of spammers for a weekend. My logs are rotated at midnight.

I also check for valid SPF and valid character sets being used. For example, nobody expects any of my users to use non-English languages, so if I see any characters that aren't latin1, to spam it goes.

From the high level, my gateway server is just SMTP and doesn't support anything except server-to-server SMTP traffic.  No IMAP, no clients attempting to send on 465/587 ports either.  If email comes from my domain, it must come from the main email server AND only that system.

And be certain to check whether your email gateway allows anything bad like being an open relay. That will get your IP put onto spammer lists is just a few minutes, so check for that yourself. There are websites that will perform email server checks.

---

