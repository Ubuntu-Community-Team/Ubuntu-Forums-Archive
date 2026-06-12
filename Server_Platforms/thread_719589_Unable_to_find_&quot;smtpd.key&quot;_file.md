---
title: "Unable to find &quot;smtpd.key&quot; file"
date: 2008-03-09
forum: Server Platforms
---

### Post by sshahir on 2008-03-09
Hi All,

I have installed the Postfix Mail Transfer Agent (MTA) by going through [the Postfix documentation]("https://help.ubuntu.com/7.04/server/C/postfix.html") on my desktop Ubuntu 6.06. I have also gone through the basic configure and  SMTP Authentication sections up to the point the smtpd.key access has to be modified; however, I couldnt find smtpd.key as instructed on the SMTP  section:(. I am wondering where the file is located or maybe I am  missing the smtpd.key.

I appreciate for any comments for suggestions.

Cheers,
sshahir

---

### Post by sshahir on 2008-03-09
I have fixed the issue by going through [the Postfix Ubuntu Wiki documentation]("https://help.ubuntu.com/community/Postfix").

I have installed libsasl2 (Ubuntu 6.06) for SMTP AUTH, but I still couldn't find "/etc/default/saslauthd" as instructions indicate. I am wondering why I am missing the "/etc/default/saslauthd".

I appreciate for any comments for suggestions.

Cheers,
sshahir

---

