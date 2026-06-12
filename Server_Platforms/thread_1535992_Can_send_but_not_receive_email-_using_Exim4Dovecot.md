---
title: "Can send but not receive email- using Exim4/Dovecot"
date: 2010-07-21
forum: Server Platforms
---

### Post by melville74 on 2010-07-21
Hi- I have set up Ubuntu 10.04 Server with Exim4 and Dovecot. (followed instructions [here]("https://help.ubuntu.com/10.04/serverguide/C/email-services.html"))

I can send email from the command line (**mail tom@anotheremailaddress**) and it works. 

When I try receiving an email sent from an external address, it bounces back and says 
**Reason: Remote SMTP Server Returned: 550 #5.1.0 Address rejected**

One other item that hopefully won't confuse anyone... when I do a commandline mail to myself on the server, it shows a message in the /Maildir/new directory (1279741006.H861133P7444.merlin.mydomainname.org) so I know something is there. But when I enter the mail command and is says no mail for tom.

I am not sure what I'm doing wrong. I am pretty good with computers but feel like a fish out of water here. Firewall is inactive till I can figure out the problem.

Thanks for any help.

---

