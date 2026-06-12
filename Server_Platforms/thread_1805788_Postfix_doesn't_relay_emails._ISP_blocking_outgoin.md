---
title: "Postfix doesn't relay emails. ISP blocking outgoing email?"
date: 2011-07-16
forum: Server Platforms
---

### Post by niglas on 2011-07-16
How can I test if my ISP has blocked outgoing email?

I tried...```
telnet smtp.randomisp.com 587
```...and I obviously a connection was established. Then it's not blocked right?

When I tried to send an email to a gmail-address my logs says:

```
Jul 16 21:02:41 domain postfix/smtp[28857]: initializing the client-side TLS engine
Jul 16 21:03:02 domain postfix/smtp[28857]: connect to gmail-smtp-in.l.google.com[74.125.39.27]:25: Connection timed out
Jul 16 21:03:23 domain postfix/smtp[28857]: connect to alt1.gmail-smtp-in.l.google.com[209.85.225.27]:25: Connection timed out
Jul 16 21:03:44 domain postfix/smtp[28857]: connect to alt2.gmail-smtp-in.l.google.com[74.125.65.27]:25: Connection timed out
Jul 16 21:04:05 domain postfix/smtp[28857]: connect to alt3.gmail-smtp-in.l.google.com[74.125.93.27]:25: Connection timed out
Jul 16 21:04:26 domain postfix/smtp[28857]: connect to alt4.gmail-smtp-in.l.google.com[209.85.143.27]:25: Connection timed out

```These are my first lines in master.cf:

```
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
#smtp      inet  n       -       -       -       -       smtpd
submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING

```Does that uncommented line mean use port 587 for outgoing or incoming email? From the above log it seems to connect to googles servers on port 25.

---

### Post by SeijiSensei on 2011-07-16
Postfix will use SMTP over port 25; I'm guessing that's blocked by your ISP.

Port 587 is the "[mail submission]("http://www.ietf.org/rfc/rfc2476.txt")" port.  It's intended for messages from clients to an SMTP server for further delivery.  Actual exchanges between SMTP servers take place over port 25.

---

### Post by hawkmage on 2011-07-16
The line in the config will make postfix listen in port 587.

If you want postfix to send to your ISPs SMTP server on port 587 you need to look at the "main.cf" you should find an entry in there named relayhost you would update it to something like this:
```
relayhost = [smtp.randomisp.com]:587
```

---

### Post by niglas on 2011-07-17
I'm trying:

```
telnet smtp.myisp.com 25
```But it times out just like:

```
telnet smtp.anotherisp.com 25
```So I guess that means I cannot relay emails to my ISP's smtp nor deliver the emails to their final destination directly. Am I out of luck here or what?

Relaying emails to my ISP's smtp isn't really an alternative in the first place, cause then I might as well fill in my ISP's smtp in the email client, right?

If I got it right, the only workaround possible for this is if I would have an external smtp that listens on another port than 25, and relay it thru that one. But then again my smtp server wouldn't be of any use, cause I could send the emails directly to that server instead.


Please verify my three above reflections...

---

### Post by SeijiSensei on 2011-07-18
> **niglas said:**
> So I guess that means I cannot relay emails to my ISP's smtp nor deliver the emails to their final destination directly. Am I out of luck here or what?

Relaying emails to my ISP's smtp isn't really an alternative in the first place, cause then I might as well fill in my ISP's smtp in the email client, right?

Not necessarily.  It depends on whether the ISP is willing to forward messages from domains other than its own.  However, I suspect the ISP's Terms of Service disallows servers, so they're not going to be very helpful if you're trying to make an end-run around their TOS.

> If I got it right, the only workaround possible for this is if I would have an external smtp that listens on another port than 25, and relay it thru that one. But then again my smtp server wouldn't be of any use, cause I could send the emails directly to that server instead.

Pretty much.  Did you try hawkmage's suggestion of using the ISP's port 587 by editing the relayhost directive?

---

