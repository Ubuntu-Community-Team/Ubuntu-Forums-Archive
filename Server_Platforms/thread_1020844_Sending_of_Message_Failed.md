---
title: "Sending of Message Failed"
date: 2008-12-24
forum: Server Platforms
---

### Post by 451422 on 2008-12-24
I installed 8.10 server a few weeks ago.  Both Thunderbird or Evolution email clients are unable to send email.  They can receive email.  The mail server I use is remote and not used on this server.

The SMTP doesn't work.  There is no firewall / iptables activated. I administrate the remote mail server and have numerous clients retrieving and send email with no problems.  So I know the remote server is fine.  In addition, I have tried another smtp server and receive the same message. 

Any ideas are appreciated.  Attached is the screen shot I receive when mail delivery begins.

Thank you.

---

### Post by eel on 2009-01-09
I have the exact same problem and it kills me because i need to send mail for my work (yeah yeah don't mess with your computer if you need it i know but hey i waited, for the first time, for the official release instead of the beta!)

Did you find any solutions?

---

### Post by eel on 2009-01-09
Solved it!

For some reason the portnr was changed, it was set to 587 which doesn't work but the default 25 works fine here (sweden). Go to your internet company's website and see if they have any tuts or guides or troubleshooting, even if it's for outlook it will basically be the same as for thunderbird. Hope it works for you too!

---

