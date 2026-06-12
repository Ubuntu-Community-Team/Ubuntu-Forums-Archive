---
title: "Issue with the Postfix Mail Transfer Agent(MTA) installation"
date: 2008-03-09
forum: Server Platforms
---

### Post by sshahir on 2008-03-09
Hi,

I tried to install the Postfix Mail Transfer Agent (MTA) by going through the [Postfix Ubuntu Wiki documentation]("https://help.ubuntu.com/community/Postfix") on my desktop (Ubuntu 6.06). I have  gone through the  configure sections up to the point that a few lines on /etc/default/saslauthd have to be modified. Even though I have installed libsasl2 for SMTP AUTH,  I couldn't find "/etc/default/saslauthd" as mentioned in the instructions. I am wondering why I am missing the "/etc/default/saslauthd".

I appreciate for any comments for suggestions.

Cheers,
sshahir

---

### Post by sshahir on 2008-03-10
I got it. Apparently, I should install SASL packages before trying to modify the saslauthd file.

Thanks,
sshahir

---

