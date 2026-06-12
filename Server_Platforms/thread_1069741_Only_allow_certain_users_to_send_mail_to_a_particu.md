---
title: "Only allow certain users to send mail to a particular mail id - POSTFIX"
date: 2009-02-14
forum: Server Platforms
---

### Post by rahmath on 2009-02-14
Dear Techies,

I have a postfix server with around 100 users. It is configured with virtual domains. I have created a group mail called "users@our-domain.com" and populate the /etc/postfix/virtual file with all the user names. This will result in sending a mail to "users@our-domain.com" will deliver mail to all the users mentioned in this virtual file (like aliases file)

Now my problem is i need to allow only 5 users to send mail to this "users@our-domain.com". If any other user tried, it should not allow to do so.

Kindly advice me for this problem.

Thanks in advance...

---

