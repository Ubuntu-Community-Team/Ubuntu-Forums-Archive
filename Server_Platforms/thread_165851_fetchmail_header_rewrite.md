---
title: "fetchmail header rewrite?"
date: 2006-04-25
forum: Server Platforms
---

### Post by Flibblebot on 2006-04-25
Hi

Hope someone can help me, and that I'm asking in the right place.
I'm trying to set up a small server which, among other things, manages e-mail for my home and business.
I have a couple of hosted websites which forward e-mail to my ISP POP account (the original e-mail address is kept in the "X-originally to" header). I then want to use fetchmail to pick up e-mail from the ISP account and then forward it onto postfix for delivery to the final mailboxes.
I've setup postfix successfully, as per flurdy's how to (I can telnet to port 25 and successfully send an e-mail), but I'm having problems adding fetchmail into the mix.

Here's my /etc/fetchmailrc:
```

set no bouncemail
set daemon 600

poll mail.myisp.co.uk proto pop3
        envelope x-originally-to
        user "myusername" with pass "password"
        keep

```
but here's the debug log from fetchmail:
```

fetchmail: POP3< +OK ISP POP3 Server Ready
fetchmail: POP3> CAPA
fetchmail: POP3< -ERR You must login first.
fetchmail: You must login first.
fetchmail: Repoll immediately on myusername@mail.myisp.co.uk
fetchmail: POP3< +OK ISP POP3 Server Ready
fetchmail: POP3> USER myusername
fetchmail: POP3< +OK Please enter your pass, with the PASS command.
fetchmail: POP3> PASS *
fetchmail: POP3< +OK Logged in.
fetchmail: selecting or re-polling default folder
fetchmail: POP3> STAT
fetchmail: POP3< +OK 2 10323
fetchmail: POP3> LAST
fetchmail: POP3< -ERR Invalid command.
fetchmail: Invalid command.
fetchmail: POP3> UIDL
fetchmail: POP3< +OK UIDL List
fetchmail: POP3< 1 1145971950.H494450P24070.mail.myisp.co.uk,S=7824
fetchmail: POP3< 2 1145972473.H892482P25515.mail.myisp.co.uk,S=2275
fetchmail: 2 is unseen
fetchmail: POP3< .
2 messages (1 seen) for myusername at mail.myisp.co.uk (10323 octets).
skipping message myusername@mail.myisp.co.uk:1 not flushed
fetchmail: POP3> LIST 2
fetchmail: POP3< +OK 2 2327
fetchmail: POP3> RETR 2
fetchmail: POP3< +OK Message follows.
reading message myusername@mail.myisp.co.uk:2 of 2 (2327 octets)
fetchmail: SMTP< 220 mailserver.ubuntuserver.com ESMTP Postfix
fetchmail: SMTP> EHLO mail.myisp.co.uk
fetchmail: SMTP< 250-mailserver.ubuntuserver.com
fetchmail: SMTP< 250-PIPELINING
fetchmail: SMTP< 250-SIZE 10240000
fetchmail: SMTP< 250-ETRN
fetchmail: SMTP< 250-STARTTLS
fetchmail: SMTP< 250-AUTH LOGIN PLAIN DIGEST-MD5 CRAM-MD5
fetchmail: SMTP< 250-AUTH=LOGIN PLAIN DIGEST-MD5 CRAM-MD5
fetchmail: SMTP< 250 8BITMIME
fetchmail: forwarding to localhost
fetchmail: SMTP> MAIL FROM:<sender@another.email.com> SIZE=2327
fetchmail: SMTP< 250 Ok
fetchmail: SMTP> RCPT TO:<fetchmail@localhost>
fetchmail: SMTP< 250 Ok
fetchmail: SMTP> DATA
fetchmail: SMTP< 354 End data with <CR><LF>.<CR><LF>
#***************fetchmail: SMTP>. (EOM)
fetchmail: SMTP< 250 Ok: queued as 27099318385
 not flushed
fetchmail: POP3> QUIT
fetchmail: POP3< +OK Goodbye. See you again sometime :)
fetchmail: 6.2.5 querying mail.myisp.co.uk (protocol POP3) at Tue 25 Apr 2006 14:41:24 BST: poll completed
fetchmail: swapping UID lists
fetchmail: SMTP> QUIT
fetchmail: SMTP< 221 Bye
fetchmail: Writing fetchids file.

```

I think the line that's causing the problem is the "RCPT TO:<fetchmail@localhost>", because in the postfix logs, I can see this:
```

Apr 25 14:41:24 localhost postfix/virtual[8531]: 718B4318397: to=<fetchmail@ubuntuserver.com>, orig_to=<fetchmail@localhost.ubuntuserver.com>, relay=virtual, delay=0, status=bounced (unknown user: "fetchmail@ubuntuserver.com")

```

How do I get fetchmail to send the e-mail to the correct user, not the fetchmail user?
I've tried the "set silent" and "no rewrite" options, but they don't seem to have any effect.

Can someone help, because I'm like this ](*,) at the moment :(

TIA

---

### Post by Flibblebot on 2006-04-26
OK, so I've done a bit of reading, and I think I need to use procmail by adding the **mailbox_command = /usr/bin/procmail** into postfix's main.cf file.
The question is: what exactly do I need to do with procmail to make it send the e-mail to the intended recipient rather than the fetchmail user?

Please help, I'm a linux newbie and I desperately want to get this working.

Many thanks...

---

### Post by Flibblebot on 2006-04-26
Well, thanks for all your help, I've worked out the solution - it's nothing to do with procmail at all (thank goodness, I've never been able to get my head round grep!) - I needed to add all of the domain names that my mailserver handles to the fetchmailrc file so it becomes:
```

set no bouncemail
set daemon 600

poll mail.myisp.co.uk proto pop3
        envelope x-originally-to
        localdomains domain1.com domain2.com ISPdomain.com localhost
        user "myusername" with pass "password"
        keep

```

---

