---
title: "Postfix question"
date: 2011-11-12
forum: Server Platforms
---

### Post by JKyleOKC on 2011-11-12
While attempting to troubleshoot another problem involving 554 rejections of messages sent by a script, I came across a puzzling thing in /var/log/mail.log as illustrated by the following trace of a single test message:```
Nov 12 11:15:36 mehitabel postfix/pickup[31877]: 0F6BF100042: uid=1000 from=<jk>
Nov 12 11:15:36 mehitabel postfix/cleanup[32523]: 0F6BF100042: message-id=<20111112171536.0F6BF100042@adsl-66-143-22-xxx.dsl.okcyok.swbell.net>
Nov 12 11:15:36 mehitabel postfix/qmgr[1410]: 0F6BF100042: from=<xxx@jimkyle.com>, size=329, nrcpt=9 (queue active)
Nov 12 11:15:36 mehitabel postfix/smtp[32526]: 0F6BF100042: to=<a@adsl-66-143-22-xxx.dsl.okcyok.swbell.net>, orig_to=<a>, relay=none, delay=0.82, delays=0.79/0.01/0.03/0, dsn=5.4.6, status=bounced (mail for adsl-66-143-22-xxx.dsl.okcyok.swbell.net loops back to myself)
Nov 12 11:15:36 mehitabel postfix/smtp[32526]: 0F6BF100042: to=<forwarding@adsl-66-143-22-xxx.dsl.okcyok.swbell.net>, orig_to=<forwarding>, relay=none, delay=0.82, delays=0.79/0.01/0.03/0, dsn=5.4.6, status=bounced (mail for adsl-66-143-22-xxx.dsl.okcyok.swbell.net loops back to myself)
Nov 12 11:15:36 mehitabel postfix/smtp[32526]: 0F6BF100042: to=<is@adsl-66-143-22-xxx.dsl.okcyok.swbell.net>, orig_to=<is>, relay=none, delay=0.82, delays=0.79/0.01/0.03/0, dsn=5.4.6, status=bounced (mail for adsl-66-143-22-xxx.dsl.okcyok.swbell.net loops back to myself)
Nov 12 11:15:36 mehitabel postfix/smtp[32526]: 0F6BF100042: to=<mail@adsl-66-143-22-xxx.dsl.okcyok.swbell.net>, orig_to=<mail>, relay=none, delay=0.82, delays=0.79/0.01/0.03/0, dsn=5.4.6, status=bounced (mail for adsl-66-143-22-xxx.dsl.okcyok.swbell.net loops back to myself)
Nov 12 11:15:36 mehitabel postfix/smtp[32526]: 0F6BF100042: to=<of@adsl-66-143-22-xxx.dsl.okcyok.swbell.net>, orig_to=<of>, relay=none, delay=0.82, delays=0.79/0.01/0.03/0, dsn=5.4.6, status=bounced (mail for adsl-66-143-22-xxx.dsl.okcyok.swbell.net loops back to myself)
Nov 12 11:15:36 mehitabel postfix/smtp[32526]: 0F6BF100042: to=<simple@adsl-66-143-22-xxx.dsl.okcyok.swbell.net>, orig_to=<simple>, relay=none, delay=0.82, delays=0.79/0.01/0.03/0, dsn=5.4.6, status=bounced (mail for adsl-66-143-22-xxx.dsl.okcyok.swbell.net loops back to myself)
Nov 12 11:15:36 mehitabel postfix/smtp[32526]: 0F6BF100042: to=<test@adsl-66-143-22-xxx.dsl.okcyok.swbell.net>, orig_to=<test>, relay=none, delay=0.82, delays=0.79/0.01/0.03/0, dsn=5.4.6, status=bounced (mail for adsl-66-143-22-xxx.dsl.okcyok.swbell.net loops back to myself)
Nov 12 11:15:36 mehitabel postfix/smtp[32526]: 0F6BF100042: to=<this@adsl-66-143-22-xxx.dsl.okcyok.swbell.net>, orig_to=<this>, relay=none, delay=0.82, delays=0.79/0.01/0.03/0, dsn=5.4.6, status=bounced (mail for adsl-66-143-22-xxx.dsl.okcyok.swbell.net loops back to myself)
Nov 12 11:15:37 mehitabel postfix/smtp[32527]: 0F6BF100042: to=<xxx@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.65.26]:25, delay=1.7, delays=0.79/0.01/0.26/0.63, dsn=2.0.0, status=sent (250 2.0.0 OK 1321118137 q15si6316124anp.165)
Nov 12 11:15:37 mehitabel postfix/bounce[32528]: 0F6BF100042: sender non-delivery notification: 04C05100043
Nov 12 11:15:37 mehitabel postfix/qmgr[1410]: 0F6BF100042: removed

```
The command that generated this was ```
sendmail xxx@gmail.com "this is a simple test of mail forwarding"
```
What's puzzling me is that each word of the test message appears in the log as a "to:" value; the final result however is that it did send to the gmail account, which responded with a 250 status, yet the message was treated as a bounce by Postfix, and I've not been able to find it on the gmail account.

I'm running Lucid 10.04.3 fully updated; could this indicate that my Postfix configuration is somehow messed up?

The original 554 problem is that my main mail server (not the local one) is refusing communication from my local Postfix, because of the "bad reputation of the MTA" -- but this is only happening on two of the multiple boxes at SecureServer and eventually, several days of attempts, the message finally gets through to me. Currently I have four such messages in the queue, re-trying every second or so, and filling my log! I'll have to take that up with my mail provider (GoDaddy) but I want to rule out local misconfiguration possibilities first...

If need be I'll post the configuration files (suitably redacted of course) but I'm looking for general hints as a first step.

---

### Post by SeijiSensei on 2011-11-14
I use sendmail rather than Postfix, but this error:

> adsl-66-143-22-xxx.dsl.okcyok.swbell.net loops back to myself

usually means that the server is not configured to accept mail addressed to [email]user@adsl-66-143-22-xxx.dsl.okcyok.swbell.net[/email].  In sendmail, I'd just add the domain to the list in /etc/mail/local-host-names.  There must be an equivalent in Postfix to define the domains for which the server legitimately accepts mail.

---

### Post by JKyleOKC on 2011-11-14
I appreciate the response, but that "loops back to self" report isn't bothering me. What does concern me is why "to=<a@adsl-66-143-22-xxx.dsl.okcyok.swbell.net>, orig_to=<a>," shows up along with similar log entries for every word in the message. It looks as if sendmail is treating the message text itself as a sequence of target addresses!

Perhaps I should have used "echo" to put the message into stdout, and piped it to sendmail instead of adding it on the command line... In that case it's simply another "ID-ten-T" error, or maybe "PEBKAC"!

---

### Post by lisati on 2011-11-14
I'm wondering if you have the syntax correct for the command. An example of sending an email through the "sendmail" command can be found here: [http://www.linuxquestions.org/questions/linux-general-1/sendmail-command-line-examples-please-207756/](http://www.linuxquestions.org/questions/linux-general-1/sendmail-command-line-examples-please-207756/)

---

### Post by SeijiSensei on 2011-11-14
Oh.  It's sometimes hard to pick out the specific error in a post as long as yours.

```
sendmail xxx@gmail.com "this is a simple test of mail forwarding"
```

First, if you want to send mail from the command line, it's a lot easier to use the "mail" program in **bsd-mailx**.  If you install that package, try using:

```
echo 'this is a simple test of mail forwarding' | mail -s 'test message' you@example.com
```

You can try the same syntax replacing mail with sendmail.  I recommend using single quotes to ensure the entire string is treated as a single parameter.  However you would need to omit the "-s 'test message'" option if you use sendmail, since it doesn't support that method of defining the message's subject.  Sendmail expects a fully pre-formatted message with headers.

From the sendmail man page:

> Sendmail is not intended as a user interface routine; other programs provide user-friendly front ends; sendmail is used only to deliver pre-formatted messages.

---

### Post by JKyleOKC on 2011-11-14
I had been using sendmail but with redirected input from a text file, in the original application, until the 554 error began showing up about 10 days ago. Of course, it was working then.

Then I began trying to troubleshoot the 554 error, sending test messages, and completely lost sight of the need to put the message text in via stdin rather than on the command line. Along the way, I installed "mailx" and of course it works properly. I've made major changes now to the original script, to use mailx and echo and also to send to a gmail account rather than directly to my public mail address.

Thanks to both of you for the suggestions. It definitely was a Problem Between Keyboard And Chair (PEBKAC) situation!

---

### Post by lisati on 2011-11-14
Cheers, SeijiSensei. When I was typing my other post in this thread, I was thinking of adding something along similar lines to your post, but Mrs Lisati was getting on my case to do something for her..... :D

---

