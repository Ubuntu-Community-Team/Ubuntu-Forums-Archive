---
title: "[SOLVED] All in One Printer pop/smtp setup"
date: 2008-07-11
forum: Server Platforms
---

### Post by mbeach on 2008-07-11
I am currently using Google Hosted Domains to give employees mail/docs etc.  Works great for my needs.

I have a Dell 1815dn, which I allows me to email scanned jobs.  I cannot set it up to use a [email]fax@mydomain.com[/email] (account exists fine) because I don't believe the device supports STARTTLS/SSL.  I get a "SMTP Error" on the display.

If I use an email address/pop settings, my ISP provides, it works as expected.  The problem with that is the isp provided email is like [email]faxmydomain@mailserv.myispadvertisement.com[/email].

I think I'm looking for a mail proxy of sorts so I can point the printer to the server, which would subsequently make the pop or imap connection to my google hosted domain email account and send the mail.  This would also allow me to monitor what is being sent via the normal gmail (hosted) account's sent mail.

Would postfix handle this somehow?  Sendmail?  Something even simpler?

---

### Post by HermanAB on 2008-07-11
Hmm, the simplest solution is to install something simple like nullmailer and point it at your ISP mail server, then set the fax server to mail to localhost, which will then be redirected to the ISP through nullmailer:
[http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/)

'Hope that helps!

Cheers,

Herman

---

### Post by mbeach on 2008-07-13
H, thanks for the suggestion.  Over the last day or so I stumbled onto nullmailer as well, but it doesn't appear to support starttls.  I'm still unsuccessfull getting mail to send from the scanner through my server to gmail.  Getting closer though, looking at the estmp package and the instructions at:
[http://esmtp.sourceforge.net/manual.html](http://esmtp.sourceforge.net/manual.html)
Particularly the section:
"Interfacing with particular mail servers"

---

### Post by mbeach on 2008-07-13
ended up more or less following the tutorial listed at:
[http://ubuntuforums.org/showthread.php?t=329294](http://ubuntuforums.org/showthread.php?t=329294)

used postfix for the job.

---

