---
title: "Rackin Frackin Outlook and Dovecot"
date: 2006-07-01
forum: Server Platforms
---

### Post by herald on 2006-07-01
OK, so I know it isn't Outlook's fault (Outlook 2K3 btw), it's my shoddy configuration, but I can't get Outlook to pull from Dovecot.

In the error log, I get a "returned error 89".
I have an idea that this is due to my mail server being on a different network, because when I telnet via the localhost, I can authenticate just fine.  I don't know enough about the pop3 protocol to try and run a full session test, but It feels like a network access issue.  I am probably wrong, but hey...:confused: 

My postfix seems to allow SMTP connections (the standard telnet test to send an email) from the private subnet to the public mail server.

As I said, telnetting to the public hostname address from the host itself will allow me to auth to the pop3 server.

Is there a config setting in Dovecot to specify what subnets hosts are allowed to connect from?
At any rate, any help would be greatly appreciated!

---

