---
title: "fetchmail and postfix &lt;cr&gt;&lt;lf&gt;.&lt;cr&gt;&lt;lf&gt; problem"
date: 2012-05-30
forum: Server Platforms
---

### Post by nachovr on 2012-05-30
Hello to everyone

I have a server running ubuntu 9.10 and set up a mail system with fetchmail 6.3.9 and posftix 2.6.5

On some occasions there's apparently a <CR><LF>.<CR><LF> in the middle of the message body so the mail won't be downloaded completely.

Fetchmail seems to be downloading the mail correctly but when passing it to postfix to be stored in the corresponding mailbox it detects the premature <CR><LF>.<CR><LF> and the message gets stripped.

Here are some fetchmail logs if that helps (although they seem good to me):

fetchmail: POP3> LIST 12
fetchmail: POP3< +OK 12 634630
fetchmail: POP3> TOP 12 99999999
fetchmail: POP3< +OK
fetchmail: reading message [EMAIL="xxxx.xxxxx.xxxxxx.xx@pop3.xxxxxxxx.xxx"]xxxx.xxxxx.xxxxxx.xx@pop3.xxxxxxxx.xxx[/EMAIL]:12 of 12 (634630 octets)
fetchmail: Trying to connect to XXX.XXX.XXX.XXX/25...connected.
fetchmail: SMTP< 220 xxxx.xxxxxxx.xxx ESMTP Postfix
fetchmail: SMTP> EHLO C-023-srv
fetchmail: SMTP< 250-xxxx.xxxxxxxx.xxx
fetchmail: SMTP< 250-PIPELINING
fetchmail: SMTP< 250-SIZE 150000000
fetchmail: SMTP< 250-ETRN
fetchmail: SMTP< 250-STARTTLS
fetchmail: SMTP< 250-ENHANCEDSTATUSCODES
fetchmail: SMTP< 250-8BITMIME
fetchmail: SMTP< 250 DSN
fetchmail: SMTP> MAIL FROM:<xxxxxxx.xxxxxxx@xxxxxxx.xxx> SIZE=634630
fetchmail: SMTP< 250 2.1.0 Ok
fetchmail: SMTP> RCPT TO:<xxxxxxx.xxxxxxx@xxxxxxx.xxx>
fetchmail: SMTP< 250 2.1.5 Ok
fetchmail: SMTP> DATA
fetchmail: SMTP< 354 End data with <CR><LF>.<CR><LF>
fetchmail: SMTP>. (EOM)
fetchmail: SMTP< 250 2.0.0 Ok: queued as 6C848203E4

As you can see the size is supposed to be 634630, when I check the file in the mail box its size is 4073

Thanks

---

### Post by SeijiSensei on 2012-05-30
[Sendmail]("http://docstore.mik.ua/orelly/networking/tcpip/appe_02.htm") has a command-line switch, "-i", that tells it to ignore embedded dots in messages.  Postfix is supposed to be a drop-in replacement for sendmail, but I don't know whether it supports all sendmail's command-line options.  I'd do a little research on whether Postfix supports this option, or whether it has an equivalent option.  As I recall, you can tell fetchmail what sendmail command string to use to deliver the mail.

If you can't find a way to do this with Postfix, you can consider switching to sendmail as your MTA.  For local delivery, as in your situation, I think it works pretty much out-of-the-box.

---

### Post by nachovr on 2012-05-30
> **SeijiSensei said:**
> [Sendmail]("http://docstore.mik.ua/orelly/networking/tcpip/appe_02.htm") has a command-line switch, "-i", that tells it to ignore embedded dots in messages.  Postfix is supposed to be a drop-in replacement for sendmail, but I don't know whether it supports all sendmail's command-line options.  I'd do a little research on whether Postfix supports this option, or whether it has an equivalent option.  As I recall, you can tell fetchmail what sendmail command string to use to deliver the mail.

If you can't find a way to do this with Postfix, you can consider switching to sendmail as your MTA.  For local delivery, as in your situation, I think it works pretty much out-of-the-box.

Thank you so much. It's been most helpful

Took me a while to find out where to set the "-i" option for sendmail but it has worked perfectly.

In case anyone faces the same issue the option must be set at /etc/postfix/disclaimer  At the end of the file there's this call

$SENDMAIL **-i** "$@" <in.$$

And that's the place to set this option

---

