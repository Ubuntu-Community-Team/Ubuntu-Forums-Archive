---
title: "How do I configure Postfix to send outgoing mail via a relay?"
date: 2013-09-14
forum: Server Platforms
---

### Post by sefs on 2013-09-14
Hi all,

I am using this guide.

[http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/](http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/)

But it is not working for me.  When I check the logs, postfix is trying to send email directly instead of via the relay I configured.
What am I missing.

---

### Post by CharlesA on 2013-09-14
Can you post your main.cf file? It shouldn't be too big.

---

### Post by sefs on 2013-09-14
> **CharlesA said:**
> Can you post your main.cf file? It shouldn't be too big.

Thank you for making me look at that file again to sanitize it before posting.
I discovered that I was setting relayhost early up, but then later down I missed that it was being unset by another relayhost entry that was already there in the default file.  After addressing that outgoing mail was sent, but not as I expected.  When it reached the relay server (gmail) it not only stored the mail in gmail's sent folder but when the mail arrived at the intended recipient the from field was the gmail user!?!?! and not the original user that sent the email. sighs.

---

### Post by CharlesA on 2013-09-14
Ok, then it's working as intended.

What did you want to accomplish?

---

### Post by sefs on 2013-09-14
> **CharlesA said:**
> Ok, then it's working as intended.

What did you want to accomplish? 

Send an email from [email]a@domainX.com[/email] to [email]b@domainY.com[/email], and have it relayed from a to b vis mail.domainZ.com and to arrive at [email]b@domainY.com[/email] with all sender information intact and not the sender information of the relayer.

---

### Post by CharlesA on 2013-09-14
You'd need to set up your own mail server for that.

---

### Post by sefs on 2013-09-14
> **CharlesA said:**
> You'd need to set up your own mail server for that.


domainX is my mailserver.  Do you mean i would have to replace mail.domainZ.com with another mailserver of my creation?

---

### Post by CharlesA on 2013-09-14
Not sure, but the mail server at mail.domainZ.com would need to be setup to allow it to relay mail from domainX.

Otherwise you can just have one mail server send mail for all your domains, if you set it up as such.

---

### Post by sefs on 2013-09-14
My ISP blocks outgoing 25, which is why I was trying with the relay thing.
I think this is special behavior by the big G.  I will have to find another relay server and test.
Thanks.

---

